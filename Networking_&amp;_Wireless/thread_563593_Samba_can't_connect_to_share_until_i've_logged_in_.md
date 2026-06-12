---
title: "Samba: can't connect to share until i've logged in on the server"
date: 2007-09-30
forum: Networking &amp; Wireless
---

### Post by daclink on 2007-09-30
Hi guys,

I have samba working on my machine, however I can't connect to the share from my windows XP machine until I have gone to my server and logged in using the GUI. I don't think samba is being stared by X, so I'm at a bit of a loss as to what is going on. My smb.conf is below just in case.

Any help would be greatly appreciated.

Thanks in advance,

Justin


[global]
   workgroup = draconis
   server string = %h server (Samba, Ubuntu)
   hosts allow = 192.168.1.0/255.255.255.0
   interfaces = 192.168.1.100/255.255.255.0

[raid]
   path = /media/disk
   available = yes
   browsable = no
   public = no
   writable = yes

---

### Post by conjur3r on 2007-09-30
Does the following give you something similar?

# find /etc/rc* -name "*samba"
/etc/rc0.d/K19samba
/etc/rc1.d/K19samba
/etc/rc2.d/S20samba
/etc/rc3.d/S20samba
/etc/rc4.d/S20samba
/etc/rc5.d/S20samba
/etc/rc6.d/K19samba

---

### Post by daclink on 2007-09-30
It gives me exactly the same as you:

find /etc/rc* -name "*samba"
/etc/rc0.d/K19samba
/etc/rc1.d/K19samba
/etc/rc2.d/S20samba
/etc/rc3.d/S20samba
/etc/rc4.d/S20samba
/etc/rc5.d/S20samba
/etc/rc6.d/K19samba

Thanks

---

### Post by conjur3r on 2007-09-30
In that case, samba should be started in runlevels 2, 3, 4, and even 5.  Runlevel 5 is your X session with networking and multiuser (your GUI).  Theoretically, samba should have been started before you see the GUI login screen.

Now, you'll need to debug where the problem really is.  Try the usual log files in /var/log and the samba ones in /var/log/samba/.  Does anything jump out at you?

---

