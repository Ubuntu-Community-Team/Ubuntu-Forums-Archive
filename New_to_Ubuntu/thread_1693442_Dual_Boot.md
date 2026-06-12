---
title: "Dual Boot"
date: 2011-02-22
forum: New to Ubuntu
---

### Post by wgwwm34 on 2011-02-22
Hey so I recently installed Windows 7 back on to my machine in addition to Ubuntu 10.10 and I'm now reading that I really should have went about it the other way around. I don't have the option to boot to Ubuntu and I'm not sure if there is a boot loader I can install from Windows to give me that option? I don't really know what I'm doing clearly but I was wondering how I would go about giving me the option to dual boot or if that's possible at this point.

Thanks.

---

### Post by Hakunka-Matata on 2011-02-22
yes, you can fix it.  Search on 'install grub' and you'll find MANY threads about installing Grub.

---

### Post by Hakunka-Matata on 2011-02-22
and yes, you're correct in thinking if you install windows first, then ubuntu, it's all done.  But don't worry, you can re-install Grub from where you are.

---

### Post by wgwwm34 on 2011-02-22
Thanks I'll check it out.

---

### Post by Hakunka-Matata on 2011-02-23
you marked this thread SOLVED, did you get your dual boot sorted?  I just came across the method spelled out by member 'oldfred' again.  I copied it and send it on to you in case you haven't reinstalled Grub 2 to the MBR of your linux disk.  

> #Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# After rebooting into working system
#to make sure you have osprober:
sudo apt-get install os-prober
sudo update-grub

You only have to install grub to the MBR and you will be able to boot and with osprober find all other bootable systems, but if XP is not there, then it will of course not boot that.

If concerned, the above will just install grub2 to the MBR. It is easy to restore a windows boot loader. The boot loader in the MBR for windows is the same for all versions and just looks for the active partition(boot flag) and jumps to that to boot.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

You can also restore a windows type bootloader - lilo from the Ubuntu liveCD. It uses the same logic, find boot flagged partition and jump to code in the partition.
Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR, not the lilo boot code that goes into the partition as we still want windows code in the partition.
__________________
Let us know what works and to mark your thread as [SOLVED], use Thread Tools on forum page.
Howto: [https://wiki.ubuntu.com/UnansweredPo.../SolvedThreads](https://wiki.ubuntu.com/UnansweredPo.../SolvedThreads)

---

### Post by Hakunka-Matata on 2011-02-23
That information comes from here: > [http://ubuntuforums.org/showthread.php?t=1689533&page=2](http://ubuntuforums.org/showthread.php?t=1689533&page=2) post# 28

---

