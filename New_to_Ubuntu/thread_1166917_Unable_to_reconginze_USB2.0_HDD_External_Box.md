---
title: "Unable to reconginze USB2.0 HDD External Box"
date: 2009-05-22
forum: New to Ubuntu
---

### Post by uppidada on 2009-05-22
I've dual boot in my system.Windows Xp and Ubuntu
I was copying data from HDD to my logical drives.
I exactly don't remember what i'e done later.Probably i've restarted my system and booted windows without unmounting external drive.
Suddenly it says USB device not recognized.
The flash light is well glowing as well..!!
When i return back to Ubuntu,device gets undetected.
What could possibly be the remedy for this problem...??

Thanks in advance

---

### Post by kpkeerthi on 2009-05-22
Is it NTFS formatted? If yes and if you still have Windows, boot into windows, connect the drive, then "Safely remove" the drive from the system tray icon. Then try with Ubuntu.

---

### Post by uppidada on 2009-05-22
Thanks for instant reply.
No,it is FAT32 file system.
Also it isn't detecting even in windows.So,no question of safely remove hardware..

---

### Post by kpkeerthi on 2009-05-22
OK. Connect your drive to Ubuntu, wait for a few seconds and post the outputs of the below commands:

```

dmesg | tail

```
```
sudo fdisk -l
```
```
mount
```

---

### Post by uppidada on 2009-05-22
upesh@upesh-desktop:~$ dmesg | tail
[   43.160748]  [<c011dba2>] native_safe_halt+0x2/0x10
[   43.160760]  [<c0102e3c>] default_idle+0x3c/0x60
[   43.160764]  [<c0102413>] cpu_idle+0x53/0xe0
[   43.160784]  [<c03e3a85>] start_kernel+0x325/0x3b0
[   43.160793]  [<c03e31f0>] unknown_bootoption+0x0/0x260
[   43.160830]  =======================
[   43.160832] handlers:
[   43.160834] [<ecbfd480>] (via_driver_irq_handler+0x0/0x1d0 [via])
[   43.160844] Disabling IRQ #20
[   45.182049] eth0: no IPv6 routers present

---

### Post by uppidada on 2009-05-22
ouput for sudo fdisk -l:
upesh@upesh-desktop:~$ sudo fdisk -l
[sudo] password for upesh:

Disk /dev/hda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x172f172e

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1530    12289693+   c  W95 FAT32 (LBA)
/dev/hda2            1531        8315    54500512+   f  W95 Ext'd (LBA)
/dev/hda3            8316        9733    11390085   83  Linux
/dev/hda5            1531        2254     5815498+   b  W95 FAT32
/dev/hda6            2255        3529    10241406    b  W95 FAT32
/dev/hda7            3530        4422     7172991    b  W95 FAT32
/dev/hda8            4423        6971    20474811    b  W95 FAT32
/dev/hda9            6972        8246    10241406    b  W95 FAT32
/dev/hda10           8247        8315      554211   82  Linux swap / Solaris

---

### Post by uppidada on 2009-05-22
upesh@upesh-desktop:~$ mount
/dev/hda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)

---

### Post by kpkeerthi on 2009-05-22
OK. I'm lost. From the dmesg output, it appears that Ubuntu made no attempts to mount the drive because, as you can see from fdisk -l output, the drive was not recognized.

Is it powered on?

---

### Post by uppidada on 2009-05-22
Yes.Device is powered on.. Flash lights are on as well..
I'm afraid is it the case that device is damaged..? But if it is so,how come flash lights are working well...

Direct me please..
Anywayz thanks for your concern in helping me.

---

### Post by uppidada on 2009-05-22
Someone please help me with this....

---

### Post by card_ace on 2009-05-22
boot into windows and then go to start- settings- control panel.  put it into classic view and click on administrative properties or whatever its called.  should be the 4th icon across the top.  double click on computer management and then click on disk management along the left side.  see if windows is seeing it and just can't load it.  if windows recognizes anything at all it should appear in here.

---

### Post by koleoptero on 2009-05-22
Boot in windows, and try to fix it from there.

Go to the control panel, try to find the administrative tools there, and from those open the computer management one. It has somewhere on the left a tool that shows you information about storage media connected to the computer. It might be that the device shows there but it has no partitions (which means the partition table of the drive is damaged). Try then to create a new partition and format it to ntfs (not fat32, it sucks).

You can also use other programs to check this out, like the free [Easus partition manager]("http://www.partition-tool.com/").

You can check out from your linux installation this too by using Gparted (it's in the add/remove).

EDIT: I just saw the post above from card_ace, sorry for saying the same things twice.

---

### Post by uppidada on 2009-05-22
Well.. Even in storage,i couldn't find usb box.
DO i have to do something with Registry editor..??

---

### Post by blacksadness on 2009-05-23
Looks like a hardware failure, what type of external box is it? self assembled or branded, can you remove the hdd from it? if so, try to connect that hdd directly to the pc, and see if it's recognised, and try to put a second hdd in that box,
i'm taking a blind shot here, but also try to change the usb cable, on your pc also, if you're using front usb ports, try using the back ports.

---

