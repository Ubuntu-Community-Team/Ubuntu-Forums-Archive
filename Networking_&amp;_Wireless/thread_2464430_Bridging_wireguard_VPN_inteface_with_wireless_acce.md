---
title: "Bridging wireguard VPN inteface with wireless access point"
date: 2021-07-01
forum: Networking &amp; Wireless
---

### Post by bomberb17 on 2021-07-01
Hello,
My Raspberry Pi 4 runs Ubuntu server 20.04 and I have wireguard VPN client configured on it, which can connect to my home openwrt router whenever I am.
The wireguard interface is wg0, the allowed peer IP in wireguard client configuration is 10.14.0.2/32 and the wireguard server IP (my router) is 10.14.0.1/32.

My goal is to use an external USB wireless adapter I have and use it as access point on my RPi for my wireless devices (e.g. phone, laptop). However I want these devices to seamlessly use the tunnel which is setup already, without them explicitly running a wireguard VPN client themselves.

I read this guide to setup a wireless access point in Ubuntu which suggest to bridge the wireless and the ethernet interfaces (e.g. wlan0 and eth0). What should I do in my case? Should I bridge wlan0 and wg0 or is this not going to work?

---

