---
title: "Can't find USB drive"
date: 2009-08-28
forum: New to Ubuntu
---

### Post by celticdevildog on 2009-08-28
I am trying to set up a file server with an external drive that has previous information on it.  I am running the server edition of 9.04 so I am command line only (with limited knowledge of command line).

This USB drive was previously hooked up to a windows machine and has all my music files on it.

I connected it to the server and I cannot find it in /dev.  I have posted an abbreviated output since I am typing this from my windows box and not the server.  If you need more information from an output please let me know.

**running df -k:**

```
/dev/sda1     /
tmpfs     /lib/init/rw
varrun     /var/run
varlock     /var/lock
udev     /dev
tmpfs     /dev/shm
lrm     /lib/modules/2.6.28-15-server/volatile
/dev/sdb1     /media/data
/dev/sdc1     /media/private
```the /dev/sdb1 and /dev/sdc1 are two internal drives.

**here is the output of lsusb:**

```
ID 1d6b:0002 Linux Foundation 2.0 root hub
1d6b:0001 Linux Foundation 1.1 root hub
1d6b:0001 Linux Foundation 1.1 root hub
413c:2006 Dell Computer Corp.
413c:1004 Dell computer corp.
1d6b:0001 Linux Foundation 1.1 root hub
1d6b:0001 Linux Foundation 1.1 root hub
```**running dmesg | tail after plugging in the USB drive:**

```
[sdd] Mode Sense: 38 00 00 00
[sdd] Assuming drive cache: write through
[sdd] Write Protect is off
[sdd] Mode Sense: 38 00 00 00
[sdd] Assuming drive cache: write through
sdd: sdd1
[sdd] Attached SCSI disk
Attached scsi gebneric sg4 type 0
USB disconnect, address 4
```I figured the drive was given the name /dev/sdd with a partition of /dev/sdd1 so I tried to mount it using the following command:

```
sudo mount /dev/sdd1 /media/music
```but it gives me the output of

```
mount: special device /dev/sdd1 does not exist
```This drive worked on my windows machine.  Is there something else I can try to get it set up and mounted?

---

### Post by LewRockwell on 2009-08-28
silly question...

you've got a current back-up of the data on that drive...right?

.

---

### Post by celticdevildog on 2009-08-28
Not of that drive...well, I mean I have all the CDs that I could re-upload but that would take a million years.

I'm trying to get this stuff on the server since I will run backups of the data that will be on the server, if that makes sense.

---

### Post by unutbu on 2009-08-28
It looks to me as though, for some reason, the Linux kernel is failing to connect to the USB drive:
> 
Attached scsi gebneric sg4 type 0
USB disconnect, address 4

I'm not sure I know enough to help you, but would you please post your entire dmesg, /var/log/messages and /var/log/syslog?

Since they can be rather long, perhaps run
```

dmesg | bzip2 > dmesg.bz2
bzip2 -c /var/log/messages > messages.bz2
bzip2 -c /var/log/syslog > syslog.bz2
```

Then post dmesg.bz2, messages.bz2 and syslog.bz2 as attachments.

---

### Post by celticdevildog on 2009-08-28
Here is the output of the requested files.

I could, if need be, hook the drive back up to my windows box and copy the files over to the already connected drives...but that would take much longer than trying to figure out how to get the server to recognize the USB drive.

---

### Post by unutbu on 2009-08-28
Actually, I think my first opinion might have been mistaken.
Here is a snippet from your /var/log/messages:

```
Aug 28 10:48:49 orgrimmar kernel: [ 3715.803908] scsi 4:0:0:0: Direct-Access    [COLOR="Red"] WDC WD50 00KS-60MNB0[/COLOR]           PQ: 0 ANSI: 2
Aug 28 10:48:49 orgrimmar kernel: [ 3715.825764] sd 4:0:0:0: [sdd] 976773168 512-byte hardware sectors: ([COLOR="Red"]500 GB[/COLOR]/465 GiB)
Aug 28 10:48:49 orgrimmar kernel: [ 3715.828014] sd 4:0:0:0: [sdd] Write Protect is off
Aug 28 10:48:49 orgrimmar kernel: [ 3715.849387] sd 4:0:0:0: [sdd] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
Aug 28 10:48:49 orgrimmar kernel: [ 3715.851764] sd 4:0:0:0: [sdd] Write Protect is off
Aug 28 10:48:49 orgrimmar kernel: [ 3715.851829]  [COLOR="Red"]sdd: sdd1[/COLOR]
Aug 28 10:48:49 orgrimmar kernel: [ 3715.854070] sd 4:0:0:0: [sdd] Attached SCSI disk
Aug 28 10:48:49 orgrimmar kernel: [ 3715.854170] sd 4:0:0:0: Attached scsi generic sg4 type 0
Aug 28 11:00:25 orgrimmar kernel: [ [COLOR="Red"]4411[/COLOR].682169] usb 1-4: USB disconnect, address 4
```


It shows that a 500GB drive was connected at time 3715s, and it appears to have been given device name /dev/sdd,
and one partition was found on this drive: /dev/sdd1.

It wasn't until time 4411s, (11 minutes later), that the drive was disconnected.

Let's make things as simple as possible. Please boot with the drive connected.
Then open a terminal and type
```

sudo fdisk -l
```

what is the output?

---

### Post by celticdevildog on 2009-08-28
Reboot recognized the device.  I can't believe it was that simple!!  After years of working with Windoze you would think I'd have done that first.

Thanks for your help.

---

