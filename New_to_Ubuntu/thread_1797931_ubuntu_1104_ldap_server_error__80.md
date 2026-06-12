---
title: "ubuntu 1104 ldap server error  80"
date: 2011-07-05
forum: New to Ubuntu
---

### Post by lance bermudez on 2011-07-05
reflowing guid at [http://tuxnetworks.blogspot.com/2010/07/howto-samba-ldap-on-1004-lucid-short.html](http://tuxnetworks.blogspot.com/2010/07/howto-samba-ldap-on-1004-lucid-short.html)

only change i mad is dc=lbermudez,dc=net
to match my stuff. I'm creating a new database as in their is no prier database. every thing should be new.

lance@Therese:~$ sudo ldapadd -Y EXTERNAL -H ldapi:/// -f ~/backend.ldif
SASL/EXTERNAL authentication started
SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
SASL SSF: 0
adding new entry "cn=module,cn=config"
ldap_add: Other (e.g., implementation specific) error (80)
	additional info: <olcModuleLoad> handler exited with 1

---

### Post by lance bermudez on 2011-07-05
what is in the ldif file
# Load dynamic backend modules
dn: cn=module,cn=config
objectClass: olcModuleList
cn: module
olcModulepath: /usr/lib/ldap
olcModuleload: back_hdb

# Database settings
dn: olcDatabase=hdb,cn=config
objectClass: olcDatabaseConfig
objectClass: olcHdbConfig
olcDatabase: {1}hdb
olcSuffix: dc=lbermudez,dc=net
olcDbDirectory: /var/lib/ldap
olcRootDN: cn=admin,dc=lbermudez,dc=net
olcRootPW: luminous
olcDbConfig: set_cachesize 0 2097152 0
olcDbConfig: set_lk_max_objects 1500
olcDbConfig: set_lk_max_locks 1500
olcDbConfig: set_lk_max_lockers 1500
olcDbIndex: objectClass eq
olcLastMod: TRUE
olcDbCheckpoint: 512 30
olcAccess: to attrs=userPassword by dn="cn=admin,dc=lbermudez,dc=net" write by anonymous auth by self write by * none
olcAccess: to attrs=shadowLastChange by self write by * read
olcAccess: to dn.base="" by * read
olcAccess: to * by dn="cn=admin,dc=lbermudez,dc=net" write by * read

---

### Post by luvshines on 2011-07-06
Maybe the following entry in ldif file is causing this```
olcDatabase: {1}hdb
```

Try removing the {1} from there

---

### Post by wojtek.bogusz on 2011-07-25
hi, i have exactly the same problem :(
lance did you solve yours? 

luvshines, i did try to remove "{1}" but it does not help. i don't think it should be removed. few tutorials have this in.

i have no idea why ldap has to be so unhumanly complicated ;)

help!

---

### Post by luvshines on 2011-07-26
I think I got carried away with some other thoughts while making earlier comment :)

Maybe this launchpad bug points to same behavior you are observing:[https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/677998]("https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/677998")

See if that fix helps

---

### Post by wojtek.bogusz on 2011-07-26
thank you luvshines U R * :) it works!

---

### Post by jwxie on 2013-01-10
I also encountered this error. The fix provided from the launchpad works!

Just modify old backend ldif as suggested.

):P

---

