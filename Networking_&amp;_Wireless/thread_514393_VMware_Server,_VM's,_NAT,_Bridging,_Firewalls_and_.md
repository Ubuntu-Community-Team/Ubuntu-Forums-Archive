---
title: "VMware Server, VM's, NAT, Bridging, Firewalls and Wireless/Wired"
date: 2007-07-31
forum: Networking &amp; Wireless
---

### Post by Zooberdeaux on 2007-07-31
Phew, thought I'd like everything.  But, seriously, here is the situation and question:

Background:

I have a Feisty install on a T40 IBM Thinkpad [60GB HDD, 1GB RAM, 128MB Video Memory, 1.6GHz Centrino with Intel Speed Step).  Most everything (after a little tweaking here and there) is working, including VMWARE Server (found a link that explained the ANYSERVER patch), sound [but still haven't patched it, it is definitely a bug however], and other things.

Desire:

I wish to be able to operate VMWARE Server and have the Virtual Machines (guests such as XP, and Vista) obtain a networking connection via either the Thinkpad WIRED or WIRELESS connection.  It's just that simple.

Complications:

(1) Ubuntu Running:  I plug in a wired CAT5 ethernet to the RJ45 port, and the wireless connection (which was, until the moment I plugged it in -- working fine) dies completely.  The wired ethernet network, however, comes up rapidly via DHCP.  Although I understand the issues with a multihomed computer, this is part of my desire.  I wish for Ubuntu NOT to automatically decide which network connection is my preferred - and instead let me decide.  Can I write a shell script which would poll/detect the presence of both ETH0 [ethernet, wired] and ETH1 [wireless 802.11b] and somehow prompt me to make a routing decision on which one will become default?  It can't possibly be that hard, can it?

(2) I wish for all of my Virtual Machines (XP, Vista) to have TWO network connections (physically emulated, of course, in the VM), such as LAN 1 and LAN 2.  Behind the scenes, I'd like LAN-1 to be always mated/matched up with ETH0 on the laptop, preferably in a bridged (but sometimes necessarily, I'd have to switch to NAT) mode.  The issue here isn't that this isn't possible, but it is VERY confusing.  At times, I'm not even sure which VMNET is hooked to which.  It is going to take some study time to work this out properly, I suppose.  The fallout here is that say, XP is running in a VM, and is doing NAT networking in the VM and get's an IP and info just find from VMWARE's built-in DHCP server, it is going to fail if ETH0 (which the VM was aligned with/linked to) goes down.  I want it to now (mid-stream) re-route to Wireless if it's up and available.

(3) Do I make any sense here?


Thanks all

---

