---
title: "Network interface priority"
date: 2007-11-30
forum: Networking &amp; Wireless
---

### Post by rob_connolly on 2007-11-30
Hi,

I have a problem with which network interface Ubuntu want to use. Here's my situation:

I have an Ethernet connection which connects to a router which connects to my local wired/wireless network. This network has not internet connection as broadband is not available in my area. Therefore I connect to the internet via my Intel536 modem, this connection works for the most part.

However, when I am plugged into the local network, I cant access any pages over the dial-up connection! The only things I can access are over the local network even though my modem is active and ppp0 is shown in ifconfig.

At first I thought that this may be a firewall problem, so I reconfigured my Firestarter firewall to use ppp0 as the internet connection and eth0 as the lan connection. This didn't work!

Then I thought maybe it was a nameserver problem, so I checked /etc/resolv.conf before and after connecting over my modem, just to see if the ISP nameservers were being added correctly, they were, so that's not the problem.

I think perhaps this may be a routing problem, but I have no idea how to fix it!

The weird thing is that the only way I can back my internet access after connecting to the lan is to disconnect the cable and reboot! Just bringing the network interface down doesn't work!

Anyone got any ideas? I'm using Gutsy.

Thanks in Advance,

Rob

---

