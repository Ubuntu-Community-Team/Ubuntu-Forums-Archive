---
title: "Need help mounting NSLU2 via smb on Dapper desktop box"
date: 2007-01-25
forum: Networking &amp; Wireless
---

### Post by mjblane on 2007-01-25
I have a stock Linksys NSLU2 with a singe 500Gig USB drive attached.
It mounts as advertised on my wife's XP machine.
I am having trouble getting it mounted to my Dapper Drake desktop machine. Once that's successful, I plan to mount it on my old laptop that's running Edgy (the laptop is connected to my stereo for playing FLAC files from the NSLU2/DISK 1).

Here's what I've tried and the results:
This will mount it by hand:
michael@moles:~$ sudo mount -t smbfs //LKG7D1D4A/DISK\ 1 /home/ZZ_NSLU2

This is the output from /etc/mtab:
michael@moles:~$ cat /etc/mtab
/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
/sys /sys sysfs rw 0 0
varrun /var/run tmpfs rw 0 0
varlock /var/lock tmpfs rw 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
devshm /dev/shm tmpfs rw 0 0
lrm /lib/modules/2.6.15-27-386/volatile tmpfs rw 0 0
/dev/hdb1 /home/ZZ_30G ext3 rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
//LKG7D1D4A/DISK_1 /home/ZZ_NSLU2 smbfs rw 0 0

Then umounted and did the following.

Tried adding this in etc/fstab:
//LKG7D1D4A/DISK\0401   /home/ZZ_NSLU2  smbfs   rw      0       0
Ran: sudo mount -a
Root owns it and using sudo chown on /home/ZZ_NSLU2 gets denied. But otherwise works OK.

Rebooted:
Takes about 10x longer to boot, slows at Starting Hardware abstraction layer hald.
Finally boots, login, GUI takes longer to come up.

File Browser shows /home/ZZ_NSLU2 is an unknown type (and takes a while to do that).

From terminal:
michael@moles:~$ ls /home/ZZ_NSLU2
ls: /home/ZZ_NSLU2: Input/output error

From terminal:
michael@moles:~$ sudo umount /home/ZZ_NSLU2
michael@moles:~$ ls /home/ZZ_NSLU2
michael@moles:~$

And removed:
//LKG7D1D4A/DISK\0401   /home/ZZ_NSLU2  smbfs   rw      0       0
from /etc/fstab.

Rebooted and all seems OK except that I still need to get the NSLU2 mounted.

Any thoughts, suggestions, pointers where to look are all greatly appreciated.

Thanks,
Michael

---

### Post by mjblane on 2007-02-07
Well, either no one could duplicate, or no one knew what to do.

Here's my current work around.

I re-formatted the drive as Fat32, put it back in /etc/fstab using its current drive name (HDD_1_1_1) and all seems OK. It still shows root as owner and denies any changes but, at the moment that's a minor problem that I'll get to.

It is currently doing what I need it to do. When I figure out the ownership problem I'll post that.

Thanks to all who read and gave it some thought.

Michael

---

### Post by HellRat on 2007-04-04
So, how did that work out for you? I just bought a nslu2 and I'm collecting as much info on it as possible since I need to use it without a windows installation. Any luck with writing to it or using ext3?

---

