---
title: "Network Manager not working."
date: 2006-07-30
forum: Networking &amp; Wireless
---

### Post by khughes on 2006-07-30
Hello everyone,

I just installed dapper, ran all the updates, and then ran Automatix to install the essentials including the network manager which I had on here before. My problem is, the network manager is not working with my wireless at all. I can click on it and see wired networks but there is no option for any other devices. Does anyone know how to fix this? I am using an ipw bg2200.

---

### Post by khughes on 2006-07-31
Anyone?

---

### Post by arnieboy on 2006-07-31
If it is not managing your network connections after upgrading to Dapper, you'll need to comment out the references to all interfaces (except lo) in /etc/network/interfaces to let NetworkManager handle them.

```
sudo cp /etc/network/interfaces /etc/network/interfaces.bak
sudo nano /etc/network/interfaces
```

It should look similar to this when you are done:
> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
# auto eth1

# iface eth1 inet dhcp


Then reboot and you should be good to go! 

Also bookmark the following link (from where I copied and pasted the above):
[https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

---

### Post by khughes on 2006-07-31
Thanks alot Arnieboy.

That was exactly what I was looking for. It was a very simple fix.

---

