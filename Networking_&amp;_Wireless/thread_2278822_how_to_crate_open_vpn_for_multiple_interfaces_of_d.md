---
title: "how to crate open vpn for multiple interfaces of different ubuntu hosts?."
date: 2015-05-19
forum: Networking &amp; Wireless
---

### Post by kalamram on 2015-05-19
I want to create OpenVPN tunnel between two Ubuntu 12.10 hosts which has two interfaces, say:
  Host1: eth0, eth1
Host2: eth2, eth3

  A tunnel is wanted between:
  Host1 (eth0) <-> Host 2 (eth2)
Host1 (eth1) <-> Host2 (eth3)

  Question:
  1) How to create two separate tunnel (openvpn) for each link (here two links).
2) Is it possible to create two tunnels between two hosts?.


    In openvpn config, one bridge but multi tap creation can be done  that I have seen, but how to create two bridge and two tap each attached  with eth0 or eth1 interface, how to create this setup. Any iptable  config do I need to do.

---

