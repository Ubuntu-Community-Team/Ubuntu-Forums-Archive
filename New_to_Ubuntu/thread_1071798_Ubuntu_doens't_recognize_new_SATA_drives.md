---
title: "Ubuntu doens't recognize new SATA drives"
date: 2009-02-16
forum: New to Ubuntu
---

### Post by -=juicyjuice=- on 2009-02-16
Hi, i just added two new SATA hard drives (500 GB, and 1 TB). Also i added in a DVD -RW SATA drive.

I checked my mobo bios and it recognizes them just fine. however, Ubuntu doesn't seem to see them at all, and when i try to install (by booting from the live CD) it seems to not recognize them either. Please help im going insane! 

Thanks, 
    JuicyJuice

---

### Post by cmnorton on 2009-02-16
What designators are you using to find these drives? What's the output of df showing the original drive?

---

### Post by malathion on 2009-02-16
Most likely ubuntu does "see" them but is not mounting them because they have not been added to fstab.

Please run this command and paste the results:

```
$ sudo fdisk -l
```

---

### Post by -=juicyjuice=- on 2009-02-16
juicyjuice@juicyjuice-desktop:~$ sudo fdisk -l
[sudo] password for juicyjuice: 

Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1ffb1ffa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9331    74951226   83  Linux
/dev/sda2            9332        9733     3229065    5  Extended
/dev/sda5            9332        9733     3229033+  82  Linux swap / Solaris
juicyjuice@juicyjuice-desktop:~$

---

### Post by agarzon on 2009-02-16
Check the contents of your partition with 


more /etc/fstab

It should give you something like this

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /boot           ext3    defaults        0       2
/dev/hda3       /home           ext3    defaults        0       2
/dev/hda6       /mnt/hda6       ext3    defaults        0       0
/dev/hda7       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/sda1       /mnt/sda1       ext3    defaults        0       0
agarzon@ferengi:~$

---

### Post by -=juicyjuice=- on 2009-02-16
> **agarzon said:**
> Check the contents of your partition with 


more /etc/fstab

It should give you something like this

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /boot           ext3    defaults        0       2
/dev/hda3       /home           ext3    defaults        0       2
/dev/hda6       /mnt/hda6       ext3    defaults        0       0
/dev/hda7       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/sda1       /mnt/sda1       ext3    defaults        0       0
agarzon@ferengi:~$

i did this command and got:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=9dcc3ff9-0669-484d-86f5-30d52226fbc6 /               ext3    relatime,error
s=remount-ro 0       1
# /dev/sda5
UUID=73714163-2392-4163-a996-bdc1046b2894 none            swap    sw            
  0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
## usbfs is the USB group in fstab file:
none /proc/bus/usb usbfs devgid=124,devmode=664 0 0

---

### Post by malathion on 2009-02-16
> **-=juicyjuice=- said:**
> juicyjuice@juicyjuice-desktop:~$ sudo fdisk -l
[sudo] password for juicyjuice: 

Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1ffb1ffa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9331    74951226   83  Linux
/dev/sda2            9332        9733     3229065    5  Extended
/dev/sda5            9332        9733     3229033+  82  Linux swap / Solaris
juicyjuice@juicyjuice-desktop:~$

All right, fdisk does not see the drives. Have they been partitioned? Run gparted to check:

```
$ sudo apt-get install gparted 
$ gksudo gparted
```

Once in gparted, go to gparted->devices and see if your drives appear there. If they do, you can use gparted to partition them. **BE VERY CAREFUL WHEN DOING THIS** since if you accidentally repartition the wrong drive you will irrevocably lose all your data.

---

### Post by -=juicyjuice=- on 2009-02-16
i installed gparted and ran it, refreshed to find new devices and still, all it shows is my 80 GB HD

---

### Post by agarzon on 2009-02-16
This idea may seem desperate, so please if some of the experts call it stupid please let me know in a gentle manner :P

Since Ubnutu can't see the drives, neither from the command line (fdisk or in fstab), nor can gparted see them, try this

Boot from the Ubuntu live CD, then check if gparted  (System/Administration/PartitionEditor)  sees them. If it does, format the drives from there and reboot the system. As it was mentioned earlier, make sure you don't screw up your current 80GB drive.

---

### Post by caljohnsmith on 2009-02-16
Does your BIOS have an "AHCI" or "RAID" option for your SATA drives? If so, enable AHCI, or if you can't do that, try enabling RAID. Then when you boot the Live CD, at the main menu press F6 for boot options, and then to the boot line add:
```
pci=nomsi
```
Then use the "Try Ubuntu without making any changes" option. Let me know if that works for you or not.

---

### Post by -=juicyjuice=- on 2009-02-16
i have to leave now, but i will do this as soon as i get back home.. thank you for the support, and i will get back to you all

---

### Post by Gramps on 2009-02-16
Might be time to start some simple trouble shooting.

Remove all the new drive except the 500 mb and boot with the LiveCD and see if the drive shows up.

If it show up shutdown and add the 1TB back in

Restart with LiveCD, are both drive there?

Could this be the problem?
```
The jumper block adjacent to the SATA interface connector
 on SATA 300MB/s drives can be used to force the drive into
 SATA 150MB/s mode for use with older SATA controllers
 that only work with SATA 150MB/s drives.
```

---

### Post by click4851 on 2009-02-16
those error messages, remind me of a harddrive upgrade I did, once I had the harddrive replaced and the data moved over it wouldn't boot till I went in and updated the UUID's.

---

### Post by -=juicyjuice=- on 2009-02-17
> **caljohnsmith said:**
> Does your BIOS have an "AHCI" or "RAID" option for your SATA drives? If so, enable AHCI, or if you can't do that, try enabling RAID. Then when you boot the Live CD, at the main menu press F6 for boot options, and then to the boot line add:
```
pci=nomsi
```
Then use the "Try Ubuntu without making any changes" option. Let me know if that works for you or not.


THANK YOU SO MUCH! i changed to AHCI in the bios and did what you said with F6 and the pci=nomsi and it worked! I will let everyone know if anything else arises. 

thanks again, 
     juicy juice

---

### Post by caljohnsmith on 2009-02-17
That's great news, glad to hear that worked OK. Cheers and hope your Ubuntu installation goes smoothly. :)

---

