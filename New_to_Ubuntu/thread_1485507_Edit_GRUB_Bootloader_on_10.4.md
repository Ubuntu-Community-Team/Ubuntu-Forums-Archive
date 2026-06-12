---
title: "Edit GRUB Bootloader on 10.4"
date: 2010-05-16
forum: New to Ubuntu
---

### Post by walkerchuckwalker on 2010-05-16
Can someone please help, I want to edit the grub boot loader to get rid of some of those extra entries in the list. I have tried typing 

/boot/grub/menu.lst

sudo /boot/grub/menu.lst

sudo vi /boot/grub/menu.lst

and this one seemed to kinda work:

gksudo gedit /boot/grub/menu.lst

So I typed the above gksudo gedit /boot/grub/menu.lst into terminal and gedit came up but is blank, theres no entries, typing, or anything. I have tried to manually go to the /boot/grub directory and find menu.lst and its not a file in that directory. Could someone please post a small beginner guide to editing the boot loader? I just installed Ubuntu 10.4 Could GRUB be updated?



Ok, so I have go to Synaptic Package and found the entires

linux-headers-2.6.32-22
linux-headers-2.6.32-22-generic
linux-image-2.6.32-22-generic
linux-image-2.6.32-21-generic

Which should I uninstall? The -21 or -22? There is only 1 -21 entry.

---

### Post by nhasian on 2010-05-16
your not suppose to edit grub2 by hand like you did with the legacy grub.  do you just want to get rid of the older kernels listed during bootup?  You can do that from the synaptic package manager.  There are three packages that must be removed for each kernel:

linux-headers-2.6.32-xx
linux-headers-2.6.32-xx-generic
linux-image-2.6.32-xx-generic

you should also probably run from a terminal:

```
sudo update-grub
```

if you would like to tweak your boot menu you can use:

```
sudo apt-get install startupmanager
```

---

### Post by Ozymandias_117 on 2010-05-16
Grub 2 uses the file /etc/default/grub and the folder /etc/grub.d

Here is a good guide on modifying it:
[http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")

---

### Post by drs305 on 2010-05-16
In addition to the Grub 2 Basics thread previously mentioned, there are several additional threads in my signature line for accomplishing particular things with Grub 2. 

Some are pretty geeky, while others are fairly easy to implement. The "G2-Basics" link may be all you need.

There is also startupmanager, a GUI app originally designed for Grub legacy but which can still set some of the basic Grub 2 settings.

---

### Post by walkerchuckwalker on 2010-05-17
> **nhasian said:**
> your not suppose to edit grub2 by hand like you did with the legacy grub.  do you just want to get rid of the older kernels listed during bootup?  You can do that from the synaptic package manager.  There are three packages that must be removed for each kernel:

linux-headers-2.6.32-xx
linux-headers-2.6.32-xx-generic
linux-image-2.6.32-xx-generic

you should also probably run from a terminal:

```
sudo update-grub
```if you would like to tweak your boot menu you can use:

```
sudo apt-get install startupmanager
```
Thank you SO much, and for everyone else with the same problem, THIS WORKS!!!

Go to Synaptic Manager and type -2.6.32 and you should find what you need.

---

