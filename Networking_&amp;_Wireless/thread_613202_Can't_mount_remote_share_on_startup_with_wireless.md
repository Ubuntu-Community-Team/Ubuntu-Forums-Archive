---
title: "Can't mount remote share on startup with wireless"
date: 2007-11-14
forum: Networking &amp; Wireless
---

### Post by Iram on 2007-11-14
Like many others I have not been able to successfully use /etc/fstab to mount a Windows share over my wireless network. I suspect it is because fstab is doing its thing before the wireless connection is succesfully made.

This always works: sudo smbmount //192.168.1.4/myshare ~/music

This line in fstab always fails: //192.168.1.4/myshare /home/music smbfs username=myname,password=mypass,umask 022 0 0

I've tried to use cifs instead to no avail.

Iram

IIs there any way to first, verify that the problem is because the network connection is not established yet, and then to run a script later in the startup to mount the share.

I'm very new to linux, using UBUNTU Gutsy, but am comfortable with batch programming in Windows so  I'll need fairly detailed guidance.

Thanks,

Iram

---

