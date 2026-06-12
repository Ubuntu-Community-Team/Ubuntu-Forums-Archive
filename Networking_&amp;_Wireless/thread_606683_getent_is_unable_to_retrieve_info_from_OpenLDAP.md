---
title: "getent is unable to retrieve info from OpenLDAP"
date: 2007-11-08
forum: Networking &amp; Wireless
---

### Post by mesh2005 on 2007-11-08
I setup Kerberos & OpenLDAP successfully on my server "Ubuntu 6.06" (called machine1). I can successfully kinit & ldapsearch from another machine (machine2). I'm using ldaps only and a self-signed certificate. The problem is, I disabled the simple bind, all users have to use -Y GSSAPI to query the LDAP database. This works fine with ldap tools but unfortunately it does not with getent.

Without a ticket, the getent is unable to establish a connection to my LDAP server, here is the log:
Nov  8 14:07:21 machine2 getent: GSSAPI Error: Miscellaneous failure (Unknown code krb5 195)
Nov  8 14:07:21 machine2 getent: nss_ldap: failed to bind to LDAP server ldaps://machine1: Local error
Nov  8 14:07:21 machine2 getent: nss_ldap: could not search LDAP server - Server is unavailable

If I create a ticket using one of the principals (e.g. mesh), getent can successfully establish connection; however, it is still unable to get any info, it always returns blank. Here is the log (slapd):
Nov  8 14:20:00 machine1 slapd[2004]: SASL proxy authorize [conn=80]: authcid="mesh" authzid="mesh"
Nov  8 14:20:00 machine1 slapd[2004]: connection_get(10)
Nov  8 14:20:00 machine1 slapd[2004]: SRCH "ou=People,dc=mydomain,dc=com" 2 0
Nov  8 14:20:00 machine1 slapd[2004]:     0 0 0
Nov  8 14:20:00 machine1 slapd[2004]:     filter: (objectClass=posixAccount)
Nov  8 14:20:00 machine1 slapd[2004]:     attrs:
Nov  8 14:20:00 machine1 slapd[2004]:  uid
Nov  8 14:20:00 machine1 slapd[2004]:  userPassword
Nov  8 14:20:00 machine1 slapd[2004]:  uidNumber
Nov  8 14:20:00 machine1 slapd[2004]:  gidNumber
Nov  8 14:20:00 machine1 slapd[2004]:  cn
Nov  8 14:20:00 machine1 slapd[2004]:  homeDirectory
Nov  8 14:20:00 machine1 slapd[2004]:  loginShell
Nov  8 14:20:00 machine1 slapd[2004]:  gecos
Nov  8 14:20:00 machine1 slapd[2004]:  description
Nov  8 14:20:00 machine1 slapd[2004]:  objectClass
Nov  8 14:20:00 machine1 slapd[2004]:
Nov  8 14:20:00 machine1 slapd[2004]: send_ldap_result: err=10 matched="" text=""
Nov  8 14:20:00 machine1 slapd[2004]: connection_get(10)

I added ldap to my nsswitch.conf and here is /etc/libnss_ldap.conf:
base dc=mydomain,dc=com
uri ldaps://machine1
ldap_version 3
nss_base_passwd ou=People,dc=mydomain,dc=com
nss_base_shadow ou=People,dc=mydomain,dc=com
nss_base_group  ou=Group,dc=mydomain,dc=com
ssl start_tls
ssl on
use_sasl on
sasl_auth_id
sasl_auth_id nssldap/machine1

Please note that I created a principal nssldap/machine1 and I added its key to the keytab file. I installed all packages using apt-get from Ubuntu repositories.

Any help is highly appreciated.

Thank you very much

---

