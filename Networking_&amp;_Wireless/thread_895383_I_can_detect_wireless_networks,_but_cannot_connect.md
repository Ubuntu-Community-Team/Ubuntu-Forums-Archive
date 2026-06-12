---
title: "I can detect wireless networks, but cannot connect"
date: 2008-08-20
forum: Networking &amp; Wireless
---

### Post by MarlonDean on 2008-08-20
Hey everyone,

I am having the strangest problem. I use a broadcom 4311, and got it working fine. I can detect several wireless networks, but when i try to connect, it doesnt accept my key. The odd thing is that vista does, but not ubuntu

Why can i dectect networks, but cannot connect even though i know the key is correct?

---

### Post by smn8600 on 2008-08-20
I have a similar problem.  My windows machine was able to detect networks and connect, however, under Ubuntu I couldn't connect to anything greater than WEP.  e.g. WPA, WPA-2.  Someone please advise.

Thanks!

---

### Post by MarlonDean on 2008-08-20
It seems that i am able to connect to unencrypted networks. I googled this and all i found was forums where other people had the same issue, but no viable solutions

---

### Post by amedac on 2008-08-20
Hello to everyone, you must install and configure wpa_supplicant. Here is link: [http://www.lipasys.de/docu/en/wlanlinux](http://www.lipasys.de/docu/en/wlanlinux)

---

### Post by smn8600 on 2008-08-20
THANKS!!!  If ya don't hear back from me, it worked.  Thanks again :P

---

### Post by MarlonDean on 2008-08-20
Will this work for WEP aswell or only WPA?

---

### Post by timcredible on 2008-08-20
that's for wpa only.  wep has issues with the version of network manager that shipped with 8.04.  the new version of network manager that's shipping with 8.10 handles wep, wpa, vpn, wireless broadband.  if your system sees the SSIDs, but doesn't connect, i would suggest upgrading to network manager 0.7.  do a search, there's a good how-to.

---

### Post by Ayuthia on 2008-08-20
> **MarlonDean said:**
> It seems that i am able to connect to unencrypted networks. I googled this and all i found was forums where other people had the same issue, but no viable solutions

Can you post your lshw -C network info?  I would like to know which revision of the 4311 you are using and which wireless module you are using.  I have been able to connect via WEP but I have a rev 01.

---

### Post by MarlonDean on 2008-08-22
I know I have a BCM 4311 rev 2. I will try NM 0.7, thanks for all the info guys

---

