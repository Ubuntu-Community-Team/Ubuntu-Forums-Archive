---
title: "LDAP Logins Hang after Password Auth"
date: 2008-04-30
forum: Networking &amp; Wireless
---

### Post by oxtub on 2008-04-30
I have installed and configured libnss-ldap and libpam-ldap (auth-client-config) on edubuntu 8.04 (amd64) to authenticate through a Windows 2003 Active Directory. I am currently in the following situation:

1.) getent passwd: works for all local users, shows account information correctly for users that I have configured.

2.) When I try to login via ssh using an AD account, I am prompted for a password. If I enter an incorrect password, it gives me Access Denied. If I enter the correct password, it just hangs, and outputs the following to /var/log/auth.log:

Apr 30 08:51:05 ts1-e sshd[9730]: Accepted password for mike from 10.39.53.157 port 2843 ssh2
Apr 30 08:51:06 ts1-e sshd[9733]: nss_ldap: reconnecting to LDAP server...
Apr 30 08:51:06 ts1-e sshd[9733]: nss_ldap: reconnected to LDAP server ldap://10.39.53.1 after 1 attempt
Apr 30 08:51:07 ts1-e sshd[9733]: nss_ldap: reconnecting to LDAP server...
Apr 30 08:51:07 ts1-e sshd[9733]: nss_ldap: reconnected to LDAP server ldap://10.39.53.1 after 1 attempt

3.) When I try to su to this user from root, it just hangs, and I get (pretty much the same thing):

Apr 30 08:52:25 ts1-e su[9737]: Successful su for mike by root
Apr 30 08:52:25 ts1-e su[9737]: + pts/0 root:mike
Apr 30 08:52:25 ts1-e su[9737]: nss_ldap: reconnecting to LDAP server...
Apr 30 08:52:26 ts1-e su[9737]: nss_ldap: reconnected to LDAP server ldap://10.39.53.1 after 1 attempt
Apr 30 08:52:26 ts1-e su[9737]: nss_ldap: reconnecting to LDAP server...
Apr 30 08:52:26 ts1-e su[9737]: nss_ldap: reconnected to LDAP server ldap://10.39.53.1 after 1 attempt

Any thoughts?

# getent passwd | grep mike
mike:*:10000:1001:Mike:/home/mike:/bin/bash

/etc/nsswitch:
...
passwd:         files ldap
group:          files ldap
shadow:         files ldap
...

/etc/pam.d/common-auth:
auth    sufficient      pam_ldap.so
auth    required        pam_unix.so nullok_secure

/etc/pam.d/common-account:
account sufficient       pam_ldap.so
account required         pam_unix.so

/etc/ldap.conf:
host 10.39.53.1
base dc=internal,dc=TGSNET
rootbinddn cn=Unix Ldap User,ou=Special,dc=internal,dc=TGSNET
# RFC 2307 (AD) mappings
nss_map_objectclass posixAccount user
nss_map_objectclass shadowAccount user
nss_map_attribute uid sAMAccountName
nss_map_attribute homeDirectory unixHomeDirectory
nss_map_attribute shadowLastChange pwdLastSet
nss_map_objectclass posixGroup group
nss_map_attribute uniqueMember member
pam_login_attribute sAMAccountName
pam_filter objectclass=User
pam_password ad

/etc/ldap.secret
[password]

---

### Post by deadkey on 2008-05-02
There is a thread describing a similar problem.

[http://ubuntuforums.org/showthread.php?t=772398](http://ubuntuforums.org/showthread.php?t=772398)

---

