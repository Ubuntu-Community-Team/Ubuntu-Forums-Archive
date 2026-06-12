---
title: "Networking in mixed enviroments"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by fareforce on 2009-03-25
I have a file server that I loaded Ubuntu desktop onto. I chose the desktop version due to the graphical interface. Now I need to get my iMac, and Vista laptop networked to the server so I can share files between the three. What all do I need to load on the server so the computers can see the server, and what else do I need to do?

---

### Post by Hospadar on 2009-03-25
You have a couple options:
In my opinion, the easiest (and certainly most secure method) is ssh.
You could also use samba

Search for "ssh" and "samba" in the community docs linked in my sig, you'll find some guides there.
samba is the normal windows "share a folder" protocol, and osx supports it natively I believe.  ssh is a protocol that can be used to securely transfer files and remote control a machine.  You install the ssh server on your fileserver, then install clients (like winscp for windows, I don't know mac ones offhand, but they are out there for sure) on your server machines.  This doesn't provide shared folders per say, but it is a very secure way to transfer files and remote control.

---

### Post by pytheas22 on 2009-03-25
Assuming your server is running Windows and sharing files via the SMB protocol, you just need to install samba in Ubuntu in order to access the Windows file shares.

[This guide]("https://help.ubuntu.com/community/SettingUpSamba") should contain everything you need.

---

### Post by fareforce on 2009-03-25
> **pytheas22 said:**
> Assuming your server is running Windows and sharing files via the SMB protocol, you just need to install samba in Ubuntu in order to access the Windows file shares.

[This guide]("https://help.ubuntu.com/community/SettingUpSamba") should contain everything you need.

There is no windows server. Just a client laptop running vista. The only server is the Ubuntu File server.

---

### Post by fareforce on 2009-03-25
> **Hospadar said:**
> You have a couple options:
In my opinion, the easiest (and certainly most secure method) is ssh.
You could also use samba

Search for "ssh" and "samba" in the community docs linked in my sig, you'll find some guides there.
samba is the normal windows "share a folder" protocol, and osx supports it natively I believe.  ssh is a protocol that can be used to securely transfer files and remote control a machine.  You install the ssh server on your fileserver, then install clients (like winscp for windows, I don't know mac ones offhand, but they are out there for sure) on your server machines.  This doesn't provide shared folders per say, but it is a very secure way to transfer files and remote control.

Thanks, I don't want to use ssh, but samba sounds like a good way to go. I will check out the docs.

---

### Post by InfectedWithDrew on 2009-03-25
I heard a lecture on Samba and it's relatively easy to setup and configure for a home user.

Definitely give it a go.

---

