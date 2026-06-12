---
title: "Cannot mount my external hardisk."
date: 2009-04-27
forum: New to Ubuntu
---

### Post by firdaus313 on 2009-04-27
Hi friends,
Im a new user of ubuntu. my first problem is ubuntu cannot mount my external hardisk while it can be used on other windows pc. can anyone advice me on this? TQ

---

### Post by llamabr on 2009-04-27
Say more about the hard disk, and how you're connecting it.

Then, plug it in, and post the last ten or so lines of dmesg, from the terminal.

---

### Post by firdaus313 on 2009-04-27
OK.
Im using my external casing to connect it via usb. and my hardisk is the SATA 3.5HDD (NTFS).
When i connect the external HD, it stated CANNOT MOUNT VOLUME

Error org.freedesktop.Hal.Device.UnknownError.

---

### Post by firdaus313 on 2009-04-27
Also stated that:
Error opening device: No such device or address Failed to mount '/dev/sdb2': No such device or address You seem to have a SoftRAID/FakeRAID hardware and must use an activated, different device under /dev/mapper/, (e.g. /dev/mapper/ nvidia_eahaabcc1) to mount NTFS. Please see the 'dmraid' documentation for help.

:confused:

---

### Post by llamabr on 2009-04-27
And the last few lines of dmesg?

---

### Post by firdaus313 on 2009-04-27
Thats only text appeared in the box. 
But when i connect it once again another dmesg stated:

$LogFile indicates unclean shutdown (0, 0) Failed to mount '/dev/sdb5': Operaton not supported Mount is denied because NTFS is marked to be in use. Choose one action: Choice 1: If you have windows then disconnect the external devices by clicking on the 'Safely Remove Hardware' icon in the windows taksbar then shutdown Windows cleanly. Choice 2: If you don't have Windows then you can usr the 'force' option for  your own responsibilities. For example type on the command line: mount -t ntfs-3g /dev/sdb5 /media/(MYHDNAME)_ -o force Or add the option to the relevant row in the /etc/fstab file: dev/sdb5 /media/(MYHDNAME)_ ntfs-3g force 0 0

I've tried the force option but it replied 'only root can do that'

Getting more confused..:confused:

---

### Post by Jimbley on 2009-04-27
Hi,

Try this:

```
sudo mount -t ntfs-3g /dev/sdb5 /media/(MYHDNAME)_ -o force
```

Let me know how you get on.

Cheers

Jim

---

### Post by llamabr on 2009-04-27
except before you do that, do this:

```
cd /media/
sudo mkdir disk
```

then replece above with:


```
sudo mount -t ntfs-3g /dev/sdb5 /media/(MYHDNAME)_ -o force
```

rather than:
```
/media/(MYHDNAME)_
```

---

### Post by llamabr on 2009-04-27
Sorry:

```
sudo mount -t ntfs-3g /dev/sdb5 /media/disk -o force
```

---

### Post by firdaus313 on 2009-04-28
I've tried your suggestion. But this dmseg appeared:

ntfs_attr_pread: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.

Any other way? TQ friends..

---

