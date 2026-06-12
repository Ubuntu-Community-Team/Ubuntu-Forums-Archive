---
title: "Complete Newb with two problems"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by FireFox1435 on 2009-03-14
Hey There Gang

     I have an older generic computer with a 1.3 AMD Duron processor.  I've recently nuked it, and installed Ubuntu 8.04 as the OS with no partition.  So far so good, but I am having some problems.  When I shut down from the desktop, I end up with some gobbledy gook on a black screen ending with "make sure message bus daemon is running".  The computer does not shut down,
and this screen stays up.  I have to turn the rocker switch on the back of the tower off to shut the computer down.  My second issue is on start up.  The monitor will intermittently not come off of stand by.  When it doesn't, I get nothing.  If I wait the appropriate amount of time, I can type in my username and password and get in to the desktop.  I just can't see it!  This happens with the on board video card in my tower, and the pci slot card I've switched too.  When it works, the monitor is just fine with no problems.  Hopefully I've posted this in the appropriate place, and someone can help me.  

Thanks!

---

### Post by desperado665 on 2009-03-14
Sounds like you may be able to fix it by adding [COLOR="Red"]acpi=off[/COLOR] to your /boot/grub/menu.lst file. 


Here's what mine looks like: 

```
title Ubuntu 8.04.1, kernel 2.6.24-23-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-23-generic root=UUID=5a03f6f1-6071-47ee-ae43-511bc0608637 acpi=off ro quiet
initrd /boot/initrd.img-2.6.24-23-generic
quiet

title Ubuntu 8.04.1, kernel 2.6.24-23-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-23-generic root=UUID=5a03f6f1-6071-47ee-ae43-511bc0608637 acpi=off ro single
initrd /boot/initrd.img-2.6.24-23-generic

title Ubuntu 8.04.1, kernel 2.6.24-22-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-22-generic root=UUID=5a03f6f1-6071-47ee-ae43-511bc0608637 acpi=off ro quiet splash
initrd /boot/initrd.img-2.6.24-22-generic
quiet

title Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-22-generic root=UUID=5a03f6f1-6071-47ee-ae43-511bc0608637 acpi=off ro single
initrd /boot/initrd.img-2.6.24-22-generic

title Ubuntu 8.04.1, kernel 2.6.22-14-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=5a03f6f1-6071-47ee-ae43-511bc0608637 acpi=off ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet

title Ubuntu 8.04.1, kernel 2.6.22-14-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=5a03f6f1-6071-47ee-ae43-511bc0608637 acpi=off ro single
initrd /boot/initrd.img-2.6.22-14-generic

title Ubuntu 8.04.1, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin
quiet 
```

You can edit the menu file by using the terminal command: gksudo gedit /boot/grub/menu.lst

Hope this helps

---

### Post by FireFox1435 on 2009-03-14
desperado

     Well, I altered the code in my /boot/grub/menu.lst exactly as you instructed.  Now when I shut down the computer, I get a different screen but the same issue.  I've included a shot of the screen.  I sure appreciate your help.

---

### Post by desperado665 on 2009-03-14
ok, try re-editing the file to say: acpi=off pci=noacpi irqpoll all_generic_ide

It looks like the same issues I had with an older machine and newer kernels. 

Will it shut down at all now or is it hung at the screenshot?

---

### Post by FireFox1435 on 2009-03-14
Ok, I did the edit as you instructed, and I'm back to the original screen I was ending up on before I did any editing on the /boot/grub/menu.lst.  See below.

---

### Post by desperado665 on 2009-03-14
Ok, are you getting this on shutdown and not fully shutting down or in a restart situation?

---

### Post by FireFox1435 on 2009-03-14
I am getting this screen from a "shut down" command.  I click on the red "off" button icon from the desktop, then select the "shut down" command.  The Ubuntu symbol shut down bar empties, then the last screen I posted shows up.  That's where the computer stops.

---

### Post by desperado665 on 2009-03-14
Ok, I have just found this in the forums and it seems to have fixed other hardy installations. See post #13

[http://ubuntuforums.org/showthread.php?t=772733&page=2](http://ubuntuforums.org/showthread.php?t=772733&page=2)

---

### Post by FireFox1435 on 2009-03-14
I want to thank you for all the leg work your doing for my issue.  I've searched the forums for my problems and haven't had much luck.  Now, I did exactly as the post you sent me instructed.  It was simple enough to cut those command lines, and reapply them.  It even made a twisted kind of sense.  But...  Now when I shut down, I get the following screen.  I don't want to be a pain in the butt.  I think I'm giving up for tonight.
Thanks Again

---

### Post by desperado665 on 2009-03-14
No problem FireFox... Now it may be as simple as removing all the kernel mods we tried earlier (ie: acpi=off pci=noacpi irqpoll all_generic_ide).

If you havent already removed them from your menu.lst, give that a try and see what happens.

---

