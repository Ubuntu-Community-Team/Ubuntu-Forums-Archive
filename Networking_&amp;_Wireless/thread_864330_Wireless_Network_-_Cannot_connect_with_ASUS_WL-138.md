---
title: "Wireless Network - Cannot connect with ASUS WL-138G V2"
date: 2008-07-19
forum: Networking &amp; Wireless
---

### Post by Nightmist on 2008-07-19
I have a supported card according to some sticky thread, but I can't connect to the internet:

Model: WL-138G V2	
Chipset: Broadcom BCM4318 	
Driver: bcm43xx 	
Supported: Can see networks but cannot connect.
Comments: Driver installed in Feisty, lacks firmware. bcm43xx-fwcutter in repos will fetch the firmware.

I have used Linux before, but I'm a newbie by most standards. And I have no idea how to install a wireless network. ASUS does have a Linux driver, but I didn't understand what to do with it:
[http://support.asus.com/download/download.aspx?SLanguage=en-us&model=WL-138g%20V2](http://support.asus.com/download/download.aspx?SLanguage=en-us&model=WL-138g%20V2)

I have no network connection beside wireless, so I have to install it offline. I can dual-boot to windows with internet connection. I have Kubuntu 8.04 KDE4.

Hope anyone can help me get connected.

---

### Post by Nightmist on 2008-07-19
I have another question as well...

A HowTo suggested I download a .deb file, then double click it. But when I do, all I get is an empty window of some program that starts up (don't remember its name, but the icon is cardboard box) and I'm unable to open up .deb files with this app.

What program is suppose to start when I click a .deb file? I seem to recall it installing stuff pretty automatically for previous versions of Ubuntu.

---

### Post by Nightmist on 2008-07-19
I couldn't figure out how to get the package thing to work, so I did it with a console (I have forgotten most of this, so it took some trying and failing... remember, I have no internet connection while I am in Kubuntu) but figured it out eventually.

I had a b43-firmware_1.0-0cafuego0_all.deb file that I did the whole 'dpkg' thing with, and mess a bit with other Network commands (I have no idea what I'm doing, just remember some commands) and found out that the card was found but 'Disabled'. But I eventually got it working after a while.

But what's up with the 'Ark' program? It opens by default when you click .deb files but it can't do anything with them as far as I can tell???

---

