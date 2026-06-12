---
title: "Samba and printer sharing"
date: 2005-11-13
forum: Networking &amp; Wireless
---

### Post by fnando on 2005-11-13
Hello there!

I'm trying to setup/share a printer for a WINXP PRO.

Everything is okay except that when listing printers installed on windows the shared printer has the line below its icon saying something about denied access (I don't the exactly text because it's a non-english system). 

On my smb.conf I have:

```

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
printing = cups
printcap name = cups

# When using [print$], root is implicitly a 'printer admin', but you can
# also give this right to other users to add drivers and set printer
# properties
;   printer admin = @ntadmin

[printers]
   comment = All Printers
   browseable = yes
   path = /tmp
   printable = yes
   public = yes
   writable = no
   create mode = 0700

#====== Share Definitions ========
# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = yes
# Uncomment to allow remote administration of Windows print drivers.
# Replace 'ntadmin' with the name of the group your admin users are
# members of.
;   write list = root, @ntadmin

```

Files sharing are ok.

Thanks!

---

### Post by byourg on 2005-11-14
```
[printers]
   comment = All Printers
   browseable = yes
   path = /tmp
   printable = yes
   public = yes
   writable = no
   create mode = 0700
```

Change writable = no to writable = yes, reboot and see what happens.

---

### Post by drpatt on 2005-11-17
I'm having the same problem. Making that change from **no** to **yes** didn't help. When I look at the printer configuration dialog box, it doesn't remember the user name. It remembers the password, but not the user name.

At least I had one victory today; got throgh not being able to su in a terminal by using sudo passwd.

---

