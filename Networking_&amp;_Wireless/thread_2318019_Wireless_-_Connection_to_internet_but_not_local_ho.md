---
title: "Wireless - Connection to internet but not local hosts"
date: 2016-03-22
forum: Networking &amp; Wireless
---

### Post by Dz0rpw on 2016-03-22
Hi All,

I'm new to ubuntu and looking for a bit of help on the networking side. 

So I've just installed 15.10 on an old HP laptop. In my office it connects to everything and works great. I then walk up to the house (out of range of the original wireless router) and connect to the house wifi. I can connect to the internet no problem but I can see (or ping) any local hosts.

I've not made any changes to host files, routes etc. Everything is DHCP and my work laptop, Iphone, Ipad...etc etc you get the idea will work.
Both wireless routers are on the same network with one forwarding the DHCP requests to the other (office is routing requests to the house router).
Other than a connection password there are no ACL's applied on the routers.
As mentioned, I can get out to the internet.
Arp cache is almost empty other than the gateway and the host I'm pinging which shows as 'incomplete'.
Subnets are the same 255.255.255.0
IP is being set via DHCP to 192.168.0.12 (target server is .10)...no ping
If I browse the network, I see the folders from the server but I think these are seen and retained from the good wireless connection in the office. Once in the house and you try to click on them...No route to host.

Any pointers?

Cheers

---

### Post by Dz0rpw on 2016-03-22
Small update...now it works (Office>House) however when I return to the office...can't see any wireless. Disabled networking and re-enabled...nothing. Rebooted and it works. Is this what I should come to expect?

---

### Post by kurt18947 on 2016-03-23
> **Dz0rpw said:**
> Small update...now it works (Office>House) however when I return to the office...can't see any wireless. Disabled networking and re-enabled...nothing. Rebooted and it works. Is this what I should come to expect?

It's not what you should expect certainly. I'm not a wizard like some here but I'd probably start by posting the output of one of two commands. If your wireless card is internal, open a terminal (ctrl-alt-t) and enter this command: "lspci". If you're using a USB wifi adapter, enter this command: "lsusb". Copy/paste the output in this thread. The output on my machine looks like this:

Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 17ef:480f Lenovo Integrated Webcam [R5U877]
**Bus 001 Device 003: ID 0bda:8178 Realtek Semiconductor Corp. RTL8192CU 802.11n WLAN Adapter**
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

The bolded line is the make & model of my wifi adapter. This is a simple start and perhaps one of the more knowledgeable folks here will help out.

---

