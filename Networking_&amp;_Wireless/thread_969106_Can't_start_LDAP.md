---
title: "Can't start LDAP"
date: 2008-11-03
forum: Networking &amp; Wireless
---

### Post by slong501 on 2008-11-03
Hi, I've been following a guide to setup Ubuntu Server 8.04 as a domain controller and part of it requires LDAP, I haven't been able to start it through webmin i just get.
```
Starting OpenLDAP: slapd - failed.
The operation failed but no output was produced. For hints on what went
wrong please refer to the system's logfiles (e.g. /var/log/syslog) or
try running the daemon in Debug mode like via "slapd -d 16383" (warning:
this will create copious output).

Below, you can find the command line options used by this script to 
run slapd. Do not forget to specify those options if you
want to look to debugging output:
  slapd -g openldap -u openldap -f /etc/ldap/slapd.conf 

```
And when i try to start it in the console of the server i get.

```
Starting OpenLDAP: slapd - failed.
The operation failed but no output was produced. For hints on what went
wrong please refer to the system's logfiles (e.g. /var/log/syslog) or
try running the daemon in Debug mode like via "slapd -d 16383" (warning:
this will create copious output).

Below, you can find the command line options used by this script to
run slapd. Do not forget to specify those options if you
want to look to debugging output:
  slapd -g openldap -u openldap -f /etc/ldap/slapd.conf

```

I'm not a pro at Linux and help would be much appreciated

---

### Post by liemoffline on 2009-08-11
> **slong501 said:**
> Hi, I've been following a guide to setup Ubuntu Server 8.04 as a domain controller and part of it requires LDAP, I haven't been able to start it through webmin i just get.
```
Starting OpenLDAP: slapd - failed.
The operation failed but no output was produced. For hints on what went
wrong please refer to the system's logfiles (e.g. /var/log/syslog) or
try running the daemon in Debug mode like via "slapd -d 16383" (warning:
this will create copious output).

Below, you can find the command line options used by this script to 
run slapd. Do not forget to specify those options if you
want to look to debugging output:
  slapd -g openldap -u openldap -f /etc/ldap/slapd.conf 

```
And when i try to start it in the console of the server i get.

```
Starting OpenLDAP: slapd - failed.
The operation failed but no output was produced. For hints on what went
wrong please refer to the system's logfiles (e.g. /var/log/syslog) or
try running the daemon in Debug mode like via "slapd -d 16383" (warning:
this will create copious output).

Below, you can find the command line options used by this script to
run slapd. Do not forget to specify those options if you
want to look to debugging output:
  slapd -g openldap -u openldap -f /etc/ldap/slapd.conf

```

I'm not a pro at Linux and help would be much appreciated

Me, Too! Please help!
When I use nmap localhost
ldap port not running 
Why?
How to solve?
Thanks!

---

