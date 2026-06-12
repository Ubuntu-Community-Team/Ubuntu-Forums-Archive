---
title: "Change GRUB boot order?"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by aquascrotum on 2009-04-13
I currently dual boot Jaunty and WinXP. I want to revert to WinXP until I have a few wireless issues in Ubuntu resolved - it involves a lot of restarting etc in Windows so would like to have WinXP as the OS booted by default.

How do I go about changing the preferred boot order?

---

### Post by logic++ on 2009-04-13
You can install the Startup manager. From a terminal:
```
sudo apt-get install startupmanager
```
Then you can navigate to System>Administration>Startup Manager and I think on the first tab you have a dropdown menu with all your startup entries to choose the one you wish to have as default.

---

### Post by duanedesign on 2009-04-13
need to edit the following file. In Terminal type:

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

### Post by elliotn on 2009-04-13
menu.lst

---

### Post by aquascrotum on 2009-04-13
> **logic++ said:**
> You can install the Startup manager. From a terminal:
```
sudo apt-get install startupmanager
```
Then you can navigate to System>Administration>Startup Manager and I think on the first tab you have a dropdown menu with all your startup entries to choose the one you wish to have as default.

Assuming that install requires an internet connection, I can't do that - my problem that is forcing me to switch back to XP is my wireless in Ubuntu isn't working.

[QUOTE=duanedesign]

need to edit the following file. In Terminal type:


Code:
gksudo gedit /boot/grub/menu.lstthen copy the XP settings ahead of the Ubuntu settings in the item list and leave everything else the same.[/Quote]

Cheers, will try that.

---

### Post by softwareregisterac on 2009-07-04
> **duanedesign said:**
> need to edit the following file. In Terminal type:

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

Hi

You provided me with the easiest solution after an hour of
googling. I learnt how to mess with the grub command line.

Many Thanx

---

### Post by Smudger on 2009-07-04
Thanks for this, great help

---

### Post by RwandaTim on 2009-08-12
Great and easy solution.  I am dual-booting XP and Ubuntu.  The STARTUP MANAGER is perfect and exactly what I wanted.  (Wish I hadn't wasted so much time trying to find such a simple solution.

---

### Post by mcduck on 2009-08-12
> **duanedesign said:**
> need to edit the following file. In Terminal type:

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

If you move it into that place, you will loose the whole Windows boot option during the next kernel update!

You *can* move the Windows entry above the Ubuntu ones, but you must keep it outside of the section marked as "DEBIAN AUTOMAGIC KERNELS LIST". This whole section is automatically re-created during kernel updates and any extra entries (like the Windows boot option) will disappear. (this is actually even explained in the menu.lst file itself, if you read the comments.) If you want to move Windows entry to top of the list, place it *above* the line "### BEGIN AUTOMAGIC KERNELS LIST".

Although the normal way to set default boot option is not to move any entries, but simply change the "default 0"-line near the beginning of the menu.lst file to point to correct boot entry (starting from 0), and then changing "# updatedefaultentry=false" to "# updatedefaultentry=true" in the default options section.

---

### Post by fleppmar on 2010-04-16
Hi.

If anyone is still paying attention in this thread.

I am trying to change the boot order via theese commands, but I only get up a blank file in all of them. And when I browse the /boot/grub/ folder I cant find theese files.

Can anyone help me?
I am trying to reinstall Windows, because Ubuntu 9.10 destroyed my computer. :P

It wont boot from CD, and the keyboard doesnt work untill I reach the logon-screen.
Sometimes I even have to rebott 3-4 times before my keyboard and touchpad is uop and going.

Regards.
fleppmar

---

### Post by Jibin Ukken on 2010-05-16
thanks buddy

Could you also tell us how to change the default time

---

### Post by doninsa on 2010-05-16
> **aquascrotum said:**
> I currently dual boot Jaunty and WinXP. I want to revert to WinXP until I have a few wireless issues in Ubuntu resolved - it involves a lot of restarting etc in Windows so would like to have WinXP as the OS booted by default.

How do I go about changing the preferred boot order?

Look for Startup Manager.

---

