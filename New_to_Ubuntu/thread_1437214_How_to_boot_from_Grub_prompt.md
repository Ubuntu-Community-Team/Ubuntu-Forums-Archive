---
title: "How to boot from Grub prompt"
date: 2010-03-23
forum: New to Ubuntu
---

### Post by jeffste1 on 2010-03-23
[SIZE=2]I just finished installing Ubuntu 9.1 x64 on my C:\ drive using wubi.exe. The initial install went fine. When I rebooted I got the graphical screen and logged into the Gnome desktop. I was just beginning to play around when a screen popped up saying that roughly 265 packages needed updating, so I selected the install button and the packages were successfully download and installed. A reboot was required, but when I selected Ubuntu from the OS selection screen, instead of booting I got a grub command line. How do I boot from the grub prompt? I did a "tab" to get a list of available commands and tried a few without success. Mostly the errors displayed said something like "you need to load the kernel." I need help badly. I have no idea what to do.[/SIZE]

---

### Post by lordyosch on 2010-03-23
Isn't there a command 'startX' which starts up the graphical parts?

I (probably am) could be wrong but I guess it isn't going to break anything to try!


Jay

---

### Post by tom.swartz07 on 2010-03-23
> **jeffste1 said:**
> [SIZE=2]I just finished installing Ubuntu 9.1 x64 on my C:\ drive using wubi.exe. The initial install went fine. When I rebooted I got the graphical screen and logged into the Gnome desktop. I was just beginning to play around when a screen popped up saying that roughly 265 packages needed updating, so I selected the install button and the packages were successfully download and installed. A reboot was required, but when I selected Ubuntu from the OS selection screen, instead of booting I got a grub command line. How do I boot from the grub prompt? I did a "tab" to get a list of available commands and tried a few without success. Mostly the errors displayed said something like "you need to load the kernel." I need help badly. I have no idea what to do.[/SIZE]

Was it a busybox shell or a grub:sh> prompt?

If it was a grub prompt, theres a link in my signature to help you with just that problem. Ill look up how to boot using the busybox shell and post in a few- unless someone else gets here first.

---

### Post by themusicalduck on 2010-03-23
Try these commands. I had this problem with a laptop and fixed it using these:

If you installed in XP -

```
sh:grub>set root=(loop0)
sh:grub>linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro
sh:grub>initrd /boot/initrd.img-2.6.31-14-generic
sh:grub>boot
```

If from Vista or 7:

```
sh:grub>set root=(loop0)
sh:grub>linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro
sh:grub>initrd /boot/initrd.img-2.6.31-14-generic
sh:grub>boot
```

If you manage to boot, then once in open a terminal (Applications > Accessories > Terminal) and run ```
sudo update-grub
```

Then you should be able to reboot and use it as normal.

---

### Post by jeffste1 on 2010-03-24
Thanks MusicalDuck. Your solution worked with one minor change - I had to change sda2 to sda1.  I then ran the sudo command you suggested and when I rebooted everything worked fine.  Also, thanks to everyone else for the helpful suggestions.   Regards, JeffS

---

