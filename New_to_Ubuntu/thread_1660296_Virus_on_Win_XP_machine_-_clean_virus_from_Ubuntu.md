---
title: "Virus on Win XP machine - clean virus from Ubuntu?"
date: 2011-01-05
forum: New to Ubuntu
---

### Post by Joe3000 on 2011-01-05
I have a laptop running Windows XP Home.  It got a virus or something similar and now Windows won't start.

I am able to boot Ubuntu off a USB flash drive and can access all the files that were originally on the laptop.

I have installed and am running Avast for Ubuntu in the hope of getting rid of the virus.

Is this likely to work?  What other tools can I install on Ubuntu to find the virus/malware in Windows?

Many thanks.

---

### Post by mike555 on 2011-01-05
there are a number of "live" cds just for running anti-virus , do a search , one I use is "dr.web" from ;  [http://www.snapfiles.com/get/cureit.html](http://www.snapfiles.com/get/cureit.html)

---

### Post by seawolf167 on 2011-01-05
I have three suggestions for booting off a live cd/usb drive and scanning for viruses:


[LIST=1]
[*][ClamAV ]("https://launchpad.net/clamav-livecd")live cd
[*][Trinity Rescue Kit]("http://trinityhome.org/Home/index.php?content=TRINITY_RESCUE_KIT____CPR_FOR_YOUR_COMPUTER&front_id=12&lang=en&locale=en")
[*][UNetbootin ]("http://unetbootin.sourceforge.net/")(you can use Dr. Web, F-Secure and Kaspersky)
[/LIST]

---

### Post by Joe3000 on 2011-01-05
Thanks, will try those three.

I do not have a CD drive as its a netbook so can only boot off USB which I have done using Unetbootin.

---

### Post by BbUiDgZ on 2011-01-05
look [HERE](http://www.askvg.com/download-free-bootable-rescue-cds-from-kaspersky-bitdefender-avira-f-secure-and-others)
Kaspersky has always worked best for me

---

### Post by sammiev on 2011-01-05
I have a live USB with ubuntu 10.10 and avast installed just for that reason. Help a few window folks with it already. I included the [Geek How To]("http://www.howtogeek.com/howto/14434/scan-a-windows-pc-for-viruses-from-a-ubuntu-live-cd/") for you as well. GL :)

---

### Post by cgroza on 2011-01-05
Boot your Ubuntu Live CD, install ClamAv and then run it.

---

### Post by Andrew Jeyaraj on 2011-01-05
avast has always worked for me...:) Clam AV is pretty good too...

---

### Post by hansolo4949 on 2011-01-05
I would stick with Avast! and scan the hdd from a _LIVE CD_. If you scan from the flash drive, there is always a possibility that the virus might jump onto the drive. While that might not affect Ubuntu, if you plug it into the computer while XP is on, poof, you have a virus again. If you boot from a live cd, the virus can't jump onto the cd, and you're safe. Please keep in mind that the possibility that the virus will jump to your flash drive is low, its always best to exert caution with this sort of thing.

If you don't have a virus, your windows installation might be corrupted, and you should try to repair it from the xp cd that came with your computer.

hope that helps!

 hansolo4949

---

