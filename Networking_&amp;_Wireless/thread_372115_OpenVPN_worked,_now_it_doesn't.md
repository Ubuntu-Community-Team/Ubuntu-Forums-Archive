---
title: "OpenVPN worked, now it doesn't"
date: 2007-02-27
forum: Networking &amp; Wireless
---

### Post by puyi on 2007-02-27
I am a linux n00b, Ubuntu Edgy is the first distro I've tried. I have a dual boot setup on my laptop with Windows XP Pro. I've installed Network Manager and OpenVPN using Synaptic. For about one week I've been able to remote into my Windows network using OpenVPN client in Edgy. Please note I am NOT using Network-Manager-OpenVPN, but Network-Manager and separately OpenVPN.

For the OpenVPN Server work uses a WRT54GL router with DD-WRT firmware with OpenVPN embedded.

When viewing the Terminal log for OpenVPN, after successfully receiving "Initialization Sequence Complete" the process almost immediately restarts, then "Initialization...", then the process restarts again.

What I think is happening is after a few successful connections earlier in the week, there remain residual instances of the virtual tap adapter OpenVPN requires.

Where is the interface file for the tap adapter located? It is not in /etc/network/interfaces because in order for Network Manager to work I have to remove al adapters from interfaces except the local loopback interface "lo".

This can't be that difficult. Setting up OpenVPN in Windows by comparison was a breeze.

---

### Post by puyi on 2007-02-28
I've been able to reconnect to my Windows network again, sort of. When in Windows I initiated OpenVPN, took note of my virtual ip, disconnected and rebooted into Edgy.

I changed my OpenVPN.conf to the static ip matching my virtual ip under Windows.

I seem to be able to connect but when I initiated a ping (I use a count of ten) I get packet loss between 30% and 90%; makes for a very flaky connection.

Perhaps there's a server setting I can change to increase timeout.

---

