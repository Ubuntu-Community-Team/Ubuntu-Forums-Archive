---
title: "usbmount - fat32"
date: 2010-01-24
forum: New to Ubuntu
---

### Post by Psumi on 2010-01-24
I was wondering, how do I go about automounting a FAT32 USB Drive with usbmount? My usbmount.conf already has vfat in its FILESYSTEMS, so I don't know what the problem is.

---

### Post by Psumi on 2010-01-25
I figured it wouldn't be answered by the time I got back from my one day vacation. :D

Bump.

---

### Post by Psumi on 2010-01-26
Bumpsorx

---

### Post by warfacegod on 2010-01-26
I'm making a guess here. Try changing vfat to vfat32.

---

### Post by jd65pl on 2010-01-26
Do you get any info from dmesg when you plug it in? It should be the last information displayed if run right after the usb drive is plugged in.
```
sudo dmesg
```

Also check the log
```
tail -f /var/log/messages
```

You can check udev is running,
```
ps aux | grep udevd | grep -viE 'grep'
```

---

### Post by Psumi on 2010-01-26
dmesg:

```
[  156.823063] usb 1-4: USB disconnect, address 2
[  160.800153] usb 1-4: new high speed USB device using ehci_hcd and address 3
[  160.933177] usb 1-4: configuration #1 chosen from 1 choice
[  160.936337] scsi3 : SCSI emulation for USB Mass Storage devices
[  160.936628] usb-storage: device found at 3
[  160.936635] usb-storage: waiting for device to settle before scanning
[  165.936431] usb-storage: device scan complete
[  165.937052] scsi 3:0:0:0: Direct-Access     SanDisk  Cruzer           8.01 PQ: 0 ANSI: 0 CCS
[  165.938306] sd 3:0:0:0: Attached scsi generic sg2 type 0
[  165.942888] sd 3:0:0:0: [sdb] 15682559 512-byte logical blocks: (8.02 GB/7.47 GiB)
[  165.944668] sd 3:0:0:0: [sdb] Write Protect is off
[  165.944681] sd 3:0:0:0: [sdb] Mode Sense: 45 00 00 08
[  165.944689] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[  165.958840] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[  165.958851]  sdb: sdb1
[  165.967739] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[  165.967747] sd 3:0:0:0: [sdb] Attached SCSI removable disk
```

tail -f /var/log/messages:
```
Jan 26 13:55:12 isuma kernel: [  156.823063] usb 1-4: USB disconnect, address 2
Jan 26 13:55:16 isuma kernel: [  160.800153] usb 1-4: new high speed USB device using ehci_hcd and address 3
Jan 26 13:55:16 isuma kernel: [  160.933177] usb 1-4: configuration #1 chosen from 1 choice
Jan 26 13:55:16 isuma kernel: [  160.936337] scsi3 : SCSI emulation for USB Mass Storage devices
Jan 26 13:55:21 isuma kernel: [  165.937052] scsi 3:0:0:0: Direct-Access     SanDisk  Cruzer           8.01 PQ: 0 ANSI: 0 CCS
Jan 26 13:55:21 isuma kernel: [  165.938306] sd 3:0:0:0: Attached scsi generic sg2 type 0
Jan 26 13:55:21 isuma kernel: [  165.942888] sd 3:0:0:0: [sdb] 15682559 512-byte logical blocks: (8.02 GB/7.47 GiB)
Jan 26 13:55:21 isuma kernel: [  165.944668] sd 3:0:0:0: [sdb] Write Protect is off
Jan 26 13:55:21 isuma kernel: [  165.958851]  sdb: sdb1
Jan 26 13:55:21 isuma kernel: [  165.967747] sd 3:0:0:0: [sdb] Attached SCSI removable disk
```

and ps aux | grep udevd | grep -viE 'grep':
```
root       407  0.0  0.1   2308   764 ?        S<s  13:52   0:00 udevd --daemon
root      1389  0.0  0.1   2696  1004 ?        S<   13:55   0:00 udevd --daemon
root      1403  0.0  0.1   2308   732 ?        S<   13:55   0:00 udevd --daemon
```

---

### Post by jd65pl on 2010-01-27
Is it not mounted for /media/sdb ? what is the output of

```
sudo fdisk -l
```

---

### Post by Psumi on 2010-01-27
> **jd65pl said:**
> Is it not mounted for /media/sdb ? what is the output of

```
sudo fdisk -l
```

That output is as follows for the USB Drive:

```
Disk /dev/sdb: 8029 MB, 8029470208 bytes
255 heads, 63 sectors/track, 976 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000bc467

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         976     7839698    b  W95 FAT32
```

The drive is NOT mounted however, as you cannot open files from it through programs like smplayer or totem without first left clicking it in pcmanfm on the tree pane (it appears as SanDisk cruzer, and is only there for show until you click on it; then it becomes mounted.)

---

### Post by jd65pl on 2010-01-27
Once it is mounted what is the output of:

```
mount -l
```

I can't replicate or offer any solution, I'm using KDE FWIW

---

### Post by Psumi on 2010-01-27
> **jd65pl said:**
> I can't replicate or offer any solution, I'm using KDE FWIW

That's because KDE and GNOME automount properly. Installing the mini.iso and then installing xfce4 metapackage or lxde metapackage or doing an openbox setup without nautilus/etc. will cause the issue I have. Anyway, mount -l:

```
/dev/sdb1 on /media/MELODY type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077) [MELODY]
```

This is after it's mounted (left clicked in pcmanfm.)

---

### Post by jd65pl on 2010-01-27
Try this [http://wiki.archlinux.org/index.php/HAL#USB_sticks_and_drives_do_not_automount_correctly](http://wiki.archlinux.org/index.php/HAL#USB_sticks_and_drives_do_not_automount_correctly)

---

### Post by Psumi on 2010-01-27
> **jd65pl said:**
> Try this [http://wiki.archlinux.org/index.php/HAL#USB_sticks_and_drives_do_not_automount_correctly](http://wiki.archlinux.org/index.php/HAL#USB_sticks_and_drives_do_not_automount_correctly)

I don't have an /etc/hal directory, what should I do? Create it?

I also don't have policykit installed, is this a problem?

---

### Post by jd65pl on 2010-01-27
This is probably a symptom of you adding a DE to a server install and something not quite going smoothly.

```
sudo apt-get install hal
```

---

### Post by Psumi on 2010-01-27
> **jd65pl said:**
> This is probably a symptom of you adding a DE to a server install and something not quite going smoothly.

```
sudo apt-get install hal
```

Already installed. I checked this before going through with posting my previous reply.

And no, it isn't a server install, it's this: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by jd65pl on 2010-01-27
```
hald --version
```

---

### Post by Psumi on 2010-01-27
```
HAL package version: 0.5.13
```

By the way, HAL is not implemented fully in 9.10, and 10.04 moves it to the kernel and removes hal itself.

---

### Post by jd65pl on 2010-01-27
```
ps aux | grep 'hald' | grep -v 'grep'
```

---

### Post by Psumi on 2010-01-27
```
103        619  0.0  0.7   5976  3816 ?        Ss   07:39   0:00 hald --daemon=yes
root       802  0.0  0.2   3344  1220 ?        S    07:39   0:00 hald-runner
root       941  0.0  0.2   3412  1112 ?        S    07:39   0:00 /usr/lib/hal/hald-addon-ipw-killswitch
root       972  0.0  0.2   3416  1116 ?        S    07:39   0:00 /usr/lib/hal/hald-addon-leds
root       976  0.0  0.2   3412  1092 ?        S    07:39   0:00 /usr/lib/hal/hald-addon-generic-backlight
root      1002  0.0  0.2   3420  1144 ?        S    07:39   0:01 hald-addon-input: Listening on /dev/input/event6 /dev/input/event0 /dev/input/event7 /dev/input/event4 /dev/input/event2 /dev/input/event1
root      1011  0.0  0.2   3420  1140 ?        S    07:39   0:01 hald-addon-storage: polling /dev/sr0 (every 2 sec)
root      1012  0.0  0.2   3428  1128 ?        S    07:39   0:00 /usr/lib/hal/hald-addon-cpufreq
103       1015  0.0  0.2   3264  1116 ?        S    07:39   0:00 hald-addon-acpi: listening on acpi kernel interface /proc/acpi/event
root      1553  0.0  0.2   3420  1136 ?        S    07:45   0:00 hald-addon-storage: polling /dev/sdb (every 2 sec)
```

---

### Post by Psumi on 2010-01-27
Fine, I'll use ubuntu-desktop or gnome. Geez, no one wants to help revive old hardware.

---

