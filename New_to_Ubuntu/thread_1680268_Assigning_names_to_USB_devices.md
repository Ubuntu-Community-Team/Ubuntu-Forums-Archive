---
title: "Assigning names to USB devices"
date: 2011-02-02
forum: New to Ubuntu
---

### Post by lesliek on 2011-02-02
I was having problems yesterday mounting a USB HDD in Ubuntu 10.04. It wasn't mounting automatically and I couldn't mount it manually. When I plugged it in, it showed up in dmesg and in lsusb, but it wasn't being given a name like /dev/sdb1. I know that because, when I ran "ls /dev/sd?" or fdisk or gparted, all that appeared was either my internal HDD, /dev/sda, or its partitions.

I confirmed that the problem wasn't my hardware by using a Knoppix live CD in my computer. When I did that and plugged the USB HDD in, it automatically mounted, having been given the name /dev/sdb1.

Today, the problem's gone away, but I'm afraid it'll be back, so I'd like to understand how Ubuntu assigns names to USB devices when they're plugged in. Is there some straightforward explanation of that available?

Thanks,

Leslie

---

### Post by cipherboy_loc on 2011-02-02
1) What type of USB Drive was it? (Make/model/manufacturer)
2) How long have you had this flash drive? Did you just get it, or have you had it for some time, and the problem just appeared?

Also, if I understand it correctly, the device path (/dev/sd[a-z][number]) is assigned by the Linux Kernel and the udev/rdev commands. 


Cipherboy

---

### Post by ajgreeny on 2011-02-02
I would try re-formatting it with gparted, probably as a fat32 partition filling the drive, depending on its size, and when you have the partition made give it a label that means something to you, again using gparted.  Then when it mounts, it will automatically mount to /media/<label>

---

### Post by srs5694 on 2011-02-02
If I understand correctly, the problem occurred once and then went away after a reboot. If so, I wouldn't worry about it unless it starts to recur regularly. I've seen this sort of thing before, and I suspect it's data corruption or a bug in the kernel or udev subsystem. (Linux uses udev to assign device filenames in /dev.) For me, it happens very rarely -- once a year or so, on over half a dozen computers.

If it does occur frequently for you, I recommend you use "dmesg" and "udevadm monitor" to investigate. The "dmesg" command displays the kernel ring buffer. Type this command (perhaps piped through "tail", as in "dmesg | tail") before and after inserting the disk to see if any kernel errors appear. You can use "udevadm monitor" to see what udev is doing with the device; type that command before inserting the device and you'll see messages when you insert it. Perhaps it'll show an error or some other clue about why it's not getting a device name.

---

### Post by quadproc on 2011-02-02
> **lesliek said:**
> I was having problems yesterday mounting a USB HDD in Ubuntu 10.04. It wasn't mounting automatically and I couldn't mount it manually.
This sounds like the system could not see the disk.  Did you retry the boot without changing anything?  If so, did the same problem occur?  Did you look in /media?

You may have encountered a race condition.  I have recently managed to determine that the system which I am using occasionally encounters a race condition which prevents the graphics from working properly at login time.  A similar problem could prevent a disk from mounting every now and then.

quadproc

---

