---
title: "static ip linksys BEFSR41 port forwarding problem"
date: 2008-02-17
forum: Networking &amp; Wireless
---

### Post by whoop on 2008-02-17
I have a cisco linksys BEFSR41 ver 4.2 wired router (latest firmware 2.00.1, Sep 11 2006), ubuntu 7.10 and I want to have proper connections with torrent protocol.

The first thing I did was make my IP static via the network settings GUI. changed the roaming mode to static IP addess and assigned 192.168.1.40 as the ip address, 255.255.255.0 as the subnet mask and 192.168.1.1 as the gateway (this is the routers IP).

I fooled around with my OS a bit and it all seemed to be working in perfect order.

The next thing I did was to launch my routers webapplication, go to the "Applications
& Gaming" tab and to the "Port Range Forwarding" sub-tab. there I added port range start "26737" port range end "26737" protocol "both" ip address "192.168.1.40" checked the enabled checkbox and saved the settings (port 26737 is used by my bittorrent client).

Now with this configuration I keep losing internet connections for short periods of time. It just goes on and of by itself. As soon as I disable port forwarding I don't lose connection anymore.

This is driving me nuts... Help much appreciated.

---

