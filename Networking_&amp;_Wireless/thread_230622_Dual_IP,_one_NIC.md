---
title: "Dual IP, one NIC"
date: 2006-08-06
forum: Networking &amp; Wireless
---

### Post by RudolfMDLT on 2006-08-06
Hi!

I've heard that it is possible but have no Idea how to do it. How can I bind a second IP range on my Ethernet card. My adsl router and all the machines on the network run on 10.0.0.X range while the PABX - Astrix machine, SIP phones and bridges all work on the 192.168.10.X range. How can i setup 2 IP address on 1 network card so that i can have Internet and browse the network on the 10.0.0.x range AND do maintenance on the 192.168.10.x range without changing the IP address every time I need to switch?

---

### Post by pdub on 2006-08-06
I have a similar setup. Here is a clip from my /etc/network/interfaces file.


---clip---

auto eth0
iface eth0 inet static

address 192.168.0.10 
netmask 255.255.255.0 
gateway 192.168.0.1

auto eth0:0
iface eth0:0 inet static

address 10.0.0.10 
netmask 255.255.255.0 

---clip ---

**Make a backup first:**

sudo cp /etc/network/interfaces /etc/network/interfaces.bak

**Then edit your interfaces file**:

sudo gedit /etc/network/interfaces

**Then restart networking;**

sudo /etc/init.d/networking restart

My 192.168.0.0 network is the main network and provides my Internet access as well. The 10.0.0.0 network is private and only my network switches and routers are on this network for management.

Hope this helps.

---

### Post by RudolfMDLT on 2006-08-06
Perfect! Thanks a lot! Works like a charm!:-D

---

