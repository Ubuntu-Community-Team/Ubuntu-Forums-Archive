---
title: "Samba file/folder security issue"
date: 2005-11-01
forum: Networking &amp; Wireless
---

### Post by RayH on 2005-11-01
I have three Ubuntu 5.10 boxes.  One of them is a 450mhz PC that I have setup as a file server.  The other two are client PCs.  I have Samba setup on the server, both of the clients can browse to it and the contents of the share.  I even have each client PC mounting the share to /home/<username>/ShareDrive and they mount fine, shortcut shows on the desktop and I can browse from there fine as well.

My problem is with file security, specifically writing.  I log into each box using the same username and password.  However I noticed the following issues:

1.  Files that existed on the server can be edited on the server, but not by the client PCs.
2.  Neither of the client PCs can create files or folders when using the mounted folder from fstab.
3.  If I browse via Places --> Network Servers, the client PCs can create a folder or file, but then cannot edit it once it's created.
4.  Files moved from my wive's XP box can only be modified from the XP box.  Not even the file server can edit them.

I'd like to set it up as a completely open share where the server and all client PCs can read/write any file.

---

### Post by RayH on 2005-11-06
Resolved it.  I ran chmod using Sudo to overide the existing security.  Doing so opened the drive wide open (I'm sharing the entire drive on my internal LAN, behind a firewall) which is not for everyone.  The command I used was:

sudo chmod -R 0775 /mnt/ShareDrive

The reason I was so confused was because I would get slightly less restrictions when browsing to the file server, but when I went through the mounted drive (through fstab) it was locked down tight.  Now I can create/modify anything in there either way.

---

