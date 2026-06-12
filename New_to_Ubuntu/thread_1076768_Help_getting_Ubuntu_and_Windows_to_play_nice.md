---
title: "Help getting Ubuntu and Windows to play nice"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by Lachlanus on 2009-02-21
I am new to linux, so please be gentle.  I have Ubuntu 8.10 Intrepid, 64-bit.  My linux box has a drive and a printer I would like to share.  I have installed samba, and modified my smb.conf as follows:

[global]
workgroup = BELCHER
netbios name = LinuxBox
printing = CUPS
printcap name = CUPS
show add printer wizard = no
wins support = yes
usershare owner only = False

[printers]
path = /var/spool/CUPS
printable = Yes
guest ok = Yes
use client driver = Yes

[Data]
path = /media/Data
public = yes
browseable = yes
writeable = yes

Most of that I copied from someone else's example and slightly modified.  My linux box lists itself on the workgroup, and can browse other winXP computers.  From the WinXP computers, the linux box shows up on the workgroup, but when you try to access it you get the "access denied" message.  The shared printer and folder do not show up in "my network places."  All the tutorials I can find seem to say this should work, but obviously it does not.  What am I missing?

---

### Post by Iowan on 2009-02-21
Your Windows user has an account on the Ubuntu machine and Samba? (via smbpasswd)

---

