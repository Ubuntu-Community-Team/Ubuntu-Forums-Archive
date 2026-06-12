---
title: "Domain Like System With Roaming Profiles"
date: 2007-11-11
forum: Networking &amp; Wireless
---

### Post by Vince4Amy on 2007-11-11
Hey, I need some assistance in setting up a network, I am running my network under the current configuration:
 
This Machine - Server - Kubuntu 7.10
Secondary Machine - Fedora Core 8
Laptop - Fedora Core 8
 
How would one be able to set up this machine so it acts as a server much like you can in Windows XP pro, I would need a domain system where I can have my users on roaming profiles, how easy will this be.
 
Also the secondary machine is used for computer repairs too, so how would I get that to share the Internet connection coming from this machine (I Will consult help from Fedora if I need to on this one).

---

### Post by ginge6000 on 2007-11-11
Hi, I managed to do this using LDAP autentication for the logins and NFS to share the users home directory allowing a "roaming profile".

I used these links(had to mix an match between them to get it to work!

LDAP:
[http://ubuntuforums.org/showthread.php?t=597056&highlight=nfs+home](http://ubuntuforums.org/showthread.php?t=597056&highlight=nfs+home)
[https://help.ubuntu.com/7.04/server/C/](https://help.ubuntu.com/7.04/server/C/)
[https://help.ubuntu.com/community/LDAPClientAuthentication](https://help.ubuntu.com/community/LDAPClientAuthentication)
[https://wiki.ubuntu.com/AuthClientConfig](https://wiki.ubuntu.com/AuthClientConfig)

NFS:
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

Hope these help!

Ben

---

