---
title: "Wifi managed by Netplan won't respond to ARP (i.e. Neighbor Discovery)"
date: 2020-08-18
forum: Networking &amp; Wireless
---

### Post by bmccann on 2020-08-18
Fresh install of Kubuntu 20.04 on brand new hardware with Intel Wifi 6 NIC and a separate (inactive) ethernet port. 

The following tests all work **correctly** :
[LIST]
[*]WIndows 10 networking (as network client) works fine.
[*]Netplan with the 'NetworkManager' renderer works fine. (I.e. KDE manages networking). Inbound and outbound TCP connections are OK.
[*]Netplan with networkd renderer, wifi with static IP and access point listed in /etc/netplan, can make **outbound** connections to other clients and to the Internet.
[/LIST]

What doesn't work is that other computers on the Wifi network can't connect to my test system when I use Netplan with networkd. *ARP doesn't even work*. Other computers on the Wifi network report Host Unreachable.

Here are the failing Netplan yaml files:

*01-ether.yaml*
```
network:
  version: 2
  renderer: networkd
  ethernets:
    enp42s0:
      addresses:
        - 192.168.2.22/24
```

*02-wifi.yaml*
```
network:
  version: 2
  renderer: networkd
  wifis:
    wlo1:
      dhcp4: no
      dhcp6: no
      addresses: [192.168.10.22/24]
      gateway4: 192.168.10.1
      nameservers:
        addresses: [192.168.10.1, 8.8.8.8]
      access-points:
        "HappyCheetah":
          password: "*******"
```

I've checked iptables and the input policy is ACCEPT and that shouldn't affect ARP anyway. I spot checked the wifi router and it has no access controls active and, besides, inbound connections to the new server work fine with the network-manager renderer.

I'm out of ideas. Anyone have a suggestion?

Thanks

---

### Post by bmccann on 2020-08-19
One other data point...

I said that outbound connections (ssh, ping, web, etc) using Netplan with networkd work OK. That's not quite true. I see a delay of *several* seconds when I ping another PC after this new server has been idle for a long time. It's almost as if Netplan/Networkd are bringing the Wifi network up on demand instead of leaving it up all the time.

That said, I can't solve the *incoming* connection problem by continuously pinging my router to keep the Wifi up. The pings are 100% OK (so Wifi is working fine) but I still can't ARP the IP address on that Wifi NIC.

This is the screwiest bug. And, like I said above, everything works fine if I just use 'Network Manager' as the netplan renderer. The problem with that solution is that this is a desktop Linux PC that is also my home file server. If it reboots due to power failure then it is inaccessible until I log back into my KDE desktop again.

---

### Post by bmccann on 2020-08-20
Some more data. I set up the following experiment:[LIST]
[*]Reboot server configured with netplan using networkd renderer.
[*]After reboot, start wireshark listening on the Wifi interface.
[*]Ping from another Linux PC on Wifi network, No reply, No ARP response.
[*]
[/LIST]
Wireshark shows **no** activity on the wifi interface until I ping another device on the network from the broken PC. As soon as I do, then the outbound ping works and inbound pings work as well. (The ARP works and the other station is able to resolve my IP address).

Here's the IP and wireless status before doing the outbound ping that brings up the network. Everything looks fine to me...

```

[deneb:~]$ ip address show dev wlo1
3: wlo1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether e0:d4:e8:19:51:c2 brd ff:ff:ff:ff:ff:ff
    inet 192.168.10.22/24 brd 192.168.10.255 scope global wlo1
       valid_lft forever preferred_lft forever

[deneb:~]$ iwconfig
virbr0-nic  no wireless extensions.

wlo1      IEEE 802.11  ESSID:"HappyCheetah"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 8C:3B:AD:10:A1:A2   
          Bit Rate=86.7 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=43/70  Signal level=-67 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:273   Missed beacon:0

[deneb:~]$ ip route
default via 192.168.10.1 dev wlo1 proto static 
192.168.10.0/24 dev wlo1 proto kernel scope link src 192.168.10.22 
192.168.122.0/24 dev virbr0 proto kernel scope link src 192.168.122.1 linkdown 

``` 

Note, this is the state when the device is non-responsive. As soon as I ping outbound it starts responding to traffic on the Wifi.

Any ideas?

---

