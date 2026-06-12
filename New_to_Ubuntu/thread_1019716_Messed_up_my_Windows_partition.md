---
title: "Messed up my Windows partition?"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by Sly-.- on 2008-12-23
Hey, I was on XP and created a partition for Ubuntu, installed it on this new partition using wubu, and everything went fine. I even shutdown and logged back into Windows a few times, all was ok.

Then I went back into Windows, the XP loading screen came up and just as it finishes to load, I get a blue screen and it shuts down. I get this every time.

Any advice? Thanks.

---

### Post by Titan8990 on 2008-12-23
Hit F5 right before the windows splash screen shows up. Select the option to disable automatic restart.

It will now halt on the blue screen so you can write down the stop code.

---

### Post by ZhiZaki on 2008-12-23
Sounds like a typical Windows issue. Did you resize your windows partition or attempt to write to NTFS on that partition? It's the only thing I could think of that would be related to your Ubuntu install.

---

### Post by Sly-.- on 2008-12-23
I actually didn't do anything on or with it. Anywho, this is what it says on boot failure:

UNMOUNTABLE_BOOT_VOLUME

Yadda, yadda, yadda.

Technical Information:

*** STOP: 0x000000ED (0x89BB1900, 0xC0000000, 0x00000000, 0x00000000)

Possible to put this right?

---

### Post by muteXe on 2008-12-23
I did'nt think you needed to do any partitioning if you install with wubi?

---

### Post by ajgreeny on 2008-12-23
I was about to ask more or less the same as muteXe.  I thought wubi simply installed Ubuntu as if it was a program running on windows, rather than having to make a separate partition for it.

---

### Post by Sly-.- on 2008-12-23
I wanted them in separate drives. Any, if I can't fix this and have to re-install Windows, would it be fine if I left this drive I have Ubuntu installed on, format my C drive which has Windows on, and do a clear install or that on there, or would that screw up my Ubuntu aswell?

---

### Post by sajnox on 2008-12-23
I don't know precisely what will happen with the ubuntu install, but you are going to have problems with the windows loader.

Wubi don't use Grub and uses the windows loader instead, as you are going to have a windows fresh install you won't have the settings to start with ubuntu or windows.

Though I think it won't be that dificult to add the option to boot with ubuntu and windows

---

### Post by mapes12 on 2008-12-23
Try restoring your MBR (Master Boot Record): [http://www.tippscout.de/repair-and-restore-master-boot-record-mbr_tipp_3114.html](http://www.tippscout.de/repair-and-restore-master-boot-record-mbr_tipp_3114.html)

Then format the Ubu partition and follow one of the guides in my signature file for dual booting or installing with wubi a fresh.

---

### Post by Sly-.- on 2008-12-23
Well I got Windows working fine again, and still have Ubuntu in the other drive. Is it possible to add Ubuntu to the boot menu? Or isit just best to reinstall ubuntu and use GRUB instead?

---

### Post by mapes12 on 2008-12-23
> Well I got Windows working fine againFor the benefit of the rest of us, how did you do this?

With regard to Ubu then personally I would start again but setup a [dual boot configuration]("http://www.psychocats.net/ubuntu/dualboot").

---

### Post by Sly-.- on 2008-12-23
I tried running the command fixmbr and fixboot c: as suggested but it made things even worse. I wasn't even able to boot into Ubuntu after doing so. So, I just formatted my C drive and reinstalled Windows.

Anyway, thanks for the guide, and cheers for all the help everyone else provided. :KS

---

### Post by ajgreeny on 2008-12-23
I agree, go with a standard dual boot system.  I am still completely baffled as to how you did the wubi install, which does not use a separate partition.  That was supposed to be one of its major advantages for the uninitiated, ie. you do not need to mess around with partitions; you seem to have complicated a simple manner of installing ubuntu as a program by adding un-necessary partitions.

---

### Post by DNK on 2008-12-24
I uninstalled ubuntu by simply deleting the partition it was installed on. Had a grub22 error. Fixed that. Now Vista has unexpected shutdowns very often. I'd like to get vista working again. And possibly install ubuntu again :)

---

