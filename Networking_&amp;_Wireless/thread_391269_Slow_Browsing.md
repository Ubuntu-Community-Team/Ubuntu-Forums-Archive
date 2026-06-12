---
title: "Slow Browsing"
date: 2007-03-23
forum: Networking &amp; Wireless
---

### Post by scrayen on 2007-03-23
Problem:
Web browsing with Firefox is extremely slow.  It takes about 2 minutes for a webpage to begin loading and then it loads slow.  I have not seen this condition mentioned anywhere.  It does connect but takes about 2 minutes for every page to begin loading.  Booting to Win XP and Web browsing with Internet Explorer is normal and fast.  I suspect my Linksys WRT54GS Router

My setup is:
Motorola Surfboard SB5120 Cable Modem
Software vSB5120-2.19.0.6-SCM05-NOSH, Hardware v4, MIB vII, GUI v1.0, VxWorks V5.4.  I use the Ethernet interface.
Linksys WRT54GS Router v1.1 (I disabled wireless and use the wired ports)
	Firmware is v4.71.1 (the latest)
2 Computers and 1 network printer are connected to the router.  All networking works properly with the exception of Firefox with Ubuntu.
My Computer has 2 hard drives. Windows XP is on its own hard drive.  I added an older 7GB hard drive just for Ubuntu and let it set up Grub to dual-boot.  
Everything is setup using DHCP.

Troubleshooting I have done:
1. I have taken a very long Ethernet cable and connected it directly from my computer to the cable modem, thus bypassing the router and the entire house Ethernet wiring. Firefox works fast and normal under that condition.
2. I have also connected the same very long Ethernet cable directly from my computer to the router.  Firefox was very slow under that condition.
3. So I believe I have narrowed the problem down to the Linksys WRT54GS Router.
4. I have lowered the router’s MTU from 1500 to 1300, 1400, and a few others with no improvement.

Questions.
1. While experimenting with the router’s MTU I saved the settings on the Router then looked for results.  Should I have also rebooted the router?  
2. Should the computer MTU match the router MTU?  
3. Does the computer need to be rebooted after changing the MTU?
4. Would rerunning the setup CD for the router help?  I do not want to run it unless it will help.  I do not remember what all was on it.


Thanks for any help.

---

### Post by gradedcheese on 2007-03-23
You should start by disabling ipv6 in Firefox (go to the URL "about:config" and type "ipv6" to find the key) and also in Ubuntu (search the forum for how, it's a quick edit to /etc/modprobe.d/aliases).  Many routers can't do ipv6 (including yours) and that slows things down.

---

### Post by scrayen on 2007-03-24
Thank you "gradedcheese". That solution reduced the time down to about 10-15 seconds.  A big improvement.  I wonder if that is normal for everyone or should it be faster with Roadrunner cable?

One question though.  In the article about editing the aliases file, it was referred to as both ipv6 and ivp6.  I used ipv6 on all the edited lines.  That must have been correct because it was such a large improvement.  There are not 2 different ones are there?

Thanks again

---

### Post by gradedcheese on 2007-03-24
Yeah, it's only ipv6, the latter is probably a typo.

---

