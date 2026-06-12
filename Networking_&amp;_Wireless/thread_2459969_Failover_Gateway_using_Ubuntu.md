---
title: "Failover Gateway using Ubuntu"
date: 2021-03-30
forum: Networking &amp; Wireless
---

### Post by ghulican on 2021-03-30
Hello!

I am trying to use Netplan to handle some routing based on internet being up or down, and I keep getting a bit stuck.

What I would like to have happen:
[IMG]https://i.imgur.com/KYTO8iv.png[/IMG]


Current landscape:

network:
version: 2
renderer: networkd
ethernets:
enp1s0:
addresses:
- 10.0.0.210/24
dhcp4: false
gateway4: 10.0.0.1
nameservers:
addresses: [10.0.0.1, 8.8.8.8]
enp2s0:
optional: true
enp3s0:
optional: true
enp4s0:
optional: true
usb0:
addresses:
- 172.16.0.9/24
dhcp4: false
routes:
- to: 0.0.0.0/0
via: 172.16.0.1
metric: 100
table: 100
routing-policy:
- to: 172.16.0.9/24
table: 100
- from: 172.16.0.9/24
table: 100
nameservers:
addresses: [8.8.8.8, 8.8.4.4]



I have a route rule configured on my router/gateway to allow traffic to 172.16.0.1 so I am able to access the gateway across, but my main problem right now is how do I maintain a constant internet connection in case enp1s0 has no traffic allowed in/out.

I setup basic firewall rules to test blocking 10.0.0.210 and it seems like it doesn't know how to switch between interfaces.

Any help would be appreciated.

---

