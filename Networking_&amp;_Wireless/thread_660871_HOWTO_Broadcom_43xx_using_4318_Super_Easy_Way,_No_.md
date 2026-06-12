---
title: "HOWTO: Broadcom 43xx using 4318 Super Easy Way, No Terminal Use"
date: 2008-01-07
forum: Networking &amp; Wireless
---

### Post by kolejame on 2008-01-07
Well it looks to me that everyone likes to use the terminal I don't, especially when I know I do not have to so here is a quick guide to set up wireless easily, every bit of info is given.

My current card came with an old Compaq computer that had Windows XP, but I have always wanted a linux interface, since I have recently purchased a brand new laptop I decided it is time to turn my old one into a linux with Ubuntu, so far the best interface I can find. It took me about one day to find out how to setup my wireless card to work with linux, I hate reading and doing all this code stuff, so this ended up working without even a reboot, very easy, I am surprised how easy it was to say the least.

My Wireless Card is: Broadcom BCM43xx
or Broadcom BCM4318 [AirForce One 54g] 802.11g

Ubuntu version installed on Computer: Desktop Edition Ubuntu 7.10 Standard personal computer (x86 architecture, Pentiumtm, Celerontm, Athlontm, Semprontm)
Ubuntu file name:ubuntu-7.10-desktop-i386.iso

Pre-Setup:Used a CD and Roxio to Burn ISO Image onto a regular 700mb CD.

I first installed bcm43xx-fwcutter_20060108-6build1_i386.deb

Put file wl_apsta-3.130.20.0.0 on Desktop

Opened System>>Administration>>Restricted Drivers Manager
	and clicked Enable on Broadcom Wireless card

When asked for firmware directed path to wl_apsta-3.130.20.0.0 (NOTE:if you can not unzip attatchment below, do a google search for this file)

Should be Enabled now.

Clicked on Wireless connectio button on top right toolbar
	Entered connection name(Previously known) entered type of password(WAP Personal, WAP2 Personal, Etc.) Entered password and put in connection type (TKIP, Etc.) If entered correctly you should be connected to the internet.

Than installed wifi-radar_1.9.7-0ubuntu4_all.deb
	reason: If I go roaming and want to check out other Public, Etc. connections.

ENJOY!!

I also created a ZIP and will try to attatch it with all above files except for the ubuntu version, download ubuntu at the ubuntu website, duh!

---

### Post by csat on 2008-01-07
Very interesting but where from did you get wl_apsta-3.130.20.0.0 ???

---

### Post by RAF01 on 2008-02-17
!! wow what can I say? Finally, I found a GREAT guide to how to install my wireless card on my old Dell Laptop, it worked like a charm, Thank you so and very much mate!

---

### Post by lostthetrail on 2008-02-24
Wow. Just wow. I can not believe someone finally got this working reliably. I can finally get rid of XP and not have to compromise anything.

Thank you so much.

---

### Post by biffinson on 2008-02-24
Doesn't work for me :(  When i try to connect it asks me for WEP password, tries to connect, 30 seconds later asks for password again.

---

### Post by todd1049 on 2008-02-27
Where did you find bcm43xx-fwcutter_20060108-6build1_i386.deb?

---

