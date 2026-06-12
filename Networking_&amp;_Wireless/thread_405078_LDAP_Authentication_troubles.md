---
title: "LDAP Authentication troubles"
date: 2007-04-09
forum: Networking &amp; Wireless
---

### Post by mopok on 2007-04-09
Hello. I'm experiensing troubles while trying to set up my Ubuntu Dapper box to authenticate users using Kerberos+ldap sheme from Active Directory. I've set up Kerberos and I can successfully obtain kerberos tickets using kinit. Now I'm trying to get user information from my Windows 2003 R2 PDC using ldap. The libnss-ldap.conf file looks like this:

host 192.168.0.252
base dc=mydomain,dc=local
uri ldap://mypdc.mydomain.local/
binddn [email]linuxproxy@mydomain.loca[/email]l
bindpw password
scope sub
ssl no
nss_base_passwd cn=Users,dc=mydomain,dc=local?sub
nss_base_shadow cn=Users,dc=mydomain,dc=local?sub
nss_base_group cn=Users,dc=mydomain,dc=local?sub?&(objectCategory =group)(gidnumb$
nss_map_objectclass posixAccount user
nss_map_objectclass shadowAccount user
nss_map_objectclass posixGroup group
nss_map_attribute gecos cn
nss_map_attribute homeDirectory unixHomeDirectory
nss_map_attribute uniqueMember member

Here is my nsswitch.conf file:

passwd:         compat ldap
group:          compat ldap
shadow:         compat ldap

hosts:          files dns mdns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

This files were taken from this tutorial:
[http://blog.scottlowe.org/2007/01/15...ion-version-4/](http://blog.scottlowe.org/2007/01/15...ion-version-4/)

Also I've tried to use this tutorial:
[http://developer.novell.com/wiki/ind...the](http://developer.novell.com/wiki/ind...the) ntication

And this one:
[https://help.ubuntu.com/community/ActiveDirectoryHowto](https://help.ubuntu.com/community/ActiveDirectoryHowto)

And the result was the same: I can't get information from AD using 'getent passwd' command. What am I doing wrong?

---

