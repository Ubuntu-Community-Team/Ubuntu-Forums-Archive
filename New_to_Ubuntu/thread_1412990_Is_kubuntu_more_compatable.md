---
title: "Is kubuntu more compatable?"
date: 2010-02-21
forum: New to Ubuntu
---

### Post by WubiNoob on 2010-02-21
I was wondering if kubuntu was more compatable with some of the very inportaint drivers like wi-fi, that ubuntu just does not understand flat out. I am considering switching to kubuntu 9.10, and wanted to know how the change would affect me. If wi-fi dosent even work(BroadCam Chipset), then there really is no point. I don't want to install kubuntu if these don't work, because then the only difference would be a couple of widgets on the desktop. 

In general: ubuntu or kubuntu for driver compatability?:confused:

---

### Post by Ozymandias_117 on 2010-02-21
There is no difference between the two on that front. The only difference is your desktop manager (Gnome or KDE)

---

### Post by Ozymandias_117 on 2010-02-21
Have you tried System > Administration > Hardware Drivers? Usually wireless drivers show up there and you can just click and install them.

---

### Post by WubiNoob on 2010-02-21
Yes, and they only work on the Live CD mode. Once installed to the hard drive, the drivers won't even show up. This has been the case for all ubuntu like distros, exept linux mint. I guess the desktop really is the only difference.

---

### Post by marshmallow1304 on 2010-02-22
Did you update your package list before opening the Hardware Drivers utility?

```
sudo apt-get update
```

---

### Post by clint0n on 2010-02-22
Can you hook up the computer in question to the internet via ethernet(hard-wired)?

---

### Post by KIAaze on 2010-02-22
I use Kubuntu.
There shouldn't be any differences with the drivers since both distros use the same kernel and modules.

However I have several problems with Kubuntu:
-Kernel sometimes hangs when I plug in a USB stick (I think it's a conflict with gvfs, but not sure yet): [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/514485](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/514485)
-Sound in flash, skype and GTK apps like VLC doesn't work sometimes (seems to be when a KDE app is using sound)
-Sometimes my screen becomes completely garbled. Have to restart plasma-desktop. (and even then the system tray icons are broken)

I haven't run Ubuntu on this PC yet, so it's possible that not all problems are related to KDE.
So while KDE is pretty great, Kubuntu doesn't seem to be the best implementation of it.
I mainly stick to it because of Klipper and the more stable desktop effects (except for [this bug]("https://bugs.launchpad.net/ubuntu/+bug/474654")).

It also offers scale/expose for all windows or just the windows of the current desktop. Does compiz have that yet?

---

