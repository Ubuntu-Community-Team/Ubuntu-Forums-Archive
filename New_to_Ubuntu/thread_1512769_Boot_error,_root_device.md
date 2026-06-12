---
title: "Boot error, root device"
date: 2010-06-18
forum: New to Ubuntu
---

### Post by blackhydra866 on 2010-06-18
I've searched this and tried the only solutions which have made sense to me but it's still not working.

First time installing xubuntu on a fresh formatted hard-drive I get this on boot:

```
Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
 - Check rootdelay= (did the system wait long enough?)
 - Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by/-uuid/8af17d27-4f54-4564-9fb6-e4344095988c does not exist. opping to a shell!

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in comannds.

(initramfs)
```[http://imgur.com/GNcd5.jpg](http://imgur.com/GNcd5.jpg)

Thanks in advance.

---

### Post by Gone fishing on 2010-06-18
This is bad

On boot the system is not finding / . As its a clean install I'd suggest starting again as something has gone wrong with the installation.

However, this looked interesting  

[http://www.kevinbrosnan.net/upgrading-to-ubuntu-910](http://www.kevinbrosnan.net/upgrading-to-ubuntu-910)

and suggests the following commands 

```
mount -o remount, rw /
grub-install --recheck /dev/sda
```

from a live CD

---

### Post by blackhydra866 on 2010-06-19
sudo mount -o remount, rw / doesnt seem to do anything, and doesn't give me an error in terminal. just scrolls to the next line.

grub-install --recheck /dev/sda returns:

```

/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?)
No path or device is specified.
Try '/usr/sbin/grub-probe --help' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option '--modules' explicitly.

```

---

### Post by Gone fishing on 2010-06-20
How many hard drives do you have in the Box? Is it just the one or is grub on a different hard drive to / ?

---

### Post by wilee-nilee on 2010-06-20
A new install might be the answer, but if you can post the script in my sig we can see whats going on better post it in code tags .

---

