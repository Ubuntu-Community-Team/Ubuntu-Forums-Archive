---
title: "Windows asks for Password to access Ubuntu shares but nothing works"
date: 2007-05-11
forum: Networking &amp; Wireless
---

### Post by RCC2k7 on 2007-05-11
I have Samba setup nicely (or so I thought), so I can share folders on my home network between both Linux and Windows. I can use Ubuntu to access Windows shares without problems. I can also access shares Linux to Linux.

The problem is when I try to access Ubuntu shared folders from within Windows XP SP2. I'm asked for a password and none of my Ubuntu user accounts work for this; neither does trying to use guest as a username. I don't have access problems from Windows to PCLinuxOS or from Windows to Xandros. I only get this problem accessing from Windows to Ubuntu. Am I missing something? I don't see anything on the Shared Folders dialog concerning the assignment of a username and password for the share to work.

---

### Post by Austin_KW on 2007-05-11
You need to add a samba user password for one of your users, for the command line
sudo smbpasswd -a yourUserName

You may be prompted for your sudo password, then the smb password to set.

edit; You may then need to restart samba
sudo /etc/init.d/samba restart

---

### Post by RCC2k7 on 2007-05-11
Thanks, that worked.

---

### Post by ethos101 on 2007-05-20
Just wanna say thanks.  Helped me also.  :D

---

