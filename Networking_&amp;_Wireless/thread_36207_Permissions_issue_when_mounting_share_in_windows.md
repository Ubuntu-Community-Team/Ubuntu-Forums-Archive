---
title: "Permissions issue when mounting share in windows"
date: 2005-05-22
forum: Networking &amp; Wireless
---

### Post by b1k3r4ck on 2005-05-22
I have a Win2k3 server with 3 XP clients and 1 Ubuntu client. I set up the Ubuntu box to mount a share on the Win2k3 server on boot up and it worked ... once. 

Now when I boot up it the share is mounted but the owner is root. I'm not sure how to change this. I have my fstab set up per [these](http://www.ubuntuguide.org/#automountnetworkfoldersall) instructions (although when I did it I found a thread on these forums). Here is what my fstab looks like:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
#/dev/hdc6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc6       /               ext3    defaults,errors=remount-ro,user_xattr 0       1
/dev/hdc3       /boot           ext3    defaults        0       2
/dev/hdc5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdb        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
//192.168.1.2/robin	/mnt/robin	cifs	credentials=/root/.smbcredentials,dmask=777,fmask=777 	0	0


I was pretty sure that was it and it did work right after I set this up but after a reboot it stopped working. I guess my issue is permission more than mounting.  Here's what the share looks like after it's mounted:

dr----x--t   1 root root    0 2005-05-20 10:44 robin

Any suggestions on how to make this 777 at boot would be appreciated. (I tried to chmod but get a permission denied error).

Thanks in advance.

---

### Post by b1k3r4ck on 2005-05-22
Sorry.. I'm retarded .. meant to post this in the hoary forums. 

Reposted [here](http://ubuntuforums.org/showthread.php?p=183113#post183113).

---

