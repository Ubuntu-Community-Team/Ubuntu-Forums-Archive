---
title: "Wired and Wifi Communication"
date: 2008-07-19
forum: Networking &amp; Wireless
---

### Post by bayvista on 2008-07-19
I am running Ubuntu Hardy on my Desktop and communicate with the Internet via a D-Link Wireless Router using an Ethernet cable. I also have a Laptop which communicates with the same Router using WiFi.

My question is: How can I communicate between the Desktop and Laptop? 

I know that I can plug the Laptop into an Ethernet port, but is it possible to communicate between the two networks?

---

### Post by pikabuntu on 2008-07-19
are you talking about like a shared folder or something like that?
Even though these are connected to your router differently, they are part of the same network.

---

### Post by bayvista on 2008-07-19
> **pikabuntu said:**
> are you talking about like a shared folder or something like that?
Even though these are connected to your router differently, they are part of the same network.
Yes, a shared folder

---

### Post by superprash2003 on 2008-07-19
yes its possible. what OS is the laptop running?

---

### Post by bayvista on 2008-07-19
The Laptop is running Windows Vista. I have been able to share folders OK using a wired connection. However, I have relocated the Laptop upstairs and don't want to run wires.

---

### Post by superprash2003 on 2008-07-20
firstly ensure if both the pcs are able to ping each other

---

### Post by bayvista on 2008-07-21
Well, that's odd. I can ping the Desktop (Ubuntu) from the Laptop (Vista). But I can't ping the Laptop from the Desktop. Have tried both IP address and name.

---

### Post by superprash2003 on 2008-07-21
disable vista firewall temporarily and then try,.. maybe its firewall blocking

---

### Post by bayvista on 2008-07-23
Thanks for that. I Disabled 'wireless' in the Vista Firewall and it all works like magic.

---

