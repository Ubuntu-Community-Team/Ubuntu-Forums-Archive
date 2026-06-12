---
title: "pam ldap setup,pam_ldap: ldap_initialize Time limit exceeded"
date: 2008-09-04
forum: Networking &amp; Wireless
---

### Post by henrikm85 on 2008-09-04
Hi. I've set up a server with an ldap directory. It's filled with data and stuff like su, id <username> etc. on the clients works just fine. But when I try to ssh into the machine I keep getting 

> pam_ldap: ldap_initialize Time limit exceeded


as the only message in auth.log. Also, the client connects to the ldap server (which is openldap  / slapd) and requests stuff:

> Sep  4 06:56:08 (none) slapd[6603]: conn=177287 fd=19 ACCEPT from IP=10.254.199.225:42775 (IP=0.0.0.0:389) 
Sep  4 06:56:08 (none) slapd[6603]: conn=177287 op=0 BIND dn="cn=admin,dc=cloud,dc=openbig,dc=org" method=128 
Sep  4 06:56:08 (none) slapd[6603]: conn=177287 op=0 BIND dn="cn=admin,dc=cloud,dc=openbig,dc=org" mech=SIMPLE ssf=0 
Sep  4 06:56:08 (none) slapd[6603]: conn=177287 op=0 RESULT tag=97 err=0 text= 
Sep  4 06:56:08 (none) slapd[6603]: conn=177287 op=1 SRCH base="ou=People,dc=cloud,dc=openbig,dc=org" scope=2 deref=0 filter="(&(objectClass=posixAccount)(uid=henrik))" 
Sep  4 06:56:08 (none) slapd[6603]: conn=177287 op=1 SRCH attr=uid userPassword uidNumber gidNumber cn homeDirectory loginShell gecos description objectClass 
Sep  4 06:56:08 (none) slapd[6603]: conn=177287 op=1 SEARCH RESULT tag=101 err=0 nentries=1 text= 
Sep  4 06:56:08 (none) slapd[6603]: conn=177287 op=2 SRCH base="ou=People,dc=cloud,dc=openbig,dc=org" scope=2 deref=0 filter="(&(objectClass=posixAccount)(uid=henrik))" 
Sep  4 06:56:08 (none) slapd[6603]: conn=177287 op=2 SEARCH RESULT tag=101 err=0 nentries=1 text= 
Sep  4 06:56:08 (none) slapd[6603]: conn=177287 op=3 SRCH base="ou=Group,dc=cloud,dc=openbig,dc=org" scope=2 deref=0 filter="(&(objectClass=posixGroup)(|(memberUid=henrik)(uniqueMember=uid=henrik,ou=people,dc=cloud,dc=openbig,dc=org)))" 
Sep  4 06:56:08 (none) slapd[6603]: conn=177287 op=3 SRCH attr=gidNumber 
Sep  4 06:56:08 (none) slapd[6603]: conn=177287 op=3 SEARCH RESULT tag=101 err=0 nentries=0 text= 

I've been googling a lot and can't really figure out what's wrong. I'd really apreciate some pointers as I have no idea on how to proceed. If you need any more information feel free to ask I'll get it for you asap :(

Henrik

---

