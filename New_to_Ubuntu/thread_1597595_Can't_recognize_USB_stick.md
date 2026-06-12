---
title: "Can't recognize USB stick"
date: 2010-10-15
forum: New to Ubuntu
---

### Post by Nox55 on 2010-10-15
I recently installed Ubuntu netbook(unity).  I'm trying to access my usb stick that is plugged in, but nothing happens.  The usb stick lights up like it should but nothing happens in Ubuntu. I read somewhere that it's supposed to auto-mount and appear on the desktop.  Please this is really frustrating.  Thank you.

---

### Post by EvilGiantRobot on 2010-10-15
I'm a n00b myself, but I'd look through the subfolders in /media to see if anything's there.

Also try running lsusb in the terminal, and see if your stick is listed.

---

### Post by AndyM3 on 2010-10-15
I'd say open up a file browser and look at the side pane. I don't know how Unity shows USB sticks.

---

### Post by Nox55 on 2010-10-15
When I enter lsusb in terminal I see it in the list. It shows me:


Bus 001 Device 006: ID 0951:162d Kingston Technology 

but I can't see it anywhere in the GUI not to mention being able to access whats on it.

---

### Post by cariboo on 2010-10-15
It sounds like your device isn't being auto mounted. Open a terminal and type:

```
dmesg | tail -n10
```

just after you plug the device in, the output should look something like this:

```
cariboo@natty:~$ dmesg | tail -n10
[ 6669.242546] scsi 4:0:0:0: Direct-Access     Lexar    JD Secure II +   1100 PQ: 0 ANSI: 0 CCS
[ 6669.243212] sd 4:0:0:0: Attached scsi generic sg3 type 0
[ 6670.556799] sd 4:0:0:0: [sdc] 15663104 512-byte logical blocks: (8.01 GB/7.46 GiB)
[ 6670.557916] sd 4:0:0:0: [sdc] Write Protect is off
[ 6670.557920] sd 4:0:0:0: [sdc] Mode Sense: 43 00 00 00
[ 6670.557922] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 6670.563293] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 6670.563301]  sdc: **sdc1**
[ 6670.567173] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 6670.567179] sd 4:0:0:0: [sdc] Attached SCSI removable disk
```

In my case the device shows up as /dev/sdc1. You should be able to mount it manually if it has a device label eg:

```
sudo mount /dev/sdc1 /media/disk
```

Once you are sure you can mount the device manually, then it time to see why it won't mount automagically.

---

### Post by Nox55 on 2010-10-15
Thank You!!!
 I managed to mount it manually.  It to show up in media now.  How would I go about getting it mount automatically?

edit:
new development.  When I plug in my USB stick now I get this error message:

Unable to mount KINGSTON
Error creating moint point: Input/output error

---

### Post by cariboo on 2010-10-15
It looks like it is trying to automount your device, if it is already mounted, you'll get that error.

I'd suggest unmounting the device:

```
sudo umount /media/<mountpoint>
```

then re-inserting it to see if it will auto-mount now.

---

### Post by Nox55 on 2010-10-15
Nope it doesn't work.

I also followed the instructions of another thread about auto mounting.  I checked in preferences in nautilus about auto mounting and the tabs were checked yes.

---

