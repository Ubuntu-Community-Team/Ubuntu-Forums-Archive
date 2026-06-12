---
title: "LDAP help..."
date: 2007-11-30
forum: Networking &amp; Wireless
---

### Post by XtremeGamer99 on 2007-11-30
I'm trying to install a server that would allow me to store users and home directories on a server, and have the client log in from the client machine. I've looked around, and I was going to use NIS+ until I found out that it was unsupported and LDAP was recommended. Now I'm trying to look into LDAP, yet it got way to confusing really fast.

What I'm trying to do is add users to the server. When they are added, the users can use client machines to log in using the usernames and passwords on the server, and the server will send their home directory so that the client machine can mount it so that the users can work on their own files. That's the gist of what I'm trying to do; I have no idea if that's enough info to get any help. So if you need more information (network set-up, etc.), tell me and I'll do my best to provide it. =)

What do I need to install? I hate installing from source, because it never works for me, so packages are best. After I install everything, what will I need to edit on the server and client machines for them to work with each other in sending and mounting home directories and authentication. What do I do?

Thanks a bunch!

---

### Post by XtremeGamer99 on 2007-12-02
bump...

---

### Post by gpredrag on 2007-12-02
Try
[https://help.ubuntu.com/community/OpenLDAPServer](https://help.ubuntu.com/community/OpenLDAPServer)
and
[https://help.ubuntu.com/community/LDAPClientAuthentication](https://help.ubuntu.com/community/LDAPClientAuthentication)
and then come here for more :)

---

### Post by XtremeGamer99 on 2007-12-18
I followed the first link, and I'm stuck on the installation. The wiki's description of the configuration and installation does not match what's happening on my screen.

I installed these components and any packages loaded with them:[LIST]
[*]slapd
[*]ldap-utils
[*]db4.2-util
[/LIST]

When i installed slapd, it asked me for a admin username and password. I just left it blank for now (I don't know what it's used for at the moment) and it continued to install the package. I noticed that there was a lot of ALSA lib errors, whatever those are, but it started nonetheless.

I'm at this part in the wiki:
```
# Make sure you edit or add these directives after the first 'database' directive.

suffix          "dc=example,dc=com"
directory       "/var/lib/ldap"
rootdn          "cn=admin,dc=example,dc=com"
rootpw          {SSHA}d2BamRTgBuhC6SxC0vFGWol31ki8iq5m
```

and I don't know where to put that in /etc/ldap/slapd.conf.

This is my current configuration file, untouched:
```
# This is the main slapd configuration file. See slapd.conf(5) for more
# info on the configuration options.

#######################################################################
# Global Directives:

# Features to permit
#allow bind_v2

# Schema and objectClass definitions
include         /etc/ldap/schema/core.schema
include         /etc/ldap/schema/cosine.schema
include         /etc/ldap/schema/nis.schema
include         /etc/ldap/schema/inetorgperson.schema

# Where the pid file is put. The init.d script
# will not stop the server if you change this.
pidfile         /var/run/slapd/slapd.pid

# List of arguments that were passed to the server
argsfile        /var/run/slapd/slapd.args

# Read slapd.conf(5) for possible values
loglevel        0

# Where the dynamically loaded modules are stored
modulepath	/usr/lib/ldap
moduleload	back_bdb

# The maximum number of entries that is returned for a search operation
sizelimit 500

# The tool-threads parameter sets the actual amount of cpu's that is used
# for indexing.
tool-threads 1

#######################################################################
# Specific Backend Directives for bdb:
# Backend specific directives apply to this backend until another
# 'backend' directive occurs
backend		bdb
checkpoint 512 30

#######################################################################
# Specific Backend Directives for 'other':
# Backend specific directives apply to this backend until another
# 'backend' directive occurs
#backend		<other>

#######################################################################
# Specific Directives for database #1, of type bdb:
# Database specific directives apply to this databasse until another
# 'database' directive occurs
database        bdb

# The base of your directory in database #1
suffix          "dc=nodomain"

# rootdn directive for specifying a superuser on the database. This is needed
# for syncrepl.
# rootdn          "cn=admin,dc=nodomain"

# Where the database file are physically stored for database #1
directory       "/var/lib/ldap"

# For the Debian package we use 2MB as default but be sure to update this
# value if you have plenty of RAM
dbconfig set_cachesize 0 2097152 0

# Sven Hartge reported that he had to set this value incredibly high
# to get slapd running at all. See http://bugs.debian.org/303057
# for more information.

# Number of objects that can be locked at the same time.
dbconfig set_lk_max_objects 1500
# Number of locks (both requested and granted)
dbconfig set_lk_max_locks 1500
# Number of lockers
dbconfig set_lk_max_lockers 1500

# Indexing options for database #1
index           objectClass eq

# Save the time that the entry gets modified, for database #1
lastmod         on

# Where to store the replica logs for database #1
# replogfile	/var/lib/ldap/replog

# The userPassword by default can be changed
# by the entry owning it if they are authenticated.
# Others should not be able to see it, except the
# admin entry below
# These access lines apply to database #1 only
access to attrs=userPassword,shadowLastChange
        by dn="cn=admin,dc=nodomain" write
        by anonymous auth
        by self write
        by * none

# Ensure read access to the base for things like
# supportedSASLMechanisms.  Without this you may
# have problems with SASL not knowing what
# mechanisms are available and the like.
# Note that this is covered by the 'access to *'
# ACL below too but if you change that as people
# are wont to do you'll still need this if you
# want SASL (and possible other things) to work 
# happily.
access to dn.base="" by * read

# The admin dn has full write access, everyone else
# can read everything.
access to *
        by dn="cn=admin,dc=nodomain" write
        by * read

# For Netscape Roaming support, each user gets a roaming
# profile for which they have write access to
#access to dn=".*,ou=Roaming,o=morsnet"
#        by dn="cn=admin,dc=nodomain" write
#        by dnattr=owner write

#######################################################################
# Specific Directives for database #2, of type 'other' (can be bdb too):
# Database specific directives apply to this databasse until another
# 'database' directive occurs
#database        <other>

# The base of your directory for database #2
#suffix		"dc=debian,dc=org"
```

So, where exactly do I enter stuff?

Thanks!

---

### Post by XtremeGamer99 on 2008-01-04
Okay... I've gotten to this point:

> add the new content sudo slapadd -l init.ldif

But, when I execute that command, it gives me this error:
slapadd: line 6: database (dc=nodomain) not configured to hold "dc=example,dc=com"
slapadd: line 6: database (dc=nodomain) not configured to hold "dc=example,dc=com"

I don't understand what this means...

Here's my slapd.conf. I stuck with all the defaults from the wiki page, and haven't really changed anything:

```
# This is the main slapd configuration file. See slapd.conf(5) for more
# info on the configuration options.

#######################################################################
# Global Directives:

# Features to permit
#allow bind_v2

# Schema and objectClass definitions
include         /etc/ldap/schema/core.schema
include         /etc/ldap/schema/cosine.schema
include         /etc/ldap/schema/nis.schema
include         /etc/ldap/schema/inetorgperson.schema

# Where the pid file is put. The init.d script
# will not stop the server if you change this.
pidfile         /var/run/slapd/slapd.pid

# List of arguments that were passed to the server
argsfile        /var/run/slapd/slapd.args

# Read slapd.conf(5) for possible values
loglevel        0

# Where the dynamically loaded modules are stored
modulepath	/usr/lib/ldap
moduleload	back_bdb

# The maximum number of entries that is returned for a search operation
sizelimit 500

# The tool-threads parameter sets the actual amount of cpu's that is used
# for indexing.
tool-threads 1

#######################################################################
# Specific Backend Directives for bdb:
# Backend specific directives apply to this backend until another
# 'backend' directive occurs
backend		bdb
checkpoint 512 30

#######################################################################
# Specific Backend Directives for 'other':
# Backend specific directives apply to this backend until another
# 'backend' directive occurs
# backend		bdb

#######################################################################
# Specific Directives for database #1, of type bdb:
# Database specific directives apply to this databasse until another
# 'database' directive occurs
database        bdb

# The base of your directory in database #1
suffix          "dc=nodomain"

# rootdn directive for specifying a superuser on the database. This is needed
# for syncrepl.
# rootdn          "cn=admin,dc=nodomain"

# Where the database file are physically stored for database #1
directory       "/var/lib/ldap"

# For the Debian package we use 2MB as default but be sure to update this
# value if you have plenty of RAM
dbconfig set_cachesize 0 2097152 0

# Sven Hartge reported that he had to set this value incredibly high
# to get slapd running at all. See http://bugs.debian.org/303057
# for more information.

# Number of objects that can be locked at the same time.
dbconfig set_lk_max_objects 1500
# Number of locks (both requested and granted)
dbconfig set_lk_max_locks 1500
# Number of lockers
dbconfig set_lk_max_lockers 1500

# Indexing options for database #1
index           objectClass eq

# Save the time that the entry gets modified, for database #1
lastmod         on

# Where to store the replica logs for database #1
# replogfile	/var/lib/ldap/replog

# The userPassword by default can be changed
# by the entry owning it if they are authenticated.
# Others should not be able to see it, except the
# admin entry below
# These access lines apply to database #1 only
access to attrs=userPassword,shadowLastChange
        by dn="cn=admin,dc=nodomain" write
        by anonymous auth
        by self write
        by * none

# Ensure read access to the base for things like
# supportedSASLMechanisms.  Without this you may
# have problems with SASL not knowing what
# mechanisms are available and the like.
# Note that this is covered by the 'access to *'
# ACL below too but if you change that as people
# are wont to do you'll still need this if you
# want SASL (and possible other things) to work 
# happily.
access to dn.base="" by * read

# The admin dn has full write access, everyone else
# can read everything.
access to *
        by dn="cn=admin,dc=nodomain" write
        by * read

# For Netscape Roaming support, each user gets a roaming
# profile for which they have write access to
#access to dn=".*,ou=Roaming,o=morsnet"
#        by dn="cn=admin,dc=nodomain" write
#        by dnattr=owner write

#######################################################################
# Specific Directives for database #2, of type 'other' (can be bdb too):
# Database specific directives apply to this databasse until another
# 'database' directive occurs
database        bdb

# The base of your directory for database #2
#suffix		"dc=debian,dc=org"

# Make sure you edit or add these directives after the first 'database' directive.

suffix          "dc=example,dc=com"
directory       "/var/lib/ldap"
rootdn          "cn=admin,dc=example,dc=com"
rootpw          {SSHA}rm43Jb3lHp4zv2kvSEdyL3Wa3ZHGIaZt
```

My lapd.conf:
```
BASE    dc=nodomain
BASE	dc=example,dc=com
```

And my init.ldif:
```
dn: dc=example,dc=com
objectClass: dcObject
objectClass: organizationalUnit
dc: example
ou: Example Dot Com

dn: cn=admin,dc=example,dc=com
objectClass: simpleSecurityObject
objectClass: organizationalRole
cn: admin
description: LDAP administrator
userPassword: {SSHA}I9zjZgmRLMBDYGmd2D/yJYI6fDZpVjUD

dn: ou=people,dc=example,dc=com
objectClass: organizationalUnit
ou: people

dn: ou=groups,dc=example,dc=com
objectClass: organizationalUnit
ou: groups

dn: uid=lionel,ou=people,dc=example,dc=com
objectClass: inetOrgPerson
objectClass: posixAccount
objectClass: shadowAccount
uid: lionel
sn: Porcheron
givenName: Lionel
cn: Lionel Porcheron
displayName: Lionel Porcheron
uidNumber: 1000
gidNumber: 10000
userPassword: {SSHA}wi5/EfE7Csb3UDnZLnVeGWqlPCaljUPn
gecos: Lionel Porcheron
loginShell: /bin/bash
homeDirectory: /home/lionel
shadowExpire: -1
shadowFlag: 0
shadowWarning: 7
shadowMin: 8
shadowMax: 999999
shadowLastChange: 10877
mail: lionel.porcheron@example.com
postalCode: 31000
l: Toulouse
o: Example
mobile: +33 (0)6 xx xx xx xx
homePhone: +33 (0)5 xx xx xx xx
title: System Administrator
postalAddress:
initials: LP

dn: cn=example,ou=groups,dc=example,dc=com
objectClass: posixGroup
cn: example
gidNumber: 10000
```

---

### Post by XtremeGamer99 on 2008-01-07
Anyone?

---

### Post by XtremeGamer99 on 2008-01-13
*bump*

---

### Post by Despot on 2008-01-13
The problem you've got is caused by mixing suffixes: you've got "dc=nodomain" and "dc=example,dc=com" going at the same time. You'll want to replace all occurances of the second with the first in the file you're feeding into slapadd.

I found this discussion of how LDAP represents its data to be helpful, perhaps it will help you as well:

[http://www.zytrax.com/books/ldap/ch2/index.html#model]("http://www.zytrax.com/books/ldap/ch2/index.html#model")

---

### Post by XtremeGamer99 on 2008-01-14
So, in lamest terms, replace all the 'dc=example,dc=com' with 'dc=nodomain' in the init.ldif file?

I'll try that tomorrow when I get access to the server again.

One question, though. What was the point of me adding
```
suffix          "dc=example,dc=com"
directory       "/var/lib/ldap"
rootdn          "cn=admin,dc=example,dc=com"
rootpw          {SSHA}rm43Jb3lHp4zv2kvSEdyL3Wa3ZHGIaZt
```
to the config file if I can't use 'example.com'? Or should I have replaced everything within the first database with the above, keeping it 'nodomain'? I'm so confused when it comes to this stuff. :confused:

Thanks for the link though. I'll look through it tonight. :)

---

### Post by HornedBeast on 2008-01-29
[http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760)

This guide here should do EXACTLY what your asking for.

I've been trying the same thing for a long time and found this. I suggest reading the entire thread too, as you may come up against some issues other people have.

Seems to work like a charm though.

---

### Post by rickyjones on 2008-01-29
> **HornedBeast said:**
> [http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760)

This guide here should do EXACTLY what your asking for.

I've been trying the same thing for a long time and found this. I suggest reading the entire thread too, as you may come up against some issues other people have.

Seems to work like a charm though.

Yes, this guide will do what you want to do. It will allow LDAP authentication for clients and the clients will use NFS to mount their home drives.

-Richard

---

