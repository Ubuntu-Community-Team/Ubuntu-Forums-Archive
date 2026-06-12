---
title: "Removing partitions via Live CD, without deleting Windows"
date: 2011-02-16
forum: New to Ubuntu
---

### Post by LinuxFox on 2011-02-16
My mother uses Ubuntu via Wubi and she gave me the ok to install it as a dual boot.  Everything was going well until the middle of install, it stopped at 48% saying the disc drive was faulty (which it's not since it's still loaded the live CD).

My question, how do I remove a partition and resize my Windows partition without losing it?  Since the install failed, I want to go back to using Wubi on her computer.  The disc is not defective as I used it to dual-boot on my computer (without Wubi).

Please answer my question and thanks.

Edit, I'm using Ubuntu 10.04, sorry I forgot to post that.

---

### Post by sydbat on 2011-02-16
> **LinuxFox said:**
> My mother uses Ubuntu via Wubi and she gave me the ok to install it as a dual boot.  Everything was going well until the middle of install, it stopped at 48% saying the disc drive was faulty (which it's not since it's still loaded the live CD).

My question, how do I remove a partition and resize my Windows partition without losing it?  Since the install failed, I want to go back to using Wubi on her computer.  The disc is not defective as I used it to dual-boot on my computer (without Wubi).

Please answer my question and thanks.How big is the hard drive you are trying to install on?

How did you set up your partitions? (eg. /, /home, /swap) How much space for each?

How did you resize your Windows partition in the first place? With gparted? From inside Windows?

---

### Post by LinuxFox on 2011-02-16
> **sydbat said:**
> How big is the hard drive you are trying to install on?

How did you set up your partitions? (eg. /, /home, /swap) How much space for each?

How did you resize your Windows partition in the first place? With gparted? From inside Windows?

Question 1: It's a 111 GB hard drive

Question 2 & 3: I used the Ubuntu Installer, and chose to install Ubuntu side by side with Windows.  It repartitioned my hard drive using the installer, though it appears in GParted. It goes as follows...

Extended (sda2)
-ex4 55.83 GiB (sda5)
-unallocated 1.00 MiB (unallocated)
-linux-swap 1.33 GiB (sda6)

---

### Post by snowpine on 2011-02-16
Step 1, BACK UP the entire windows partition to an external drive. You may find a Live CD such as Clonezilla useful for this purpose.

Step 2, boot your Ubuntu Live CD. Run the Gparted Partition Editor (it's under System->Administration if I recall correctly, otherwise press Alt+F2 and type 'gksu gparted').

Gparted is a very easy to use graphical partition editor. You simply click on the partitions you wish to delete, then resize the Windows partition into the empty space.

If the installer didn't get very far, then the Windows boot loader is probably still intact. If not, you can easily restore it from your Windows CD, there are lots of easy tutorials online how to do this. 

Good luck! :)

---

### Post by sydbat on 2011-02-16
> **LinuxFox said:**
> Question 1: It's a 111 GB hard drive

Question 2 & 3: I used the Ubuntu Installer, and chose to install Ubuntu side by side with Windows.  It repartitioned my hard drive using the installer, though it appears in GParted. It goes as follows...

Extended (sda2)
-ex4 55.83 GiB (sda5)
-unallocated 1.00 MiB (unallocated)
-linux-swap 1.33 GiB (sda6)OK. 

Forgot a question - Which version of Windows? XP? Vista? 7?

If Vista or 7, I think you have to use the partition app Windows comes with before trying to install.

Also, have you tried just starting again? This time, do the "Manual" partition and check to make sure that everything looks OK before installing in the already created ext partitions.

EDIT - snowpine has a lot of really good advice too!

---

### Post by LinuxFox on 2011-02-16
I don't have anyway to back up the Windows partition. :(  Can't I just remove the partitions and resize Windows, or this will delete it.  If something happens to Windows, my mother will be mad since she needs some Windows programs for work.  She mostly uses Ubuntu to browse the net.

Edit for sydbat, she has Windows XP installed

Edit: Ok, I removed the partitions for Linux-swap and ext4.  Now it says

Extended
-unallocated (57.15 GiB)

Edit again:  Now it's deleted and says unallocated.  I still need to resize Windows, but the message says risk loss of data.

---

### Post by snowpine on 2011-02-16
If you are asking for my permission NOT to back up your Mom's precious data before messing with her computer, sorry, I can't do that. :( 

External hard drives are very inexpensive; for less than $100 you can do it the safe way. Plus, she should have a backup anyway--it is just common sense--and if you help her set it up, she'll thank you someday. :)

---

### Post by LinuxFox on 2011-02-16
Ok, I was able to resize Windows without deleting it, but now Windows won't boot.  Instead it just says "A disk read error occured, press Ctrl+Alt+Del to restart"

Windows is there, but now it won't boot.  Please help me fix this.  If Ubuntu just installed like it should, then none of this would have happened.

Snowpine: I just remembered, her Windows files are backed up on an internal HD (her old computer), I just transfered everything from that.  So there is a backup.

---

### Post by snowpine on 2011-02-16
I am not a Windows expert, but there are a ton of "how to restore windows xp boot loader" tutorials on the web, for example:

[http://www.ehow.com/how_5089290_restore-windows-xp-bootloader.html](http://www.ehow.com/how_5089290_restore-windows-xp-bootloader.html)

---

### Post by LinuxFox on 2011-02-16
> **snowpine said:**
> I am not a Windows expert, but there are a ton of "how to restore windows xp boot loader" tutorials on the web, for example:

[http://www.ehow.com/how_5089290_restore-windows-xp-bootloader.html](http://www.ehow.com/how_5089290_restore-windows-xp-bootloader.html)Ok, I tried that and nothing.  I'm going to have a friend look at it since it's a boot loader problem.  Thanks for your help guys, it was appreciated even though I can't boot Windows.

Hopefully I can re-install Ubuntu as Wubi.  It's Wubi, but it's better than no Ubuntu.  Besides, if Windows gets reinstalled, I'll just load everything back from the old computer's HD.

I don't understand why Ubuntu didn't even install, it's the same disk I used for my install.

---

