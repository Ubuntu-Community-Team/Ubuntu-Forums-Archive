---
title: "Network wakes up after a couple of  tries"
date: 2007-11-08
forum: Networking &amp; Wireless
---

### Post by gnikol on 2007-11-08
Hi, 
I have an ubuntu machine connected to the internet thru a modem-router via usb. 
The same machine is connected to a local area network via the ethernet card to a couple of computers running windows.  The reason I'm doing this is that I don't want my internal LAN to have any  acess to the internet. 
I have configured samba and everything works fine, but the networks (internal & external) 
usually does not wake up on the first try. That means the most of times on the first boot the network is dead, and I have to reboot the ubuntu machine to make it all work. 
Is there a way to wake up the network without having to reboot the computer again?

---

### Post by Lambert on 2007-11-08
> **gnikol said:**
> Hi, 
I have an ubuntu machine connected to the internet thru a modem-router via usb. 
The same machine is connected to a local area network via the ethernet card to a couple of computers running windows.  The reason I'm doing this is that I don't want my internal LAN to have any  acess to the internet. 
I have configured samba and everything works fine, but the networks (internal & external) 
usually does not wake up on the first try. That means the most of times on the first boot the network is dead, and I have to reboot the ubuntu machine to make it all work. 
Is there a way to wake up the network without having to reboot the computer again?

try this command from a terminal

```

sudo /etc/init.d/networking restart

```

you shouldn't have to run this but that's how to restart networking services. When it doesn't work I would suggest running the command dmesg or looking in /var/log/sys.log for errors happening when you boot.

---

