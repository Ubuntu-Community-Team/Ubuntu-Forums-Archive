---
title: "Set Windows as default in dual-boot?"
date: 2009-10-15
forum: New to Ubuntu
---

### Post by Anton32828 on 2009-10-15
I would like Windows to be the top selection and default OS on the boot-loader screen (grub?). When the boot-loader times out, I would like Windows to start if I do nothing to select Ubuntu.

Can you help me? 

From searching this forum, I think I need to do some text-editing in a file used by grub. It has been many years since I fired up a command line text editor.

System configuration: HP Mini 110 netbook with WinXP pre-installed. Ubuntu desktop remix 9.04 installed as dual-boot on a 20GB partition.

Editorial comment: I tried the netbook remix on an exteral USB drive before installing it. I was very impressed how it delivers on the "it just works" promise. The last time I dabbled in Linux (six or so years ago) it was a major accomplishment for an average user like me to get the machine to simply boot and run a few basic apps.

---

### Post by duanedesign on 2009-10-15
need to edit the following file. In Terminal(Applications > Accesories > Terminal) type:

```
gksudo gedit /boot/grub/menu.lst
```

you should see this at the end of your list (mine is Vista)

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1
```

move this section above the first Ubuntu entry

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1
## ## End Default Options ##

title		Ubuntu jaunty (development branch), kernel 2.6.28-11-generic
uuid		366e0eb3-7812-4381-9b6c-438d98c4e43b
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=366e0eb3-7812-4381-9b6c-438d98c4e43b ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu jaunty (development branch), kernel 2.6.28-11-generic (recovery mode)
uuid		366e0eb3-7812-4381-9b6c-438d98c4e43b
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=366e0eb3-7812-4381-9b6c-438d98c4e43b ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu jaunty (development branch), memtest86+
uuid		366e0eb3-7812-4381-9b6c-438d98c4e43b
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

that should make xp your default.

here is a link to the [online grub manual]("http://www.gnu.org/software/grub/")

---

### Post by Paqman on 2009-10-15
If you install startupmanager it'll give you a nice GUI tool to manage this, and many other things related to booting.

---

### Post by vipulkelkar on 2009-10-15
sudo apt-get install startupmanager

then go to

system->administration->startup manager

It is a gui tool that handles all sorts of boot settings.You can also set colors n time out etc...check it out

---

### Post by Mark Phelps on 2009-10-15
A simpler change to menu.lst involves only changing the Default line to have the number of the stanza containing the MS Windows boot.  These are indexed from zero, so if MS Windows is the 6th stanza, change the "0" on the Default line to "5", save, and reboot.

It may take a couple of changes to get the number correct, but when done, that will be your default OS boot.

---

### Post by Anton32828 on 2009-10-15
Thank you to all who replied. I used duanedesign's gedit command (thanks, much nicer than vi) and Mark Phelp's advice to simply change the number of the "default" line. I now have Windows XP as my default until I get comfortable enough with Ubuntu to decide otherwise. 

I'll install startupmanager too at some point to check it out.

Thanks again!

---

### Post by neojimfang on 2009-12-06
**I used Paqman's recommendation. With Startupmanager as an application, it was too easy to [B]Set Windows as default in dual-boot**. Thanks Paqman.[/B]

---

