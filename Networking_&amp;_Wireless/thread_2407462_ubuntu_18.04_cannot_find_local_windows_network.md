---
title: "ubuntu 18.04 cannot find local windows network"
date: 2018-12-04
forum: Networking &amp; Wireless
---

### Post by elim-qiu on 2018-12-04
I did a clean instllation and an upgrade from ubuntu 16.04, both find my iMac on the local network but cannot find computers running windows on the local network. 

The one upgraded demages the working 16.04 local network configuration.

---

### Post by Morbius1 on 2018-12-04
The Mac broadcasts it's name to the network using mDNS ( Bonjour in macos / avahi in Linux ). The Windows machine - at least as far a Linux is concerned - uses netbios.

Because of changes made to samba netbios " discovery" does not work. You have two choices:

[1] While you cannot browse the network to find the Windows machine you can still access it but you need to do so explicitly by name or ip address using Connect to Server for example.

[2] You can edit /etc/samba/smb.conf and add a line under the **workgroup = WORKGROUP** line:
```
client max protocol = NT1
```
If you have no smb.conf install smbclient:
```
sudo apt install smbclient
```
None of these changes will impact how the Mac works in your network because Linux and Mac can do Samba without any Windows ... um ... stuff.

Notes on NT1:

** NT1 is slow as molasses and "chatty" but it was the default in Ubuntu 16.04 
** NT1 corresponds to SMBv1 on WIndows and Win10 for example disables it so if you set your linux client to NT1 you will be able to see the WIn10 machine but you will not be able to access it - ar any other machine that has disabled SMB1.

---

### Post by elim-qiu on 2018-12-04
Thanks a lot [**[COLOR=#000000]Morbius1[/COLOR]**]("https://ubuntuforums.org/member.php?u=982144") !  I tried your method 1. It's working.

I also installed smbclient and added the line you suggested. But after a reboot, so thing changed....

---

