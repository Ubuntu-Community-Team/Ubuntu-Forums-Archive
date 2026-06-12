---
title: "NetworkManager keeps asking for WPA2 Personal Key even though it's correct"
date: 2008-11-26
forum: Networking &amp; Wireless
---

### Post by dkrepitD on 2008-11-26
```

```My System:
Ubuntu 8.10
R51 IBM Thinkpad

Since my new installation of the OS, I have had trouble accessing the Wireless networks. I log in and I can see that there ia WiFi network available, I try to connect to it, it asks for the WPA key (which is WPA2 Personal, exactly what is configured on my router), I enter the key (not a difficult key, BTW) and it looks like it is trying to connect but after 20-25 seconds it just comes back up to the enter password screen, even if I re-enter the key it just keeps doing this over and over. The funny part is that I upgrded this machine from the 7.10 version and on that version the WiFi worked fine on the same AP.
I have looked at .var/log/syslog and I could not see any obvous error in authentication or otherwise just a timed out message on eth1.
Can someone shed some light?
Thanks,
D

EDIT: New information I get the following errors when I look at the /var/log/wpa-supplicant.log
```
CTRL-EVENT-SCAN-RESULTS 
Trying to associate with 00:14:bf:6c:46:3a (SSID='nene' freq=2437 MHz)
Association request to the driver failed
Authentication with 00:14:bf:6c:46:3a timed out.
CTRL-EVENT-SCAN-RESULTS 
Trying to associate with 00:14:bf:6c:46:3a (SSID='nene' freq=2437 MHz)
Association request to the driver failed
CTRL-EVENT-SCAN-RESULTS 
Authentication with 00:14:bf:6c:46:3a timed out.
CTRL-EVENT-SCAN-RESULTS 
Trying to associate with 00:14:bf:6c:46:3a (SSID='nene' freq=2437 MHz)
Association request to the driver failed
Authentication with 00:00:00:00:00:00 timed out
```

---

### Post by spgerber on 2009-02-20
I have the exact same problem on NetworkManager.

I am using a ralink wireless - which worked fine on 8.04 on the same wireless.

Cheers

---

### Post by zancoste on 2009-02-20
Now did you change your passwords? if you did, try the older passwords.

---

### Post by Datz on 2009-03-08
I am also having this problem with 8.10.  I did not have it with 8.04.  I am using WEP and have not changed the key.

Did anyone resolve this issue yet?

Humm, while writing this, I reset my router and it ubuntu was able to connect with the key.

I will see if this issue occurs again.

---

### Post by evozero on 2009-03-12
Hi All,
I am having the same problem on two pc's. 1st is a fresh install on a Philips X59 laptop, the 2nd upgraded 8.04 install with a USR wireless card.Was working pre upgrade. So i don't think its a card driver problem, I think its a bug in Network manager? Anyone making progress with this?
Cheers
Ian

---

### Post by insaini on 2009-05-03
I am having the exact same problem now with Jaunty.. upgraded from 8.10 where it was working just fine.. but now it keeps asking for the password.. something im sure its with the kernel modules .. if I load the system with the kernel from 8.10 the wireless connects without a hitch.. if I boot from grub with the jaunty kernel.. it wont..

i am at a loss .. tried searching everywhere.. does anyone have any idea how to solve this?

---

### Post by justin23 on 2009-05-03
just posted a minute ago with the same problem.  I guess its something to do with the wpa supplicant for those of you having trouble connecting with wpa1.  I tried everything and still no luck

---

### Post by Nattydread69 on 2010-02-07
I have this same probelm with my wireless laptop, is this still not fixed?

---

### Post by Nattydread69 on 2010-02-08
I solved this problem by simply reinstalling the networkmanager and neworkmanager-applet.

---

### Post by adam22030 on 2010-02-08
Did you check the encryption keys you are using? I believe the NetworkManager assumes you are using AES and I do not believe there is a option to change to TKIP. So, if your router is setup for TKIP you might get that type of password error.

This happend to me installing 9.10. My wireless connection worked fine on the network I initially set it up on, but on my home network, which uses TKIP I kept being asked for the password. After I reconfigured my router to AES the connection proceeded normally.

Adam

---

### Post by regstraton on 2010-02-08
Hi

The reason for this is there is a bug in the v1.8.0.0 RaLink RT2860 driver relating to WPA.

You need to revert to the v1.7.1.1 driver or upgrade to the v2.2.0.0 driver.

For the life of me I can't find the really great web site that documents the fix nice and neatly...

---

### Post by tirithen on 2010-10-20
I think I'm having a similar problem with ubuntu 10.04 and my router at work [http://ubuntuforums.org/showthread.php?t=1589957](http://ubuntuforums.org/showthread.php?t=1589957). I need to try 10-20 times to be able to connect, many of those times NetworkManager asks me about the personal key. At home or in windows (dual boot) everything is fine.

---

### Post by frogging on 2010-11-18
OK so I guess this is where I need to be I have Ubuntu 10.10 installed on the church Multi-Media machine I had 10.04 and with the Windows drivers was able to connect fine.  when I upgraded to 10.10 I have not been able to connect.  I see the networks and 3 of them are unsecured.  Our Church network is secured.  I know the pass code I wrote it down and I connect with the other Windows machines.  BTW The Media machine is the only Linux boot machine in the church.  the other 5 are Windows XPs and the pass code works fine on them I know I set the network up.

> **adam22030 said:**
> Did you check the encryption keys you are using? I believe the NetworkManager assumes you are using AES and I do not believe there is a option to change to TKIP. So, if your router is setup for TKIP you might get that type of password error.

This happend to me installing 9.10. My wireless connection worked fine on the network I initially set it up on, but on my home network, which uses TKIP I kept being asked for the password. After I reconfigured my router to AES the connection proceeded normally.

Adam

Adam 
1.  I can't connect to secured or unsecured networks they just time out.
2.  Will Windows connect to a AES network or does Windows only see TKIP?  Hate to disable 5 computers from the network just to get one working.

---

### Post by scoobs22 on 2010-12-03
I'm using the Ralink 2860 chipset and can confirm that setting my router to AES-only cleared up the problem immediately. And I have two windows boxes (XP and 7)  also connected to the network, so no worries there.

Thanks for all the good info :)

--S

---

