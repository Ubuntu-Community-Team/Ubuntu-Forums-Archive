---
title: "feisty ldap replication"
date: 2007-06-11
forum: Networking &amp; Wireless
---

### Post by Thearnold on 2007-06-11
I am trying to setup ldap replication between to feisty servers.  I used the following to configure replication from the ubuntu help site: [https://help.ubuntu.com/7.04/server/C/openldap-server.html](https://help.ubuntu.com/7.04/server/C/openldap-server.html).

First off the replog is not getting created in the /var/lib/ldap/replog like the slapd.conf is configured by default. Secondly without the log it is hard to troubleshoot the replication problem.  I did not see any errors in syslog and I setup the log level to 3 in slapd.conf

Here is the master slapd.conf for replication 

replica uri=ldap://hsfnp02.mthcs.net:389 binddn="cn=Manager,dc=mthcs,dc=net" b bindmethod=simple credentials=password

 replogfile     /var/lib/ldap/replog/

Here is the slave slapd.conf for replication

 updatedn       cn=Manager,dc=mthcs,dc=net
 updateref      ldap://hsldap01.mthcs.net
 replogfile     /var/lib/ldap/replog

Any ideas?

Thanks for your help!
TheArnold

---

