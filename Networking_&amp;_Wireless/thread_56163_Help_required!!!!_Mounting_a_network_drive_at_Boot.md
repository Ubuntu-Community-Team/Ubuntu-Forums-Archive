---
title: "Help required!!!! Mounting a network drive at Boot up"
date: 2005-08-11
forum: Networking &amp; Wireless
---

### Post by YaAqoB on 2005-08-11
Hello.
I have a file server running Ubuntu and a workstation dual booting with XP Pro and Ubuntu.
With XP i have mapped the network drives & and can read/write no worries what so ever. Easy...
With Ubuntu I have added the mount info into my fstab file........but when ever I boot into Ubuntu none of my icons appear, it does not mount the network drive and after about 3 minutes Ubuntu slows down to the point where I have to hit the reset button. ](*,) 
Now if I start ubuntu, edit the fstab file and comment out the network drive line and then save/restart the computer starts Ubuntu sweet as no worries.
It runs fine. 
I then edit the fstab file, uncomment the network drive entry, save and then go:
sudo mount -a 
it mounts the network drive and every thing runs mint as...... untill I have to restart where I have to do the above process again.
I can't see why it fails on bootup but then runs fine if you manually mount it after boot.
Below is my fstab contents:
Please Help!!!

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /	 ext3    defaults,errors=remount-ro 0       1
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hda1       /mnt/WindowsDrv  ntfs    umask=0222      0       0
/dev/hdb1       /mnt/WindowsApps  ntfs    umask=0222      0       0
//192.168.1.2/ServerStorage   /mnt/networkdrive smbfs credentials=/root/.smbcredentials,dmask=777,fmask=777   0       0

---

### Post by YaAqoB on 2005-08-11
Someone told me that I need to have a _netdev in there to tell it to wait for the network before trying to mount it. Is that true???
I have tried but I can't figure out where in the line to put it with out it giving an error.
HELP!!!!!!!!

---

