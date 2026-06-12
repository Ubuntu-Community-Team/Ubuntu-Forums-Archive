---
title: "LDAP Authentication Troubles"
date: 2005-09-08
forum: Networking &amp; Wireless
---

### Post by tincan on 2005-09-08
I have to say i was a little shocked to see very little documentation on authentication to an LDAP server in ubuntu or debian for that matter.  The best document I found was here:

[http://craige.mcwhirter.com.au/blog/archive/2005/01/17/making_a_debian_or_ubuntu_mach](http://craige.mcwhirter.com.au/blog/archive/2005/01/17/making_a_debian_or_ubuntu_mach) 

The config on this link, however, created a nasty double authentication problem trying to sudo - asking for your password and then asking for an ldap password...never authenticating to the ldap password.  Obviously, not being able to sudo is a bad thing in ubuntu!

This is finally fixed by using the following pam.d configs:

/etc/pam.d/common-auth
```
auth    required        pam_env.so
auth    sufficient      pam_unix.so likeauth nullok shadow
auth    sufficient      pam_ldap.so use_first_pass
auth    required        pam_deny.co
``` 
/etc/pam.d/common-password
```
password   sufficient   pam_unix.so nullok obscure min=4 max=8 md5
password   sufficient   pam_ldap.so use_authtok
password   required     pam_deny.so
``` 
/etc/pam.d/common-account
```
account required        pam_unix.so
account sufficient      pam_ldap.so
```
/etc/pam.d/common-session
```

session         required        pam_limits.so
session         required        pam_unix.so
session         required        pam_mkhomedir.so skel=/etc/skel/ umask=0
session         optional        pam_ldap.so

```

This config gets me about 80% torwards the goal of seamless LDAP auth including sudo.  I can now sudo but only if I "su" to a local account first.  Pretty messed up huh?  Regardless, at least I can sudo now!  I'm hoping someone out there knows pam better than me and is more familiar with ubuntu.  This happens to be my first day with it.

---

### Post by .::welemski::. on 2005-09-10
One question,
do I have to implement the configuration for the "pam.d" config files as instructed by "craige.mcwhirter" before I can implement your examples? or should I configure the "pam.d" config files directly using your examples.. Assuming that "libpam-ldap" and "libnss-ldap" is installed correctly...

---

### Post by Glarbl_Blarbl on 2006-02-25
Awesome!  I thought the /etc/pam.d/common-password stuff looked a little fishy, but this is my first foray into the magical realm of LDAP.

When I followed the Debian howto I ended up with no local password authentication.  Luckily ssh was configured to disallow logins w/ no passwords and vsftp apparently doesn't use ldap by default...  

Just went through and replaced the stuff I did before with your options and now it's all good.

You're right about there not being any documentation on the Ubuntu site for LDAP... Easily fixed though, just clean this thread up a bit and ship it over to the tips and tweaks (IIRC) section.  Eventually it should make it to the wiki.

g

---

