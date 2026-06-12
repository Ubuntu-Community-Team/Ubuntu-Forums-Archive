---
title: "Wicd is good... but there's a problem with a shared disk on the network"
date: 2007-11-23
forum: Networking &amp; Wireless
---

### Post by MauroKTM on 2007-11-23
I've installed wicd. Very good application... (better than network-manager) but since I've installed this the network shared disk on my server is not automatically mounted at startup. I always type 
```
sudo mount -a
```

than it mount the network disk

this is my fstab:
```

proc /proc proc defaults 0 0
# Entry for /dev/sda3 :
UUID=8cd00af3-3606-473a-95a4-11737a167081 / ext3 defaults,errors=remount-ro 0 1
/dev/sda1 /media/sda1 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/sda4 :
/dev/sda4 /media/sda4 vfat defaults,utf8,umask=007,gid=46 0 1
# Entry for /dev/ !! UNKNOW DEVICE !! :
#UUID=e693d311-6f2d-41ae-a79d-c6bbeb34bf5d none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
//cnsat-desktop/Netdisk /media/netdisk smbfs username=xxxx,password=xxxx,dmask=777,fmask=777,iocharset=utf8 0 0

```

Any idea?...

Thnx, M.

---

### Post by bettermentflux on 2008-01-01
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/wicd/+bug/179654](https://bugs.launchpad.net/wicd/+bug/179654) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				For whatever it's worth I'm seeing th same problem. Bug report posted at [https://bugs.launchpad.net/wicd/+bug/179654](https://bugs.launchpad.net/wicd/+bug/179654)

---

### Post by imdano on 2008-01-01
I have a feeling this has to do with when the wicd init script runs during startup.  Its probably running after network disks get mounted (or are attempted to be mounted, in this case).  We'll try to figure out if that's actually what's happening and fix it if we can.

---

### Post by hmsf on 2008-01-04
Yeah, same happens to me, using CIFS to mount a network shared partition:
```
# Entry for /mnt/cpu1 :
//192.168.1.106/xxx /media/cpu1 cifs guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```
Seems like it has an easy workaround, am I right? Anyway, I'm subscribing this thread and the Launchpad entry for it as well...

---

### Post by t0n1 on 2008-04-19
I have almost the same question: is it possible to use wicd to mount network shares after it connects to my home wireless network?
Particularly, the "Run script after connect" script?
Any help is appreciated.

---

### Post by drdrewusaf on 2008-05-31
Ok, after trying multiple ways in the rc.local script, I came up with a work around.  First off, just putting "mount /whatever/mount/point" in rc.local does not work.  Forcing rc.local to sleep did not work 100% (it was a crap shoot whether or not it would mount).  So here it is:

1.  Make sure rc.local is executable:
```
sudo chmod +x /etc/rc.local
```
2.  There are two ways to do this part, you can put the script directly into rc.local or you can make a separate script and have rc.local run it.  I chose the latter simply because I prefer my rc.local script to be clean, and I don't trust if/else statements in it.  I named my script shrmnt, you can name it whatever you want.
```
sudo gedit /usr/bin/shrmnt
```
Copy and paste this script - don't forget to edit the mount point. This script, first, checks to see if the drive was already mounted (maybe a newer version of Wicd has a fix).  If it is mounted it'll tell you with stars - if it's not mounted, then it sleeps to give the network time to settle before mounting.
```
#!/bin/bash
netDrive=/YOUR/DRIVE/MOUNT/POINT
varCheck=`mount | grep " $netDrive "`

if [[ ${#varCheck} > 0 ]]
then
   echo "*"
   echo "* The network drive $netDrive is already mounted! *"
   echo "*"
elif [[ ${#varCheck} == 0 ]]
then
   sleep 10
   mount $netDrive
fi
```
Save the file!

3.  Next edit rc.local to run it.
```
sudo gedit /etc/rc.local
```
Put the command (fully qualified, just in case) above "exit 0".  My rc.local looks like this (don't mind the modprobe...just tethering on sprint for free :) ) :
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

/sbin/modprobe ipaq vendor=0x0bb4 product=0x00cf

/usr/bin/shrmnt

exit 0
```
There you have it, a perfectly good and probably too-complicated work around.



Drew

---

### Post by drdrewusaf on 2008-06-01
Found out that, on my wife's laptop, the network connection comes up mush slower than mine.  Instead of adjusting the sleep time, I rewrote the script to use functions to loop...I'm a noob.


```
#!/bin/bash
netDrive=/media/share450
varCheck=`mount | grep " $netDrive "`
n=0

mnt () {
if [[ $n = 10 ]]
then
   exit
else
   sleep 5
   mount $netDrive
   ((n+=1))
   check
fi
}
check () {
if [[ ${#varCheck} > 0 ]]
then
   echo "*"
   echo "* The network drive $netDrive is already mounted! *"
   echo "*"
   exit
else
   mnt
fi
}

check
```



Drew

---

