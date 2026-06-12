---
title: "Sharing a folder with windows networks."
date: 2008-05-24
forum: Networking &amp; Wireless
---

### Post by Vigh on 2008-05-24
When I try to share a folder on my network i get the following error-

'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.

how can i run this as administrator? Cheers Anthony

---

### Post by superprash2003 on 2008-05-24
try typing sudo nautilus in the terminal.. a window would open.. try sharing through that window

---

### Post by Iowan on 2008-05-24
IIRC, there's a section in the (new) smb.conf that mentions adding a "net usersharing" user to the usershare group.

---

### Post by mapes12 on 2008-05-24
I couldn't get sharing to work at all across my home LAN therefore I gave up on Samba network shares. Having read a number of posts my network now accesses clients using Secure Shell - SSH. I find it much easier. There are utilities to connect XP and Ubuntu boxes via this protocol.

These links may be helpful:

[http://pigtail.net/LRP/printsrv/cygwin-sshd.html](http://pigtail.net/LRP/printsrv/cygwin-sshd.html)

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

[http://www.openssh.org/](http://www.openssh.org/)

---

