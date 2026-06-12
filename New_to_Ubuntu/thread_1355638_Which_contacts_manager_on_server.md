---
title: "Which contacts manager on server"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by RichardCL on 2009-12-15
Dear Forum,

Which program should I be using to store all the contacts on Ubuntu server? Is Zimbra a good choice or LDAP? The Outlook clients attach to a whole series of IMAP servers. There is no exchange server.

Many thanks in advance.


Richard




My office set up is
1. Desktop with Ubuntu Karmic desktop
2. Virtual box with Win7 and office ultimate
3. Laptop with XP and office professional
4. Web and documents server with Ubuntu Karmic server

All computers are connected to the internet through a hardware firewall/router. The laptop also has a connection to open internet through UMTS for use on the road. The server (4) has port forwarding enabled in the firewall and router. At the moment ports are forwarded for web (80), SSH and CUPS (631).

I'm now faced with a mix of contact managers that need to get syncronised and organised. Outlook on the two office variants, possibly evolution on the Ubuntu machine and my mobile (Sony W850i at the moment).

I also pay the web hoster for space for mail storage so it may make sense to install some kind of exchange-like server on the server box and download everything from the server. In the end, I'd like to move away from web hosting and have everything running from my own server.

---

### Post by northern lights on 2009-12-15
I have no experience with Zimbra, so I cannot give input on which of the two tools you've sofar considered is better. However, LDAP is a really good utility as it is light and fast. Also, you might want to check out [LDIF]("http://en.wikipedia.org/wiki/LDAP_Data_Interchange_Format"), you'll need that for your tasks (if you choose to go with LDAP, that is).

---

### Post by ukripper on 2009-12-15
More info on LDAP and how to setup on 9.10 [https://help.ubuntu.com/9.10/serverguide/C/openldap-server.html](https://help.ubuntu.com/9.10/serverguide/C/openldap-server.html)


I'd also look into CITADEL Groupware which is very easy to install [http://www.citadel.org/doku.php/doku.php?id=start](http://www.citadel.org/doku.php/doku.php?id=start)

---

### Post by shapamit on 2009-12-15
Firstly , you should probably install a later version of ubuntu - 7.10 is no longer supported, unless an LTS version, each version is only supported for 18 months. 7.10 was not a LTS version. As you can get into xp fine, I would try to install either 9.04 or 9.10 version of ubuntu and hopefully grub will configure itself properly and will overwrite the mbr so that (in theory) xp and ubuntu will be able to dual boot. 9.04 uses the 'old' grub, known as grub-legacy, 9.10 uses the 'new' grub, known as grub 2. Just tell ubuntu to install over the top of the location that you have 7.10 and things should be fine, unless you have a quirky bios that doesn't take kindly to grub - but that is rare. If a later version of ubuntu doesn't behave properly, post back and someone will help you sort things out, but due to lack of support, 7.10 should not be your choice for ubuntu.

---

### Post by northern lights on 2009-12-15
> **shapamit said:**
> Firstly , you should probably install a later version of ubuntu - 7.10 is no longer supported, unless an LTS version, each version is only supported for 18 months. 7.10 was not a LTS version. As you can get into xp fine, I would try to install either 9.04 or 9.10 version of ubuntu and hopefully grub will configure itself properly and will overwrite the mbr so that (in theory) xp and ubuntu will be able to dual boot. 9.04 uses the 'old' grub, known as grub-legacy, 9.10 uses the 'new' grub, known as grub 2. Just tell ubuntu to install over the top of the location that you have 7.10 and things should be fine, unless you have a quirky bios that doesn't take kindly to grub - but that is rare. If a later version of ubuntu doesn't behave properly, post back and someone will help you sort things out, but due to lack of support, 7.10 should not be your choice for ubuntu.He's running Karmic. Where did you read anything about Gutsy?

---

### Post by ukripper on 2009-12-15
> **northern lights said:**
> He's running Karmic. Where did you read anything about Gutsy?

i think he posted to the wrong thread.

---

### Post by shairozan on 2009-12-15
Hey there, 

Zimbra is going to be your prime choice for what you want to do. I run it for my organization and it's been the best mail server I've used across any organization I've worked in. 

You'll have to move to 8.04 as it's the supported version at the moment. Once 10.04 (The new LTS comes out) it'll most likely become the new supported version. 

I would recommend ZCS 5 over the new release though, as I have had a lot of issues getting the newest version to install.

---

### Post by RichardCL on 2009-12-15
Yes, running Karmic (9.10) on the server and that seems to be a problem. Zimbra seems to work only up to 8.04LTS, which rules it out since I'll not go back a release.

> [http://ubuntuforums.org/showthread.php?t=1180044](http://ubuntuforums.org/showthread.php?t=1180044)

Therefore, I'm going to go with LDAP / LDIF as per your posts. Many thanks for the pointers to tutorial and Wikipedia. It seems that LDAP has been around for a while and should be stable. My plan is to move to the server as a main contacts manager very quickly.

---

