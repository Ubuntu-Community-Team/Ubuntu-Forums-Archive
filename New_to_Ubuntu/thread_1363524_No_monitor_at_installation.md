---
title: "No monitor at installation"
date: 2009-12-24
forum: New to Ubuntu
---

### Post by sylva on 2009-12-24
Hell!

After thoroughly searching the site, I haven't found any article/inquiry regarding the HP w2207 monitor. I have one of those and it's absolutely great. However, Ubuntu 7.4 does not detect it at installation. Ubuntu asks for updated drivers. I went to HP's site, but, apparently, they don't have any Linux drivers for this monitor. Is there something else I can do? Ubuntu installer doesn't pass and it displays the following message:

Can't access tty; job control turned off (initramfs). Debian's helper is summoning me to type in 'help', but, in spite of a blinking cursor after (initramfs), nothing can be typed in. 

Thanks for your help, S:confused:

---

### Post by running_rabbit07 on 2009-12-24
I thing the Ubuntu7.04 may be the problem. It is way out of date. Try using Ubuntu 8.04, 9.04, or 9.10.

What graphics card do you have?

---

### Post by adam814 on 2009-12-24
Monitors usually work on a standard (either DVI or VGA) so I doubt it's a driver for the monitor you need.  Not being able to type at the prompt makes me think the monitor isn't the problem at all.

Is your keyboard USB or PS/2?  If it's USB try connecting it directly to USB ports on the computer, not through a hub (i.e. the ports on the monitor).  In either case make sure the cables are firmly and properly connected.

Do you have any other operating system installed? Does it operate correctly?

---

### Post by sylva on 2009-12-24
Thank you both!

Well, here is the history of my Ubuntu installations. In 2007 when I installed it in a different computer (much advanced than the one I am installing now into), I didn't have any detection problems. The card was an Nvidia Geforce 8500 GT. The problem with that was that I could not bounce resolution up to the monitor's native resolution of 1650/1080. Now, in Ubuntu unleashed (2007), I am reading that Ubuntu does not have drivers for cards issued by ATI and Nvidia, as they have to be downloaded from their sites. This I'll do next. 

The keyboard is a standard PS/2, so no problems of USB detection here. 

I do have Win7 on a different partition. But on the other computer I also have XP SP3 and installation went without a hitch. So there.

I'll try the ATI Radeon 9250 Linux drivers (**if** they exist), but if they don't I'll order 9.10.

ThHanks again, S.

---

### Post by running_rabbit07 on 2009-12-24
I am not very familier with the ATI drivers, I do hear they are better in Karmic. I use nVidia and once the install was complete, the Hardware Drivers app popped up offering the drivers. I hope you get it going.

---

### Post by adam814 on 2009-12-24
If you have a Radeon 9250 you won't be able to use the newest drivers from ATI, you'll have to use version 9.3 or older.  I'd recommend using the open-source radeon driver
```
sudo aptitude install xorg-driver-ati xorg-driver-radeon
```

I doubt this is why you're stuck at that prompt though...

I think the problem may be that the SATA support in 7.04 doesn't include your HD controller causing it to be unable to mount the root filesystem.

---

### Post by sylva on 2009-12-24
Yeah, but...

I don't have SATA on this machine. It's PATA. I have Win7 mounted on a partition, the rest of the 250 gig is nonpartitioned, so I counted on Ubuntu to enable me to partition the unused space just for Linux and some Windows data. The next trial was through Ubuntu's Install with updated drivers. Dutifully, Ubuntu stopped and asked me to insert a disk with drivers. I did but Ubuntu won't find the ATI 8.8 drivers I just downloaded from AMD's site (I burned them on a CD). I'll download the 9.1 drivers and give them a try tomorrow. 

Gentoo stalls as well after giving me one page of installation log. Cursor is stuck at the low left corner; blinking gone. I won't waste my time with this. Will order Ubuntu 9.10. Still, I don't think even this version will contain the updated Radeon drivers because they are proprietary to AMD. Without them installation will stall. So will with nVidia (the MoBo has nVidia chipset with a VGA video controller) because its drivers are proprietary as well. I don't have much luck with my Radeon 9250 display card. Win7 does not go higher than 1280/1024 with its generic drivers. I'd hate to loose this card. It's a great digital card, only 4 years old. 

*** Adam, thanks for the code, but how will I type it in when Ubuntu stalls at the get go of the installation? ***

S.

---

### Post by adam814 on 2009-12-24
Good point...I guess that was a suggestion assuming you made further progress and were able to at least type at the prompt.  I blame post-final exam brain drain.

Are you able to check the CD for errors?  The installer should boot past that point even if it can't detect some of your hardware.

There are multiple drivers for ATI Radeon cards.  There is the proprietary binary-only "fglrx" from ATI and there is the open-source community maintained "radeon" driver.  But I digress...that's something to worry about post-install for sure.

I doubt the "update drivers" option will help since if the installer was really in a pinch for a driver it would use the vesa driver (universally compatible but with no acceleration).

Hopefully you have more luck with 9.10

---

