---
title: "Can't samba share folders in NTFS partition."
date: 2016-10-09
forum: Networking &amp; Wireless
---

### Post by ganoo on 2016-10-09
What I did

sudo apt-get install samba

then

sudo useradd -M -N -g sambashare john

then

sudo smbpasswd -a john
>New SMB password
>Retype new SMB password
>"user john was created (or something like that)"


Now all that I have to do is right click any folder and click share this folder and it works. I didn't have to edit smb.conf or anything at all. The problem is that when I right click and share this folder on a folder located in an NTFS partition, it'll show the folder in the network, but it'll give me a permission error when i try opening it on another pc. My folders shared on my Ubuntu partition work fine.

when i [id john] i get this, the account used to access the shares:

uid=1001(john) gid=128(sambashare) groups=128(sambashare)


heres id command for the main account:

uid=1000(netbook) gid=1000(netbook) groups=1000(netbook),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),113(lpadmin),128(sambashare)

here's some relevent information on my system, note that i have not edited smb.conf at all, it's all default settings:

```

netbook@netbook-AO722:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "syslog" option is deprecated
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE

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
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb


[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No


[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers



netbook@netbook-AO722:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda3 during installation
UUID=b1b36b32-3235-4368-8412-1221a275082b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=8c28c538-bdb3-4430-9280-e75a899026b4 none            swap    sw              0       0



netbook@netbook-AO722:~$ sudo blkid
[sudo] password for netbook: 
/dev/sda1: LABEL="System Reserved" UUID="E034909034906B74" TYPE="ntfs" PARTUUID="00074aa5-01"
/dev/sda2: UUID="26929A6A929A3E6D" TYPE="ntfs" PARTUUID="00074aa5-02"
/dev/sda3: UUID="b1b36b32-3235-4368-8412-1221a275082b" TYPE="ext4" PARTUUID="00074aa5-03"
/dev/sda5: UUID="8c28c538-bdb3-4430-9280-e75a899026b4" TYPE="swap" PARTUUID="00074aa5-05"
/dev/sda6: UUID="A6A4AE70A4AE4323" TYPE="ntfs" PARTUUID="00074aa5-06"
netbook@netbook-AO722:~$ 

```

here's the path of the folder i'm trying to share in the ntfs partition but won't work:

```

/media/netbook/A6A4AE70A4AE4323/linux/share

```

also earlier experimenting i tried editing /etc/fstab with sudo gedit and ubuntu started giving me report problem errors so I guess gedit is not a good editor for what im trying to do..

---

