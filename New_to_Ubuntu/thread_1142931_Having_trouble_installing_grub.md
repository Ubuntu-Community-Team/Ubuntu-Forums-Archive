---
title: "Having trouble installing grub"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by alohatim on 2009-04-29
I successfully reinstalled windows xp then tried to install Ubuntu 8.1 from the live CD.  I needed to do the ubunbtu install in safe graphics mode.  Because I was doing it "blind" (I couldn't see the buttons on the bottom of the screen), I messed up a couple of times.  I got Ubuntu installed, but I don't have grub.  

I can boot with the live disk.  When I do find /boot/grub/stage1, I get:  "Error 15: File not found". 

I sense that I am pretty close.  I just don't know what to do to get the grub installed in the right place. 

Thanks for any help!

---

### Post by Didius Falco on 2009-04-29
This will walk you through it.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

I hope it helps...

---

### Post by old_geekster on 2009-04-29
> **alohatim said:**
> I successfully reinstalled windows xp then tried to install Ubuntu 8.1 from the live CD.  I needed to do the ubunbtu install in safe graphics mode.  Because I was doing it "blind" (I couldn't see the buttons on the bottom of the screen), I messed up a couple of times.  I got Ubuntu installed, but I don't have grub.  

I can boot with the live disk.  When I do find /boot/grub/stage1, I get:  "Error 15: File not found". 

I sense that I am pretty close.  I just don't know what to do to get the grub installed in the right place. 

Thanks for any help!

See if this link helps you:

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

Good luck!

---

### Post by alohatim on 2009-04-29
Thanks Didius and geekster.  The amendment to Didius' link looked promising.  I tried it but I still get stopped when I do find /boot/grub/stage1, I get: "Error 15: File not found"

I think I will try to install ubuntu again. Any tips on what to do with the ext3 partition?  I told the partitioner to make it a "/" partition.  The swap file is in swapon mode.  

It is very difficult to do this in safe graphics mode.  I would try text only but I don't have any more blanks CDs to burn an alternative disk.  Funny that that make the installer windows so that you cannot see the buttons in safe graphics mode.

---

### Post by alohatim on 2009-04-29
I think I will give up on this machine and give it all back to windows.  I am trying to delete the ext3 partition in gparted but it won't let me unmount it because it is in use.  Any ideas?

---

### Post by kansasnoob on 2009-04-29
> **alohatim said:**
> I think I will give up on this machine and give it all back to windows.  I am trying to delete the ext3 partition in gparted but it won't let me unmount it because it is in use.  Any ideas?

You can't work on mounted partitions. You'll have to run Gparted from the Live CD.

---

### Post by alohatim on 2009-04-29
That's the crazy thing.  I was in the live CD.  It still would not let me unmount the partition.

---

### Post by Didius Falco on 2009-04-29
If you are just going to delete the ext3 from that pc, put in your Windows install disc and when it gets to the choices menu load the "recovery console" and run ```
fixboot
``` and ```
fixmbr 
```

Then quit the CD and reboot.

That'll wipe Grub out of the MBR and you should then boot directly into Windows. Fire up the Windows partition manager and just delete the Ubuntu partition.

Warning - If you are going to resize your Windows partition, check around for advice from a Windows-centric place. I can tell you that you'll want to defrag your Windows drive thoroughly - it's probably best to do it 2x.

Also, anytime you are tinkering around resizing partitions, there is a chance, however small, of data loss.

Sorry Ubuntu didn't work out for you on that PC.

Good luck, and I hope this helps.

---

### Post by alohatim on 2009-04-29
Yup, I was able to boot to windows and delete the partition there. 

Thanks again!

---

