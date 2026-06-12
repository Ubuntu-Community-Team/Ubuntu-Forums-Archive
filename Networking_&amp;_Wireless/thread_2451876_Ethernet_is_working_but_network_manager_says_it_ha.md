---
title: "Ethernet is working but network manager says it has never been used"
date: 2020-10-12
forum: Networking &amp; Wireless
---

### Post by knight69 on 2020-10-12
I am setting up a new server on Ubuntu 20.04 server using the Mate DE.  It is connected via ethernet (eno1) and is working fine. I attempted to set a static address using the advanced network connections in the control panel, but when I first opened it, I was informed there were no network connections.  I added a network connection identifying eno1 as the ethernet device in my computer and set all the normal parameters including a static address 192.186.1.186.  I saved the settings, rebooted the computer and there were no changes. 

The small network icon in the upper right corner (resembles an open fan) indicates there are no connections. The Ethernet Network option on the drop down menu is grayed out. When I click on Edit Connections it says my ethernet connection has never been used. The enable networking option is checked and (as you can see from this message) the network is working fine. I just have no way to manage it.

What have I done wrong and how can I set a static IP address if this isn't working?

---

### Post by TheFu on 2020-10-12
Which ISO was installed?  Server or some desktop ISO?

Linux Servers don't have GUIs. No GUI network manage tools are included and they don't expect any, ever.
For 20.04 server, networking is controlled in the netplan files under /etc/netplan/

If you want to modify system stuff with a GUI, install using a desktop ISO, not Server.  Otherwise, configure the system doing it the server way.  The Ubuntu Server Guide has instructions for many server tasks, but not te entire 5,000,000+ things a linux sever can do.

---

