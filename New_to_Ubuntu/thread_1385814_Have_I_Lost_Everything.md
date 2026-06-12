---
title: "Have I Lost Everything"
date: 2010-01-20
forum: New to Ubuntu
---

### Post by rbscairns on 2010-01-20
Ubuntu 9.10, clean install and new to Linux.

From memory (mine, not the computer's) I had a clean install of Ubuntu 9.10 onto my 160GB HDD. With GParted added, I set my HDD up with a 40GB partition containing the OS and an extended partition of 120GB containing a 4GB swap file area and the rest I was intending to use for data storage.

While playing around trying to get set the system up so that I could use the 120GB partition, I unmounted that partition. While trying to re-mount that partition, I rebooted the computer.

GRUB load comes up, then GNU GRUB version 1.97~beta4. I choose the option Ubuntu, Linux 2.6.31-17-generic (recovery mode). Kots of stuff scrolls by and I end up with-

OS_Package_Files: clean, 159254/2501856 files, 003479/10000454 blocks
One or more of the mounts listed in /etc/fstab cannot yet be mounted:
(ESC for recovery shell)
/usr/local: waiting for UUID=14de7734-8955-4723-bd8f-e58718ff6a5b

I have waited over 30 minutes. Nothing happened. I then pressed ESC and got-

^[
mountall: cancelled
init: mountall main process (440) terminated with staus 1
General error mounting filesystem.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and re-try
root@admin-Linux:~#

I then press Ctrl+D and end up again with the-

Mountall: start/starting
swapon: /dev/disk/by-uuid/836e8ed3-835d-438f-b698-b0602233d059 [943] terminated with status 255
mountall: Problem activating swap: /dev/disk/by-uuid/836e8ed3-835d-438f-b698-b0602233d059/dev/disk/by-uuid/836e8ed3-835d-438f-b698-b0602233d059
One or more of the mounts listed in /etc/fstab cannot yet be mounted:
(ESC for recovery shell)
/usr/local: waiting for UUID=14de7734-8955-4723-bd8f-e58718ff6a5b

Have I lost everything and must do a new install?

HELP!

---

### Post by x33a on 2010-01-20
sounds like trouble with your swap.

ok first try the following steps:

from the recovery shell, comment out the swap line.

or if the recovery shell doesn't work, try the livecd.

To comment out the swap line, use nano or vim
```
nano /etc/fstab
```after saving the file, reboot the computer and see if it works.

if it does, then we'll try fixing the swap later.

---

### Post by rbscairns on 2010-01-20
In shell and I type in-```
nano /etc/fstab
```press Enter and I get what looks like a copy of File: /etc/fstab

The last two lines of this file read-```
# swap was on /dev/sda5 during installation
UUID=846e8ed3-835d-438f-b698-b0602233d059  none   swap   sw   0   0
```I assume to comment out a line, you mean put a "#" at the beginning of the line.

Am I right in assuming that the last UUID= line is the swap line to be commented out?

Once I comment out the correct line, how do I save the file?

---

### Post by x33a on 2010-01-20
yes, put a # in front of the UUID.

like this
```

# swap was on /dev/sda5 during installation
#UUID=846e8ed3-835d-438f-b698-b0602233d059  none   swap   sw   0   0
```

then, to save press ctrl-o

---

### Post by rbscairns on 2010-01-20
x33a, you are a magician. I commented, saved and rebooted. Now back with my GUI but without mouse. Should I try to get my mouse to work again first, or work on re-establishing the swap file?

---

### Post by x33a on 2010-01-20
if you have enough ram and not hibernating/suspend (at least for now), you should first fix the mouse problem.

Try searching the forums for a solution or open a new thread (for the mouse problem).

---

### Post by rbscairns on 2010-01-20
I have 2GB RAM and have not yet been able to get hibernating/suspend to work properly since first installing Ubuntu 9.10.

I'll work on the mouse problem now and later concern myself wih the swap file.

Again, thank you very much for your guidance.

---

### Post by lotharmat on 2010-01-20
> **rbscairns said:**
> I have 2GB RAM and have not yet been able to get hibernating/suspend to work properly since first installing Ubuntu 9.10.

I'll work on the mouse problem now and later concern myself wih the swap file.

Again, thank you very much for your guidance.


Do you have an SD card inserted? - This totally knackered Suspend / Hibernate for me!

---

### Post by rbscairns on 2010-01-21
The mouse problem was fixed by just unplugging and plugging back in.

As for the Suspend/Hibernate, no SD cards inserted. I have other Ubuntu things I need to work on before that.

---

