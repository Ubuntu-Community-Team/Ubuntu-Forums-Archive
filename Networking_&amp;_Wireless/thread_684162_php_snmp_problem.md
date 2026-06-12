---
title: "php snmp problem"
date: 2008-01-31
forum: Networking &amp; Wireless
---

### Post by superbo8218 on 2008-01-31
HI,

i have problem with snmp support in php5 on ubuntu 7.10 gutsy server:

i have installed snmp, snmpd and php5-snmp packages;

snmp works from shell command line but when i try to use it from php it gives me:

Fatal error: Call to undefined function snmpget() in /path/to/file/snmp.php on line 2

where line 2 is like: $a = snmpget(.......)

the php refernce manual says that i should uncomment something in the ucd-snmp config.h but i dont have ucd-snmp under /usr/include where it should be. i think that ucd-snmp is the older version of net-snmp that i have installed

PLEASE HELP :( :confused:

---

### Post by superbo8218 on 2008-01-31
sorry, this was really stupid from me:

just restarted apache and it works fine

:D

---

