---
title: "Problem with configuration to routing between 3 different network."
date: 2016-11-24
forum: Networking &amp; Wireless
---

### Post by aristotele on 2016-11-24
[COLOR=#555555][FONT=&amp]Hello everyone[/FONT][/COLOR]

[COLOR=#555555][FONT=&amp]I have a little problem in the operation of a linux box as a router. I basically 3 different networks:  192.168.2, 165.52.81.0 and 10.10.10.0. Each network is connected to a switch and all 3 converge in a linux machine that should farw by routing to direct requests from one network to another and vice versa. Set routing rules are that if you are prompted for the network : 192.168.2 0 goes to eth0; If you are prompted for the network 165.52.81.0 goes to eth1 and if you are prompted for the network 10.10.10.0 goes towards eth3. I have also enabled the ip_forwarding setting it to 1 in sysctl. conf file. In this way I can from all 3 networks to see networked devices but I can ping only of course towards linux machine from all 3 networks and from rwte eth0 (192.168.2.0) towards eth3 or 10.10.10.10 but not vice versa. I assigned to all network adapters on the linux machine IP Static, eth0 IP  : 192.168.1.1 with gateway 192.168.1.254; eth1 IP are 192.168.2.1, eth2 IP has 165.52.81.1 and eth3 :10.10.10.1 IP .  on the network adapters of the PCs connected to the switch IP addresses in the range are obviously of the network where they are. The 3 networks communicate with each other using Ip addresses, but if I use the computer names not. Probably configuration of DNS? Give me a hand? Please

Thank You.[/FONT][/COLOR]

---

