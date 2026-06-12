---
title: "Asus Striker Extreme, 8.04 - No network"
date: 2008-06-07
forum: Networking &amp; Wireless
---

### Post by chatman22222 on 2008-06-07
Hi,

I have been using Ubuntu 7.10 for a while, but when i upgraded to 8.04 the network connections stopped working.

I think i remember reading about this somewhere, and it being a problem with the motherboard. However I have been unable to find the solution.

Any help or suggestions would be appreciated.

---

### Post by OnsoSan on 2008-09-21
here's a solution
[http://ubuntuforums.org/showthread.php?t=387312](http://ubuntuforums.org/showthread.php?t=387312)

what worked for me:
Add the following line to ***/etc/modprobe.d/options***

**options forcedeth msi=0 msix=0**

Then rebuild initramfs like this
**sudo update-initramfs -u**

and reboot

I hope that helps

---

### Post by babisvovos on 2008-09-21
Hey man, don't know if it helped the other guy but for me you are a life savier.
thanks

babis

---

### Post by OnsoSan on 2008-09-23
Considering the ***Announcement: ATTENTION ALL USERS: Malicious Commands***

More information about update-initramfs:

**Description:**
The **update-initramfs** script manages your initramfs images on your local box. It keeps track of the  existing  initramfs  archives  in	/boot. There  are three modes of operation create, update or delete. You must at least specify one of those modes.
The initramfs is a gzipped cpio archive. At  boot  time,  the	kernel unpacks	that archive into RAM disk, mounts and uses it as initial root file system. All finding of the root  device  happens  in  this  early userspace.

**Options:**
**-k  version** -> Set the specific kernel version for whom the initramfs will be generated. For example the output of uname  **-r**  for  your  currently  running  kernel. This argument is optional for update. The default is the latest kernel version. The use of "all" for the version string specifies **update-initramfs** to execute the chosen action for all kernel versions, that are already known to update-initramfs.
**-c** -> This mode creates a new initramfs.
**-u -> This mode updates an existing initramfs.**
**-d** -> This mode removes an existing initramfs.
**-t** -> Allows to take over an custom initramfs with a newer one.
**-v** -> This option increases the amount of information  you  are  given during the chosen action.
**-b** -> Set an different bootdir for the image creation.
**-h** -> Print a short help page describing the available options in update-initramfs.

For more information read manpages
**man update-initramfs**

---

