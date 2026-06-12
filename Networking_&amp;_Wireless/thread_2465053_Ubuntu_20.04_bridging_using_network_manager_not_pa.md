---
title: "Ubuntu 20.04 bridging using network manager not passing traffic."
date: 2021-07-20
forum: Networking &amp; Wireless
---

### Post by keith-goodwin on 2021-07-20
I have acquired a couple of 10Gb sfp+ network cards and I am trying to connect 2 servers together using them, but I don't have a 10Gb sfp+ switch so figured I would try bridging them as I have a server running on my home network that is configured to connect to my router using a standard 1Gb ethernet connection through a switch, which works correctly.

There are a lot of tutorials available and I have followed them multiple times, without any success. I have used both nmcli and nm-connection-editor and both work to configure either a simple ethernet connection or a bond on either server. The problems only start when trying to get a bridge working.

Server 1 is running Ubuntu 20.04 desktop and is connected to my router through a 1Gb switch via the 1Gb ethernet and connects to other machines and the internet without any problem. It also has a dual sfp+ addon 10Gb network card.
Server 2 is also running Ubuntu 20.04 desktop and has a dual port sfp+ 10Gb network card which I wish to connect to server 1 so that it may connect to other machines and the internet through server 1.

I have tested the cards and sfp+ cable and verified they work by creating a static 10.0.0.* subnet between them and been able to ping and send files in both directions between the 2 servers, while server 1 has remained connected to my network and been able to use the internet.

IP addresses statically assigned from 192.168.8.* subnet. Router/dns is 192.168.8.1. server 1 ethernet eno1 is 192.168.8.111/24 and bridge0 is 192.168.8.112/24. Bridge0 responds to ping from any machine on the network except server 2. Server 2 is 192.168.8.121/24 and responds to ping from itself, but not server 1. It doesn't make any difference whether I set the connection on server 2 as ethernet or bridge.

output from various nmcli and ip commands on server 1
```
$ nmcli con show
NAME             UUID                                  TYPE      DEVICE   
eno1             42c95607-1ba5-47b0-b88f-1d406dd71ff4  ethernet  eno1    
bridge0          7700d504-048b-4beb-9f60-38dd78b6975f  bridge    bridge0  
bridge0-slave-1  8c0e6362-5e80-4483-a775-f359739b97f3  ethernet  enp6s0f0 

$ nmcli dev
DEVICE    TYPE      STATE         CONNECTION      
bridge0   bridge    connected     bridge0         
eno1      ethernet  connected     eno1              
enp6s0f0  ethernet  connected     bridge0-slave-1 
enp6s0f1  ethernet  disconnected  --              
lo        loopback  unmanaged     --

$ ip a s bridge0
15: bridge0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether 00:0e:1e:9c:5a:60 brd ff:ff:ff:ff:ff:ff
    inet 192.168.8.112/24 brd 192.168.8.255 scope global noprefixroute bridge0
       valid_lft forever preferred_lft forever

$ ip r
default via 192.168.8.1 dev eno1 proto static metric 300 
default via 192.168.8.1 dev bridge0 proto static metric 20425 
169.254.0.0/16 dev eno1 scope link metric 1000 
192.168.8.0/24 dev eno1 proto kernel scope link src 192.168.8.111 metric 300 
192.168.8.0/24 dev bridge0 proto kernel scope link src 192.168.8.112 metric 425

```

Output from the same commands on server 2
```
$ nmcli con show
NAME             UUID                                  TYPE      DEVICE     
bridge0          8b14746c-2221-4c29-86ab-39e350308cfd  bridge    bridge0  
bridge0-slave-1  02854344-e5cb-4454-a03c-0819f524ccce  ethernet  enp6s0f0

$ nmcli dev
DEVICE    TYPE      STATE         CONNECTION      
bridge0   bridge    connected     bridge0        
enp5s0f0  ethernet  connected     bridge0-slave-1
enp5s0f1  ethernet  disconnected  --           
eno1      ethernet  unavailable   --
lo        loopback  unmanaged     --

$ ip a s bridge0
9: bridge0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether 00:0e:1e:9c:3d:40 brd ff:ff:ff:ff:ff:ff
    inet 192.168.8.121/24 brd 192.168.8.255 scope global noprefixroute bridge0
       valid_lft forever preferred_lft forever

$ ip r
default via 192.168.8.1 dev bridge0 proto static metric 20425
169.254.0.0/16 dev eno1 scope link metric 1000
192.168.8.0/24 dev bridge0 proto kernel scope link src 192.168.8.121 metric 425

```

Any help would be gratefully received.

---

### Post by keith-goodwin on 2021-07-20
Solution to my problem was simple when I found it, but is not included in any of the many tutorials that google throws up.
I simply added my main and secondary interfaces to the bridge, not just the secondary.
The second server just needed a simple ethernet profile, not a bridge of it's own.

---

