---
title: "Gave up waiting for root device"
date: 2010-01-19
forum: New to Ubuntu
---

### Post by ShawnB391 on 2010-01-19
> 
[COLOR=black][FONT=Verdana]Boot_IMAGE=/boot/vmlinuz-2.6.31-16-generic root=UUID=9bb978bf-53f2-4b04-a5bd-771d315b9949 ro quiet splash[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Gave up waiting for root device. Common problems:[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]- Boot args (cat /proc/cmdline)[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]- Check rootdelay= (did the system wait long enough?)[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]- Check root= (did the system wait for the right device?)[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]- Missing modules (cat /proc/modules; ls /dev)[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]ALERT! /dev/disk/by-uuid/9bb978bf-53f2-4b04-a5bd-771d315b9949 does not exist. Dropping to a shell![/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana](initramfs)[/FONT][/COLOR]

 
[COLOR=black][FONT=Verdana]This is the error message that I get when I try to start my computer, it began after an update/reboot...[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]I changed rootdelay to 90, problem still exists. I changed rootdelay to 600, problem still exists...[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]I booted from a live cd to attempt a recovery some very important files, I couldn't find my Ubuntu folder, but I was able to locate my windows partition through the filesystem...[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]How can I get into my desktop to copy my homework? [/FONT][/COLOR]

---

### Post by drascus on 2010-01-20
when the computer displays the Grub boot loader hit Esc key and select either an older kernel image or the safe mode. when booting from a cd or usb your harddrive should be listed under Places and should appear as a device.

---

### Post by vijay_uforum on 2010-01-22
Hi, please check this one, it solved mine.
[http://www.uluga.ubuntuforums.org/showthread.php?t=1381617](http://www.uluga.ubuntuforums.org/showthread.php?t=1381617)

---

### Post by vijay_uforum on 2010-01-22
Find your root partition's uuid by using 
sudo blkid 

then create a sym link to that uuid in the /dev/disk/by-uuid folder, using
ln -s your-uuid-here /dev/disk/byuuid

---

### Post by jbatista on 2010-01-22
After booting Windows (blech!) and googling around, I did exactly as vijay described: a symbolic link to the actual /dev/sda# (mine was #=4, therefore /boot/grub/grub.cfg said set root=(hd0,4) ).

It still makes me wonder what might be lurking in the system that would've deleted that symbolic link. :confused:

---

### Post by JKyleOKC on 2010-01-22
> **jbatista said:**
> After booting Windows (blech!) and googling around, I did exactly as vijay described: a symbolic link to the actual /dev/sda# (mine was #=4, therefore /boot/grub/grub.cfg said set root=(hd0,4) ).

It still makes me wonder what might be lurking in the system that would've deleted that symbolic link. :confused:It may not have been deleted. During the boot process those numbers are assigned as the boot program discovers the partition, and sometimes this sequence changes (possibly according to the phase of the moon or some other mysterious reason). That's why grub & co. use the UUID rather than the partition number in most situations; it won't change.

Perhaps something changed a bit in the UUID being used, so that it became different from the one assigned to the partition...

---

