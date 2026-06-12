---
title: "usb adsl modem help"
date: 2006-08-04
forum: Networking &amp; Wireless
---

### Post by m1ck on 2006-08-04
Hi all, is there any way i can get a usb adsl modem to work with ubuntu or *any* linux distro for that matter its made by conexant.

If anybody could help i'd be very grateful.

---

### Post by vsridhars on 2006-08-14
Well,

a) USB ADSL Conextant : 
This is covered in the Ubuntu FAQ.

There is a brief discussion on how to locate the conextant driver from the Windows CD, extract the firmware using a tool and then moving it to the desired modules dir.

So far so good. I did all that.

b) Modem light should come on - that too worked. All smiles.

c) Then I got stuck in a couple of places.
--> PPPoE/PPPoA: My ISP tells me it is PPPoE
--> Installed Roaring Penguin PPPoE client, configured options - however it did not ask for the ADSL bit-settings (0/32, 1/34 etc.)
--> Tweaked a couple of conf. files, some web  scripts (based on accessrunner.sourceforge.net)

However, could not figure out 
1. What to put as the physical device - since it is not eth0 or eth1 --> it is a USB device
2.  Finally, whatever I did, the connection did not come up though hardware was detected fine.

Have switched to an Ethernet ADSL Modem for the moment - and will move up to a Wireless Router based connection later.


Rgd
Sridhar

---

### Post by vsridhars on 2006-08-14
From one of the other threads:

[http://rajeshjayaprakash.in/conexant.html](http://rajeshjayaprakash.in/conexant.html)

(haven't yet tried it out personally)

---

### Post by Nikolai D. on 2007-12-28
Hi

I've got same trouble. Can't figure out how to set my adsl usb modem up. My impression is its a dead end. Only solution is to buy Ethernet modem. I've alredy posted here in some treads. But nobody is replaying yet. Have also tryed some HowTo's, but also no luck. Atleas ive discovered that i dont have to compile the kernel, cuz some pakkage that is needed is alredy included in the kernel. I've got here sorce code for my modems driver that i have to compile. But without someones help i doubt i can accomplish it.

Source:
[http://users.fulladsl.be/spb30297/Linux%20driver/Note%20for%20Kernel%202.6/monaco_linux/](http://users.fulladsl.be/spb30297/Linux%20driver/Note%20for%20Kernel%202.6/monaco_linux/)

Ill try to search once more for sme info. But in the end, i guess, ill have to buy Ethernet modem (as the guy above sayd). Cuz one thing is if i set it on linux, but i'd like to set it also on OSX. But there's also not mutch of a success.

Okay,
Best wishes for holydays.

Nikolai

---

