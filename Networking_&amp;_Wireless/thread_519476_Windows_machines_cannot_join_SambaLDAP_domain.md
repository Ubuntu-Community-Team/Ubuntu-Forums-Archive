---
title: "Windows machines cannot join Samba/LDAP domain"
date: 2007-08-07
forum: Networking &amp; Wireless
---

### Post by Peque on 2007-08-07
Hey Guys. 

I have followed this guide for making a SAMBA/LDAP server: [http://www.nomis52.net/?section=docs&page=samldap](http://www.nomis52.net/?section=docs&page=samldap)

And everything working from Unix - I'm able to login, from Unix - But when I want to add a windows machine to the domain - I fails .

Not sure if the problems are here - But in the guide following he's howto - He´s using PHPLDAPADMIN 0.9.4 - and when making hes samba group mapping account - He could set them as SAMBASID-{NUMBERS)-Domain Admins etc - THis is not possivble in the phpldapadmin 0.9.8.3 as I use from package archive - So is there anything that's is totally wrong here - or Am I doing something wrong. 

I remember something about windows not liking the valadation of en connections - but what am I missing here : 

My different conf files_
```

Load smb config files from /etc/samba/smb.conf
Processing section "[netlogon]"
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
WARNING: passdb expand explicit = yes is deprecated
Server role: ROLE_DOMAIN_PDC
Press enter to see a dump of your service definitions

[global]
        workgroup = INSATECH
        server string = LOKE (Samba, Ubuntu)
        obey pam restrictions = Yes
        passdb backend = ldapsam:ldap://127.0.0.1
        enable privileges = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
        syslog = 10
        log file = /var/log/samba/log.%m
        max log size = 1000
        load printers = No
        add machine script = /etc/smbldaptools/smbldap-useradd -w "%u"
        logon script = logon.bat
        domain logons = Yes
        os level = 255
        preferred master = Yes
        dns proxy = No
        wins server = 192.168.2.7
        ldap admin dn = cn=admin,dc=insatech,dc=com
        ldap group suffix = ou=groups
        ldap machine suffix = ou=machines
        ldap passwd sync = Yes
        ldap suffix = dc=insatech,dc=com
        ldap user suffix = ou=users
        panic action = /usr/share/samba/panic-action %d
        invalid users = root

[netlogon]
        comment = Network Logon Service
        path = /data/samba/netlogon
        write list = @admins
        guest ok = Yes

[printers]
        comment = All Printers
        path = /tmp
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers


```

slapd.conf
```

# This is the main slapd configuration file. See slapd.conf(5) for more
# info on the configuration options.

#######################################################################
# Global Directives:

# Features to permit
allow bind_v2

# Schema and objectClass definitions
include         /etc/ldap/schema/core.schema
include         /etc/ldap/schema/cosine.schema
include         /etc/ldap/schema/nis.schema
include         /etc/ldap/schema/inetorgperson.schema
include         /etc/ldap/schema/samba.schema

# Schema check allows for forcing entries to
# match schemas for their objectClasses's
schemacheck     on

# Where the pid file is put. The init.d script
# will not stop the server if you change this.
pidfile         /var/run/slapd/slapd.pid

# List of arguments that were passed to the server
argsfile        /var/run/slapd.args

# Read slapd.conf(5) for possible values
loglevel        296

# Where the dynamically loaded modules are stored
modulepath      /usr/lib/ldap
moduleload      back_bdb

#######################################################################
# SSL:
# Uncomment the following lines to enable SSL and use the default
# snakeoil certificates.
# TLSCertificateFile      /etc/ldap/slapd-cert.crt
# TLSCertificateKeyFile   /etc/ldap/slapd-key.pem

#######################################################################
# Specific Backend Directives for bdb:
# Backend specific directives apply to this backend until another
# 'backend' directive occurs
backend         bdb
checkpoint 512 30

#######################################################################
# Specific Backend Directives for 'other':
# Backend specific directives apply to this backend until another
# 'backend' directive occurs
#backend                <other>

#######################################################################
# Specific Directives for database #1, of type bdb:
# Database specific directives apply to this databasse until another
# 'database' directive occurs
database        bdb

# The base of your directory in database #1
suffix          "dc=insatech,dc=com"
rootdn          "cn=admin,dc=insatech,dc=com"
rootpw          {MD5}fqEqSm6wTt9vo+/tj5Ej4Z==

# Where the database file are physically stored for database #1
directory       "/var/lib/ldap"

# Indexing options for database #1
index           objectClass eq

# Save the time that the entry gets modified, for database #1
lastmod         on

# Where to store the replica logs for database #1
# replogfile    /var/lib/ldap/replog

# The userPassword by default can be changed
# by the entry owning it if they are authenticated.
# Others should not be able to see it, except the
# admin entry below
# These access lines apply to database #1 only
access to attrs=userPassword
        by dn="cn=admin,dc=insatech,dc=com" write
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
        by dn="cn=admin,dc=insatech,dc=com" write
        by * read

# For Netscape Roaming support, each user gets a roaming
# profile for which they have write access to
#access to dn=".*,ou=Roaming,o=morsnet"
#        by dn="cn=admin,dc=insatech,dc=com" write
#        by dnattr=owner write

#######################################################################
# Specific Directives for database #2, of type 'other' (can be bdb too):
# Database specific directives apply to this databasse until another
# 'database' directive occurs
#database        <other>

# The base of your directory for database #2
#suffix         "dc=debian,dc=org"


```

Are ther e any smart peopole - that have this to work and can give an answer for what I'm missing/doing wrong - thanks !

---

