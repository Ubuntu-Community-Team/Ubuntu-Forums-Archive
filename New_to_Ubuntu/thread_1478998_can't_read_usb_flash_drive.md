---
title: "? can't read usb flash drive"
date: 2010-05-10
forum: New to Ubuntu
---

### Post by glngil40 on 2010-05-10
I just installed ubuntu 10.04 LT , but it doesn't allow me to get data from my flash drive.
any help would be great. The flash drive is formated FAT reads on my win 7 machine okay. when i insert it into the ubuntu the lights flash , system doesn't see this drive on the system.

---

### Post by nikhilbhardwaj on 2010-05-10
you'll need to provide us with more details
this vague description doesn't help identify the problem

do this
insert your flash drive and post the output of
```

dmesg | tail
sudo fdisk -l

```

i'm assuming you know where to execute these commands
if not just ask

---

### Post by YuiDaoren on 2010-05-10
Can you be more specific?

How is the drive formatted (What file system)?
Any error messages you get, if any?
Do you see the drive mount (icon on desktop) or nothing?

---

### Post by glngil40 on 2010-05-10
shows nothing

---

### Post by glngil40 on 2010-05-10
nothing

---

### Post by achase79 on 2010-05-10
plug in the flash drive and post the result of running lsusb in terminal.

---

### Post by Calash on 2010-05-10
> **glngil40 said:**
> nothing

For us to be able to help you we are going to need a lot more information than just single word responses.

In Post #2 are a couple of lines to try.  These are run in the terminal (Applications>Accessories>Terminal).  They are not designed to fix anything but to give us information on what may be wrong.

Run each line and then copy the output and paste it into a reply.  Surround the output with the following tags

[php]
```
Your Output
```
[/php]

This will keep the formatting and make it easier for us to read.

---

### Post by Irony on 2010-05-10
Perhaps it is this problem;

[http://shallowsky.com/blog/linux/kernel/lucid-udev.html](http://shallowsky.com/blog/linux/kernel/lucid-udev.html)

---

### Post by glngil40 on 2010-05-10
user@user-desktop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 13fe:1a00 Kingston Technology Company Inc. 512MB/1GB Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
user@user-desktop:~$

---

### Post by Calash on 2010-05-10
Well, it is show up, that is a good thing.

Try this.  With the USB key plugged in go to System>Administration>Disk Utility

On that screen check and see if there is an entry for your flash drive under Peripherals.

If so, highlight it, and at the bottom press the "Mount Volume" button and see if it then shows up.


I have seen similar issues where they volume is just not auto mounting, but works fine.  Most of the time it has to do with having VirtualBox installed, or custom entries in /etc/fstab.

---

### Post by glngil40 on 2010-05-10
if i boot with it in it gets recognized. if i remove it and put it back it now see the flash drive again. thanks all for the help

---

