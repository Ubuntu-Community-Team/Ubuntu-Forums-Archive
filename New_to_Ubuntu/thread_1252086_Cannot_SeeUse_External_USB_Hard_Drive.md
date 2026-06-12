---
title: "Cannot See/Use External USB Hard Drive"
date: 2009-08-28
forum: New to Ubuntu
---

### Post by tharman on 2009-08-28
Hello,
I am somewhat new to Linux but I've been using it for a little while now. I've installed a FOG Imaging Server and a SAMBA server and have those up running fine. But now I am trying to add an External USB Hard Drive for additional storage.

I know the computer is seeing it because I can see it connecting and disconnecting when I run dmesg and it shows up as:

 Bus 001 Device 009: ID 13fd:160f Initio Corporation

when I run lsusb.

It is a 500GB SATA Seagate Barracuda in a StarTech 3.5" eSATA/USB 2.0 Enclosure.
There is nothing fancy about the enclosure it just has a power button.


This is all I get when I run sudo fdisk -l

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3c2d759d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14762   118575733+  83  Linux
/dev/sda2           14763       14946     1477980    5  Extended
/dev/sda5           14763       14946     1477948+  82  Linux swap / Solaris


So I'm guessing I just need to mount it or format it or somthing. I just can't seem to figure out how.

Any help would be appreciated.

---

### Post by celticdevildog on 2009-08-28
What is the output of df -k 

It looks like you just need to see what ubuntu is calling the drive.  It should be in /dev somewhere.

---

### Post by tharman on 2009-08-28
df -k output:

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            116714512  53645152  57140576  49% /
tmpfs                   253940         0    253940   0% /lib/init/rw
varrun                  253940       384    253556   1% /var/run
varlock                 253940         0    253940   0% /var/lock
udev                    253940       140    253800   1% /dev
tmpfs                   253940        88    253852   1% /dev/shm
lrm                     253940      2192    251748   1% /lib/modules/2.6.28-15-g

---

### Post by celticdevildog on 2009-08-28
when you run dmesg do you see an output that looks something like

```
sdb:sdb1
```

---

### Post by tharman on 2009-08-28
Nope.

dmesg output:

[ 4547.877930] [drm:i915_getparam] *ERROR* Unknown parameter 6
[ 7594.523549] [drm:i915_getparam] *ERROR* Unknown parameter 6
[ 9147.916172] usb 1-5: USB disconnect, address 7
[ 9154.400069] usb 1-6: new high speed USB device using ehci_hcd and address 8
[ 9154.540117] usb 1-6: configuration #1 chosen from 1 choice
[ 9263.930490] usb 1-6: USB disconnect, address 8
[ 9294.890675] usb 1-6: new high speed USB device using ehci_hcd and address 9
[ 9295.068052] usb 1-6: configuration #1 chosen from 1 choice
[10515.106875] [drm:i915_getparam] *ERROR* Unknown parameter 6
[11659.267413] usb 1-6: USB disconnect, address 9
[12079.263532] [drm:i915_getparam] *ERROR* Unknown parameter 6
[12942.384069] usb 1-6: new high speed USB device using ehci_hcd and address 10
[12942.556867] usb 1-6: configuration #1 chosen from 1 choice

I've been trying out other USB ports to see if that was the problem and it has been assigning new address so that's why it's addressed as 10 right now i guess.

If I try something like mount sdb1 i get :
mount: can't find sdb1 in /etc/fstab or /etc/mtab

---

### Post by celticdevildog on 2009-08-28
try

```
ls /dev/sd*
```

and see if it gives you more than just sda and sda1

---

### Post by tharman on 2009-08-28
ls /dev/sd* output:
 /dev/sda  /dev/sda1  /dev/sda2  /dev/sda5

---

### Post by tharman on 2009-08-28
I don't know if this information is anymore helpful but here is some of the info I get when I run 'dmesg | grep sd' :

[    2.482924] Driver 'sd' needs updating - please use bus_type methods

Do I need to update something maybe?

Here is the rest of the info I get that is related to Hard Drives, not sure if it is useful tho:

[    2.842092] sd 0:0:0:0: [sda] 240121728 512-byte hardware sectors: (122 GB/114 GiB)
[    2.842124] sd 0:0:0:0: [sda] Write Protect is off
[    2.842129] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.842176] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.842316] sd 0:0:0:0: [sda] 240121728 512-byte hardware sectors: (122 GB/114 GiB)
[    2.842343] sd 0:0:0:0: [sda] Write Protect is off
[    2.842348] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.842393] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.842401]  sda: sda1 sda2 < sda5 >
[    2.874820] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.874934] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   17.764078] Adding 1477940k swap on /dev/sda5.  Priority:-1 extents:1 across:1477940k
[   18.697041] EXT3 FS on sda1, internal journal

---

### Post by celticdevildog on 2009-08-28
no.  sda is your internal harddrive.  The system is obviously seeing your external hard drive but you just need to figure out what it is calling it.  My system was calling my external USB hard drive sdd because I have multiple drives.  That's why I started you in that direction.  

Maybe someone with a little more experience than I have can help you from here.  I'm not sure the command to run to find out what ubuntu is calling it.

Unless it's viewing it as something other than a hard drive.  What does mount show?

---

### Post by tharman on 2009-08-28
mount shows:

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
rpc_pipefs on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/tharman/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=tharman)


Is it possible that it's just seeing the USB enclosure and not the Hard Drive inside because it isn't formatted or somthing? Both HDD and Enclosure are right out of the box from this morning.

---

### Post by lswb on 2009-08-28
Is your enclosure powered only by the USB cable? Sometimes it's just a case of not enough current available at the USB port to actually run the device. I see similar messages with an external drive I sometimes use if I try to connect it to my laptop without using the auxiliary power supply.

---

### Post by tharman on 2009-08-28
It has an external 12v transformer for power.

---

### Post by lswb on 2009-08-28
The dmesg string you posted "Bus 001 Device 009: ID 13fd:160f Initio Corporation" indicates only that the the system could read the USB ID from the adapter, but there is no message regarding a disk. It is possible that the disk is not connected properly inside the enclosure, or that there is some other hardware problem.

Have you tried the enclosure on another system? If it works on a different computer and/or operating system, it may be a driver problem.

---

### Post by tharman on 2009-08-31
I figured out that the Hard Drive wasn't sitting properly in the enclosure. Instead of using the spring-loading kind of mechanism it tells you to use I just pushed it in manually. This caused it to see the hard drive with an fdisk -l right away.
Thanks for the help and sorry 'bout that.

---

