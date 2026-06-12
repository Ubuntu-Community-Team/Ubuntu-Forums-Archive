---
title: "Got Sharing Wirless Internet via Ethernet Working...."
date: 2008-07-30
forum: Networking &amp; Wireless
---

### Post by RealG187 on 2008-07-30
As people on the forums may have read, [I was having trouble sharing my wireless internet with my computers that I did not want to buy additional wireless hardware for, but that were behind a router connected to my single machine that did have a USB Wireless Adaptor](http://ubuntuforums.org/showthread.php?t=384024). I finally got it to work. I was always using the method[here](http://support.microsoft.com/kb/306126), basically using this screen checking off the enable sharing connection option of my wireless connection:

[img]http://www.annoyances.org/pictures/articles/ics_xp_2.gif[/img]
I did this on my "Wireless Connection"

However before it did not work. There was two things I did to make it work (after I figured it out one day). My Dlink's router IP was set to 192.168.0.1, one day when I tried to [http://support.microsoft.com/kb/306126](http://support.microsoft.com/kb/306126) ICS it gave me a dialogue of an IP conflict, saying that the ICS host needs to be 192.168.0.1, funny thing is it never said this before and my router has always had that IP! So I changed my Router's IP.

The second problem is that my router is set to be the source of the internet for my network, not a computer connected to the network to be the source. I had to disable DHCP on my 2nd router. I think the ICS Host Computer has it's own DHCP server that manages all the connections, because when the router's DHCP is off, as long as that computer is On any clients get IPs. So the second problem is that the router expects to manage the network (DHCP), but the ICS computer is to do this.

As of now I am using Windows XP to on the computer that shares the connection. Now that I know the computer's IP must be 192.168.0.1 and DHCP on the router must be disabled for it to work, I was wondering if there is a way to do [this](http://support.microsoft.com/kb/306126) on Ubuntu instead of XP?

For those who don't understand what I am doing take a look at this picture (Sorry for my bad computer drawing skills :))


[size=5][COLOR="Red"]**NOTE: Where it says "Second Router, WLAN port unused" is should say "WAN port unused"!!**[/COLOR][/size]
[[IMG]http://img205.imageshack.us/img205/3482/icsmu9.th.png[/IMG]](http://img205.imageshack.us/my.php?image=icsmu9.png)

---

### Post by RealG187 on 2008-11-19
Would this help?

[http://ubuntuforums.org/showthread.php?p=6060607#post6060607](http://ubuntuforums.org/showthread.php?p=6060607#post6060607)

---

### Post by superprash2003 on 2008-11-20
yes internet connection sharing is possible via ubuntu.. an easy way to do it is by installing firestarter(sudo apt-get install firestarter) it has an internet connection sharing(ICS) option

---

### Post by RealG187 on 2008-11-20
I was tols about that before but it didn't work. But the way in Windows didn't work until I did what I said. So now firestarter should work? (Can I share with Windows?)

---

### Post by superprash2003 on 2008-11-21
yea, give it a shot!!

---

### Post by RealG187 on 2008-11-21
I am trying it now, as I am on my IBM running Ubuntu (Before I was runnning Windows on it)

---

