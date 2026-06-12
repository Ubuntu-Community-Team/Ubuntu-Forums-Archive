---
title: "Why is my ldap-server not working ?"
date: 2011-02-13
forum: New to Ubuntu
---

### Post by WitchCraft on 2011-02-13
I've installed OpenLDAP, and want to administer it.

When I go to:
```

http://localhost/phpldapadmin/

```

login using this dn:
```

cn=admin,dc=example,dc=local

```

and pw:
```

a123456789A

```


I always get: 
> 
Unable to connect to LDAP server My LDAP Server
Error: Invalid credentials (49) for user


What's the matter?
I can also use slappasswd and enter the hash instead of the plain-text password, and the same thing happens.


root@IS1300-1:/etc/ldap# gedit ldap.conf
```

#
# LDAP Defaults
#

# See ldap.conf(5) for details
# This file should be world readable but not world writable.

#BASE	dc=example,dc=com
BASE    dc=example,dc=local
URI	ldap://127.0.0.1


#URI	ldap://ldap.example.com ldap://ldap-master.example.com:666

#SIZELIMIT	12
#TIMELIMIT	15
#DEREF		never

```

/etc/ldap# gedit slapd.conf
```

# Make sure you edit or add these directives after the first 'database' directive.

suffix          "dc=example,dc=local"
directory       "/var/lib/ldap"
rootdn          "cn=admin,dc=example,dc=local"
rootpw          a123456789A

```

Afterwards I did:
```

/etc/init.d/slapd restart

```


Do I need to do anything else besides editing this 2 files and restarting ?

When I use xplorer, it just says connecting, and then nothing happens at all.

---

### Post by WitchCraft on 2011-02-13
Ah, solved - more or less.

The documentation at:
[https://help.ubuntu.com/community/OpenLDAPServer#Put](https://help.ubuntu.com/community/OpenLDAPServer#Put) your LDAP server to use
is out of date


Used this instead:
[https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html](https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html)

---

