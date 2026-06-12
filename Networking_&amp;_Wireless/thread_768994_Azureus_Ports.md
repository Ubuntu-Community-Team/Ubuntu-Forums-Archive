---
title: "Azureus Ports"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by D351 on 2008-04-26
Okay, I have scanned the forums and the rest of the internet for longer than reasonable... Here's the problem.

I'm trying to get Azureus to work, but from the start, I can't get it to work with a port (trying 49152, getting 20s timeout). My router has no filters or firewalls. Also, the port is showing up as open when I scan my router via Network Tools. My only conclusion is that Ubuntu is stopping it from working, and I don't know how to fix it. All of the guides I could find were about forwarding ports (which I attempted anyway, with no results) and additionally, they all linked to the same site which doesn't have my router listed in the first place. Any help would be met with enormous appreciation.

btw: I'm using Ubuntu Hardy, if it makes a difference.

---

### Post by spacegypsy on 2008-04-26
Check out this page; [http://www.azureuswiki.com/index.php/NAT_problem](http://www.azureuswiki.com/index.php/NAT_problem)

scroll down till; Port Forwarding on Linux, specifically Ubuntu


Hopes it will help you.

---

### Post by Monicker on 2008-04-26
> **spacegypsy said:**
> Check out this page; [http://www.azureuswiki.com/index.php/NAT_problem](http://www.azureuswiki.com/index.php/NAT_problem)

scroll down till; Port Forwarding on Linux, specifically Ubuntu


Hopes it will help you.


Hrmm. That wiki articles does not seem to be accurate.  I have never had iptables locked down by default when using Ubuntu.


The OP did not mention the brand/model router, but it is likely that he is behind NAT, and needs to properly configure port forwarding.  The documentation for the device should have more details on that.

---

### Post by spacegypsy on 2008-04-26
I had randomly some NAT problems in the past with Azureus in Ubuntu.

Did some googling, found that wiki about NAT problems and Ubuntu, did what the wiki said to do and I never had any NAT problems anymore afterwards.

---

### Post by Monicker on 2008-04-26
> **spacegypsy said:**
> I had randomly some NAT problems in the past with Azureus in Ubuntu.

Did some googling, found that wiki about NAT problems and Ubuntu, did what the wiki said to do and I never had any NAT problems anymore afterwards.

If he is behind NAT, and port forwarding is not properly configured, it won't matter how iptables is configured.

One thing that section does have right about is the first sentence:  *"Firstly the earlier notes on port forwarding for your router apply as before."*

---

### Post by Monicker on 2008-04-26
> **D351 said:**
> Okay, I have scanned the forums and the rest of the internet for longer than reasonable... Here's the problem.

I'm trying to get Azureus to work, but from the start, I can't get it to work with a port (trying 49152, getting 20s timeout). My router has no filters or firewalls. Also, the port is showing up as open when I scan my router via Network Tools. My only conclusion is that Ubuntu is stopping it from working, and I don't know how to fix it. All of the guides I could find were about forwarding ports (which I attempted anyway, with no results) and additionally, they all linked to the same site which doesn't have my router listed in the first place. Any help would be met with enormous appreciation.

btw: I'm using Ubuntu Hardy, if it makes a difference.


What brand and model router do you have?

---

### Post by D351 on 2008-04-27
> **Monicker said:**
> What brand and model router do you have?

I've got a Network Everywhere NWR11B

---

### Post by D351 on 2008-04-27
> **spacegypsy said:**
> Check out this page; [http://www.azureuswiki.com/index.php/NAT_problem](http://www.azureuswiki.com/index.php/NAT_problem)

scroll down till; Port Forwarding on Linux, specifically Ubuntu


Hopes it will help you.

Wow, thanks... this problem was far simpler than I had imagined. Though I still don't know why I needed to do that stuff if my router doesn't have anything set to block.

---

### Post by Monicker on 2008-04-27
> **Monicker said:**
> What brand and model router do you have?


That model is covered here, towards the bottom:

[http://portforward.com/english/routers/port_forwarding/NetworkEverywhere/NWR11B/Utorrent.htm]("http://portforward.com/english/routers/port_forwarding/NetworkEverywhere/NWR11B/Utorrent.htm")

You will need to configure port forwarding of port 49152 to the ip address of the computer which is running Azureus.

---

