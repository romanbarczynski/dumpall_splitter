PostgreSQL pg_dumpall SQL backup files splitter
===============================================

* Works ONLY with SQL structure & data dumps.
* Reads SQL from STDIN, creates `.sql.bz2` files in CURRENT DIRECTORY.

Usage
-----

`bzcat dump.sql.bz2 | dumpall_splitter`

`dumpall_splitter < dump.sql`


Files
-----

New files are created for:

- pg_roles,
- every database structure,
- every database data (multiple, with ~ 500 MB limit),

File names are created in a way that `ls|sort` will order it correctly for restore with `psql`:

`ls |sort |grep 'database' |xargs bzcat |psql database`

this way your SQL statements are executed in exact order as they would be from one file backup.
