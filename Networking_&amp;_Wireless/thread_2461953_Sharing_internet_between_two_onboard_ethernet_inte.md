---
title: "Sharing internet between two onboard ethernet interfaces doesn't seem to work"
date: 2021-05-10
forum: Networking &amp; Wireless
---

### Post by Cursed Lemon on 2021-05-10
Hey guys, having a little trouble here on Xubuntu 20.04. I have a computer and a video game console side-by-side, with the computer having two onboard ethernet ports. I am trying to share the internet connection to the video game console by having the internet connected to one ethernet port and then having that connection shared through to the other ethernet port where the console is connected (getting both DHCP from my router as well as an internet connection). 

This is not really out of necessity, I have several other options available to me including just taking the time to run another ethernet connection to the console. This is more of a "why the hell doesn't this work" affair that I want to solve. 

The computer in question is dual-booted and this setup works perfectly by creating a network bridge in Windows between the two interfaces. When I boot up Linux, however, it doesn't work. 

I have entered **nm-connection-editor** and chosen to share enp6s0 (netplan-enp6s0, the port with the internet connection) with other computers. The second ethernet connection is netplan-enp5s0 and is set to Automatic (DHCP). According to Google, this is all I should have to do in order for this to work. 

Here is an **ifconfig** readout:

```
enp5s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        ether 20:cf:30:e1:54:30  txqueuelen 1000  (Ethernet)
        RX packets 32  bytes 10944 (10.9 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 3299  bytes 689708 (689.7 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

enp6s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.117  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::46f0:8e27:cd42:332c  prefixlen 64  scopeid 0x20<link>
        ether 20:cf:30:e1:54:93  txqueuelen 1000  (Ethernet)
        RX packets 590670  bytes 719221368 (719.2 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 264507  bytes 24930006 (24.9 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 157665  bytes 15196781 (15.1 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 157665  bytes 15196781 (15.1 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


```

My netplan config is: 

```
network:
 version: 2
 renderer: NetworkManager
 ethernets:
  enp5s0:
   dhcp4: true
  enp6s0:
   dhcp4: true
```

My **/etc/network/interfaces** file is currently empty. 

Any help would be appreciated.

EDIT: When I hover above the Network Manager icon, which is currently displaying the "looking for signal" wireless icon, I get this message. 

[IMG]https://i.imgur.com/X55jVAp.png[/IMG]

After this process cycles, it simply lists netplan-enp5s0 as "disconnected" in the NetworkManager menu.

EDIT 2: As an aside, I tried doing a network bridge using netplan, but that didn't work and I don't believe that's the proper approach for what I'm trying to do?

---

### Post by Cursed Lemon on 2021-05-10
Okay nevermind, I solved my own problem, somehow. Apparently a netplan bridge was the way to go, I was just somehow misconfiguring it this whole time. My netplan config looks like this now:

```
network:
 version: 2
 renderer: NetworkManager
 ethernets:
  enp5s0:
   dhcp4: no
  enp6s0: 
   dhcp4: no
 bridges:
  br0:
   dhcp4: yes
   interfaces: [enp6s0, enp5s0]


```

And my resulting ifconfig: 

```
br0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.111  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::22cf:30ff:fee1:5430  prefixlen 64  scopeid 0x20<link>
        ether 20:cf:30:e1:54:30  txqueuelen 1000  (Ethernet)
        RX packets 6254  bytes 6914523 (6.9 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 4903  bytes 576909 (576.9 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

enp5s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        ether 20:cf:30:e1:54:30  txqueuelen 1000  (Ethernet)
        RX packets 60  bytes 8924 (8.9 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1780  bytes 318409 (318.4 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

enp6s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        ether 20:cf:30:e1:54:93  txqueuelen 1000  (Ethernet)
        RX packets 240274  bytes 293910338 (293.9 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 108436  bytes 10628548 (10.6 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 77769  bytes 7742958 (7.7 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 77769  bytes 7742958 (7.7 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


```

Console is now getting DHCP. I swear I tried exactly this like five times already, but it works now. :P

All the entries in **nm-connection-editor** are now netplan-related: 

[IMG]https://imgur.com/LUlbxIj.png[/IMG]

---

