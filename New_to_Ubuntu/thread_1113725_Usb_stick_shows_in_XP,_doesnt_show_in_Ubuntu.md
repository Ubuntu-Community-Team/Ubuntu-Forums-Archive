---
title: "Usb stick shows in XP, doesnt show in Ubuntu"
date: 2009-04-01
forum: New to Ubuntu
---

### Post by Cornbreadly on 2009-04-01
I am not that much of a new user but this seems so simple to me I can't believe I am not able to figure it out on my own.  A good post for the New User area.

I have new 8gb [OCZ Diesel Usb stick]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820227332") works excellently in windows.  In ubuntu, i can't get it to show up in gparted to format.  It doesn't automount like every other usbstick I have.  I have some output from what I have gleaned.  It is simply not there.

It is formated NTFS via xp.  I could not find it.  IS the 8gb an issue?  I have the ntfs and fat32 libs installed as I port stuff to and fro from work all the time.  This is just weird.  I thought all usb sticks were the same.

dmesg | tail
```
[149030.746568] sd 2:0:0:0: [sdc] 1994385 512-byte hardware sectors (1021 MB)
[149030.749578] sd 2:0:0:0: [sdc] Write Protect is off
[149030.749588] sd 2:0:0:0: [sdc] Mode Sense: 03 00 00 00
[149030.749593] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[149030.750182]  sdc: sdc1
[149030.778049] sd 2:0:0:0: [sdc] Attached SCSI removable disk
[149030.778565] sd 2:0:0:0: Attached scsi generic sg4 type 0
[149030.837564] sr2: scsi3-mmc drive: 8x/40x writer xa/form2 cdda tray
[149030.838749] sr 2:0:0:1: Attached scsi CD-ROM sr2
[149030.839151] sr 2:0:0:1: Attached scsi generic sg5 type 5

```

fdisk -l
```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002edd4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4863    39062016   83  Linux
/dev/sda2            4864       14593    78156225    5  Extended
/dev/sda5            4864        5015     1220908+  82  Linux swap / Solaris
/dev/sda6            5016       14593    76935253+  83  Linux

Disk /dev/sdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7109    57103011   83  Linux
/dev/sdb2            7110        7297     1510110    5  Extended
/dev/sdb5            7110        7297     1510078+  82  Linux swap / Solaris

```

---

### Post by cariboo on 2009-04-01
I can't tell exactly, from the output of dmesg, it looks like your usb device is being mounted as a cd.

Jim

---

### Post by llamabr on 2009-04-01
That is weird.  The relevant bit is here:

```
[149030.750182]  sdc: sdc1
```

It looks like it's not automounting.  Until you get that figured out, you can mount it manually, like this:

```
sudo mkdir /media/usb/
sudo mount /dev/sdc1 /media/usb/
cd /media/usb/
ls
```

Also, fdisk is useful, but we could also stand to see the output of 

```
df
```

and 

```
cat /etc/fstab/
```

---

### Post by Cornbreadly on 2009-04-02
In windows, when I was able to see the thumbdrive, I could see that 40 mb was taken up already from the thmbdrive that showed up as something "proprietary"ish even I after I renamed the drive (OCZ Diesel something something.)  I had an cruzer micro that always had a partition show up as a cd in windows machines.  I think it could encrypt it I wanted too.  DO you think the 8gb Diesel is doing something along those lines?
fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=ca5e4b76-c75b-4f4f-af61-3a3b1ff32490 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=f8c23ee5-a527-4f0d-b38e-32b5eacfd3b7 /home           ext3    relatime        0       2
# /dev/sda5
UUID=7d0ae231-aa3e-4a3d-891e-e73b6487b23a none            swap    sw              0       0
# /dev/sdb5
UUID=aae91925-3f2e-4e77-9de9-960e0d97e0c2 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

df
```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda6             75728068   3258200  68623108   5% /
tmpfs                   256812         0    256812   0% /lib/init/rw
varrun                  256812       104    256708   1% /var/run
varlock                 256812         0    256812   0% /var/lock
udev                    256812      2808    254004   2% /dev
tmpfs                   256812       588    256224   1% /dev/shm
lrm                     256812      2004    254808   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sda1             38448276  23126184  13368992  64% /home

```

And dmesg is doing something new.
```
[   30.744550] NET: Registered protocol family 17
[   32.566031] NET: Registered protocol family 10
[   32.568419] lo: Disabled Privacy Extensions
[   43.020018] eth0: no IPv6 routers present
[  118.412317] ppdev0: registered pardevice
[  118.460227] ppdev0: unregistered pardevice
[  119.564118] ppdev0: registered pardevice
[  119.612038] ppdev0: unregistered pardevice
[  119.629595] ppdev0: registered pardevice
[  119.676347] ppdev0: unregistered pardevice

```

and fdisk -l...
```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002edd4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4863    39062016   83  Linux
/dev/sda2            4864       14593    78156225    5  Extended
/dev/sda5            4864        5015     1220908+  82  Linux swap / Solaris
/dev/sda6            5016       14593    76935253+  83  Linux

Disk /dev/sdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7109    57103011   83  Linux
/dev/sdb2            7110        7297     1510110    5  Extended
/dev/sdb5            7110        7297     1510078+  82  Linux swap / Solaris


```

---

### Post by mikechant on 2009-04-02
Is it the 'U3' business - a special partition which looks like a CDROM to fool windows into autorunning software?

See [http://en.wikipedia.org/wiki/U3](http://en.wikipedia.org/wiki/U3) in particular the 'non-Windows issues' bit.

If you have a Mac or Windows install available, the U3 suppliers have removal tools available (links from wikipedia article). There is annoyingly no removal tool available for Linux, but I found these instructions
> Peter wrote at 21 January, 2009 05:21... 

So hopefully someone will find this useful. After lots of googling I found that there weren't any instructions for removing U3 under linux. Truth be told, it's really easy, but the solution is as obscure as it is easy.

1)Mount the U3 "cd" partition
2)Run Mount to find out the name of the device that U3 is on. It should be some thing like scd#, the important part is the number there.
2.5) Just to be sure you've got the right device check that /dev/sr# is a symlink to /dev/scd# that you just found.
3) Now that you know which device you're looking for you can start the actual removal. cd to /sys/class/block/sr#/device/
4)In this directory is a file named delete, it's write only by root, and if you write to it (I've only ever tried with "1") the U3 partition will be removed. With root privileges 'echo "1" > delete' removes it quite nicely. 

These instructions appear at the bottom of this web page: 
[http://noisetheatre.blogspot.com/2006/08/uninstall-u3-and-free-your-usb-drive.html](http://noisetheatre.blogspot.com/2006/08/uninstall-u3-and-free-your-usb-drive.html)

However, it seems you have to be able to sucessfully mount the U3 partition (as a CDROM) so do this, and I'm not clear if you have managed this.

Apparently just wiping the partition with gparted does not work.

---

### Post by Cornbreadly on 2009-04-02
This is getting weird.  

I just recieved my shiny new eee in te mail today.  I was going to install eeebuntu right away but I decided to see if the the OS that the eee came with would recognize it.  It did.  

My ubuntu 8.10 install is the only PC that can't find the 8gb deisel thumbdrive.  It is not a U3 styled drive.  Thanks for the info though, i removed the U3 software on two of my other thumbdrives.

I will update when i get eeebuntu installed.

---

### Post by Cornbreadly on 2009-04-02
It shows on the eee.  It any idea why it won't show on my older desktop?

---

### Post by Cornbreadly on 2009-04-02
I am lost.  It does not work on just one desktop. I think that points to a hardware issue but... USB 2.0 is USB 2.0 right?

**PC type: result**
[LIST]
[*]xp laptop sp 3: view and mount
[*]xp desktop work sp 2: view and mount
[*]ubuntu 8.04 desktop: view and mount
[*]eee 901 eeebuntu: view and mount
[*]ubuntu 8.10 desktop:  A mystery?
[/LIST]

Please help.  I will be up for a few more hours tonight.  I would love to fix this.

---

### Post by llamabr on 2009-04-02
Are you able to mount it manually?  (see my post above).

---

### Post by Cornbreadly on 2009-04-02
No I was not.  Do you want some more output from the command line?

---

### Post by Cornbreadly on 2009-04-05
I still would like to figure this out.  anyone game?

---

### Post by any.linux12 on 2009-04-06
In which file system is the usb stick? Maybe you have to do apt-get install ntfs.

---

### Post by tarps87 on 2009-04-06
Can you post the output of the error message when you tried to mount it manually please

---

### Post by card_ace on 2009-04-06
this may not apply here but sometimes my USB drives don't show up in ubuntu 8.10 either.  i've found that if i boot into win. XP and "Safely Remove Hardware" then it works fine, but i'm not sure why.  That's all i got, good luck!

---

### Post by Cornbreadly on 2009-04-25
The promblem was not anything linuxy... it was design.

 THe front USB female slots are deep and the male USB nub is short... basically it was not a match made in heaven. Going in the back door was the answer in this case.  The USB sticks mounts automagically like everything else, I just had to use the back USB slots.  Weird because even in the front, I would get an LED flash from the USB stick.  

I guess I just have a freaky computer.

How about Jaunty though?  Awesome right?

---

