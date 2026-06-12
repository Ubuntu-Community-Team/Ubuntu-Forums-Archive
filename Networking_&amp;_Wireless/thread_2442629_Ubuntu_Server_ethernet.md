---
title: "Ubuntu Server ethernet"
date: 2020-05-05
forum: Networking &amp; Wireless
---

### Post by xxteraxx on 2020-05-05
I tried using ubuntu server so I can install i3 without any other desktop.  I booted it up and plugged in my ethernet cable (Which did work on other installs of ubuntu) and no lights and my pc was not connected.  I thought that I just had to put the interface up so I tried with Ifconfig and it said that the command ifconfig did not exist and I needed to install it.  But how do I install net-tools without internet.  Is there a way that i can connect without the use of ifconfig. (I'm using ethernet) because I really want to get it up and running. Any help would be much appreciated 

Info: Ubuntu 20.04lts
hp 15-cs0022cl

---

### Post by TheFu on 2020-05-05
ifup/down has been deprecated for a few releases.  Use the ip commands.
Ubuntu Server has been using netplan for ip/network configs since 17.10.  That is the expected method on 20.04 server.

netplan config files go into /etc/netplan/.  To get wired DHCP working,
```
network:
  version: 2
  renderer: networkd
  ethernets:
    enxcxxyyzzaabb:
      dhcp4: true
      dhcp6: false
```
This is a yaml file, so indentation is absolutely critical.  Get that wrong and it won't work.  Change the enxcxx... to be your ethernet device.
Then:
```
sudo netplan generate
sudo netplan apply --debug

```
Static ip setup is a little different.

---

