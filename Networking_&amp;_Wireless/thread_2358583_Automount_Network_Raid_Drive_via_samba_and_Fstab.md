---
title: "Automount Network Raid Drive via samba and Fstab"
date: 2017-04-14
forum: Networking &amp; Wireless
---

### Post by zubbs1 on 2017-04-14
I am attempting to establish a LAN server sharing of a Raid array between two computers.  The server computer is Marx (running Ubuntu 16.10), second box is Tesla (running Ubutnu 16.10). I've pieced together a samba.conf that allows me to manually mount the array on Tesla using the network button in Nautilus. 

What I want to do is automount at startup, specifically so that KODI will see the RAID drive as that is where my library will be populated from.  I have zero concern for security, as only trusted family have access to this network.  Therefore, I'm attempting a solution requiring no username or password prompts.  Lastly, if possible, I'd like to have read/write access to the Raid drive.


```
sharemore@Marx:/etc/samba$ testparm
```
```

Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "syslog" option is deprecated
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE


Press enter to see a dump of your service definitions


# Global parameters
[global]
    server string = %h server (Samba, Ubuntu)
    server role = standalone server
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    usershare owner only = No
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb
    force user = sharemore




[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No




[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

```

```

zubba@Tesla:~$ cat /etc/fstab

```
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb2 during installation
UUID=f9774c56-835f-45e7-8f40-b318c78cd03d /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sdb1 during installation
#UUID=C6B1-D932  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sdb3 during installation
UUID=bd1217e5-2817-46b5-be06-1085ad9047c0 none            swap    sw              0       0
#UUID=C6B1-D932    /boot/efi    vfat    defaults    0    1
UUID=CEF7-5B25    /boot/efi    vfat    defaults    0    
//192.168.1.82/share /media/zubba/Raid cifs user=guest,iocharset=utf8, 0 0

```

```

zubba@Tesla:~$ sudo mount -a
```
```

[sudo] password for zubba: 
Password for guest@//192.168.1.82/share:  
Retrying with upper case share name
mount error(6): No such device or address
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```

I have no .credentials file to refer to, because I don't know what to populate after "user="  or "password="
If I remove "user=", then I still get prompted for a password.

I've been reading around (as I always do since I'm very new to understanding much of linux), but most advice is for people who want all the security features, or for people using Windows to connect to a Linux server.  I'm not sure if it is any different connecting linux to linux or not?

Any help is greatly appreciated.


Cheers.

---

### Post by Morbius1 on 2017-04-15
The client ( zubba ) cannot find the share labelled "share" on 192.168.1.82 ( marx ?) because you have no "share" share defined in smb.conf.

Did you create a usershare from Nautilus on 192.168.1.82?
```
net usershare info --long
```

---

### Post by zubbs1 on 2017-04-15
> **Morbius1 said:**
> The client ( zubba ) cannot find the share labelled "share" on 192.168.1.82 ( marx ?) because you have no "share" share defined in smb.conf.

Did you create a usershare from Nautilus on 192.168.1.82?
```
net usershare info --long
```

```
sharemore@Marx:~$ net usershare info --long
```
```
[Downloads]
path=/home/sharemore/Downloads
comment=
usershare_acl=Everyone:F,
guest_ok=y


[md0]
path=/mnt/md0
comment=
usershare_acl=Everyone:F,
guest_ok=n


[Raid]
path=/media/sharemore/Raid
comment=
usershare_acl=Everyone:F,
guest_ok=y

```

It all makes perfect sense now:)
I was using some default example, not quite understanding that I wasn't actually pointing to any mounted location on my server.  That command line was all I needed to understand my error.  Here is the corrected fstab entry line:
> 
//192.168.1.82/Raid /media/zubba/Raid cifs user=guest,password=,iocharset=utf8, 0 0


I did determine that without the 'password=' entry, it would still prompt for a password, however my system password did work to mount it, unlike before.

All in all, it works, and I have learned something new.  I'm always happy about that.

Thank you for your help!

Cheers.

---

