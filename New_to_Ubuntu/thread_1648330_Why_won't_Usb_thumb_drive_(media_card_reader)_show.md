---
title: "Why won't Usb thumb drive (media card reader) show up"
date: 2010-12-18
forum: New to Ubuntu
---

### Post by hanzj on 2010-12-18
I plug in my USB media card reader but it won't show up on Computer Folder or on desktop. pls help.


lsusb gives> 
Bus 002 Device 002: ID 4348:5584 WinChipHead CH34x printer adapter cable
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 011: ID 1976:1307 Chipsbrand Microelectronics (HK) Co., Ltd. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


i think it's the Chipsbrand one.

---

### Post by hanzj on 2010-12-18
I solved the problem. I am using an SD Card adapter with a MicroSD card in it. I had to flick the switch on the SD card reader. When I plugged it back in to the UBuntu comp, everything worked.

But I wish that Ubuntu would at least give the user a message saying "Dear User, we detect a USB Card reader plugged in, but can't access it until you flip the switch. Please do so now." Won't that be a good idea?


Dec 27, 2010 UPDATE: The same card reader doesn't seem to be working today. See my [latest post ]("http://ubuntuforums.org/showthread.php?p=10286330#post10286330")on this same thread.

---

### Post by fatal_ERROR777 on 2010-12-18
**hanzj**, I was writing a reply, but you have already answered your problem...

---

### Post by hanzj on 2010-12-27
fatal_error:


I've marked this thread back to unsolved because the usb media card reader does not appear anywhere whether the switch on the SD card is set to Locked or not.


Please help.

---

### Post by hanzj on 2011-01-03
I don't even see the USB device on System/Administration/Disk_Utility. Please help.

---

### Post by pers3vs on 2011-01-03
Without some media (SD Card) inserted into the card reader, I don't believe there is anything for it to mount or display. The reader shows up with a signature under "lsusb", but there is nothing else for it to do. This applies when the card is "turned off" as well, since either way it cannot be mounted.

---

### Post by hanzj on 2011-01-03
pers3vs,
but there IS an SD card inside the reader. and the card is NOT turned off.

---

### Post by Crazedpsyc on 2011-01-03
Post the output of
```
mount
```
wihtout any arguments, mount just shows the available drives

---

### Post by hanzj on 2011-01-03
mount output

> ~$ mount
/dev/sdb1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jc/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jc)
/dev/sda1 on /media/06e8190d-af68-41ff-9bf4-c6200be0845d type ext4 (rw,nosuid,nodev,uhelper=udisks)

---

### Post by Crazedpsyc on 2011-01-04
Is the device formatted to Ext4? It shouldn't be.
Otherwise, it doesn't look like mount sees it a all, so it's no wonder it won't mount!
That is a serious problem. But have you tried it in another USB drive, or have you tried another device in that drive?

---

### Post by lonestar21 on 2011-01-04
I have a similar (same?) problem.

us@us-laptop:/media$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 413c:3010 Dell Computer Corp. Optical Wheel Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 008: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 2.0 Stick (4GB) / PNY Attache 4GB Stick
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

us@us-laptop:/media$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/us/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=us)

tried all my usb ports, and 3 different drives.  Same error all around.  please help

---

### Post by fatal_ERROR777 on 2011-01-06
[SIZE="1"]I think there's a post similar to this, I will update this post if there is.[/SIZE]
OK, I have found a simple solution for you. Does your SD card come with a blank one?
> **pollywog said:**
> I hate to admit this, but I just realized that these things come with a blank SD card. With an actual SD in place both work like a charm. OOPS!
-> [Source]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1271145") <-

Fatal_Error777
----
[SIZE="1"]and sorry for grammar, I'm Russian...[/SIZE]

---

### Post by fatal_ERROR777 on 2011-01-06
Also, you may try installing Ubuntu common restricted extras, it will install some codecs for your computer, but I'm not sure weather this is going to work.

While doing it, you must try this:
 > **llamabr_and_edited_by_me said:**
> 
1.Plug in SD card 
2.Wait 10 seconds
3.While waiting open terminal
4.After plugging and waiting, run this command in the terminal:

```
dmesg | tail -10

```
And post the output
If the output will look something like this:
```
Anonymous@anonymous-desktop:~$ dmesg | tail -10
[ 3857.830048] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:13:5f:04:0d:05:08:00 SRC=73.215.216.1 DST=255.255.255.255 LEN=352 TOS=0x00 PREC=0x00 TTL=255 ID=34930 PROTO=UDP SPT=67 DPT=68 LEN=332 
[ 3864.160542] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:13:5f:04:0d:05:08:00 SRC=73.215.216.1 DST=255.255.255.255 LEN=352 TOS=0x00 PREC=0x00 TTL=255 ID=34968 PROTO=UDP SPT=67 DPT=68 LEN=332 
[ 3876.541116] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:13:5f:04:0d:05:08:00 SRC=73.215.216.1 DST=255.255.255.255 LEN=352 TOS=0x00 PREC=0x00 TTL=255 ID=35011 PROTO=UDP SPT=67 DPT=68 LEN=332 
[ 3878.687112] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:13:5f:04:0d:05:08:00 SRC=73.215.216.1 DST=255.255.255.255 LEN=348 TOS=0x00 PREC=0x00 TTL=255 ID=35024 PROTO=UDP SPT=67 DPT=68 LEN=328 
[ 3878.735162] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:13:5f:04:0d:05:08:00 SRC=73.215.216.1 DST=255.255.255.255 LEN=348 TOS=0x00 PREC=0x00 TTL=255 ID=35025 PROTO=UDP SPT=67 DPT=68 LEN=328 
[ 3882.682816] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:13:5f:04:0d:05:08:00 SRC=73.215.216.1 DST=255.255.255.255 LEN=348 TOS=0x00 PREC=0x00 TTL=255 ID=35037 PROTO=UDP SPT=67 DPT=68 LEN=328 
[ 3882.755366] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:13:5f:04:0d:05:08:00 SRC=73.215.216.1 DST=255.255.255.255 LEN=348 TOS=0x00 PREC=0x00 TTL=255 ID=35040 PROTO=UDP SPT=67 DPT=68 LEN=328 
[ 3886.704006] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:13:5f:04:0d:05:08:00 SRC=73.215.216.1 DST=255.255.255.255 LEN=348 TOS=0x00 PREC=0x00 TTL=255 ID=35050 PROTO=UDP SPT=67 DPT=68 LEN=328 
[ 3886.750108] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:13:5f:04:0d:05:08:00 SRC=73.215.216.1 DST=255.255.255.255 LEN=348 TOS=0x00 PREC=0x00 TTL=255 ID=35051 PROTO=UDP SPT=67 DPT=68 LEN=328 
[ 3893.018017] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:13:5f:04:0d:05:08:00 SRC=73.215.216.1 DST=255.255.255.255 LEN=352 TOS=0x00 PREC=0x00 TTL=255 ID=35071 PROTO=UDP SPT=67 DPT=68 LEN=332 
Anonymous@anonymous-desktop:~$
```
OR mine output:```
FATL@fatal-laptop:~$ dmesg | tail -10
[124539.005345] scsi 7:0:0:0: Direct-Access     Multi    Flash Reader     1.00 PQ: 0 ANSI: 0
[124539.007475] sd 7:0:0:0: Attached scsi generic sg2 type 0
[124539.664318] sd 7:0:0:0: [sdb] 15523840 512-byte logical blocks: (7.94 GB/7.40 GiB)
[124539.665154] sd 7:0:0:0: [sdb] Write Protect is off
[124539.665162] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[124539.665169] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[124539.668406] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[124539.668416]  sdb: sdb1
[124539.675659] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[124539.675671] sd 7:0:0:0: [sdb] Attached SCSI removable disk
FATAL@fatal-laptop:~$ 
```



Then your SD card reader is working, but there is problem displaying the little icon on your desktop



Fatal_Error777

---

### Post by hanzj on 2011-01-07
mount does not see the USB card reader, but lsusb does see it.

---

### Post by hanzj on 2011-01-07
I haven't installed ubuntu-restricted-extras yet.
> dmesg | tail -10
[   78.564029] Clocksource tsc unstable (delta = -193349082 ns)
[  493.221736] ndiswrapper (NdisMIndicateStatus:2084): unrecognized PMKID ignored
[ 1093.353294] ndiswrapper (NdisMIndicateStatus:2084): unrecognized PMKID ignored
[ 1693.485305] ndiswrapper (NdisMIndicateStatus:2084): unrecognized PMKID ignored
[ 2293.616569] ndiswrapper (NdisMIndicateStatus:2084): unrecognized PMKID ignored
[ 2595.585150] usb 1-10: USB disconnect, address 3
[ 2600.460042] usb 1-9: new high speed USB device using ehci_hcd and address 4
[ 2893.748598] ndiswrapper (NdisMIndicateStatus:2084): unrecognized PMKID ignored
[ 3044.795066] usb 1-9: USB disconnect, address 4
[ 3171.556045] usb 1-10: new high speed USB device using ehci_hcd and address 5


---

### Post by fatal_ERROR777 on 2011-01-15
Hmm, actually ubuntu commonly restricted extras won't help you, it installs codecs for audio and video formats, but there should be an plug-in with a similar name for media support.

looking for it...

~fatal_Error

EDIT: I'm feeling lost, but I'll find a solution for you

---

### Post by hanzj on 2011-01-22
Hmmmm. I noticed that if I plug in the media card reader (with the sd card inserted) before I turn on the computer, then the computer will "see" the card reader. 

But, if I insert the media card reader after getting to Ubuntu screeen, then no good.

---

