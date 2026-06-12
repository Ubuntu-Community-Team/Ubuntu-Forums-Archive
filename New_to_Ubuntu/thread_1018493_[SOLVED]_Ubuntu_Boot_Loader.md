---
title: "[SOLVED] Ubuntu Boot Loader"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by TheDarkMaster on 2008-12-22
Hi all,
At home I am now dual-booting windows XP and Ubuntu. I'm rather happy with it and I try not to boot into XP if possible. But now I get a problem:
I installed Ubuntu on a 500GB external HDD en windows XP on my internal 80GB HDD. Now if I disconnect the external HDD I get GRUB error 22. I guess that means he didn't find Ubuntu. That happend because GRBU was installed on my internal HDD, right? So now I want to restore the windows boot loader for my internal HDD and install the Ubuntu Boot loader on my external HDD. So in fact it would the just boot windows when I disconnect my external HDD, right? And my external HDD would become a portable OS if the BIOS preferences are right. Now I don't know how to do that so if anyone has a sugestion,
it would be welcome.

---

### Post by neu2buntu on 2008-12-22
this happened me ages ago,. i will try and find you the command to do in windows for the cmd prompt ...if i rem right it is 1line

---

### Post by neu2buntu on 2008-12-22
here it is.... Boot from your *install* CD or a floppy, choose the repair option, run recovery console, type FIXMBR    this should fix win 4 u  .... then we will work on grub

---

### Post by hyper_ch on 2008-12-22
(1) you need to add grub to the second harddisk. Generally you'd have to run this:
```

sudo fdisk -l

```
to check whether the external hd is recognized as "first" or "second" harddisk.

(2) then you run this to enter grub:
```

sudo grub

```

(3) in grub you run then:
```

root (hd1,0)
setup (hd1) 

```
root (hd1,0) means that grub shall look on the second harddrive in the first partition for the /boot folder/partition.

setup (hd1) means that grub shall be installed on the second harddrive.

If the external one is recognized as first one, then you'd run:
```

root (hd0,0)
setup (hd0) 

```
If /boot is not on the first partition, then alter the "0" to another value.

(3) you will get a success message and then you leave grub by issuing ```

quit

```

---

### Post by bumanie on 2008-12-22
With the xp installation, boot and go into console mode, via the repair option. Choose the operating system you want to repair (usually choice 1) then type FIXBOOT, followed by FIXMBR Answer, y to any questions you get asked - this will fix windows by removing grub.

To fix ubuntu on the external hard drive will need to be done with the ubuntu live cd. First get into a grub shell > sudo grubThen > root (hdx,x) depnding on the partition numbers of the drive [If it's the only other hard drive probably will be (hd1,0)] the > setup (hdx) > quitYou have to substitute the x for your drive numbers. If you don't know post the output of sduo fdfisk -l with the external drive plugged in.

---

### Post by neu2buntu on 2008-12-22
this link should help ... and change the settings to (hd1,0) and (hd1) or whatever the external drive is

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

---

### Post by TheDarkMaster on 2008-12-22
Thanks all it worked...
**[COLOR="Red"]BUT[/COLOR]** he now boots windows XP standard, as that drive has first priority, but when I set my external HDD to first priority I get GRUB error 18. This doesn't when I manually select my external HDD as boot device only when I say so in the BIOS settings. Anyone has who has an answer for this will be more than welcome.

---

### Post by TheDarkMaster on 2008-12-22
Well that problem was solved by putting the priority of HDD boot in front of CD-Boot so I will have to select boot device when I use a boot disk but I'm fine with that.

---

