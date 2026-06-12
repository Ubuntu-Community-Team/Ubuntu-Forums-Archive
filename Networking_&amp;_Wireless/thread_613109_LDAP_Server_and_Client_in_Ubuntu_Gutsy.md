---
title: "LDAP Server and Client in Ubuntu Gutsy"
date: 2007-11-14
forum: Networking &amp; Wireless
---

### Post by process91 on 2007-11-14
I am having a very tough problem setting up a brand new LDAP server on Ubuntu Gutsy. I am using Ubuntu Gutsy for both the server and the client. Part of the issue is that all the instructions available indicate two files which have now been merged into one. How Tos that are available (even on Ubuntu's [documentation]("https://help.ubuntu.com/community/LDAP-Samba_PDC_%28for_Linux_and_Windows%29?highlight=%28ldap%29") [ site]("https://help.ubuntu.com/community/LDAPClientAuthentication?highlight=%28ldap%29")) indicate two files - /etc/libnss-ldap.conf and /etc/pam_ldap.conf have been merged into one /etc/ldap.conf.

First my online problem-submitting credentials. I have searched on google and on ubuntuforums and on the gentoo wiki and have come up with various pieces of the puzzle. In fact, some places claim to create exactly what I want, but at the end leave me high and dry. Ubuntu's documentation does have one page I would love if it worked - 
[LDAP-Samba PDC for Linux and Windows]("https://help.ubuntu.com/community/LDAP-Samba_PDC_%28for_Linux_and_Windows%29?highlight=%28ldap%29")
That is exactly what I want. However, after running through all the setup instructions I am no further along than when I started, and in fact had to reformat several times.

On to the problem. I believe I have a LDAP server working correctly on Ubuntu Gutsy, but I am not sure. I set up my Webmin module and it can see and add users and groups to it. To me this means that the LDAP server is working correctly.

I am on to trying to authenticate against this LDAP server but I am having no luck at all. I followed [this howto]("http://ubuntuforums.org/showthread.php?t=597056&highlight=ldap") which explains how to authenticate against an LDAP server in Ubuntu Gutsy but it did not work at all on my machine. It in fact caused my network interfaces file to reset to having no devices and then it would cause my computer to hang on shutdown.

All I really want to do is setup a simple LDAP server with roaming profiles in Ubuntu Gutsy, but nothing has worked. I think it would also be good to have a thread which contained all of this information in one spot for other users, so as I find out more information I will post it here. Thank you in advance

---

### Post by process91 on 2007-11-14
I know it's bad to reply to my own post before someone else does, but I'll try to give you as much information as I can.

The server appears to be working correctly, that is I can add/delete users from it using the webmin control panel and I can search through it with the ldapsearch command. Following [this howto]("https://help.ubuntu.com/community/LDAPClientAuthentication?highlight=%28ldap%29") I was able to list the users by typing getent passwd and I can see the two LDAP users I created on the server now. When I try to su username I receive this in response:

```
su: Authentication service cannot retrieve authentication info
Sorry.
```

If I instead type "sudo su && su username" it will log me in, but I'm sure this doesn't indicate that it is actually a real login.

So I am stuck at this point and I think after spending 12+ hours straight on it I will let it marinate for a bit before returning to it.

---

### Post by HornedBeast on 2008-01-30
This is a really awesome guide on setting up LDAP.

Im not having a huge amount of luck with desktop logins though. No-one can sudo once they've logged in,even though they are part of the admin group :(.

[http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760)

Maybe you will have more luck.

---

### Post by WeyOh on 2008-04-23
Did you manage to solve the problem of the two merged .conf files?

---

