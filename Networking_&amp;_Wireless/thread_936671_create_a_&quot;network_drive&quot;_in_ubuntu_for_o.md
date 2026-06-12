---
title: "create a &quot;network drive&quot; in ubuntu for other windows boxes to use"
date: 2008-10-03
forum: Networking &amp; Wireless
---

### Post by survient on 2008-10-03
I see a lot of reverse posts about this, users trying to get access to a windows server that has a network drive they're trying to access through ubuntu. I'm looking to do the opposite. I have a ubuntu server with one big shared folder that access as the network file server, all the files in my network get dumped there. I've seen other windows computers have situations where they have a "network drive" available to access, which I believe is a Windows Server thing right? I'm just curious if I can do something with samba or something similar so that in my windows boxes, a network drive shows up in My Computer. This is less me trying to find a solution and more just tinkering around to see if I can do it. Thanks

---

### Post by jpkotta on 2008-10-03
Yes, you would use Samba for this.  I have this working on my file server, which runs Dapper, but I recently tried to get this going on my workstation at work.  No go.  I'm no samba guru though.  I've been using swat, and it works great for the server.

[https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)

---

### Post by cariboo on 2008-10-03
I've always found this document very help when setting up samba:

[www.samba.org/samba/docs/Samba3-ByExample.pdf](www.samba.org/samba/docs/Samba3-ByExample.pdf)

If you do decide to use swat to setup your shares, it has to be run as root to be able to save /etc/samba/smb.conf

Jim

---

### Post by survient on 2008-10-29
Ok, I was stupid, this isn't an ubuntu thing, it's something windows does for itself. In my computer if you click Tools, then map network drive, point to the shared folder on the ubuntu machine and assign a drive letter, windows will treat that samba share as a network drive. So simple, yet so far away.......

---

