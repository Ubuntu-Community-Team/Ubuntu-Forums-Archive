---
title: "Ubuntu boots to grub&gt; command line"
date: 2010-09-13
forum: New to Ubuntu
---

### Post by Andyjt on 2010-09-13
Hello. I'm a bit new to ubuntu. I have had it running fine for a while. I ended up downloading the updates and now when I boot up the computer it boots to a grub> command line.

FYI: I'm running windows 2000 professional and ubuntu partitioned on the same single hard drive. 


Any help would be greatly appreciated. I just needs
 To know what to get it to boot back to the os boot menu. 
Thanks!
-andrew

---

### Post by Andyjt on 2010-09-14
Anyone have any help please :(

---

### Post by honeybear on 2010-09-14
> **Andyjt said:**
> Anyone have any help please :(

grub1 or grub2 ?




for grub2 you may try:

> 
        insmod part_gpt
        insmod ext2
        set root='(hd0,gpt1)'
        search --no-floppy --fs-uuid --set HEREYOURUID
        linux   /boot/vmlinuz-2.6.32-5-686 root=UUID=HEREYOURUID ro single 
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-2.6.32-5-686

then you can pres b to boot also



---

### Post by wilee-nilee on 2010-09-14
If the last post doesn't get you in to the OS post the bootscript in my signature in code tags as described. The text from running this script will give us a larger look at your setup.

---

### Post by oldfred on 2010-09-15
honeybear has the newest verison that Maverick uses. And using gpt partitioning, most of us have MBR/msdos

Manual boot:

Adjust drive, partition to your install:
sh:grub>ls
#If on (hd1,3) or sdb3
sh:grub>ls (hd1,3)/
#Should show the links vmlinuz & initrd.img
sh:grub>linux (hd1,3)/vmlinuz root=/dev/sdb3
sh:grub>initrd (hd1,3)/initrd.img
sh:grub>boot

Where grub counts:

```
      grub    grub2
sda1    hd0,0    hd0,1
sda2    hd0,1    hd0,2

sdb1    hd1,0    hd1,1

```

---

### Post by Andyjt on 2010-09-15
Here is the screen I get at startup:


GNU GRUB version 1.98-1ubuntu7

Minimal BASH-like editing is supported. For the first word TAB lists possible command completions. Anywhere else TAB lists possible device or file completions. 

grub>





Anyone have any ideas? Thanks in advanced!

---

### Post by jeight on 2010-09-15
TRY Super Grub Disk:

[http://linux.softpedia.com/get/System/Boot/Super-Grub-Disk-8071.shtml](http://linux.softpedia.com/get/System/Boot/Super-Grub-Disk-8071.shtml)

That should help you repair or reinstall grub.

---

### Post by ballboy_gray on 2010-10-03
OldFred you are a superstar! Thanks...

---

