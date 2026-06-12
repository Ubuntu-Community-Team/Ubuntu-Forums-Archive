---
title: "Cant mount windows drive"
date: 2008-03-02
forum: Networking &amp; Wireless
---

### Post by hardon on 2008-03-02
Ok, here's the deali-O

I have a machine running xp with a seperate hdd being shared.  The share name is Public (P)

On the other machine I have Ubuntu 7.1 on it.  The problem is I can not get this machine to mount the drive. If I go to Place>Connect to server I can do it, but I cant access that drive from within programs.  I added the share to the /etc/fstab file, 

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=c280b933-887f-4823-9059-2e57b683b9d5 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=0c04743f-1f56-4915-8e22-0e05032c6130 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
#  //home-01  /media/Public  cifs  guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0
//192.168.1.2/Public (P)  /media/Public  cifs  credentials=~/.smbcredentials,dmask=777,fmask=777  0  0
```

the ~/.smbcredentials simply has my windows username and password.  I also tried changing fstab to allow for guest login of share, but that didnt work either.

when I do a mount -a, I get the following:

```
mount: wrong fs type, bad option, bad superblock on //192.168.1.2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

dmesg | tail gives me:

```
[  455.511987] smbfs: mount_data version 1684370019 is not supported
```

Not sure what is going on...any help would be awesomely appreciated!

---

### Post by dmizer on 2008-03-03
your fstab reads:
```
//192.168.1.2/Public [COLOR="Red"](P)[/COLOR]  /media/Public  cifs  credentials=~/.smbcredentials,dmask=777,fmask=777  0  0
```
it should read
```
//192.168.1.2/Public  /media/Public  cifs  credentials=~/.smbcredentials,dmask=777,fmask=777  0  0
```

try that.  if you still get the same exact error ("mount: wrong fs type, bad option, bad superblock"), try this:
```
sudo aptitude install smbfs
```
and reboot to see if the share will mount.

---

