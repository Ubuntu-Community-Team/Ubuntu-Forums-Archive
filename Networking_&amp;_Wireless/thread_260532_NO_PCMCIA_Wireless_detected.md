---
title: "NO PCMCIA Wireless detected"
date: 2006-09-18
forum: Networking &amp; Wireless
---

### Post by JayDSee on 2006-09-18
I just installed XUbuntu on my IBM Laptop (600e) and my wireless LinkSys PCMCIA card was not detected.  I had previously installed Ubunto and that installation detected the wireless card without problem.

I issued the following commands:

sudo lshw  --> no wireless LinkSys card detected

sudo cardctl ident  --> command not found

gksudo gedit /etc/pcmcia/config.opts  -->  command not found

lspci -V | grep subordinate -->
Bus: primary=00,  secondary=01, subordinate=01, sec-latency=176
Bus: primary=00,  secondary=02, subordinate=05, sec-latency=176
Bus: primary=00,  secondary=06, subordinate=09, sec-latency=176

like I said, under Ubuntu the wireless card functions correctly.  Under XUbuntu the card is not detected.

Could it be that XUbuntu is not loading something?

Any help would be greatly appreciated.

J

---

### Post by JayDSee on 2006-09-19
I've discovered that my wireless card (LinkSys wpc11 v3) is recognized when I boot from the XUbuntu CD.  After, I install XUbuntu on the harddrive, the card is no longer recognized.  I've spent many hours researching in the forums but have not found anything that resolved my problem.  I did learn about some troubleshooting documentation at the following location:  Ubuntu Forums > Dapper Drake 6.06 Release > Hardware Help > Wireless Support.  There I found the file “WifiDocs/WirelessTroubleShootingGuide”.  In this guide, under the check device section, it had me issue the follow commands:  lshw lspci and lsusb to recognize the wireless card.  None of these commands were able to recognize the card.

Could it be that XUbuntu is not loading some required package?  Like for pcmcia.

I’m at a loss at this point.  Any Ideas?

---

### Post by JoJoArmani on 2008-02-11
looks like no one got back to you on this - did you ever resolve this problem? I have a similar issue...

---

### Post by Cha1n5aW on 2008-02-11
I too cannot seem to get my pcmcia wifi card to work either.  If I try to boot with the card plugged in, the system doesnt boot at all, if I plug in the card after everything is booted & loaded, nothing happens.  Odd part is, it works perfectly fine if I boot from livecd.

specs.
Ubuntu 7.10 gutsy
compaq presario 2105ca notebook
linksys WPC54G ver.2 pcmcia wifi card

Thanks
- Shawn

---

### Post by rustybronco on 2008-02-11
> **Cha1n5aW said:**
> I too cannot seem to get my pcmcia wifi card to work either.  If I try to boot with the card plugged in, the system doesnt boot at all, if I plug in the card after everything is booted & loaded, nothing happens.  Odd part is, it works perfectly fine if I boot from livecd.

specs.
Ubuntu 7.10 gutsy
compaq presario 2105ca notebook
linksys WPC54G ver.2 pcmcia wifi card

Thanks
- ShawnThat is odd, [http://ubuntuhcl.org/pub/reviews.php?product_id=408](http://ubuntuhcl.org/pub/reviews.php?product_id=408) 
can you install 7.10 without the card then plug it in and see if it works then?
I have used that card many times with no problems, one of the reasons I don't use 7.10 on my laptop is when I use acpi=force it becomes so slow it's unusable.

---

### Post by Cha1n5aW on 2008-02-12
Thanks Rustybronco, its highly likely that I had the card plugged in while installing.  The card has never worked since I installed to hard drive.  Is there any way to fix this without reinstalling Ubuntu?  Should I edit my /boot/grub/menu.lst and add acpi=force and pci=noacpi to the end of the kernel line? currently it reads like...
```
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=5f20bc4e-396f-4424-9c9f-70b154d6f15e ro quiet
```

Thanks
- Shawn

---

### Post by rustybronco on 2008-02-12
i use acpi=force because my bios is too old (pre 1999) that is the only way my processor fan runs correctly also without using it my laptop won't shut off correctly. (i run hardy alpha 4 now because of the slow boot in 7.10)

can you connect from the command line? 
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

try installing wicd if you can connect from the command line [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

what does **lshw -C network** show between what you have now and on a live cd?

***edit*** wpc54g-ver2 doesn't work in 8.04 yet.

just posted
[http://ubuntuforums.org/showthread.php?t=695531](http://ubuntuforums.org/showthread.php?t=695531)
[http://ubuntuforums.org/showpost.php?p=4322430&postcount=5](http://ubuntuforums.org/showpost.php?p=4322430&postcount=5)

---

### Post by Cha1n5aW on 2008-02-13
lshw only shows eth0, wifi simply doesnt exist.  I've surrendered to reinstalling Ubuntu.  I tested again last night from the livecd & the card works perfectly fine in the live environment.  I've a few other reasons to reinstall anyways.  Since it's my first install with Ubuntu I've managed to mess up a few other things as well.  Also, I'd like to install into a different hard drive because I'm beginning to see problems with the drive I'm currently running.  Anyone who reads this, do yourself a favor and NEVER EVER EVER buy a Seagate hard drive.

Thanks for all the help
- Shawn

---

### Post by Cha1n5aW on 2008-02-14
Just in case anybody is still reading this thread, I had to reinstall ubuntu WITHOUT the pcmcia wifi card plugged in.  I guess if you install with anything plugged into pcmcia slot things dont work right.  Also for some reason, Ubuntu must be booted with the card in for it to work, plugging in the card while system is already running does nothing.  Thanks to everyone who helped, and happy V-day-0!

- Shawn

---

### Post by rustybronco on 2008-02-14
Did it work when you re-installed the os without the card inserted,  then inserted the card after the os was installed?
did you check the cd for errors?

---

### Post by Cha1n5aW on 2008-02-14
Yep, all is good now.  After I installed ubuntu to a new hdd, I shut down, plugged the linksys card in & booted up, wifi worked great, no need to mess around with drivers or anything as ubuntu has native drivers for the WPC54Gv2.  Many other things working better too.  I had to reinstall anyways because I wanted to switch to a better hdd.  Turns out my old seagate drive was finished, so I had to switch to my IBM travelstar drive.  Today, I got another pcmcia wifi card (netgear WPNT511) so I had a bit of an adventure to get that pcmcia card working as well.  Had to use ndiswrapper and winXP airgo drivers, but got that card also works.  I wish I could plug the card in without rebooting, but I'm happy to have both cards working.  Much thanks for all the help.  For more info on my netgear wifi card adventure, check out this thread [http://ubuntuforums.org/showthread.php?t=696903]("http://ubuntuforums.org/showthread.php?t=696903")

- Shawn

---

### Post by Gwijde on 2008-05-11
Try installing this package:

```

linux-ubuntu-modules-2.6.24

```

Worked for me!

Good luck!

---

