---
title: "Blank/Empty Installation Window - Cannot Install 10.04"
date: 2010-07-05
forum: New to Ubuntu
---

### Post by Escee on 2010-07-05
When I boot from the Ubuntu CD (burned and verified from an ISO off the website) I get the "ubuntu" loading screen, then the wallpaper and the "Install" window.  However, the window is blank, empty:
[http://selan.jbcomptech.com:81/files/temp/IMG_2846.jpg](http://selan.jbcomptech.com:81/files/temp/IMG_2846.jpg)
See the above image.  Nothing happens from here.  I know what is supposed to appear as I have in the past successfully installed older versions of Ubuntu on other machines.  This is my first time with 10.04, and my first time with this particular machine.

I have tried re-burning the CD, and have tried both the 386 and AMD64 images, but both images result in the same.  This leads me to believe it's some kind of hardware or other system issue, so here are the specs of this machine:

Athlon 64 Newcastle 3400+
Gigabyte GA-K8VM800M (s754, VIA chipset)
2048MB Gskill PC3200
Sapphire X1650Pro
Plextor PX-708A DVDR/W
Rosewill RD450-2DB PSU
2x Sony CPD-G520 monitor (connected to DB15 and DVI connectors on Radeon)
Creative Audigy2

It has three hard drives, one PATA and two SATA.  Windows 7 Professional is already installed on the primary drive (PATA), and I intend to put Ubuntu on the same drive in a separate partition, which has already been created.

Thanks for any advice.

---

### Post by -humanaut- on 2010-07-06
Could have something to do with the VIA chipset (not the most Linux friendly of companys) are you burning the CD's at the slowest possible speed and also try using the Alternate CD instead of the standard live CD that might solve all your problems.

---

### Post by Escee on 2010-07-07
Yeah, I'm burning at 8x, which is the slowest my burner can go.  I also checked the MD5 checksum of the ISO, and had Nero (my burning utility) verify the written data.

Well, I've tried the Alternate CD, and that works a lot better!  However, bewilderingly when I do the "Check CD" function, it finds problems, even though as I said I've checked the MD5 of the ISO and had my burning utility validate the data was written properly.  Well, I ignored this and tried installing anyway, and it was successful, although I did have to do the rescue function to re-install GRUB because I couldn't boot the first time after installation.

But, it is really glitchy and I either can't even log in, or the system locks up shortly afterwards.  Windows 7 and Windows XP run fine on this machine, so I know the machine itself is stable.  Must be the VIA chipset.

I actually tried the Live CD in another machine (with an AMD chipset) and it runs fine.  Anything I can do to improve stability for a VIA system with Linux?  I also tried SUSE and while it does install and run without crashing, it is unbearably slow.  Any alternate drivers or anything?

Thanks for help so far.

---

