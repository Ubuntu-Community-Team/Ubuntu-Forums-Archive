---
title: "Installed updates from update manager now will not boot"
date: 2010-01-07
forum: New to Ubuntu
---

### Post by lostmarine85 on 2010-01-07
I installed Ubuntu using Wubi 9.10 I just installed the lastest updates and now Ubuntu will not boot. Now it tries to boot and it goes to a black screen like DOS. I am thinking about uninstalling and reinstalling but I would prefer not to loose all of my data like command prompt.

---

### Post by ubudog on 2010-01-07
What updates did you install?

---

### Post by lostmarine85 on 2010-01-07
I'm not sure I was on the internet and the update manager thing popped up and said there were updates so I clicked install then it said it needs to reboot so I click reboot and now it won't boot ubuntu.

---

### Post by lostmarine85 on 2010-01-07
I rebooted it tries to load ubuntu and the says no wubildr on a black screen then opens a thing like command prompt I pressed tab to get the commands and typed boot it say no kernel

---

### Post by tom.swartz07 on 2010-01-07
> **lostmarine85 said:**
> I installed Ubuntu using Wubi 9.10 I just installed the lastest updates and now Ubuntu will not boot. Now it tries to boot and it goes to a black screen like DOS. I am thinking about uninstalling and reinstalling but I would prefer not to loose all of my data like command prompt.

Looks like you got a bad kernel update, and/or a bad GRUB update. No biggie.

Try and boot to a LiveCD. 
open a terminal from applications>accessories, type ```
sudo fdisk -l
```

and post the output here.

I could help you rebuild your bootloader and get back up.



EDIT::::

I didnt see youre using WUBI. This has been happening quite a bit lately.
If you can boot to Windows, Defragment your hard drive several times. I would suggest the free program Defraggler. Its free on Cnet.

Try defragging and then booting into your Ubuntu build.

---

### Post by lostmarine85 on 2010-01-07
I'm not sure how to do that I'm in Windows XP right now so I reboot and when it goes to the command prompt thingy type sudo fdisk -l??

> **tom.swartz07 said:**
> Looks like you got a bad kernel update, and/or a bad GRUB update. No biggie.

Try and boot to a LiveCD. 
open a terminal from applications>accessories, type ```
sudo fdisk -l
```

and post the output here.

I could help you rebuild your bootloader and get back up.



EDIT::::

I didnt see youre using WUBI. This has been happening quite a bit lately.
If you can boot to Windows, Defragment your hard drive several times. I would suggest the free program Defraggler. Its free on Cnet.

Try defragging and then booting into your Ubuntu build.

---

### Post by bcbc on 2010-01-07
Try the following (if it fails search the forums - this happened to a lot of people running karmic using Wubi - and there are a lot of posts about it):
> Re: sh:grub > desperation 
WUBI Installs Only

I tried wubi when it first came out a few years ago but am no longer familiar with exactly how it works. There were enough problems recently that I rearranged my laptop's partitions so I could once again install wubi. Once I got wubi installed, I experimented until I could boot from a grub prompt. 

This is how I am able to manually boot from the Grub 2 prompt in wubi. My Windows partition is on sda1, which would be fairly standard.

Lines starting with a # are explanatory only. Do not type them.

Quote:
# Add the ntfs module
insmod ntfs
# Set root (normally would be sda1, or hd0,1 Change as necessary
set root=(hd0,1)
loopback loop0 /ubuntu/disks/root.disk
# Yes, set root for a second time. I don't know why...
set root=(loop0)
# Set the kernel. You can (and should) use Tab (twice) to complete entries such as the kernel when possible - type vml and then TAB twice and it will autocomplete to the point where there are two possibilities. Tab complete ensures the path/file names as typed exist. Additionally, if you suspect the new kernel is the problem, you might want to select an earlier one. vmlinuz.... should be a complete kernel entry such as "vmlinuz-2.6.31-15-generic-pae" *
linux /boot/vmlinuz.... root=/dev/sda1 loop=/ubuntu/disks/root.disk ro
# Set the initrd image - complete or tab to get the full name Example: "/boot/initrd.img-2.6.31-15-generic-pae"
initrd /boot/initrd/initrd.img... 
# Boot.
boot 


* If this line scrolls off the screen as you type it, due to its length: To make it easier type "linux root=/dev/sda1 /ubuntu/disks/root.disk ro" and then cursor back before "root=" to type/tab in the kernel name.


If you successfully boot, run "sudo update-grub". Also inspect your /etc/default/grub file, which contains menu timeout and default kernel selections and determine if there is a problem with the menu.
__________________
GRUB2 : G2-Tweaks G2-Basics
G2-Tasks DiskSpace 
Expand / SUM 
Last edited by drs305; 1 Hour Ago at 06:24 PM

---

### Post by tom.swartz07 on 2010-01-07
> **lostmarine85 said:**
> I'm not sure how to do that I'm in Windows XP right now so I reboot and when it goes to the command prompt thingy type sudo fdisk -l??

I edited the post- Sorry- I shouldve cut the top.

You should try defragging the computer.
Many times when XP fragments the files for Ubuntu (Wubi installs ubuntu as a program file in Windows), Ubuntu gets lost and confused and wont boot. 9 times out of 10 a good Defrag will clear up the problem

---

