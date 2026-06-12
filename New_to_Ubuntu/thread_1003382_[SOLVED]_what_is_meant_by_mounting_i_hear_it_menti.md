---
title: "[SOLVED] what is meant by mounting i hear it mention a lot?"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by aszxcv on 2008-12-06
???

also what is the purpose of swap file?

---

### Post by jpoRS on 2008-12-06
Simple answer:

When one mounts a drive/device/whatever else, one is simply attaching it to the filesystem, allowing you to access, and depending on permissions, modify files contained within.

jim

---

### Post by cdtech on 2008-12-06
Mounting is a process by which you make a separate filesystem available to the system. After mounting a filesystem, your files and directories will be accessible under the mount-point you chose to mount the filesystem. Most mount points are located within the /mnt and /media directories.

You can read about using "swap" and why here:
[http://www.linux.com/feature/121916](http://www.linux.com/feature/121916)

---

### Post by rev0lv3r on 2008-12-06
If you have enough ram (more than 2gb... **** probably more than 1gb even) you should set swappiness to near 0.

Unused ram is wasted ram.

---

### Post by 3rdalbum on 2008-12-06
> **aszxcv said:**
> ???

also what is the purpose of swap file?

In case you were wondering, mounting is the correct computer term regardless of operating system. It's not a Linux-specific term.

A swap file is what Windows calls a "pagefile". On Linux we generally use a swap partition rather than a swap file, as it's faster and more reliable.

---

### Post by snova on 2008-12-06
Under Windows, different devices/partitions are assigned a drive letter, which you use to differentiate between each device.

Unix has taken a different route from its beginning, in which there is only one filesystem. When you want to access a device, you "mount" it, which essentially attaches the device to the filesystem at a specified point.

---

### Post by newbee70 on 2008-12-06
> **aszxcv said:**
> ???

also what is the purpose of swap file?


A file stored on the computer hard disk drive that is used as a temporary location to store information that is not currently being used by the computer RAM. By using a swap file a computer has the ability to use more memory  than what is physically installed in the computer. However, users who are low on hard disk space may notice that the computer runs slower because of the inability of the swap file to grow in size. 

It is perfectly normal for the swap file or page file to grow in size, sometimes growing several hundred megs in size.

---

