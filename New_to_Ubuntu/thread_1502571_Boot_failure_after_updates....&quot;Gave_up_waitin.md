---
title: "Boot failure after updates....&quot;Gave up waiting for root...&quot;"
date: 2010-06-05
forum: New to Ubuntu
---

### Post by gaodan on 2010-06-05
After some auto-updates Ubuntu 9.04 will not boot (hard disk partitioned, Windows XP still boots ok). Tried booting from CD, unsuccessful. Excuse me but I am inexperienced and unfamiliar with the Linux lingo: I get to to the screen which lists the Ubuntu kernels, generic and recovery and also the Windows XP boot option, is this the Grub screen? 

From there I select one of the kernel options and the boot process starts as normal, when I select the 'older' kernels the Ubuntu logo appears as before, the cirle (hourglass) ticks away for a while and then nothing, when I select the 'new' kernel the Ubuntu logo looks slightly different, then I get

------------------------------------------------------

Boot from (hd0,4) ext3    9d651bb1-107a046f4-a088-d4b85e152899
Starting up...
Loading, please wait....
Gave up waiting for root device.  Common problems:
  -Boot args (cat /proc/cmdline) 
    -Check rootdelay=(did the system wait long enough?)
    -Check root= (did the system wait for the right device?)
 - Missing modules (cat proc/modules; ls/dev)
ALERT! /dev/disk/by-uuid/9d651bb1-10a-46f4-a088-d4b85e152899 does not exist. Dropping to a shell!


Busybox v1.10.2 (Ubuntu 1;1.10.2-2ubuntu7) built-in shell  (ash)
Enter 'help' for a list of built-in commands.

(initramfs)


----------------------------------------------------------


I've looked extensively on the forums and found a similar problem on several posts. I've tried the suggested fixes but haven't got very far. I can get a grub> command line but not sure what to do with it, any help much appreciated.

---

### Post by Elfy on 2010-06-06
You need to check the uuid for the root drive - somehow get the livecd to boot - you don't say why it won't.

Run this from a terminal 

```
ls -al  /dev/disk/by-uuid/
```

Make a note - carefully - of the uuid for the drive with /

Reboot - when you get to the grub menu - shift to see it if it's normally hidden.

Highlight the first line and press e

You will now have a screen similar to the screenshot - change the UUID to the value you noted down previously - there will be 2 lines to change. Esc to return to previous menu - enter to boot with edited entry.

Assuming that works run this from a terminal 

```
cat /boot/grub/grub.cfg |grep UUID
sudo update-grub
cat /boot/grub/grub.cfg |grep UUID
```

I'd expect that the first 'cat' would show the old UUID and the second the one you gor from the livecd.

---

### Post by Gone fishing on 2010-06-06
forestpiskie - I had a similar problem but with a RAID1. I wanted to change mother boards to one with more PCI slots. I think one motherboard emulated PATA and the other didn't.

Anyway I did the UUID thing and updated grub but couldn't get it to boot, I guess something to do with mdadm setup any tips? I might try again.

---

### Post by Elfy on 2010-06-06
@ Gonen fishing - sorry I can't be any assistance - raid to me is what robbers do to banks ... 

I would suggest you post a thread about the issue

---

### Post by gaodan on 2010-06-06
Managed to boot from a cd this time, opened a terminal and 
typed 


 	Code:
 	ls -al  /dev/disk/by-uuid/ 
the following came up :
---------------------------------------------------------------------
             [SIZE=2]ubuntu@ ubuntu:-$ ls –al /dev/disk/by-uuid/[/SIZE]
  [SIZE=2]total 0[/SIZE]
  [SIZE=2]drwxr-xr-x 2 root toot 100 2010-06-06 12:52  .[/SIZE]
  [SIZE=2]drwxr-xr-x 6 root toot 120 2010-06-06 12:53[/SIZE]
  [SIZE=2]lrwxrwxrwx 1 root root 10 2010-06-06 12:52 3d00d2b6-591a-4561-93cf-e38a5066cef0[/SIZE]
  [SIZE=2] -> ../../sda6[/SIZE]
  [SIZE=2]lrwxrwxrwx 1 root root 10 2010-06-06 12:52 9d651bb1-107a-46f4-a088-d4b85e152899 [/SIZE]
  [SIZE=2]->../../sda5[/SIZE]
  [SIZE=2]lrwxrwxrwx 1 root root 10 2010-06-06 12:52 A87CBE5F7CBE2848 -> ../../sda1[/SIZE]
   -----------------------------------------------------------------------------------------

[COLOR=Black]"Make a note - carefully - of the uuid for the drive with /"

Which drive? 

The uuid beginning 9d65...... is the the one that appears when I enter 'e' from the grub menu (grub menu is the one that lists the OS options ie Ubuntu 9.04, kernel 2.6.27-17-generic etc ?)

When I enter 'e' I get the following:

------------------------------------------------------------------------
uuid 9d651bb1-107a-46f4-a088-d4b85e152899
kernel  /boot/vmlinuz-2.6.27-17-generic root =uuid=9d651bb1-107a-46f4-a088-d4b85e152899 ro quiet splash
initrd /boot/initrd.img-2.6.27-17-generic
quiet
-----------------------------------------------------------------------
[/COLOR] Tried editing the kernel line with 'kernel /boot........ root=dev/sda5' but still no joy.

---

### Post by Elfy on 2010-06-06
The UUIDs appear to match.

Try this - let it boot to the initramfs shell - wait a few minutes and then type exit and enter - does it boot after that?

---

### Post by gaodan on 2010-06-06
From 'initramfs' I type 'exit' and it brings me straight back to 'initramfs'

---

