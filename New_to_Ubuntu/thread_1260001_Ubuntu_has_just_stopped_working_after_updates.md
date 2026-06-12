---
title: "Ubuntu has just stopped working after updates"
date: 2009-09-07
forum: New to Ubuntu
---

### Post by martynk on 2009-09-07
Hi all
 
I am absolutely new to Unbuntu, and have been going through a crash course on how to use it, reading everything I can get my hands on.
 
I downloaded the latest version, and installed via a USB drive on my Acer Revo net pc, dual boot with Vista. I got it all working happily, and was working my way through getting the drivers up to date, and I also used the command to check any updates, of which there were around 145mb worth.
 
Downloaded those and restarted, and I get the prompt as to which OS to choose, and the Ubuntu splash screen appears, but just after the small bar starts, it stops and thats as far as it gets. I have tried the other Ubuntu start options including recovery, but they all just freeze.
 
I dont have enough knowledge to do much else than reinstall it, unless someone can help me with some other options? The Vista load still works fine.
 
Can I actually type anything in or do anything at this point, or am I stuck?
 
Thanks in anticipation
 
MartynK

---

### Post by kyle6513 on 2009-09-07
there should be a couple of different boot options for ubuntu such as the top one with (recovery mode) in brackets, try fiddling around it there, that could fix it =]

---

### Post by oboedad55 on 2009-09-07
> **martynk said:**
> Hi all
 
I am absolutely new to Unbuntu, and have been going through a crash course on how to use it, reading everything I can get my hands on.
 
I downloaded the latest version, and installed via a USB drive on my Acer Revo net pc, dual boot with Vista. I got it all working happily, and was working my way through getting the drivers up to date, and I also used the command to check any updates, of which there were around 145mb worth.
 
Downloaded those and restarted, and I get the prompt as to which OS to choose, and the Ubuntu splash screen appears, but just after the small bar starts, it stops and thats as far as it gets. I have tried the other Ubuntu start options including recovery, but they all just freeze.
 
I dont have enough knowledge to do much else than reinstall it, unless someone can help me with some other options? The Vista load still works fine.
 
Can I actually type anything in or do anything at this point, or am I stuck?
 
Thanks in anticipation
 
MartynK

Which version did you get, 9.04 or 9.10? 9.10 is still in alpha testing if that's what you got. So you want 9.04, jaunty jackalope.

---

### Post by martynk on 2009-09-07
Hi
 
I have got 9.04 and I have tried the various Unbuntu options at start up - all the options stop in the same place, in the safe mode it lists out everything it is doing and then stops on something like ath_pci PCI INT A -> link(LN4A) -> GSI 19 (level, 1 ou) -> IRQ 19
 
Its during the hardware driver load , I get the impression its a IRQ issue perhaps around the wlan?
 
Any help?
 
Ta

---

### Post by LewRockwell on 2009-09-07
here is where understanding how grub works will get your machine back up and running quickly(most of the time)

you'll boot up using the LiveCD(or LiveUSB) and open a terminal session:```
gksudo gedit /boot/grub/menu.lst
```

when you originally installed the distro(in this case ubuntu 9.04) and grub, the grub had a portion that looked like the following:```
## ## End Default Options ##

title Ubuntu 9.04, kernel 2.6.28-11-generic
uuid e46c59d8-a21a-4fb7-9079-769084bdc10a
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=e46c59d8-a21a-4fb7-9079-769084bdc10a ro quiet splash
initrd /boot/initrd.img-2.6.28-11-generic
quiet

title Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid e46c59d8-a21a-4fb7-9079-769084bdc10a
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=e46c59d8-a21a-4fb7-9079-769084bdc10a ro single
initrd /boot/initrd.img-2.6.28-11-generic

title Ubuntu 9.04, memtest86+
uuid e46c59d8-a21a-4fb7-9079-769084bdc10a
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```but after the updates the newer kernel(2.6.28-15-generic) will also be listed```
## ## End Default Options ##

title Ubuntu 9.04, kernel 2.6.28-15-generic
uuid e46c59d8-a21a-4fb7-9079-769084bdc10a
kernel /boot/vmlinuz-2.6.28-15-generic root=UUID=e46c59d8-a21a-4fb7-9079-769084bdc10a ro quiet splash
initrd /boot/initrd.img-2.6.28-15-generic
quiet

title Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid e46c59d8-a21a-4fb7-9079-769084bdc10a
kernel /boot/vmlinuz-2.6.28-15-generic root=UUID=e46c59d8-a21a-4fb7-9079-769084bdc10a ro single
initrd /boot/initrd.img-2.6.28-15-generic

title Ubuntu 9.04, kernel 2.6.28-11-generic
uuid e46c59d8-a21a-4fb7-9079-769084bdc10a
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=e46c59d8-a21a-4fb7-9079-769084bdc10a ro quiet splash
initrd /boot/initrd.img-2.6.28-11-generic
quiet

title Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid e46c59d8-a21a-4fb7-9079-769084bdc10a
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=e46c59d8-a21a-4fb7-9079-769084bdc10a ro single
initrd /boot/initrd.img-2.6.28-11-generic

title Ubuntu 9.04, memtest86+
uuid e46c59d8-a21a-4fb7-9079-769084bdc10a
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```So, if during your attempts to unsuccessfully boot, you were only selecting the newer kernel(perhaps the older kernel is "commented out with the #" but still listed in the menu.lst file) then you can uncomment it during editing and then retry to boot using the older kernel(which you stated was functional)

again, learning proper partitioning, proper grub administration, and proper search techniques...will ultimately result in incredible empowerment and a well-deserved sense of true accomplishment, achievement, and confidence!

.

---

### Post by martynk on 2009-09-07
Thanks Lew - means nothing to me now, but I am off to work out how to do it, and see if I can fix it.  I would rather do that than reinstall, so I can get to understand the operating system better.
 
Fingers crossed
 
Martyn

---

