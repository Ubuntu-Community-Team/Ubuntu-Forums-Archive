---
title: "Remote Desktop with Ubuntu &amp; Win7?"
date: 2010-01-21
forum: New to Ubuntu
---

### Post by Image0fman on 2010-01-21
Is it possible to setup a remote desktop connection between an ubuntu box and a win7 box? I plan to have both machines act as the host, sometimes I mite need to remote into the win7 box and sometimes I mite need to remote into the ubuntu box. Any advice/tips is greatly appreciated. Thanks~

---

### Post by cariboo on 2010-01-21
If you have Windows 7 Ultimate You can use Internet Terminal Client Server to connect to Windows from Ubuntu. If you have any other version of Windows, I would suggest VNC there are servers and clients in the Ubuntu repositories, and Windows clients and servers are available as a free download.

If you are only doing remote desktop locally, VNC is OK, if you do it from outside your local network I would suggest tunneling VNC or SSH, as VNC is one of the most prevalent ways of getting your computer cracked, due to weak passwords.

From Windows have a look [here]("http://members.shaw.ca/nicholas.fong/vnc/")

From Ubuntu look [here]("http://ubuntu-tutorials.com/2007/06/12/vnc-over-ssh-securing-the-remote-desktop/").

---

### Post by Image0fman on 2010-01-22
are you talking about this VNC for windows? [http://www.realvnc.com/products/download.html](http://www.realvnc.com/products/download.html)

---

### Post by stevanbt on 2010-01-22
Hi,
From memory, I think you should be able to use Terminal Service Client to go from Ubuntu to any version of Windows from XP onwards (and possibly with Windows 2000 if you download required software from MS).  Start Terminal Services Client and use RDPv5 if possible.

I've always found VNC to be slow and clunky at best (not to mention it's insecure if you don't tunnel via ssh).

To go from Windows to Ubuntu try Free NX ([https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)) - it's secure as it sends all traffic over ssh.

Hope this helps, Steve.

---

