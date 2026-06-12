---
title: "Hosts/address discovery on mixed Ubuntu/WinXP network"
date: 2006-12-28
forum: Networking &amp; Wireless
---

### Post by ArgentSilver on 2006-12-28
So I'm running a home LAN, partly wired with a switch and with one WAP for three laptops and a remote desktop to connect. All systems get their local addresses from the DSL gateway which runs a DHCP server. Until recently I was purely running Windows, but recently I've started to convert some of my PC's to Ubuntu (Dapper and Edgy both) or dual boot systems.

Since I've been using DHCP, the addresses are not immediately known, but on the Win machines, you can look in Network Neighborhood and see the hosts (presumably via NetBios?). One of the Ubuntu boxes is set up as a music server, which is controlled from any other PC via VNC. The VNC clients running under Windows accept just the host name of the VNC server box (which I know!), but the VNC clients running under Ubuntu want an IP address (which I don't know due to it being DHCP) and won't accept just the host name. Is there some easy way around this that I don't know (being a noob), or would the simplest thing be to quit using DHCP and change to Static IP addresses and use the Host file?

---

