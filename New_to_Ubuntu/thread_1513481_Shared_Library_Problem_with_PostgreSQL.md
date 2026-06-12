---
title: "Shared Library Problem with PostgreSQL"
date: 2010-06-19
forum: New to Ubuntu
---

### Post by humebug on 2010-06-19
I had PostgreSql installed and working on my machine, I was trying to install GeoTypes, but I accidentally got the wrong auto-complete and installed postgresplus-8.4.1-2-linux.bin again, confirming the overlaps.

Now when I try to do anything I get the error message:

/opt/PostgresPlus/8.4SS/bin/psql: error while loading shared libraries: libreadline.so.4: cannot open shared object file: No such file or directory

I have entered

LD_LIBRARY_PATH=/usr/local/pgsql/lib
export LD_LIBRARY_PATH

as suggested in the manual, and altered it to point to the /opt/ where Postgres is.

I don't know what to do. Any suggestions? (even some hints how to uninstall it might help, its not listed as a package or in the add/remove programs))

Thanks!

---

