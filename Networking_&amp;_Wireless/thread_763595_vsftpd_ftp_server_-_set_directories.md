---
title: "vsftpd ftp server - set directories"
date: 2008-04-23
forum: Networking &amp; Wireless
---

### Post by ene_dene on 2008-04-23
I've just installed vsftpd ftp server and I want that anonymous users can connect to my comp in specific directory. In /etc/vsftpd.conf I've enabled:
# Run standalone?  vsftpd can run either from an inetd or as a standalone
# daemon started from an initscript.
listen=YES
# Allow anonymous FTP? (Beware - allowed by default if you comment this out).
anonymous_enable=YES
But I don't want that anonymous users see my dir structure, only some specific folders. How can I set them? I don't see anything like that in config file.

---

### Post by sujoy on 2008-04-23
by default anonymous users can connect to the home directory of the "ftp" user, which is generally /home/ftp

---

### Post by ene_dene on 2008-04-23
Is there some way to add a few dirs from the rest of hdd?

---

