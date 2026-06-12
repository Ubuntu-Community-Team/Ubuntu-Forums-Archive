---
title: "USB ports not recognized in 10.04"
date: 2010-06-07
forum: New to Ubuntu
---

### Post by byline on 2010-06-07
Since upgrading from Ubuntu 9.10 to 10.04 on April 30 (via Update Manager), with a few minor exceptions, pretty much everything has been working the way it should. However, last night, when I plugged in my MP3 player to add a few more tracks, the device is not automatically opening up on my desktop. Also, on the MP3 player itself, when I plug it in, before there was an exclamation point inside the circle; as long as that was there, it wasn't safe to disconnect it. Now the exclamation point is not showing up.

Everything else -- printer, scanner, photo card reader, etc. -- is working properly. Any suggestions as to what the problem might be? Is it the specific device, or a problem with these two front USB ports? I never had this problem prior to the 10.04 upgrade. I notice that on boot-up, I don't see the "script" that used to run, showing devices as they were detected and so on. Is this part of the problem?

A couple of other problems have persisted since the upgrade to 10.04, and I haven't found permanent solutions to either: The swap partition is not automatically mounted on boot-up, so I have to do that manually by typing **sudo swapon -a /dev/sda1** in the terminal. And then every time I boot up, I get a mail notification window asking me to choose a mailbox. Thunderbird is the e-mail program that we use, but it's not one of the options offered. So I have to close that window every time I boot up; there doesn't seem to be any way of permanently disabling it. Not a biggie, but annoying.

An ideas on how to fix any of this? Little words, big pictures please. Linux is my husband's baby, and I'm just a casual user.

Thanks!

---

### Post by Mariane on 2010-06-07
Type:
sudo mkdir /media/mydevice

After pluggin in the device, count up to 10 and then type in a terminal window:
dmesg | tail

Look for a line with something like:
sdb:sdb1

If you don't see it, wait another 10 seconds and do dmesg | tail again. You don't have to re-type it, pressing the arrow pointing upwards on the keypad repeats the last command on the terminal window and you just have to press enter again to launch it. 

When you see sdb:sdb1 (or something like that) you type:

sudo mount /dev/sbd1 /media/mydevice

WARNING: if it is not sdb1 which appears after dmesg | tail but for example sdb:sdb2 you have to replace sdb1 by sdb2 in the command above. 

If you see no error message, your device can be reached in /media/mydevice. If you see some please post them here. 

Mariane

---

### Post by byline on 2010-06-07
> **Mariane said:**
> Type:
sudo mkdir /media/mydevice
Where do I type this, in a terminal?

Thanks!

---

### Post by Mariane on 2010-06-07
Yes, in a terminal. The first time in a terminal session in which you type "sudo something" you will be asked for the root password. 

Mariane

---

### Post by SunnyRabbiera on 2010-06-07
Well it might be the MP3 player, what brand is it?

---

### Post by frncz on 2010-06-07
With  my memory stick which I cannot erase, I get:
dmesg |tail
[16163.542891] end_request: I/O error, dev sdb, sector 3750296
[16208.507497] sd 4:0:0:0: [sdb] Unhandled sense code
[16208.507502] sd 4:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[16208.507506] sd 4:0:0:0: [sdb] Sense Key : Hardware Error [current] 
[16208.507510] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
[16208.507514] sd 4:0:0:0: [sdb] CDB: Write(10): 2a 00 00 00 3c 45 00 00 01 00
[16208.507523] end_request: I/O error, dev sdb, sector 15429
[16208.507528] __ratelimit: 47 callbacks suppressed
[16208.507530] Buffer I/O error on device sdb, logical block 15429
[16208.507532] lost page write due to I/O error on sdb

---

### Post by byline on 2010-06-07
> **Mariane said:**
> Yes, in a terminal. The first time in a terminal session in which you type "sudo something" you will be asked for the root password. 

Mariane
OK, that's what I thought. But I'm a total noob, so I thought I'd better ask!:P

I tried it, but I'm not getting anything like sdb:sdb1. Here's what shows up:

[  374.382456] scsi6 : SCSI emulation for USB Mass Storage devices
[  374.387397] usb-storage: device found at 9
[  374.387402] usb-storage: waiting for device to settle before scanning
[  375.544135] usb 1-7: usbfs: USBDEVFS_CONTROL failed cmd gvfs-gphoto2-vo rqt 192 rq 1 len 1000 ret -110
[  376.556125] usb 1-7: usbfs: USBDEVFS_CONTROL failed cmd gvfs-gphoto2-vo rqt 192 rq 1 len 1000 ret -110
[  376.676043] usb 1-7: reset high speed USB device using ehci_hcd and address 9
[  377.816701] usb 1-7: usbfs: USBDEVFS_CONTROL failed cmd gvfs-gphoto2-vo rqt 192 rq 1 len 1000 ret -110
[ 2181.528368] usb 1-7: USB disconnect, address 9

As for what brand of MP3 player I use, I'm not sure that's relevant since it worked perfectly fine under Ubuntu 9.10. But it's a Sony.

---

### Post by SunnyRabbiera on 2010-06-07
Could be a factor, but its real hard to tell.

---

### Post by byline on 2010-06-07
Hubby's been taking a look at it, but can't figure it out. In the meantime, we were able to copy the tracks over using his laptop. He's using Ubuntu 9.10 and, as with my computer when it was running 9.10, there was no problem. It's only since we upgraded to 10.04 that this became a problem. Odd. . . .

---

### Post by byline on 2010-06-09
Hubby continues trying to find a solution, to no avail. I think we may end up reinstalling 9.10, as I don't see any noticeable improvements with 10.04, yet I've actually lost some functionality. Besides the issue with the MP3 player, the swap partition *should* be mounted automatically on boot-up . . . yet it's not. And I *should* be able to completely disable that mailbox notification window on boot-up . . . yet I can't. And there don't seem to be any solutions for any of these things.

Of course, these are relatively minor issues compared with what other folks have gone through, but it's still annoying that what should have been an improvement is actually a step backward.

---

### Post by byline on 2010-06-10
Also, just to clarify my original subject line and post: The USB ports are **not** the problem. All are recognized, and in fact I can plug in a USB memory stick, and it is recognized and opens without any problem. Oddly enough, the **lsusb** command also shows the Sony MP3 player plugged in. However, it won't open on my desktop the way it did (and still does) in 9.10. Very strange.

---

### Post by byline on 2010-06-10
Edit: Oops, this turned out not to be a "fix" after all. I was pulling up our Media folder from our second hard drive, not the MP3 player. Sorry!

---

### Post by byline on 2010-06-10
OK, at least for us, hubby worked out a solution:

He deleted rhythmbox utilities and removed rhythmbox from the panel.  Plugged in the Walkman and, voila, a folder opened with the Walkman's contents!

Also, for the other issues I mentioned in my original post:

- to keep the mail notifier from opening every time you log in: System Preferences, Startup Applications, uncheck "Mail Notifier", Close
- to automatically set the swap partition as /dev/sda1, use sudo gedit to have /etc/rc.local end with:
swapon -a /dev/sda1
exit 0

---

### Post by byline on 2010-07-04
Solving problem of using swap partition automatically.

The previously described solution, of adding a swapon command to /etc/rc.local was actually more of a workaround than an actual solution.

Here's what hubby has figured out: the cause of this issue is that /dev/sda1 is an old swap partition that was formatted a few years ago and (apparently) does not contain a UUID in the superblock which Ubuntu 10.04 now requires in /etc/fstab.   No listing of a UUID link to /dev/sda1 (ls -l /dev/disk/by-uuid) and trying to use sudo tune2fs -U random /dev/sda1 indicated a UUID could not just be added.

So under System, Administration used Disk Utility to reformat /dev/sda1 and now (tada!) there's a symlink to /dev/sda1 in /dev/deisk/by-uuid.  Copied the symlink name into the entry for /dev/sda1 in /etc/fstab (sudo gedit /etc/fstab) and after a cold  reboot swap was automatically used.

---

