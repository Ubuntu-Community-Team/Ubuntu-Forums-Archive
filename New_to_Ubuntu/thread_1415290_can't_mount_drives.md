---
title: "can't mount drives"
date: 2010-02-24
forum: New to Ubuntu
---

### Post by libihero on 2010-02-24
my ubuntu wont mount drives.  it doesnt detect my windows partition, and when i plug in usbs, it wont mount them :(

---

### Post by Ozymandias_117 on 2010-02-24
Have you checked "sudo fdisk -l" after plugging in your usb devices? And if they aren't there, have you checked "sudo lsusb"?

---

### Post by libihero on 2010-02-24
This is what I get when I do sudo fdisk -l

```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc515122e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7650    61440000    7  HPFS/NTFS
/dev/sda3           29916       30401     3903795    5  Extended
/dev/sda4            7651       29915   178843612+  83  Linux
/dev/sda5           29916       30401     3903763+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 4025 MB, 4025810432 bytes
124 heads, 62 sectors/track, 1022 cylinders
Units = cylinders of 7688 * 512 = 3936256 bytes
Disk identifier: 0x000553bc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1022     3928537    c  W95 FAT32 (LBA)
```

i cant tell if my usb is being detected, but when i go to nautilus, my windows partition doesnt even show up.  it used to but i dont kno what happened

---

### Post by cronos on 2010-02-25
I have the same problem.

---

### Post by pingu1 on 2010-02-25
I once actually solved a mountingproblem (think it was a wireless mouse) by just typing "sudo lsusb" in terminal.... I guess that's what solved it... cause it worked one second after that command, but not before it....

---

### Post by libihero on 2010-02-25
i dont know if mounting is even the right word for it any more, i think its more "detect", since it's not like i can see my windows partition and not mount it.  my windows partition does not even show in nautilus, nor do plugged in usbs

---

### Post by thegod_slayer on 2010-02-25
hello everyone....
i hope this would help you all....
Windows Vista, XP, 2000, older NT systems, and Windows Server 2003 and 2008 are formatted with NTFS.  
The **ntfs-3g** driver is used in linux to read and write NTFS partitions. 
The ntfs-3g packages comes pre-installed in currently supported versions of Ubuntu and most NTFS devices should work out of the box without further configuration. 
 
**however i think somehow your ntfs-3g pakage got erased.**


try this-----
The ntfs-config application is a simple GUI configuration tool for those that find they need to enable/disable NTFS capabilities. 

you can search for "ntfs-config" in [Synaptic]("https://help.ubuntu.com/community/SynapticHowto") or install via terminal: sudo apt-get install ntfs-config

Launch **NTFS Configuration Tool** from Applications->System Tools, 
or via the terminal: gksudo ntfs-config

If you have at least one internal NTFS partition, it will allow you to
check both boxes, otherwise you can only check the box for external

If your NTFS partition(s) are not yet configured, it will ask you to
choose a name that will be used as the mount point (please no spaces).
Then enable write support for internal and/or external devices.
devices.

happy ubuntu-----:KS:KS:KS:KS

---

### Post by libihero on 2010-02-25
thanks!  that solved half the problem, i can now see my windows partition :)
but when i plug a usb into my laptop that still wont show up

---

### Post by libihero on 2010-02-25
here's a pic to explain best what i mean.  it used to only say "Filesystem" before the previous fix.  but from what i remember there was more than just "filesystem" and my windows partition...
but with a usb plugged in the usb wont even show

---

### Post by DirtyBeets on 2010-02-25
What's the output of

```
df -h
```
?

---

### Post by libihero on 2010-02-25
here it is

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda4             168G   21G  139G  13% /
udev                  943M  324K  943M   1% /dev
none                  943M  856K  942M   1% /dev/shm
none                  943M  180K  943M   1% /var/run
none                  943M     0  943M   0% /var/lock
none                  943M     0  943M   0% /lib/init/rw
/dev/sda1              59G   26G   34G  44% /media/Windows

```

---

### Post by libihero on 2010-02-26
bump...
i cant access my cd drive either, like all the drives arent showing

---

### Post by cronos on 2010-02-26
I have managed to manually mount my HDDs and CD/DVD using the Disk Utility that can be found under the System/Administration menu.  It is not an ideal fix, but I hope it helps you, too.

---

### Post by libihero on 2010-02-27
ok it does show there....
so is there a problem with nautilus or something?

---

### Post by libihero on 2010-02-28
bump :(

---

### Post by cronos on 2010-03-01
I wish I know how to fix the problem properly or what caused the problem... I am surprised that the problem doesn't seem widespread.

---

### Post by libihero on 2010-03-01
ya... i think imma just reinstall :(

---

### Post by Pritamsng on 2010-03-01
try "mount /dev/sdc1 /mnt"
 
tell me the out put..

---

### Post by teward on 2010-03-01
I usually use gparted to check drives, and would ask you to mess with system files, but if you mess with the system files, you'll nuke your systems, so I ask you to do this:  plug in the USB stick, load up gparted, see if it detects it as a second drive/device (use the dropdown list for devices)

---

### Post by cronos on 2010-03-01
> **libihero said:**
> ya... i think imma just reinstall :(

I think as long as you can manually mount the HDD/DVD, then it would be better to reinstall when Ubuntu 10.04 is released.

---

### Post by cronos on 2010-03-02
> **TrekCaptainUSA said:**
> I usually use gparted to check drives, and would ask you to mess with system files, but if you mess with the system files, you'll nuke your systems, so I ask you to do this:  plug in the USB stick, load up gparted, see if it detects it as a second drive/device (use the dropdown list for devices)

In my case, my HDD has Ubuntu and Windows XP with some NTFS partitions.  When I click on Computer from the Places menu, I can only see Filesystem, unless I manually mount the partitions, external USB HDD or CD/DVD drive using the Disk Utility from System/Administration menu.

I have never used Gparted to mess with the system.  But, when I run Gparted, it detects my external USB HDD, as well as my Windows partitions.

---

