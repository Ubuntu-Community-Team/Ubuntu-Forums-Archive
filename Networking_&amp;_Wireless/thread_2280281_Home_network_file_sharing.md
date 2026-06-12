---
title: "Home network file sharing"
date: 2015-05-29
forum: Networking &amp; Wireless
---

### Post by weyland42 on 2015-05-29
What's the best way to set up file-sharing on a home network?

I've scoured the web, and tried many suggestions found there, but nothing seems to work. The file manager -- caja -- displays no Share option, though it's apparently supposed to. Nor does Nautilus.

At the moment it involves two machines, both running Ubuntu 15.04 Mate, but I'll also be needing to share with visitors running Windoze 7 and Kubuntu 14.04. WiFi or EtherNet connections.

---

### Post by TheFu on 2015-05-29
You need samba if you want Windows to access file shares. There are multiple how-to guides. *HowToGeek* has some easy-to-follow versions.
[http://www.howtogeek.com/74459/how-to-create-samba-windows-shares-in-linux-the-easy-way/](http://www.howtogeek.com/74459/how-to-create-samba-windows-shares-in-linux-the-easy-way/)

Both the *Ubuntu Desktop* and *Ubuntu Server Guides* probably do as well. I didn't look for those.

OTOH, if you have a non-Windows network, then NFS is generally best for Linux-to-Linux or Linux-to-Mac sharing. No point-n-click solution for NFS.

When you are away from home, neither of those options work in a secure way. For that you want ssh which comes with **sftp** - use ssh-keys, never passwords and you can securely access files in your home from anywhere in the world. Every networked OS has an sftp client. 

Oh ... and before you start, ensure your "server" has a static IP.

---

