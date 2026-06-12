---
title: "Samba Server, No Permission"
date: 2006-07-22
forum: Networking &amp; Wireless
---

### Post by computergee on 2006-07-22
I just set up a Samba server out of an old PC I had. My Windows XP box see it fine, and can read and write. My main Ubuntu Box dosn't have permission to modify and of the files or folders created by my Windows machine, and vice versa. How can I make it so these machines have the ability to modify each others files? By the way, on my windows machine I have to log in using a user I made on the server, but on the Ubuntu machine it just appears, and I don't have to use a log in name. Could this be whats causing this?

---

### Post by cracker on 2006-07-22
The server probably has a user by the same name as the user you are attempting to log on with, but that user doesn't have permission to access/write those shares. It's a simple matter of users and permissions. The simplest way to solve it is to add the user you wish to log on with and give it permission to the shares you wish to access.

---

### Post by computergee on 2006-07-22
I figured it out, I had to access it by Places-Network Servers-Windows Network..., I wasn't going through the Windows Network before. Now I'm trying to mount the SMB server, but I get the following error.

26189: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed

This is what I have in my fstab.

//192.168.0.103/Server/    /media/Server smbfs  credentials=/root/.smbcredentials    0    0

The network IP of the server is 192.168.0.103, and the shared folder is in /home/admin/Server, am I setting this all up right? Thanks for the help.

---

