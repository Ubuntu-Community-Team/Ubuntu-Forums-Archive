---
title: "minimal install can't find hard drive"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by rolypolycat on 2009-01-26
Hello!

My old computer died, so I'm running an old AMD-k6 3d processor, 300mhz, 384 mb ram. Since this isn't exactly blazing fast, I'm trying to install xubuntu, or a mimimal install, but neither type can find my hard drive. Xubuntu gets to "detect disks", then can't find them. It offers drivers; I've tried ide-generic, ide-core,ide-disk,ide-scsi-scsi-mod, wd7000 (it's a western digital)--neither worked. Scsi-debug worked, but it said my 160 gig drive was only 8mb.
Hardy minimal install fared little better. When it got to download installer components, it quit. Said libcrypto0.9.8-udeb wasn't there. These are good disks; I've used them time and again for installing on other computers.
I installed Simplymepis, and it installed perfectly, although slowly. I tried debian netinstall; everything went flawlessly until I booted into the desktop. Then I had 3 pointers, a blurry screen, and it's only clear at the first inches on the left side of the screen. I can't change the resolution because I can't see it well enough to tell what I'm changing. 
Whatever it is, simplymepis has no trouble finding everything, but hardy can't. Debian installs, but I can't see 3/4 of the screen. Any ideas what's happening, and how to fix them? I want to run openbox and pcmanfm, my two favorite softwares. This system isn't fast, so a window manager is my best bet.
Any help is greatly appreciated. Thanks!

---

### Post by lavinog on 2009-02-15
You might want to try western digitals lifeguard tools bootable cd to test the connection to the drive. The problem could be due to the wrong jumper setting. (using CS with a non CS cable can make weird issues)

Are there any warnings when you boot with the live cd?

Have you tried Damn Small Linux? It is supposed to be good for older machines.
Xubuntu might still be slow on that machine.

---

