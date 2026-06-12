---
title: "Wlan0 is showing but can't connect to anything"
date: 2005-07-24
forum: Networking &amp; Wireless
---

### Post by Julius on 2005-07-24
I think I have sucessfully installed my card using a ndiswrapper script I found here. That was the only script that got my card to work... I tried installed ndiswrapper latest version manually and I succeed, but that think wouldn't take the driver as a valid one.

Anyway, I can see the wirless network in the networking GUI, the thing is that it just won't work. If I do "ifup wlan0" it won't get any IP by DCHP.

The card is shown, but it just doesn't work.

---

### Post by luca_linux on 2005-07-24
What card have you got?
Anyway, have you set the gateway up rightly?

---

### Post by Julius on 2005-07-25
My card is a Belkin F5D 7001 with a Broadcom 4306 chip.

---

### Post by mr_bean on 2005-07-25
Hmm, I had the same problem for a while with the Netgear WG311v2 PCI card, the wlan0 interface would show but no connection. It could be something with WEP. Are you using WEP? Try and configure it in the GUI. System-->Administration-->Network. I think that's how you get to it.

---

### Post by Julius on 2005-07-25
Yeah I'm using wep. But it was the same when I didnt have wep enabled, and I'm typing the web key everywhere. It just won't work :(

---

### Post by majikstreet on 2005-07-25
[QUOTE=Julius]Yeah I'm using wep. But it was the same when I didnt have wep enabled, and I'm typing the web key everywhere. It just won't work :([/QUOTE]
 dhclient wlan0 

did you try that?

---

### Post by Julius on 2005-07-25
yeah, well, right now I've broken ndiswrapper again, but that thing will say something like
"... 255.255.255.255 .."
and won't get any... proposal or whatever it says. I will copy everything when I fix ndiswrapper again

I've tried doing this, since it says that's the only way to get bcm4306 to work 
[https://wiki.ubuntu.com/SetupNdiswrapperHowto](https://wiki.ubuntu.com/SetupNdiswrapperHowto)

but
when I do this

sed -e "s/misc/kernel\/drivers\/net\/ndiswrapper/g" debian/rules > debian/temp

I says I have no permission ("permiso denegado" in spanish), even though I use sudo. I think that step is very important because otherwise ndiswrapper won't work correctly.

---

### Post by majikstreet on 2005-07-25
[QUOTE=Julius]yeah, well, right now I've broken ndiswrapper again, but that thing will say something like
"... 255.255.255.255 .."
and won't get any... proposal or whatever it says. I will copy everything when I fix ndiswrapper again

I've tried doing this, since it says that's the only way to get bcm4306 to work 
[https://wiki.ubuntu.com/SetupNdiswrapperHowto](https://wiki.ubuntu.com/SetupNdiswrapperHowto)

but
when I do this

sed -e "s/misc/kernel\/drivers\/net\/ndiswrapper/g" debian/rules > debian/temp

I says I have no permission ("permiso denegado" in spanish), even though I use sudo. I think that step is very important because otherwise ndiswrapper won't work correctly.[/QUOTE]
 Ok this is what I would do:
Insert your Ubuntu Cd into your computer
type this:
apt-get install ndiswrapper
apt-get install ndiswrapper-utils

then follow the installing windows driver section in that howto.

then setup the settings in system>>admininstration>>network selecting wlan0 as the interface.

then you can run dhclient wlan0 and it should get you your ip......

then we can worry about getting it up when you boot up, but first lets get it up now.

---

### Post by ychen on 2005-07-26
Maybe it is the WEP key's problem?

I worked out it today.

[http://www.ubuntuforums.org/showthread.php?t=51993](http://www.ubuntuforums.org/showthread.php?t=51993)

---

### Post by Julius on 2005-07-28
It works now!
I found the solution @ this post:
[http://www.ubuntuforums.org/showthread.php?t=25683&page=1&pp=10](http://www.ubuntuforums.org/showthread.php?t=25683&page=1&pp=10)

Guess I was following the wrong HOWTO before.

=)

---

