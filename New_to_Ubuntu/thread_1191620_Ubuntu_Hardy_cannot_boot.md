---
title: "Ubuntu Hardy cannot boot"
date: 2009-06-19
forum: New to Ubuntu
---

### Post by ENigma885 on 2009-06-19
Every time i try to boot up to Hardy 8.04 it keeps waiting for 4-6 min. on the splash screen then I got

```
Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/9a4fcd54-f38f-4dd6-b126-983d7a4c32b5 does not exist. Dropping to a shell !

Busybox v1.1.3 (Debian 1:1.1.3 ubuntu 12)
Built in shell (ash)

(initramfs)_
```

(i tried to make some search but all result i got were from 2006 or 2007 which i suppose are not applicable on 8.04)

---

### Post by jackson9458 on 2009-06-19
i could be completely wrong and i think i am. but when it finishes doing every thing or what ever type exit

---

### Post by go_beep_yourself on 2009-06-19
> **ENigma885 said:**
> Every time i try to boot up to Hardy 8.04 it keeps waiting for 4-6 min. on the splash screen then I got

```
Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/9a4fcd54-f38f-4dd6-b126-983d7a4c32b5 does not exist. Dropping to a shell !

Busybox v1.1.3 (Debian 1:1.1.3 ubuntu 12)
Built in shell (ash)

(initramfs)_
```

(i tried to make some search but all result i got were from 2006 or 2007 which i suppose are not applicable on 8.04)

I hate the splash screen. It's there for windows users. I like the traditional way of showing boot messages. You can get more details of what the problem is if you disable the splash. If you dont want to permanently disable it, you can temporarily disable it by editing the boot parameters from grub, actually I think Ubuntu makes you do two things to get rid of the splash screen. You have to disable the usplash service. I use the sysv-rc-conf to do that, but there are other tools included in ubuntu to do it. Remove quiet and splash from the boot parameters. If you want to make it permanent, you need to change this line in your /boot/grub/menu.lst

# defoptions=quiet splash

to this:

# defoptions=vga=791

Edit: I forgot to say that after you make those changes in your menu.lst, you must run sudo update-grub for them to take effect.

You don't have to include the vga line, but I like it because it makes my resolution higher in the virtual consoles, and the default tiny resolution kills me.

These are just some suggestions. I will help you more after your exam.

---

### Post by go_beep_yourself on 2009-06-19
Also let me know what your error is now after you changed your fstab. It shouldn't have the UUID in the error because you replaced that in your fstab. /dev/sda3 may not be the correct device anymore. I know it was the correct device before you had this problem. There are ways to find out what your root partition device is and then edit your fstab appropriately and try again.

One way:
Boot any Linux live cd and do a fdisk -l as root

Second way:
When you boot up and get that error, it drops you to a shell where you can type commands. The reason it does this is, so that you can fix the problem. Type fdisk -l there and see. Then you may have to use vi or vim to change your fstab.

Third way:
You can do it from windows, but it's a little more tricky. I will explain later.

---

### Post by jmoellers on 2009-07-03
I'm having the same problem since the last update a few days ago.
It appears that the initramfs does not create the /dev/disk/by-uuid and /dev/disk/by-label subdirs.
I am not very familiar with the udev stuff and the /etc/udev/rules/60-persistent-storage.rule does have an entry to create these /dev/disk subdirs. But when I fell into the initramfs shell, there were only the by-id and by-path subdirs, not the by-label and by-uuid. Later, when the main system is up, all four subdirs are there.

If you change your /boot/grub/menu.lst to have the "old style" root=/dev/sda1 kernel boot option, then the system will come up again.

---

### Post by ENigma885 on 2009-07-03
The system can boot now..I've just figured out I disconnected my CD room driver. But when I reconnected it again everything went as it's supposed to be. 
Most probably it has something to do with the names assigned to drivers, like sda1 and sda2, that were misplaced when the CDR wasn't there.

---

### Post by quill3033 on 2009-07-07
> **jmoellers said:**
> I'm having the same problem since the last update a few days ago.
It appears that the initramfs does not create the /dev/disk/by-uuid and /dev/disk/by-label subdirs.
I am not very familiar with the udev stuff and the /etc/udev/rules/60-persistent-storage.rule does have an entry to create these /dev/disk subdirs. But when I fell into the initramfs shell, there were only the by-id and by-path subdirs, not the by-label and by-uuid. Later, when the main system is up, all four subdirs are there.

If you change your /boot/grub/menu.lst to have the "old style" root=/dev/sda1 kernel boot option, then the system will come up again.

OK and now in English? :-))) Sorry, I wonder if you could break this down for those of us who don't know much. 

To explain - I have an eee pc with ubuntu eee (now changed its name) on one partition and xp on the other. no probs there.

my father has a desktop pc with ubuntu installed through windows and he's not able to boot since the recent updates so... I will look on  my other computer to see what menu.lst might  need to look like. 

I can just about find grub folder and the menu.lst file in  my computer but cannot work out what to write or what to change in that file. 
Don't know how to get to that file on  my father's computer from Windows XP.  Might try with a live cd. 
I'd really appreciate any help. :-)

---

### Post by quill3033 on 2009-07-07
ok I found menu.lst through windows but windows cannot open it... so it looks like I can't change it from there.
It's in: 

C:\ubuntu\disks\boot\grub

So i think i'll have to get to it through live cd or external hdd

---

