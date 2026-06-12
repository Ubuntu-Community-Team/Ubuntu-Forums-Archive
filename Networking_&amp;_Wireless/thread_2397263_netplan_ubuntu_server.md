---
title: "netplan ubuntu server"
date: 2018-07-27
forum: Networking &amp; Wireless
---

### Post by Spae on 2018-07-27
edit: ok i figured it out



I'm trying to setup a basic netplan .yaml file.

```
network:
  version: 2
  renderer: networkd
  ethernets:
    eno1:
      dhcp4: no
      dhcp6: no
      addresses: [192.168.0.1/24]
```
then i say netplan apply

I want it to be able it to be able to ping itself but when I do a ping, it  says network is unreachable.

Also when I type the command ip addr, it says state down for eno1 and does not show an ip for it. And netplan --debug generate says 'NetworkManager: definition eno1 is not for us (backend 1)'
Although ifconfig state eno1 is up - still does not specify an IP.

 I'm wondering what the correct process for setting a static ip is on ubuntu server 18.04

But also for ubuntu desktop edition, since my aim is to set up a connection between them.

edit: ok if i plug an ethernet cable in from server to pc, I can ping the server's interface from the server. I didn't realise a cable would need to be plugged in to do it lol (since it is pinging itself, not the other interface...)
Now I have to setup a static ip on the client/desktop. I want to be able to do it without altering the interface that is already set up (there are two) if possible. The other is connected to a router with dhcp.

---

