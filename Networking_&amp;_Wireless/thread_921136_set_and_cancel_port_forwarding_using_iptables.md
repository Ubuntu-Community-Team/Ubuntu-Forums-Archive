---
title: "set and cancel port forwarding using iptables"
date: 2008-09-15
forum: Networking &amp; Wireless
---

### Post by Cheesehead on 2008-09-15
I'm looking for good advice on the iptables command to forward (and a second command to later cancel) port 5500 on my router to my Xubuntu box.

Background - My mom has a VNC server, and I have a client. I want her to initiate a reverse-VNC connection, so I need only open my router's port 5500 and forward to to my machine. I can SSH into my router, so I can script it. The router runs HyperWRT v17 (linux), and does use iptables. (I can see'em, I just not smart enough to script'em)

Project - I'm building a script that will find my local and internet IP addresses, SSH to the router and forward port 5500, set my vnc client to listen for the inbound connection, and create a job to watch for the end of the vnc session and cancel the port forward.

Problem - I have it all except the iptable commands for forward/cancel. Is there more convenient method? Good iptable advice welcome...

---

### Post by Cheesehead on 2008-09-17
bump...

---

### Post by Cheesehead on 2008-09-19
bump...bump...

---

