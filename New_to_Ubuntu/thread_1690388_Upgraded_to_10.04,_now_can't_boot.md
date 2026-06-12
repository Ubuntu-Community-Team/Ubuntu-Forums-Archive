---
title: "Upgraded to 10.04, now can't boot"
date: 2011-02-18
forum: New to Ubuntu
---

### Post by elementzero on 2011-02-18
So I was on 8.04, and I decided to hit the upgrade button on the gui to upgrade to 10.04.  Well the upgrade went fine and all...until I rebooted.  Now I get this

--------------------------------------------------------------------
Starting up ...
mount: mounting none on /dev failed: No such device
udevd[984]: error getting socket: Invalid argument

error initializing netlink socket
udevd[984]: error initializing netling socket

libudev: udev_monitor_new_from_netling: error getting socker: Invalid argument
Segmentation fault
There appears to be one or more degraded LVM volumes, and your root devide may depend on the LVM volumnes being online.  One or more of the following LVM volumes are degraded:
red_urandom: /dev/urandom: open failed: No such file or directory
Gave up waiting for root deive.  Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/sda1 does not exist.  Dropping to a shell!

Busybox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
----------------------------------------------

FYI if I do ls /dev I get this

console     pts     tty2     tty4     tty6
null           tty1    tty3    tty5  

I found some other posts and tried adding the rootdelay=35 and acpi=off but those did not fix it.  This is a virtual machine running on VMWare ESXi 4.1 if that helps.

Anybody have any ideas as to what to do next?

---

### Post by elementzero on 2011-02-18
Moving the thread to the Installations & Upgrades forum

[http://ubuntuforums.org/showthread.php?t=1690498](http://ubuntuforums.org/showthread.php?t=1690498)

---

