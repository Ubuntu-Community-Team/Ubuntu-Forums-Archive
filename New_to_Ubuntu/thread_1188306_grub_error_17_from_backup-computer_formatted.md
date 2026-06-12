---
title: "grub error 17 from backup-computer formatted"
date: 2009-06-15
forum: New to Ubuntu
---

### Post by dmstringer on 2009-06-15
Hi,
My friend had ubuntu on her laptop, deleted the partition, did a system back up and then formatted her hard drive, when she puts the back up in it does all it's suppose to and then she gets a grub loading, error 17. Is there any way she can fix this? She had windows xp and ubuntu and just wanted to move some gigs from ubuntu to windows but this was what she did. Any ideas? I don't think she has the XP discs. Thanks, I appreciate all thoughts. Oh, and by the way, I did a little research and found that Grub is a program that allows you to choose from more than one operating system on a computer.

---

### Post by bhadotia on 2009-06-15
> **dmstringer said:**
> Hi,
My friend had ubuntu on her laptop, deleted the partition, did a system back up and then formatted her hard drive, when she puts the back up in it does all it's suppose to and then she gets a grub loading, error 17. Is there any way she can fix this? She had windows xp and ubuntu and just wanted to move some gigs from ubuntu to windows but this was what she did. Any ideas? I don't think she has the XP discs. Thanks, I appreciate all thoughts.

Well you will require the XP installation disc to rewrite the MBR with the windows bootloader- so you better arrange that from somewhere.

Actually this error means that, as you have formatted the ubuntu partition, grub cannot find the /boot/grub/menu.list file which was on the ubuntu partition (if you did not mount /boot somewhere else).

After arranging the disc google on how to restore the MBR using XP disc (Vista disc does it automatically for me- never tried it using the XP disc) and that will solve the problem for you (hopefully).

---

### Post by Azrael3000 on 2009-06-15
had the same issues yesterday, solved by: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by dmstringer on 2009-06-16
Well, I am pretty new to forums so not sure how to thank everyone that replies to my question, in any case, thanks everyone for responding.  When you say installation disc, is that the same as recovery disc?  My friend says she has a recovery disc for windows 98, she said the laptop had XP on it so I am not sure what the story is, she is in Miami, OK and I am in Kansas City, MO.  She has a Toshiba Tablet laptop.  She used the recovery disc and the Toshiba screen came up then she rebooted, as instructed by recovery disc paperwork, and then got the grub error 17.  Is any of this making sense?

---

### Post by bhadotia on 2009-06-17
> **dmstringer said:**
> Well, I am pretty new to forums so not sure how to thank everyone that replies to my question, in any case, thanks everyone for responding.  When you say installation disc, is that the same as recovery disc?  My friend says she has a recovery disc for windows 98, she said the laptop had XP on it so I am not sure what the story is, she is in Miami, OK and I am in Kansas City, MO.  She has a Toshiba Tablet laptop.  She used the recovery disc and the Toshiba screen came up then she rebooted, as instructed by recovery disc paperwork, and then got the grub error 17.  Is any of this making sense?

As I said above you would need a XP CD. Installation disc is the same as recovery disc (most of the time) as it is the installation disc that is used to recover the system in case of a disaster (as in your case). It would be better if your friend can arrange some XP disc.

So tell your friend to get the CD from somewhere and then boot from that CD. After that use the command prompt of the recovery disc to repair the MBR (MAster boot record). Gooling on the matter will give more info on how to recover the MBR using XP disc ([Here]("http://www.tech-recipes.com/rx/483/xp_repair_fix_master_boot_record_recovery_console/") is what I found).

---

