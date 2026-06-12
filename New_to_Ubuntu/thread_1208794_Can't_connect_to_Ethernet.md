---
title: "Can't connect to Ethernet"
date: 2009-07-09
forum: New to Ubuntu
---

### Post by rajwraith on 2009-07-09
This is what happened. I installed ubuntu 9.04, went to the "Edit connections" menu. There I put in the Mac Address, IP, Default gateway and the usuals on "Auto eth0". I click on connect but ubuntu keeps retracting to "Auto Ethernet" which doesn't have any of the settings I put in Auto th0. 
This is getting really annoying. And I need a fix. Please can anyone help?

---

### Post by jonobr on 2009-07-09
If your doing dhcp you shouldnt need to any of that.

Could you open a terminal window and type 
ifconfig

Then 

sudo dhclient


and rerun ifconfig again?

Do you obtain an ip address?

something along the lines of 192.168.1.x?

---

### Post by LewRockwell on 2009-07-09
> **rajwraith said:**
> This is what happened. I installed ubuntu 9.04, went to the "Edit connections" menu. There I put in the Mac Address, IP, Default gateway and the usuals on "Auto eth0". I click on connect but ubuntu keeps retracting to "Auto Ethernet" which doesn't have any of the settings I put in Auto th0. 
This is getting really annoying. And I need a fix. Please can anyone help?

are you sure your cables are good?

.

---

### Post by rajwraith on 2009-07-09
My cables are fine cause I'm using Vista to reply to you right now. And my ISP requires me to put in those settings. So just getting an IP won't work.

---

### Post by jonobr on 2009-07-09
Not sure I follow you there squire....

Are you trying to configure a static IP address on your machine?

If you have changed your wired settings please run ifconfig and post it here

---

### Post by rajwraith on 2009-07-13
Ok, I forgot to mention that I changed my motherboard. The problem came up then. I thought doing a reinstall would fix it but that didn't work out.

---

### Post by HereInOz on 2009-07-14
If you are endeavouring to set a static IP address for this machine, then you are best to uninstall Network Manager.  It is great for DHCP, wireless and 3G wireless, but is more trouble than it is worth for a static cable connection.

Uninstall Network Manager, and configure your interface manually:

sudo gedit /etc/networking/interfaces

It should look something like this when you have finished:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
    address    192.168.51.3
    netmask    255.255.0.0
    network    192.168.51.0
    broadcast  192.168.51.255
    gateway    192.168.51.254

Obviously change the ip addresses to suit your network, but hopefully this gives you the idea, then set your DNS server(s):

sudo gedit /etc/resolv.conf

nameserver   your.primary.DNS.server
nameserver   your.secondary.DNS.server

Hope this helps.

---

### Post by actinio on 2009-07-14
Could you please post the model of your motherboard & technical features? Surely It needs a privative driver to connect Ethernet..

---

### Post by rajwraith on 2009-07-14
it's a P5KPL-AM Asus Motherboard.

---

### Post by Wazz72 on 2009-07-19
I have the same problem,  I an connect using wireless to the network, but the wired mode is down.  All windows machines working ok on wired network.  Linux machine will work if I boot from the live cd.  But if I try to configure through the network manager than it does'nt work.  Using DHCP, or manual.
Motherboard is an ASUS PK5-e

---

