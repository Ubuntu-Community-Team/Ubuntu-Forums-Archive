---
title: "sharing printer through samba"
date: 2008-04-03
forum: Networking &amp; Wireless
---

### Post by atheistkun on 2008-04-03
hi, 
i have 2 machines--one running vista and one ubuntu 7.10
i wish access my printer connected to ubuntu machine, in vista. i tried to setup samba server but i can't access my printer, though i can access the folder i shared. 
i need to have login based  access (same users as in  linux) to printer as i m in LAN with many users.
my smb.conf
printer name -> local

---

[global]
   workgroup = WORKGROUP
   server string = %h server (Samba, Ubuntu)
   dns proxy = no
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   security = user
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   invalid users = root
   passwd program = /usr/bin/passwd %u

   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .

load printers = yes
socket options = TCP_NODELAY
browseable = no
writable = no
wins support = no

[local]
comment = Laser
path = /var/spool/samba
browseable = no
public = no
create mode = 0700
printable = yes
printer = local

what am i doing wrong? also i found that /var/pool/samba is an empty directory. plz note that i am using the the default driver for printer hp 1015 that came with ubuntu 7.10

---

### Post by dmizer on 2008-04-03
share your printer through cups instead of samba.  it's an easy point and click interface.  just go to your system menu -> printing -> and work through the share printer menu.

you'll have to modify one small config.  directions outlined here:
[http://ubuntuforums.org/showthread.php?t=268245](http://ubuntuforums.org/showthread.php?t=268245)

if you would rather, you can also configure your printer via the cups web interface.  howto here:
[https://help.ubuntu.com/community/PrintingCupsWebInterface](https://help.ubuntu.com/community/PrintingCupsWebInterface)

i've never been sucessful in making a printer share via samba, but it works every time with cups.

---

