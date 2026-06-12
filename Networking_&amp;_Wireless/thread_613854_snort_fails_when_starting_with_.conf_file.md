---
title: "snort fails when starting with .conf file"
date: 2007-11-15
forum: Networking &amp; Wireless
---

### Post by fkbandyk on 2007-11-15
I'm a first time user of snort and want to log to a mysql database. I have snort installed and it will run. I have mysql installed and the database set up with tables generated with create_mysql. When I try to start snort with "sudo snort -c /etc/snort/snort.conf" I get an error message "ERROR: Undefined variable name: (/etc/snort/snort.conf:797): ".
That line looks like this "output database: log, mysql, user=snort password=mypassword dbname=snort host=localhost".

I have done this install once before using djhedges "how to" and it worked great that time but now I need to set it up on a work machine and I'm stuck here. Any ideas?

---

### Post by jba6511 on 2008-04-14
sorry for diggin up an old thread but I am getting the same error on the same line. Any resolution? My variables should be fine as I can log in as the snort user with the defined password, view the snort database and see all of the tables.

---

