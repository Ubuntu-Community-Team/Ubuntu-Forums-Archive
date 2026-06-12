---
title: "Ubuntu 18.04 configure netplan with 2 network cards"
date: 2018-12-07
forum: Networking &amp; Wireless
---

### Post by luca-dgh on 2018-12-07
Hi to all.
I'm going to install ubuntu 18.04 on a small "server", not a real server, just a deliverer of multimedia files on demand, for a local network.
I'm recollecting info because I still have not installed 18.04 (I'm still with 16.04 on my system) and I know than 18.04 ships some news like netplan.
Now, my "server" has 2 network cards enp2s0 and eno1.
enp2s0 is connected to a switch with 16 windows pc (windows XP sob...:() obviously using samba, eno1 will be connected to a big server that broadcast internet to the whole building, with a "private" IP range and will be connected to 20 linux pcs (18.04) via VSFTPD. The 20 pcs will be connected via Wi-Fi, but the "server" will have a wired connection.
In both connections the only job of the server is to deliver multimedia files to the pc that requires it. Nothing else.

For enp2s0 I have fixed ip 192.168.1.126/32, gw 192.168.1.99.
For eno1 I'm still waiting for an IP range from the network admin, anyway we can assume something like 192.168.2.xxx .
Now I think I'll use systemd-networkd, instead on NM, because I suppose is faster and lighter, usually NM is so heavy to start at boot that gives me the impression that manages network in the same slow way.
I understand that netplan is  a very good and relatively simple way to configure the network devices, but till now I can't find, over the internet, examples of *netplan.yaml* that configures two lan cards.
So I tried to understand yaml conf file and here is my hypothetical conf file:
```

network:
       version: 2
       renderer: networkd     
       ethernets:
           enp2s0:
               addresses: [192.168.1.126/24]
               gateway4: 192.168.1.99
               nameservers:
               addresses: [200.48.0.38,200.48.0.37]
           eno1:
               addresses: [192.168.2.10/24]

``` 

That will work? With this configuration the "server" will be able to manage at the same time the two cards? Do I need some more settings?

Thx a lot for your help.
..

---

### Post by luca-dgh on 2018-12-09
Nobody? :sad:

---

