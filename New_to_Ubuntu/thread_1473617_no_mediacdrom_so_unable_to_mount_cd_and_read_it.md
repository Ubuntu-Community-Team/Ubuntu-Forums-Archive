---
title: "no /media/cdrom so unable to mount cd and read it"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by ankur1990 on 2010-05-05
hey i m using ubuntu 10.04...... there is no thing like /media/cdrom where cd gets mounter generally.
as a result i m unable to use the cd as it didn't mount it and i m unable to read it and use it.....
there is folder only /media/ and inside there is nuthing.....

my /etc/fstab file is 
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=c9759f9e-67c8-454b-b230-e64fb4215a7f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=8a775cc9-d3ff-49d1-a5c2-52ca2d94ef2e none            swap    sw              0       0
#none /sys/bus/usb/drivers usbfs devgid=1002,devmode=664 0 0

please help urgent 
Thanx in advance

---

### Post by readycarpenter on 2010-05-05
the system should automatically recognize the cd drive, are you sure it is connected properly, like set to cable select, or set to master, or slave to match the ide cable. does your system bios show you have a cd rom connected?

old drives just fail one day, it is either dead or improperly connected to your motherboard.

---

### Post by kwacka on 2010-05-05
Can you show the output of  ```
dmesg | grep sr0
```

(Sorry if I'm insulting your intelligence or abilities, but you'll need to open a terminal to enter the above.)

---

### Post by ankur1990 on 2010-05-05
> **kwacka said:**
> Can you show the output of  ```
dmesg | grep sr0
```(Sorry if I'm insulting your intelligence or abilities, but you'll need to open a terminal to enter the above.)
output is -
ankur@ankur-laptop:~$ dmesg |grep sr0
[    1.013405] sr0: scsi3-mmc drive: 47x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.013590] sr 0:0:0:0: Attached scsi CD-ROM sr0


any suggestions????????

---

### Post by zarap on 2010-05-13
I just inserted an audio-cd and it showed up in Rhythmbox but it didn't mount on /media/cdrom0.
I found it mounted in "~/.gvfs/CDDA-Medium in sr0". Couldn't open this directory with nautilus but it worked in the terminal: cd ~/.gvfs/CDDA-Medium\ in\ sr0/
Maybe it pays just to look up the ~/.gvfs directory.
I'm on Karmic so it might be different in Lucid.

btw.: if I do "dmesg | grep sr0" with an empty cd tray I have the same output, there are a lot more lines, when I have a cd inserted

---

