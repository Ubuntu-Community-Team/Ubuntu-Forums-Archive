---
title: "{Ask} How to create a network workgroup and sharing printer among Ubuntu computers?"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by asaren on 2008-12-10
Hi everyone,

Could you explain how to create a network workgroup and sharing printer among Ubuntu computers, also between Ubuntu and Windows XP as well.

Thank you so much

---

### Post by cmnorton on 2008-12-10
You will need to familiarize yourself with SAMBA. 

All Ubuntu computers in the group should have the same workgroup name as the XP workgroup.

In /etc/samba/smb.conf, it's this line:

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = <your-workgroup>

This area configures printers. You would alter this on the Ubuntu system to which the printer is connected:

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

Here is a link to Ubuntu's very good documentation on the subject:

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by superprash2003 on 2008-12-10
This should help.As mentioned above you need samba
1)Setup samba - [http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html](http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html)
2)Setup printer sharing in ubuntu via samba - [http://prash-babu.blogspot.com/2008/05/how-to-setup-network-printer-or-share.html](http://prash-babu.blogspot.com/2008/05/how-to-setup-network-printer-or-share.html)

---

