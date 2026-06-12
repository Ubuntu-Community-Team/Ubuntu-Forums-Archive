---
title: "vista recovery CD"
date: 2009-08-08
forum: New to Ubuntu
---

### Post by kalabaadshah on 2009-08-08
My laptop is HP Pavillion dv2700 special series. It came with windows vista installed in it. I replaced it with Ubuntu 9.04. Now, what I have is just the windows vista recovery cd at my disposal. I want to keep ubuntu intact and want to install vista in it. Is it possible to do so 1) only using vista recovery cd and 2) without unistalling Ubuntu at any stage of the process?

---

### Post by mikewhatever on 2009-08-08
Don't think so. Recovery cds usually format the whole disk and restore it to the original state. Backup, and then reinstall.

---

### Post by quinnten83 on 2009-08-08
I haven't done this myself, but I understand you can, but with jumping through some hoops.


First you need to repartition. You can use gparted for that. Create a new partition where you can install vista to.

Then install vista.

3. Fix Grub for startup of Ubuntu. Vista rewrites the MBR, and deletes the grub already installed.So you have to reinstall it.

---

### Post by Sidewinder1 on 2009-08-08
The issuance of the Recovery Disk only, by the major 'puter manufacturers (about 6 years ago), in lieu of a full Operating System disk, is one of the reasons that I switched to Ubuntu. I was totally satisfied with XP, other than it's security vulnerabilities.  I didn't want any parts of that piece of junk, AKA Vista, and would not be forced into using it. Just another example of Mircopoop, trying to prevent illegal distributions of their os at the expense of their legitimate, paying cutomers. I say, "Let them continue with that ignominious behavior, and they will continue to loose market share..." 

Rant off...
Side

---

### Post by presence1960 on 2009-08-08
> **quinnten83 said:**
> I haven't done this myself, but I understand you can, but with jumping through some hoops.


First you need to repartition. You can use gparted for that. Create a new partition where you can install vista to.

Then install vista.

3. Fix Grub for startup of Ubuntu. Vista rewrites the MBR, and deletes the grub already installed.So you have to reinstall it.

That will not work with a recovery CD/partition. Those recovery CD/DVDs/partitions format the entire hard disk and put it back to the way it came from the factory. Anything on the disk whether it be an OS, data and partitions will be wiped and restored to the factory image. That is the drawback of a recovery CD/DVD/partition. The advantage is it helps those who do not know how to install, partition, download & install drivers.

The process you describe is for someone with a retail or OEM Windows installation disk, not a recovery CD/DVD/partition. By the way that "jumping through hoops" you describe is pretty basic stuff. I can't tell you how many people have been walked through that process for the first time successfully in this forum. Like I said pretty basic. I suggest you really should try to refrain from using terms  like "jumping through hoops" that will serve to intimidate or discourage the user in regards to the action they need to take. Your description implies a high degree of difficulty or even danger.

---

### Post by bumanie on 2009-08-08
Agree that a recovery cd will format the entire hard drive and return it to the same state as when you purchased the computer. Depending on what is wrong with vista, you could go [neosmart]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") and download a vista repair disc that may fix the problem.

---

### Post by kansasnoob on 2009-08-08
I hate to be contrary but I've had fairly good luck with HP, Compaq, and Dell Recovery discs (Gateway no so much). I've found most to install no differently than OEM or retail Win discs, so I'd say, "maybe"!

This is a simple and good guide if you have a common default installation of Ubuntu (that is only two partitions, if that's not the case then the instructions on page 4 will need to be amended):

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

Of course you should always back up anything important because things can go wrong during any repartitioning and/or installation.

---

