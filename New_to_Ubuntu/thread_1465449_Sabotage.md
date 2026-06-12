---
title: "Sabotage"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by KirbySmith on 2010-04-29
Just when I thought my 9.10 build was working well enough to permanently say goodby to windows, today's security updates left ubuntu unstartable. What appears to have happened is that one of the updates decided to modify grub. Grub now presents an unwanted option to start a probably broken windows instance on a drive connected by USB I was about to move data from. Grub now expects ubuntu to be on sdd1, probably a data drive it found. However, ubuntu resides by itself on a drive with partitions sdc1, 2, and 5.
 
If data drives are present, the boot loader complains that it cannot find the files it wants. 
 
With all data drives removed, grub exclaims:
 
ALERT! /dev/sdd1 does not exist. Dropping to shell.
 
(At least I know it is using the grub on the ubuntu drive.)
 
In this state the shell allows ls /dev to confirm that sdc1, 2, and 5 exist. Minimal naive investigation shows that the usual high level directories are still present in the directory the shell is operating from.
 
Soooo, what I need to do is repair grub2's configuration somehow, either by some action in this limited capability shell, or via the live cd. I would prefer to not waste the last two weeks of configuration and tweaking by reinstalling from scratch.
 
Can the live cd pretend it is doing an upgrade of itself and fix grub indirectly?
 
If not, What files should I edit (with what changes) from the live cd? Or from the shell that the grub failure reveals assuming it has an editor that I didn't notice in its commands listing?
 
Thanks in advance
 
kirby
__________
it just works

---

### Post by limey_rick on 2010-04-29
You should be able to use the Live CD and re-install grub where you need it. 

See here for more info: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Specifically here: [https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

If you need more help, let the forum know.

---

### Post by KirbySmith on 2010-04-29
Thanks, limey-rick, that information looks like just what I need! I should be able to report success tomorrow.
 
kirby

---

### Post by tom.swartz07 on 2010-04-29
That should fix it. When you removed the windows partition, you probably didnt update grub to reflect the changes. That threw grub into a tailspin.

Just reinstall it and you should be great to go!

---

### Post by KirbySmith on 2010-04-29
tom.swartz07
 
Windows was never present when I built ubuntu onto a fresh drive. However, it is present on a drive I recently put into a USB caddy so I could move various files from its drive through ubuntu's kidneys into another USB caddy that has an empty drive formated in ext4. Unfortunately, this morning's "upgrade" occurred just as I was about to change ownership of the second USB drive so I could move the files there.
 
I would not claim, however, that I had no part in putting grub into a tailspin. My computer configuration and attempts to utilize data from various historical drives is perhaps unconventional. I still believe (without direct proof) that a simple conventional computer configuration (without an nVidia video card) would have had a high probability of an event-free install missing the sturm und drang of the last two weeks relating to video, sound, and usb drive detection, to name some highlights.
 
Thanks
 
kirby

---

### Post by tom.swartz07 on 2010-04-29
> **KirbySmith said:**
> tom.swartz07
 
Windows was never present when I built ubuntu onto a fresh drive. However, it is present on a drive I recently put into a USB caddy so I could move various files from its drive through ubuntu's kidneys into another USB caddy that has an empty drive formated in ext4. Unfortunately, this morning's "upgrade" occurred just as I was about to change ownership of the second USB drive so I could move the files there.
 
I would not claim, however, that I had no part in putting grub into a tailspin. My computer configuration and attempts to utilize data from various historical drives is perhaps unconventional. I still believe (without direct proof) that a simple conventional computer configuration (without an nVidia video card) would have had a high probability of an event-free install missing the sturm und drang of the last two weeks relating to video, sound, and usb drive detection, to name some highlights.
 
Thanks
 
kirby

Ah, my bad. I misunderstood your original post. I apologize. 
On this note, I will simply bow out. Good luck with it.

---

### Post by KirbySmith on 2010-04-30
I have been unsuccessful resolving the problem competing with the computer to see who is the bigger idiot, the machine that won't learn or the user who tries variants of the same thing hoping for a different result.  Windows is still in the grub boot list, and selecting a kernel leads to the complaint that grub can't find sdd1.

The process in detail, running from the Live CD, and performing the first set of steps in the Grub2 documentation called Reinstalling from LiveCD.  

Running 

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009ba9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       18706   150255913+  83  Linux
/dev/sdb2           18707       19457     6032407+   5  Extended
/dev/sdb5           18707       19457     6032376   82  Linux swap / Solaris

```This is pretty much the expected result, except that there is at present only one hard drive in the machine, and the motherboard BIOS shows only one hard drive.  So why does ubuntu assign this drive to be "sdb"?

Next steps are: 
```

ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sdb
Installation finished. No error reported.
This is the contents of the device map /mnt//boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda
(hd1)    /dev/sdb
(hd2)    /dev/sdc


```There are a couple of problems here.  Now we have evidence that grub thinks there are three drives when there is only one, and it is on IDE0 so one would expect it to be hd0.  A search with nautilus finds the device map, but I am unclear what I should do with it.  Kill hd0 and hd2?  Kill hd1 and hd2?  Kill everything and let it get reconstituted?

Anyway, whatever is happening, I end up with an old version of some grub configuration file being used to boot with.  The grub2 guide has three methods for reinstallation, but they seem to assume that within the existing installation, there is a good set of files, not a set that got messed up.  I need to know how to get into grub2 and flush whatever is wrong with it and force it to re-probe the system. 

Thanks for any help you can give

kirby

---

### Post by Sealbhach on 2010-04-30
> **KirbySmith said:**
>  The grub2 guide has three methods for reinstallation, but they seem to assume that within the existing installation, there is a good set of files, not a set that got messed up.  I need to know how to get into grub2 and flush whatever is wrong with it and force it to re-probe the system. 

Thanks for any help you can give

kirby

Just run 

sudo update-grub

This will probe for other OS's and update the grub.cfg for you.

.

---

### Post by KirbySmith on 2010-04-30
Hunting in the files while reading the Grub2 instructions I find that this sdd1 mistaken partition is rampant in grub.cfg.  So the os prober isn't updating it properly using the approach above.  

Maybe the directions should include Sealbhach's timely suggestion.

Thanks Sealbhach!   

Appending it to the still waiting terminal session I've used to copy responses to these messages, the result is:

```

ubuntu@ubuntu:~$ sudo update-grub
grub-probe: error: cannot find a device for /.


```This result may be due to my still being in Live CD, and the relevant files are mounted to /mnt/ (in the CD filesystem, I think).  I don't recall this being an available command in ash if I try to run it after the boot fails.

Is there a way to update grub as above but point it to the temporarily mounted file system.

Or, in desperation, maybe I could "cheat" and edit the grub.cfg file to get the installation to boot, and then run update-grub.

kirby

---

### Post by Sealbhach on 2010-04-30
Hi, are you following this guide? 

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

.

---

### Post by KirbySmith on 2010-04-30
This one

[[HTML]https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202[/HTML]]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")

---

### Post by Sealbhach on 2010-04-30
It's pretty much the same thing, I think.

.

---

### Post by KirbySmith on 2010-04-30
However, I can certainly try your alternative, as soon as I figure out what I have to change in [B]/etc/default/grub.

kirby
[/B]

---

### Post by KirbySmith on 2010-04-30
Actually, I doubt I have to change anything in that file.  But maybe this process, which is somewhat longer than the one I was using, will cause the desired result.  

Charging ahead....

---

### Post by KirbySmith on 2010-04-30
Just to document, including one bobble of no consequence:

```
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo mount --bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# nano /etc/default/grub
root@ubuntu:/# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-21-generic
Found initrd image: /boot/initrd.img-2.6.31-21-generic
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
done
root@ubuntu:/# grub install /dev/sdb
The program 'grub' is currently not installed.  You can install it by typing:
apt-get install grub
grub: command not found
root@ubuntu:/# grub-install /dev/sdb
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda
(hd1)    /dev/sdb
(hd2)    /dev/sdc
root@ubuntu:/# exit
ubuntu@ubuntu:~$ sudo umount /mnt/dev
ubuntu@ubuntu:~$ sudo umount /mnt/sys
ubuntu@ubuntu:~$ sudo umount /mnt/proc
ubuntu@ubuntu:~$ sudo umount /mnt

```It did build a new configuration file, and the windows went away, so a reboot is next in order.

kirby

---

### Post by KirbySmith on 2010-04-30
TA DA!!

ubuntu booted into a kernel menu from which I selected the top option (2.6.31-21-generic, which I think was the new update) and voila, the desktop appeared.  My delay is partly because the LAN connection was not functional, and the hard drive was working its butt off for no apparent reason.  (Maybe it was time for an ext4 health check.)

Anyway, an eventual second reboot yielded a functioning ethernet, (hard drive is still having a party by itself) and hence a chance to thank all of you, particularly sealbhach for his recent participation and helpful advice.  A virtual beverage of your choice is attached.

With respect to the two methods, sealbhach, the second that you suggested seems to actually update the configuration file as part of the process whereas the previous method expected the update to be performed after rebooting (with the assumption that rebooting would work.)

Now, how do I set the thread to solved?

kirby
_____________
now it just works

---

### Post by Sealbhach on 2010-04-30
Hey that's great Kirby, congrats! I think marking the thread solved would be in Thread Tools.

.

---

