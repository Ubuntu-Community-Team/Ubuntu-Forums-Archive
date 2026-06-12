---
title: "file server OS"
date: 2007-02-04
forum: Networking &amp; Wireless
---

### Post by Loki57701 on 2007-02-04
I have a real simple home file storage server running winXP pro. I store mostly movies and music on it. WinXP works fine but I was wondering if there would be any advantages to using ubuntu on it (not the server). Its mostly a windows network. four computers, 1 running Ubuntu 6.10.
Also which remote desktop client is good with linux. I would need to use a windows computer to manage the linux server remotley (similar to MS remote desktop connection). Is that possible? if so whats a good choice? Ive seen a few like VNC and vino. I dont think I would need ssh because its just a local network.

---

### Post by gradedcheese on 2007-02-04
I run a "windows file server" for a network of Windows PCs.  The file server is actually Ubuntu running samba.  It works great, never having to be rebooted.  The advantages?  Well, it's Linux... I can ssh in, add/remove users, change permissions and shares, etc. all from the shell.  I wouldn't want to have it any other way :)

---

### Post by IcarusR on 2007-02-04
Hi
Like gradedcheese says use SAMBA. I have a SAMBA running on Dapper as a server for my home network which consists of 1 XP laptop, 1 XP desktop, 1 Edgy laptop & my SqueezeBox. 
There is a lot of info on howto setup SAMBA on the net. 
Ubuntu has the advantage over any MS O/S that it requires less resources, so you can use an older box for your server & of course it is more stable.
Ubuntu has vino vnc client installed & works out of the box.
SAMBA can be administered using SWAT which is a web based admin tool.

---

