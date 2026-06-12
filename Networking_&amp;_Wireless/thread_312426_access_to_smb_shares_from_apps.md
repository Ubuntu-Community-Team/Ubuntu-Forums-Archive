---
title: "access to smb shares from apps"
date: 2006-12-04
forum: Networking &amp; Wireless
---

### Post by bmedwar on 2006-12-04
I add an smb share using Places -> Connect to Server...  This adds a shortcut to the share on my graphical desktop, but not my ~/Desktop folder.  Is it possible to access files on the share from applications other than the Nautilus file browser (I want to open a file from the share in xemacs)? I'm running 6.10.

---

### Post by dbott67 on 2006-12-04
Check my signature for [HOWTO: Mounting SMB Shares]("http://www.ubuntuforums.org/showthread.php?t=280473")

-Dave

---

### Post by bmedwar on 2006-12-04
Thanks.  It would be awesome to integrate this with the Places -> Connect to server... (or make it more obvious that connect to server is not doing an smbmount)

Here is what I did to make this work with domain authentication.

Mounting SMB Shares with domain authentication
==============================================

Add line in /root/.smbcreds, 'domain = <domain name>'.  This is used by smbclient, but ignored by smbmount.  For smbmount specify the domain as the workgroup on the command line.

List the available shares (helpful for determining upper/lower case names):
```
sudo smbclient -L bedwards2 -U% -A /root/.smbcreds
```

Mount from command line:
```
sudo smbmount //bedwards2/C$ /mnt/bedwards2_c/ -o workgroup=INSIDE,credentials=/root/.smbcreds,dmask=777,fmask=777

```

Mount in /etc/fstab:
```
//bedwards2/C$  /mnt/bedwards2_c smbfs  auto,workgroup=INSIDE,credentials=/root/.smbcreds,uid=1000,umask=000,user   0 0

```

---

### Post by dbott67 on 2006-12-06
Thanks for the tip.  I've added it to the HOWTO.

-Dave

---

