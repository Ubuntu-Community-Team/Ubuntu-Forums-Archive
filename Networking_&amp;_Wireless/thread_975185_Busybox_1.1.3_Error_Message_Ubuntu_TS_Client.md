---
title: "Busybox 1.1.3 Error Message Ubuntu TS Client"
date: 2008-11-08
forum: Networking &amp; Wireless
---

### Post by nimlc on 2008-11-08
[FONT="Arial"][SIZE="5"][/SIZE][/FONT]

Hi all, I was wondering if anyone can help. I've setup a Ubuntu Terminal Server (8.04 Hardy Heron) with 2x NIC (inside for LAN and outside interface for the Internet).

All was working fine until today, when the client connected had a "Busybox v1.1.3" error message and now won't boot into a session. I am left with a black screen similar to a terminal prompt (has initramfs and a flashing cursor) and no GUI.

The client is booted in the network at the moment as I can see its been given an IP address of 192.168.0.245 (via ifconfig) and I can cd into the var, boot, root folders etc.

The server itself had this problem (when i was setting it up), I used a solution whereby, in a terminal, I typed:

sudo ltsp-update-image

This worked for for the server and its working. However, the problem is now with the client. The client boots into the network via a network boot (in the bios). I tried the above solution but to no avail.

Anyone have any ideas or point me to the right direction? Thank you :confused::confused:

---

