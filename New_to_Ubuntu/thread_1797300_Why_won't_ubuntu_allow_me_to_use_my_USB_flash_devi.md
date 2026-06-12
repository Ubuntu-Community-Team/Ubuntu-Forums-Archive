---
title: "Why won't ubuntu allow me to use my USB flash device?"
date: 2011-07-04
forum: New to Ubuntu
---

### Post by brawnypandora0 on 2011-07-04
On the panel sidebar, it says 1.0 GB Filesystem, but when I click on it, I get a message that reads:

Unable to mount 1.0 GB Filesystem

Not Authorized

Why won't Ubuntu allow me to do such a simple task??!!!!

---

### Post by cre8ive65 on 2011-07-04
> **brawnypandora0 said:**
> On the panel sidebar, it says 1.0 GB Filesystem, but when I click on it, I get a message that reads:

Unable to mount 1.0 GB Filesystem

Not Authorized

Why won't Ubuntu allow me to do such a simple task??!!!!

Go into terminal and type
```
gksu nautilus
```

Bascially a superuser file browser, from there you can change the permissions of the drive, allowing you to use it

---

### Post by brawnypandora0 on 2011-07-04
Ok, now I see a browser with a purple background. But where do I go to change the permissions? I'm still getting the same Not Authorized popup.

---

### Post by nzjethro on 2011-07-04
Did it prompt you for your password?

You could always try to manually mount the drive, using:
```
sudo mount /dev/sdXX /mnt
```
Where sdXX is your device number which you can find from gparted, or running:
```
sudo fdisk -l
```

---

### Post by brawnypandora0 on 2011-07-04
> **nzjethro said:**
> Did it prompt you for your password?

You could always try to manually mount the drive, using:
```
sudo mount /dev/sdXX /mnt
```Where sdXX is your device number which you can find from gparted, or running:
```
sudo fdisk -l
```

Still not working

user@user-laptop ~ $ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005243b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7135    57306112   83  Linux
/dev/sda2            7135        7296     1296385    5  Extended
/dev/sda5            7135        7296     1296384   82  Linux swap / Solaris
user@user-laptop ~ $ sudo mount /dev/sda1 /mnt
user@user-laptop ~ $ sudo mount /dev/sda2 /mnt
mount: you must specify the filesystem type
user@user-laptop ~ $ sudo mount /dev/sda5 /mnt
/dev/sda5 looks like swapspace - not mounted
mount: you must specify the filesystem type

---

### Post by maizuddin35 on 2011-07-04
what os do you use?
what about check out in Disk Utility.

---

### Post by maizuddin35 on 2011-07-04
what os do you use?
what about check out in Disk Utility. then you try to mount it up in there?

---

### Post by brawnypandora0 on 2011-07-04
> **maizuddin35 said:**
> what os do you use?
what about check out in Disk Utility. then you try to mount it up in there?

How do I mount it?

---

### Post by Wim Sturkenboom on 2011-07-05
sda is (more than likely) your normal hard disk. As there is no other disk in your fdisk output, it looks like the flash drive is not properly detected.

Immediately after inserting the stick, post the last 15 lines of the output of the dmesg command. I unfortunately don't have access to a Linux desktop so can't show what you should expect (something with sdb, scsi)

```

dmesg |tail -n15

```

---

### Post by brawnypandora0 on 2011-07-05
[12949.592951] usb 1-4: configuration #1 chosen from 1 choice
[12949.594649] scsi5 : SCSI emulation for USB Mass Storage devices
[12949.594919] usb-storage: device found at 6
[12949.594924] usb-storage: waiting for device to settle before scanning
[12954.592635] usb-storage: device scan complete
[12954.593858] scsi 5:0:0:0: Direct-Access     SMI      USB DISK         1100 PQ: 0 ANSI: 0 CCS
[12954.599153] sd 5:0:0:0: Attached scsi generic sg2 type 0
[12954.601577] sd 5:0:0:0: [sdb] 2030592 512-byte logical blocks: (1.03 GB/991 MiB)
[12954.602558] sd 5:0:0:0: [sdb] Write Protect is off
[12954.602566] sd 5:0:0:0: [sdb] Mode Sense: 43 00 00 00
[12954.602573] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[12954.606310] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[12954.606322]  sdb: sdb1
[12954.611687] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[12954.611700] sd 5:0:0:0: [sdb] Attached SCSI removable disk

So what's going on? It detects it but won't mount it. I WANT it TO MOUNT.

---

### Post by brawnypandora0 on 2011-07-05
bump

---

### Post by Wim Sturkenboom on 2011-07-06
Sorry, don't know what's going on. Is it formatted? Does it work on other system (if you have one) or on other OS (if you have dual boot)?

Others might have more ideas?

Did you run the *fdisk -l* (post #5) while the stick was inserted?

---

### Post by jtarin on 2011-07-06
sudo mount /dev/sdb /mnt

then go to /mnt directory to look at the contents.

---

### Post by brawnypandora0 on 2011-07-06
> **jtarin said:**
> sudo mount /dev/sdb /mnt

then go to /mnt directory to look at the contents.

but that's too long-winded! I want plug and play like with Windows!

---

### Post by jtarin on 2011-07-06
> **brawnypandora0 said:**
> but that's too long-winded! I want plug and play like with Windows!
Sorry about that.....let me spend a few more hours researching that for you.:lolflag:

---

### Post by Wim Sturkenboom on 2011-07-06
> **brawnypandora0 said:**
> but that's too long-winded! I want plug and play like with Windows!
My goodness, lets first try to get it working. If that stick is not functioning, we are wasting our time.

And it must probably be

```

sudo mount /dev/sdb**[COLOR="Red"]1[/COLOR]** /mnt

```

---

### Post by jtarin on 2011-07-06
> **Wim Sturkenboom said:**
> My goodness, lets first try to get it working. If that stick is not functioning, we are wasting our time.

And it must probably be

```

sudo mount /dev/sdb**[COLOR="Red"]1[/COLOR]** /mnt

```I agree.

---

### Post by oldos2er on 2011-07-06
What file system is on the device? If NTFS, was it shut down cleanly on its last use?

---

### Post by brawnypandora0 on 2011-07-07
There's nothing wrong with the USB disk since it works on my other Windows computer. It's ubuntu that's the problem. Probably some permission error. 

How do I fix it?

---

### Post by jtarin on 2011-07-07
> **brawnypandora0 said:**
> 
How do I fix it?The same way I would if it were mine. First I would look for the information which is readily available anywhere on the internet for those with the initiative to look for it. It took me less than three minutes to find the answer. Ubuntu/Linux is not about being a geek...it's about information when you need it.

> To enable or disable automount open a terminal and type gconf-editor followed by the [Enter] key.

Browse to /apps/nautilus/preferences/media_automount.

The media_automount key controls whether to automatically mount media. If set to true, then Nautilus will automatically mount media such as user-visible hard disks and removable media on start-up and media insertion.

There is another key /apps/nautilus/preferences/media_automount_open. This controls whether to automatically open a folder for automounted media. This key can also be set in the Nautilus (file manager) window. From the Edit menu in Nautilus select Preferences and then select the Media tab.

If set to true, then Nautilus will automatically open a folder when media is automounted. This only applies to media where no known x-content/* type was detected; for media where a known x-content type is detected, the user configurable action will be taken instead. [This can be configured as shown below.]("https://help.ubuntu.com/community/Mount/USB") 

---

### Post by coffeecat on 2011-07-07
> **brawnypandora0 said:**
> On the panel sidebar, it says 1.0 GB Filesystem, but when I click on it, I get a message that reads:

Unable to mount 1.0 GB Filesystem

Not Authorized

Why won't Ubuntu allow me to do such a simple task??!!!!

Just a thought - did you, by chance, install the application usbmount? If you did, uninstall it.

---

