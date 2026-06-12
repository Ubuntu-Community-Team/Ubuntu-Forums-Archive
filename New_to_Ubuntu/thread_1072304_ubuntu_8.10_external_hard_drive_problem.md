---
title: "ubuntu 8.10 external hard drive problem"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by visciousirene on 2009-02-17
I had previously installed Ubuntu 8.04 and my hardrive worked fine, now I have upgraded and nothing is coming up, it reads the hard drive if i look in the terminal:

viscious@viscious-laptop:~$ sudo lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 03f0:011d Hewlett-Packard Integrated Bluetooth Module
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 016: ID 059b:0178 Iomega Corp. Hi-Speed USB-to-IDE Bridge Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Doesn't show on the desktop or in places/computer

I have read the other threads but there no one seems to have the same same problem, as far as I read.

My computer is a Compaq nc6120, if that is of any use....

Thanks for anyone helping, please make it easy cause i dont' have a clue!!

Cheers

---

### Post by taurus on 2009-02-17
You probably have to mount it first before it appears on your desktop.  What's the output of these commands from a terminal?

```
sudo fdisk -**l**
df -h
```
That would be a lower case letter L, not number 1.

---

### Post by visciousirene on 2009-02-17
This is when given sudo fdisk -l:

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xea47ef47

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7111    57119076   83  Linux
/dev/sda2            7112        7296     1486012+   5  Extended
/dev/sda5            7112        7296     1485981   82  Linux swap / Solaris

:D

---

### Post by visciousirene on 2009-02-17
Sorry forgot the second command output:

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xea47ef47

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7111    57119076   83  Linux
/dev/sda2            7112        7296     1486012+   5  Extended
/dev/sda5            7112        7296     1485981   82  Linux swap / Solaris
viscious@viscious-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              55G  7.4G   44G  15% /
tmpfs                 248M     0  248M   0% /lib/init/rw
varrun                248M  116K  247M   1% /var/run
varlock               248M     0  248M   0% /var/lock
udev                  248M  2.8M  245M   2% /dev
tmpfs                 248M  996K  247M   1% /dev/shm
lrm                   248M  2.0M  246M   1% /lib/modules/2.6.27-11-generic/volatile

---

### Post by taurus on 2009-02-17
Try unplugging the harddrive and plug it back in again.  Then, post

```
dmesg | tail
sudo fdisk -l
df -h
```

---

### Post by visciousirene on 2009-02-17
1st thanks for helping!

viscious@viscious-laptop:~$ dmesg | tail
[13908.670390] sd 10:0:0:0: [sdb] Sense Key : No Sense [current] 
[13908.670394] sd 10:0:0:0: [sdb] Add. Sense: No additional sense information
[13908.671417] sd 10:0:0:0: [sdb] Sense Key : No Sense [current] 
[13908.671422] sd 10:0:0:0: [sdb] Add. Sense: No additional sense information
[13908.672657] sd 10:0:0:0: [sdb] Sense Key : No Sense [current] 
[13908.672662] sd 10:0:0:0: [sdb] Add. Sense: No additional sense information
[13908.673906] sd 10:0:0:0: [sdb] Sense Key : No Sense [current] 
[13908.673912] sd 10:0:0:0: [sdb] Add. Sense: No additional sense information
[13908.675156] sd 10:0:0:0: [sdb] Sense Key : No Sense [current] 
[13908.675161] sd 10:0:0:0: [sdb] Add. Sense: No additional sense information

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xea47ef47

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7111    57119076   83  Linux
/dev/sda2            7112        7296     1486012+   5  Extended
/dev/sda5            7112        7296     1485981   82  Linux swap / Solaris
viscious@viscious-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              55G  7.5G   44G  15% /
tmpfs                 248M     0  248M   0% /lib/init/rw
varrun                248M  116K  247M   1% /var/run
varlock               248M     0  248M   0% /var/lock
udev                  248M  2.8M  245M   2% /dev
tmpfs                 248M 1004K  247M   1% /dev/shm
lrm                   248M  2.0M  246M   1% /lib/modules/2.6.27-11-generic/volatile

---

### Post by taurus on 2009-02-17
Try

```
lsusb
```
and wait for 5 seconds.  Then run

```
dmesg | tail
```

---

### Post by visciousirene on 2009-02-17
viscious@viscious-laptop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 03f0:011d Hewlett-Packard Integrated Bluetooth Module
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 020: ID 059b:0178 Iomega Corp. Hi-Speed USB-to-IDE Bridge Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
viscious@viscious-laptop:~$ desmg | tail
bash: desmg: command not found

---

### Post by visciousirene on 2009-02-17
in the meantime I've tried the above commands again and it worked this time

viscious@viscious-laptop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 03f0:011d Hewlett-Packard Integrated Bluetooth Module
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 020: ID 059b:0178 Iomega Corp. Hi-Speed USB-to-IDE Bridge Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
viscious@viscious-laptop:~$ dmesg | tail
[15752.539170] sd 10:0:0:0: [sdb] Sense Key : No Sense [current] 
[15752.539175] sd 10:0:0:0: [sdb] Add. Sense: No additional sense information
[15752.540416] sd 10:0:0:0: [sdb] Sense Key : No Sense [current] 
[15752.540421] sd 10:0:0:0: [sdb] Add. Sense: No additional sense information
[15752.541431] sd 10:0:0:0: [sdb] Sense Key : No Sense [current] 
[15752.541436] sd 10:0:0:0: [sdb] Add. Sense: No additional sense information
[15752.542665] sd 10:0:0:0: [sdb] Sense Key : No Sense [current] 
[15752.542671] sd 10:0:0:0: [sdb] Add. Sense: No additional sense information
[15752.543674] sd 10:0:0:0: [sdb] Sense Key : No Sense [current] 
[15752.543679] sd 10:0:0:0: [sdb] Add. Sense: No additional sense informat

---

### Post by taurus on 2009-02-17
What filesystem is your external harddrive, /dev/sdb?  Do you have an access to another machine that you can test out that external harddrive to see if it works?

---

### Post by visciousirene on 2009-02-17
Don't know what is the filesystem as I guess to find out I should open it?

---

### Post by visciousirene on 2009-02-17
I don't have another machine to test it on as it is not compatible with Macs, it does read it though, but I cannot access it. The hard drive worked fine in ubuntu 8.04 automatically, I upgraded 2 days ago and now it is not reading it any longer.

---

