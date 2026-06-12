---
title: "Freecom 500GB External Hard Drive USB-2"
date: 2009-03-20
forum: New to Ubuntu
---

### Post by krisfrajer on 2009-03-20
Hi
I just bought an external HD for back up. It has a switch to turn it on/off and it is connected via USB. All instructions to install comes in some alien language-> Windows.

How could I use this HD in my  machine? I have done some goggle'ing and I am certain it works in linux but I might have to install some drivers. When I connect the external HD into my machine, my ubuntu tries to mount the HD but it fails. I don't know what to do. As you see, I am totally new and silly ignorant about this.
Can somebody give me a hand/tip/advice?
Thxs,

---

### Post by randysilverwolf on 2009-03-20
Ive been using a few USB drives in Intrepid, i havnt had any problems with drivers or anything with them, but mine were IDE, is yours SATA, or God forbid a Solid State?

---

### Post by dwasifar on 2009-03-20
When the drive is connected but unmounted, does it show up in Gparted?

If so, you should be able to repartition and reformat it, and after that it should mount up just fine.

---

### Post by krisfrajer on 2009-03-20
I dunno if I have gparted in my system. Do  I need to install it?
I have USB connection, but I dont know what type of connection it is. Sata/IDE/solid state? No idea :o

here some info from my machine. You can see the error mounting the 500Gb,
K.



cristian@NARUTO:~/Desktop$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              62G  3.7G   55G   7% /
varrun                471M  148K  471M   1% /var/run
varlock               471M     0  471M   0% /var/lock
udev                  471M   76K  471M   1% /dev
devshm                471M   12K  471M   1% /dev/shm
lrm                   471M   44M  427M  10% /lib/modules/2.6.24-19-generic/volatile
/dev/sda6              41G  8.9G   31G  23% /export/home
/dev/sdb1              75G   50G   26G  67% /export/winXP
/dev/sda7              80G   53G   24G  70% /export/bckUP
gvfs-fuse-daemon       62G  3.7G   55G   7% /home/cristian/.gvfs

=====================================================

cristian@NARUTO:/etc$ more fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=bbe666ce-da95-4d0b-b825-76c87f36714d /               ext3    relatime,errors=remount-ro 0       
1
# /dev/sda5
UUID=43628781-6785-4072-8766-2ec290bbd01a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda6	/export/home	ext3	defaults 0 		 2
/dev/sdb1	/export/winXP   ntfs	defaults 0		 2
/dev/sda7	/export/bckUP 	ext3	defaults 0		 2
cristian@NARUTO:/etc$

---

### Post by sim-value on 2009-03-20
Try safely removing it in windows ... it then should work i think ...

---

### Post by dwasifar on 2009-03-20
> **krisfrajer said:**
> I dunno if I have gparted in my system. Do  I need to install it?

Possibly.  If you have it installed, it will be in System>Administration>Partition Editor.  If not:

```
sudo apt-get install gparted
```

---

### Post by mlentink on 2009-03-20
try checking your dmsg when you plug it in.

If you plug it in, does it show up somewhere in /dev?

I use freecom toughdrives a lot. Whenever I plug one in, it automounts in /media/disk... something or other. Seems to me you want to force it to mount in /export?

---

### Post by krisfrajer on 2009-03-20
> **mlentink said:**
> try checking your dmsg when you plug it in.

If you plug it in, does it show up somewhere in /dev?

I use freecom toughdrives a lot. Whenever I plug one in, it automounts in /media/disk... something or other. Seems to me you want to force it to mount in /export?

No, I really I am not trying to mounted to any specific point. I was hoping it was going to mount by itself. /export is my personal data folder and it is only about 50GB. My new HD is 500 GB. When I turn on the device, my machine tries to automounted but it fails...

I ran my windows virtual desktop (VMware) and it detected my new HD. It happens only that it does not work in linux...

I will keep trying,
K.

---

### Post by krisfrajer on 2009-03-20
> **sim-value said:**
> Try safely removing it in windows ... it then should work i think ...

SIM-Value... your little naughty short nifty tip work ... WORK indeed. Either You are a genius or I am a lucky *******. As you see, we both win!

Thxs a lot to you and all for your two cents,
K.

---

### Post by mlentink on 2009-03-20
Oops. Yeah. Sorry. Should've asked about that as well, because I've found windows-users usualy don't bother to 'safely remove' their usb-drives, because windows doesn;t seem to care. But Linux does care about data integrity. So in the future, in order to avoid trouble, always use the 'safely remove' feature.

Glad it turned out ok!

---

