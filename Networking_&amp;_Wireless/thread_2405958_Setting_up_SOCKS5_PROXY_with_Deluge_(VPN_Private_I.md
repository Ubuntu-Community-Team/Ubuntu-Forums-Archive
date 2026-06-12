---
title: "Setting up SOCKS5 PROXY with Deluge (VPN: Private Internet Access)"
date: 2018-11-13
forum: Networking &amp; Wireless
---

### Post by Drone4four on 2018-11-13
For many years I&#8217;ve used Vuze. They have this terrific wiki on [Proxies and VPNs]("https://wiki.vuze.com/w/Proxies_And_VPNs") teaching you how to setup your VPN to cooperate with Vuze.  Vuze seems to be no longer maintained.  Major bugs are common place.  I am now giving Deluge a try.  

As suggested in [How To Use Deluge Anonymously]("https://www.best-bittorrent-vpn.com/how-to-use-deluge-anonymously.html"), I&#8217;ve generated PPTP/L2TP/SOCKS Username and Password from the dashboard of my VPN provider (Private Internet Access). I&#8217;ve plugged in the rest of information as instructed in this guide. I restarted Deluge. I am now connected to peers and exchanging data. But how do I verify that I have successfully established a SOCKS5 Proxy connection? My little Private Internet Access icon is red instead of green in my systray, meaning my VPN is not connected. Does this mean my connection is not secured? Or is it possible to have a properly configured secure proxy connection even with my VPN tunnel being turned off?

---

### Post by mitesh.agrwl on 2018-11-13
Wireshark is a good tool to analyze network traffic. Download wireshark from the repositories. Start it and capture the traffic on the network interface in promiscuous mode. To make easy things, only run the Delgue. The traffic captured in wireshark can be analyzed to check whether it is encrypted or not. Another similar tool is **tcpdump.**

---

### Post by Drone4four on 2018-11-15
I downloaded, installed and configured Wireshark. I referenced a guide named, &#8220;How to Install and Use Wireshark on Debian 9 / Ubuntu 16.04 / 17.10&#8221;. I successfully captured some torrent traffic showing an IP address located in the Netherlands. I also followed a guide for setting up a SOCKS5 proxy in Firefox called, &#8220;How to Configure the SOCKS5 Proxy in Firefox?&#8221;. This guide was written for an audience with a different VPN provider, but I plugged in all the information that I used for Deluge from earlier for my VPN provider. When I checked my IP address with SOCKS5 turned on in Firefox, it&#8217;s not the same address that was showing in Wireshark, but the IP address is still clearly showing as located in Roosendaal, Netherlands.  I figure my connection is now secure.

---

