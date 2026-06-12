---
title: "set up Ubuntu LDAP client to authenticate against OS X ldap server"
date: 2008-07-17
forum: Networking &amp; Wireless
---

### Post by bowmasters on 2008-07-17
Hello all,

I am trying to configure the ldap client on one of my Ubuntu(8.04.1) Machines to authenticate against an LDAP database hosted on an OS X(10.4.11) server.

I installed the following packages per [these instructions]("https://help.ubuntu.com/community/LDAPClientAuthentication"): libpam-ldap libnss-ldap nss-updatedb libnss-db

then I proceeded to manually edit parts of the config files where applicable (eg. 'host' in /etc/ldap.conf)

after I finished configuring things, I ran "getent passwd" to see if the configuration worked. The LDAP users failed to show up, so something is clearly amiss.

So, next I try to modify the configuration files per [these instructions.]("https://help.ubuntu.com/community/OSXLDAPClientAuthentication")

running "getent passwd" under this new configuration returns the users in the ldap database. "su" to one of those users also works. However, if I try to ssh into that machine using an ldap user, it does not work. Perhaps this is the "*authenticating (partially) successfully*" that the walkthrough was referring to?

In any case, I decided to try a third configuration using mostly the same parameters I had on a SUSE 11 box, (since I am able to ssh onto that one successfully using ldap users.) This config didn't fix the problem on ubuntu.

The last (and current standing) config I tried on this Ubuntu box was obtained using the command "auth-client-config" (which I just recently found out about). This command made it quicker and easier to configure, but it changed little and yielded the same result (no ssh login)

Just as a note, in between trying out these different configs, as a precautionary step, I uninstalled and reinstalled the ldap packages, being sure to purge the config files so that I started with a clean setup each time.

If anyone can help me figure out what is going wrong, I'd greatly appreciate it. If there is any additional specific information I can provide to help you help me, let me know and I will include it. 

P.S. I am fairly new to linux sys admin-ing, so please forgive my noobishness if it shows

---

### Post by bowmasters on 2008-07-21
Does anyone know about the issue I'm facing or have any tips on how to solve it?

---

