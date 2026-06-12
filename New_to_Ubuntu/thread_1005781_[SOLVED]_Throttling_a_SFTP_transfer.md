---
title: "[SOLVED] Throttling a SFTP transfer"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by cdmike2k8 on 2008-12-08
I connect to a remote torrent box through ssh, and use this to transfer files.  I was wondering if there is a way to limit the speed so that it doesn't saturate the upload on the remote box.  I don't care if the configuration is server or client side.  When I used to use winscp, it had this option.  I connect to the server through places -> connect to server ans select ssh for protocol.  The upload box is headless without GUI(GUI with VNC is possible, but very slow, not really practical) and running ubunu 8.04.  The download machine is running ubuntu 8.10.  Thanks in advance.

---

### Post by cdmike2k8 on 2008-12-08
After some more research, I decided to use filezilla, and it supports this.  Problem solved.

---

