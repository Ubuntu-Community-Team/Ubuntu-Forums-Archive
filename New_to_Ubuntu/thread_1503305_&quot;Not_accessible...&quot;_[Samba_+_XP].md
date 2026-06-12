---
title: "&quot;Not accessible...&quot; [Samba + XP]"
date: 2010-06-06
forum: New to Ubuntu
---

### Post by jetgraphics on 2010-06-06
[Head butt wall flag on]
Goal:
Share XP directories on a dual boot machine, with other XP machines
Action:
Edit smb.conf file, save, reload, restart
workgroup is correct
server string shows up in network listing
Attempt to open from XP
Result:
*"Name" is not accessible.  You might not have permission..., Network path was not found...*


Testparm dump:

[global]
    workgroup = LANgroupname
    server string = %h server (Ubuntu 10.4)
    interfaces = 127.0.0.0/8, eth0
    bind interfaces only = Yes
    security = SHARE
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

[homes]
    comment = Home Directories
    read only = No
    create mask = 0775
    directory mask = 0775
    browseable = No
    browsable = No

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    guest ok = Yes
    printable = Yes
    browseable = No
    browsable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
    guest ok = Yes

[cdrom]
    comment = Samba server's CD-ROM
    path = /cdrom
    guest ok = Yes
    locking = No

[Share1]
    comment = Guest access share
    path = /media/DataDir
    read only = No
    guest ok = Yes

[Share2]
    comment = Guest access share
    path = /media/DataDir2
    read only = No
    guest ok = Yes
=======================

Help...

[update]
I found that the /media/datadir keeps resetting, and loses its "share" setting.
Any suggestions for preserving share options?

---

### Post by TVTrukChik on 2010-06-06
So you're booting in Linux and want to share NTFS-formatted drives or partitions, if I understand right?  A co-worker had this same problem, and it seems it was caused by the NTFS drives not automatically mounting.

I was able to get his machine working by following the tutorial here: [http://www.psychocats.net/ubuntu/mountlinux]("http://www.psychocats.net/ubuntu/mountlinux").  When you edit the fstab file, you will need to put in "ntfs" instead of "ext4" as shown in the example, but otherwise the procedure was the same.

---

### Post by jetgraphics on 2010-06-07
> **TVTrukChik said:**
> So you're booting in Linux and want to share NTFS-formatted drives or partitions, if I understand right?  A co-worker had this same problem, and it seems it was caused by the NTFS drives not automatically mounting.

I was able to get his machine working by following the tutorial here: [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux).  When you edit the fstab file, you will need to put in "ntfs" instead of "ext4" as shown in the example, but otherwise the procedure was the same.

Thank you x 1000.

Afterthought:
I found that re-using XP's computer name, when Ubuntu was loaded, caused a problem... or so I thought.
Can one dual boot, and use the same computer name for both?
It would simplify things.

---

### Post by TVTrukChik on 2010-06-07
You're welcome.  It's always good to know I have learned enough to be able to help someone else.

I have a dual boot machine that has the same name for both XP & Ubuntu.  Doesn't seem to cause me a problem, but then I almost never boot it to Windows.

---

