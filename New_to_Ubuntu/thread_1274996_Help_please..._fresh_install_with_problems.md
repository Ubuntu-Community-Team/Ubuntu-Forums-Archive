---
title: "Help please... fresh install with problems"
date: 2009-09-25
forum: New to Ubuntu
---

### Post by humphreybc on 2009-09-25
Hi there,

I just re-installed Ubuntu 9.04 on my laptop and I'm having some problems that I weren't having before... here they are:

1) I have a second Hard Drive in my laptop, called "Media Disk" that is formatted to ext4. Ubuntu won't mount it automatically on startup. It currently gets mounted to /media/Media Disk when I click on it. How can I get it to mount on startup? I remember doing this months ago but I've forgotten how.

2) Network Manager will no longer connect to our WPA2 Enterprise PEAP MSCHAPv2 Authenticated university network.... it was unreliable on my last install (disconnecting all the time), but now it's not connecting at all. Are there any known issues with this type of security, or is it the university's fault?

3) Suspend/Resume does not work. When I suspend, the laptop goes to sleep... but when I resume, all that happens is the laptop starts up but the screen remains OFF. There is NO hard drive activity either, and no key combinations work to restart the computer... I have to hard reset. NOTE: I am using the open source radeon drivers this time round, last time it worked with the fglrx drivers - but the whole reason I re-installed is because I wanted to switch to open source but I had some problems getting rid of fglrx/installing the radeon drivers.


I've got all the latest updates.

Please help!

---

### Post by tomBorgia on 2009-09-25
I can help with 2 - [http://ubuntuforums.org/showthread.php?t=1226032&highlight=eduroam]("http://ubuntuforums.org/showthread.php?t=1226032&highlight=eduroam")

---

### Post by NightwishFan on 2009-09-25
To mount something on startup you can add an entry to /etc/fstab

First create a mount point:
```
sudo mkdir /mnt/media
```

Then I will need the output of:
```
sudo fdisk -l
```
and
```
sudo blkid
```

When I have all of the above, you can edit the /etc/fstab file by using the command:
```
gksudo gedit /etc/fstab
```

Then add a line like this:
```
/dev/???       /mnt/media    ext4    defaults,errors=remount-ro  0  2  
```

We will either need the correct /dev/??? or the uuid from the command above.

Please ask for help if you need any.

---

### Post by humphreybc on 2009-09-25
```

benjamin@benjamin-laptop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xac578e16

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18966   152344363+  83  Linux
/dev/sda2           18967       19457     3943957+   5  Extended
/dev/sda5           18967       19457     3943926   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xac578e17

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x017d7e1c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    b  W95 FAT32
benjamin@benjamin-laptop:~$ sudo blkid
/dev/sda1: UUID="50f680be-9892-4f8b-a659-e03265301b9e" TYPE="ext4" 
/dev/sda5: TYPE="swap" UUID="c2007176-af3e-454f-874d-c2fe7201cd75" 
/dev/sdb1: LABEL="Media Disk" UUID="440d6604-ea4d-4fd1-8983-b3fe1d4726ef" TYPE="ext4" 
/dev/sdc1: LABEL="500GB Exter" UUID="E490-53EE" TYPE="vfat" 
benjamin@benjamin-laptop:~$ 

```


I think I tried this method before but it didn't really work, perhaps because of the space in the drive name "Media Disk."

I tried to rename it but it wouldn't let me.

Thanks for your help!

P.S Ignore /dev/sdc1 "500GB External" as this is, as you could guess, an external hard drive that was plugged into my computer at the time. The drive I want to mount on startup is /dev/sdb1

---

### Post by NightwishFan on 2009-09-25
Make sure the directory /mnt/media exists then add this line to /etc/fstab

Make sure that your media drive is not already added to /etc/fstab

You need to add this line:

```
UUID="440d6604-ea4d-4fd1-8983-b3fe1d4726ef"       /mnt/media    ext4    defaults,errors=remount-ro  0  2
```

---

### Post by Yagami-kun on 2009-09-25
I installed ubuntu 8.10  successfully but after 2-3 restart i stuck up into booting.Actually i dont understand what is the problem? As i restart it grub comes up and ask to choose and then ubuntu 8.10 boots but it stuck up with loading user keep on loading it. I can access to terminal thorugh Ctrl+Alt+F4.

Can anyoone help me out of this ???????

---

### Post by humphreybc on 2009-09-25
> **NightwishFan said:**
> Make sure the directory /mnt/media exists then add this line to /etc/fstab

Make sure that your media drive is not already added to /etc/fstab

You need to add this line:

```
UUID="440d6604-ea4d-4fd1-8983-b3fe1d4726ef"       /mnt/media    ext4    defaults,errors=remount-ro  0  2
```

EDIT: Okay sorry that did work, it just didn't mount it as a drive but rather as folders. That's all good. Thanks for your help!

---

