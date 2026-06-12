---
title: "Copy to USB from command prompt"
date: 2009-06-06
forum: New to Ubuntu
---

### Post by roaftech on 2009-06-06
Toshiba Satellite Pro (MS-free zone)
Please can someone help with one of these:

A]  An attempted upgrade to 9.04 has fouled up my laptop leaving me without a graphical interface (I can logon normally but then nothing appears at all) but I still have access to the command line via the CTRL+ALT+F2 routine.  I need to copy off my previous files before reloading 8.10 from scratch again. What is the command sequence for recognising a usb drive?

B] I did a fresh install on a separate partition which works fine but I cannot access any files on the old partition - what is the procedure for moving files across partitions?

Many thanks.

---

### Post by 3rdalbum on 2009-06-06
You need to mount the USB device. If your desktop is still working but hidden, the mounting should happen automatically, and the USB device will be available under /media.

If it's not, then you need to do the following:

```
mkdir ~/disk
```

Makes a new directory mountpoint, called "disk", inside your home directory. Don't use "sudo"; you want this directory to have the same permissions as your user.

```
sudo fdisk -l
```

Shows a list of available partitions, their types and their device file names, for instance "/dev/sdb". Use this to find out what device file name your USB stick is.

```
sudo mount /dev/sdb ~/disk
```

And that should mount the /dev/sdb device into the directory ~/disk. Obviously, substitute /dev/sdb for whatever the correct device file name is of the USB device.

After you're done copying, you unmount with:

```
sudo umount ~/disk
```

The same procedure can be used to mount your other partition. Happiness!

---

### Post by roaftech on 2009-06-06
G'day 3A, thanks for the quick response.  I'll give it a whirl right away.

Best wishes,
Steve

---

### Post by roaftech on 2009-06-07
Many thanks - that was the info I needed and I have been able to save my files before re-installing 8.10 satisfactorily.

Best wishes,

---

### Post by 3rdalbum on 2009-06-07
Glad to be of help.

---

