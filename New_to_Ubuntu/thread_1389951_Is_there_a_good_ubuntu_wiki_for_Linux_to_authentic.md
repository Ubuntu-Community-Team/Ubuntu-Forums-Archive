---
title: "Is there a good ubuntu wiki for Linux to authenticate against a Samba server?"
date: 2010-01-25
forum: New to Ubuntu
---

### Post by frenchn00b on 2010-01-25
```
apt-get install libpam-smbpass
``` is the first to run
but then ? 

I found this for another distro: [http://www.hants.lug.org.uk/cgi-bin/wiki.pl?LinuxHints/SambaAuth](http://www.hants.lug.org.uk/cgi-bin/wiki.pl?LinuxHints/SambaAuth)

Is there something good destined to Ubuntu ?

thank you !!

---

### Post by cariboo on 2010-01-25
Have a look [here]("https://help.ubuntu.com/community/LDAPClientAuthentication"). It is a bit out of date though. The howto you linked to should work though, as all Linux distributions are the same under the skin.

---

### Post by frenchn00b on 2010-01-26
> **cariboo907 said:**
> Have a look [here]("https://help.ubuntu.com/community/LDAPClientAuthentication"). It is a bit out of date though. The howto you linked to should work though, as all Linux distributions are the same under the skin.

the problem with ldap is that with the locking issue, the client is booting slowly after mainy retries, in soft lock, then the client is booted. The issue of ldap (bug) will apparently never solved. but well I do not understand much about it since networks >500 workstation are surely using ldap... so somehow there is ways to make it work.

---

