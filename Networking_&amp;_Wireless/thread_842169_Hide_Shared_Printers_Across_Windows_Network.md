---
title: "Hide Shared Printers Across Windows Network?"
date: 2008-06-27
forum: Networking &amp; Wireless
---

### Post by Dempsey on 2008-06-27
I have managed to successfully setup some shared folders on an Ubuntu machine which Windows machines can access without a password, but the Ubuntu machine is also sharing a Printers and Faxes folder even though I have no printers installed, just wondered if there was a way I could stop it showing so only the shared folders were listed?

Thanks for any help :)

---

### Post by RomanIvanov on 2008-12-09
I have the same problem, but I have printer installed and set in settings "Shared=false", but it is shown in Win network nevertheless.

If somebody have success in hiding the printers please share your knowledge.

---

### Post by RomanIvanov on 2008-12-09
this helped me to hide printers:

edit your /etc/samba/smb.conf
Put your settings similar to this, this is my winning formula
```
wins support = no
[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700
   available = no
   public = no

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = no
   read only = yes
   guest ok = no
   #available = no
   #public = no 
```

---

### Post by avdiscolo on 2009-12-16
I'm having the same issue.  I've edited the section in the smb.conf file to be identical to yours, but my printer share is still displayed.  I tried "sudo smbcontrol smbd reload-config".  Are there other commands that need to be executed after modifying smb.conf?

Thanks for your help.

---

### Post by gbrandys on 2011-03-18
You can hide all Samba printer shares by adding "disable spoolss = yes" in the [global] section of smb.conf

```

sudo nano /etc/samba/smb.conf

[global]
disable spoolss = yes

```

---

