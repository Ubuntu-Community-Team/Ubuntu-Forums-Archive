---
title: "Gutsy Server Ethernet Adapter Not Recognized"
date: 2007-10-01
forum: Networking &amp; Wireless
---

### Post by webdevguy on 2007-10-01
I've been checking out Gutsy on VMware virtual machines. I don't have a problem with the Desktop recognizing the ethernet adapter, but the Server won't recognize it. In Feisty I could change the MAC address in /etc/iftab to match the address in the .vmx file, but in Gutsy /etc/iftab doesn't exist. I tried adding the MAC address to /etc/network/interfaces, but that didn't help.

What changed in Ubuntu Server 7.10 with respect to the ethernet adapter, at least for VMware?

---

### Post by webdevguy on 2007-10-08
Is there anyone out there familiar with this issue, and its resolution?

---

### Post by ttruman on 2007-10-08
I had the same problem from an x86 VMWare server with Gutsy as a guest.  Look at [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/145382](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/145382).  I removed the /etc/udev/rules.d/70-persistent-net.rules file and restarted the guest and this solved my problem.

---

### Post by webdevguy on 2007-10-08
That worked for me! I deleted the /etc/udev/rules.d/70-persistent-net.rules file and restarted. The ethernet adapter now showed up using ifconfig, but it didn't have an IP address. So I deleted the MAC address line that I had added to /etc/network/interfaces and restarted again. Then I got an IP address, and I was able to ping an Internet site.

Thanks!!

---

### Post by Focher on 2007-10-31
Confirming that I had the same problem in 7.10 Ubuntu Server and removing /etc/udev/rules.d/70-persistent-net.rules and a reboot fixed the problem.

thanks!

---

### Post by Freaky#Funga on 2007-12-28
Another experience: Works also on Gutsy Desktop

(Feisty = host, Gutsy = guest)

Thanks to **ttruman** :-)

---

