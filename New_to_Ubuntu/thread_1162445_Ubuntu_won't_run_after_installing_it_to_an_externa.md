---
title: "Ubuntu won't run after installing it to an external drive."
date: 2009-05-17
forum: New to Ubuntu
---

### Post by GreenBowlPacker_3 on 2009-05-17
I have a Dell laptop running Windows XP on the C: drive. I have lots of external drives and I want to put Ubuntu on one of those. When I try to install inside of Windows it asks me what drive I want to install to, but it still installs to me C: drive. If I boot my computer with Ubuntu and select the install option everything goes smooth until I'm asked to reboot. After bios loads I get a OS menu, when I select Ubuntu this is what i get.
```
Boot from (hd1,0)ext3 7ebd8325-3415-4a2d-be09-985ddeb2d951
Starting up...
```
After that the screen goes black and this shows up.
```
[ 0.476001] ..MP-BIOS BUG: 8254 TIMER NOT CONNECTED TO IO-APIC
[ 2.504009] ata1: softrest failed (device not ready)
modprobe: fatal: could not load /lib/modules/2.6.28-11-generic/modules.dep: no such file or directory

Loading please wait...
```
Everything seems to be ok after that, I get the screen with the Ubuntu logo and the status bar. After a few minutes this gets up under evrything else.
```
Gave up waiting for root device, common problems:
 - Boot args (cat /proc/cmdline)
  -Check boot delay= (Did the system wait long enough?)
  -Check root= (Did the system wait for the right device?)
 -Missing modules (cat /proc/modules; ls/dev)
ALERT!  /dev/disk/by-uuid/ 7ebd8325-3415-4a2d-be09-985ddeb2d951 does not exist.  Dropping Shell!
busybox v1.10.2 (ubuntu 1:1 .10.2-2ubuntu) built in shell (ASH)

Enter 'help' for a list of built-in-commands

(initramfs) _
```
Can someone please help? I would like to use Ubuntu, but the only way it seems to work is on my C: drive, and I would rather have it on an external if possible.

---

### Post by bolucpap on 2009-05-18
A workaround that I used for that very same problem is this:

-Wait for the busybox prompt to appear.
-Unplug your external drive from the usb socket
-Plug it back in.
-Wait for some system message such as "assuming drive cache" or some such.
-Type "exit".

Booting will resume.

---

### Post by GreenBowlPacker_3 on 2009-05-19
Is there any way to fix it, or is that how I will have to start it everytime?

---

### Post by bolucpap on 2009-05-20
I'm waiting for a kernel upgrade. Perhaps someone with better technical knowledge will be able to help.

---

