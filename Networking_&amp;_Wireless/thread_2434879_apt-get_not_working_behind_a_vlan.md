---
title: "apt-get not working behind a vlan"
date: 2020-01-12
forum: Networking &amp; Wireless
---

### Post by tkffaul on 2020-01-12
Im trying to setup a simple print server on a vlan using Ubuntu Server 18.04. I have the netplan working. I can ping on the vlan, I can ping out to the internet, i can even use spider to get out of the network and see http pages, I can also ping the servers which apt says are unreachable. The only issue i have is apt... every time i try to use apt i get nothing... it says it cant reach the servers.

Here is my netplan config:

```
network:
  version: 2
  renderer: networkd
  ethernets:
    ens33: {}
  vlans:
     vlan.40:
        id: 40
        link: ens33
        addresses: [192.168.40.2/24]
        gateway4: 192.168.40.1
        nameservers:
           addresses: [192.168.40.1]
```

I've been working on this for two days... and I just cant see the problem. I'm just hoping someone catches the issue. BTW no firewall and no IPTABLES have been set into this setup. I figured i would get it all working before added more things. I also tried turning off all offloads as i've heard those can strip vlan tags. I have several other devices on this vlan which operate fine. I have my trunks laid out and i know this issue isn't on the network side of things.

---

