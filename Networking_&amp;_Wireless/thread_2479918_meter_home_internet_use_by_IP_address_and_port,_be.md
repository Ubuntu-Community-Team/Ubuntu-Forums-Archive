---
title: "meter home internet use by IP address and port, best tool?"
date: 2022-10-12
forum: Networking &amp; Wireless
---

### Post by mikeho2 on 2022-10-12
Hi, I have a Linux server with LTE modem, and using iptables and NAT to share the internet connection over the home LAN.

Monthly usage is limited, and I'd like to meter daily/hourly bandwidth usage by, at least, local IP address and remote port (so distinguish web use, torrents, streaming, ... ).
So can report which of my gadgets or kids is hogging the bandwidth and gigabytes. 

Better yet, be able to list top bandwidth users by site/server domain, though I suspect that is not so easy these days.

What tools should I look at for this?   Would it be a daemon to log traffic, and another to read the logs and generate a report? Or is there a pretty interactive tool?
I've seen a lot of tools for live network bandwidth monitoring, but getting a bit overwhelmed trying to find the right tool for data metering.

---

### Post by TheFu on 2022-10-13
If it were me, I'd deploy opnsense as the LAN router and use the tools it provides to control bandwidth use in a hotel-like environment.

opnsense isn't linux. It is BSD-based and designed to run on dedicated hardware.  The software has been maintained continuously the last 7+ yrs with fixes and updates every few weeks, unlike most other routers. I run opnsense on a $140 APU2c4 SBC device with a 64-bit AMD CPU from 2015 and expect to get 10 more years from it.  Because it is x86-64 compatible, we can run pfSense, OPNsense, openWRT and any number of other router distros. It supports AMD-v too, so it is possible to run virtual machines to make all sorts of things hardware agnostic and more flexible, though I don't know if VT-d is supported or not. which would be important for security of any router software running inside a VM.  I've been tempted to try it, but never got around to that.  The device doesn't have any GPU, so a console connection is mandatory for installation and configuration. Also, most typical Linux distros don't support consoles by default, so some boot options need to be setup in grub BEFORE booting.  That can be a chicken/egg problem.

Anyway, opnsense in hoteling mode is my suggestion.  I don't know if it is the best or easiest, but it is definitely used all over the world.

---

### Post by Doug S on 2022-10-13
I run a linux server with iptables and NAT and as main router gateway between LAN and WAN. You could add some iptables rules to your FORWARD chain to count packets/bytes by LAN ip addresses (I have not done this, but it should be easy). You could monitor all traffic with tcpdump and post process to split out data however you want. I have been doing this for over a decade, but typically only go back and re-process the packets captures while investigating something.

Example of iptables method:
Currently my FORWARD chain is (extracted from "sudo iptables -xvnL"):

```
Chain FORWARD (policy DROP 6 packets, 302 bytes)
    pkts      bytes target     prot opt in     out     source               destination
       0        0 DROP       udp  --  *      enp1s0  0.0.0.0/0            0.0.0.0/0            udp dpt:137
     474    47608 LOG        all  --  *      enp1s0  0.0.0.0/0            192.168.0.0/16       LOG flags 0 level 6 prefix "F192:"
     474    47608 DROP       all  --  *      enp1s0  0.0.0.0/0            192.168.0.0/16
      60     4800 LOG        all  --  *      enp1s0  0.0.0.0/0            10.0.0.0/8           LOG flags 0 level 6 prefix "F10:"
      60     4800 DROP       all  --  *      enp1s0  0.0.0.0/0            10.0.0.0/8
      10      810 LOG        all  --  *      enp1s0  0.0.0.0/0            172.16.0.0/12        LOG flags 0 level 6 prefix "F172:"
      10      810 DROP       all  --  *      enp1s0  0.0.0.0/0            172.16.0.0/12
       0        0 LOG        all  --  *      enp1s0  0.0.0.0/0            224.0.0.0/4          LOG flags 0 level 6 prefix "F224:"
       0        0 DROP       all  --  *      enp1s0  0.0.0.0/0            224.0.0.0/4
       0        0 LOG        all  --  *      enp1s0  0.0.0.0/0            240.0.0.0/5          LOG flags 0 level 6 prefix "F240:"
       0        0 DROP       all  --  *      enp1s0  0.0.0.0/0            240.0.0.0/5
       2      225 LOG        all  --  *      enp1s0  0.0.0.0/0            169.254.0.0/16       LOG flags 0 level 6 prefix "F169:"
       2      225 DROP       all  --  *      enp1s0  0.0.0.0/0            169.254.0.0/16
   38148  1857977 REJECT     all  --  br0    *       0.0.0.0/0            0.0.0.0/0            state INVALID reject-with icmp-port-unreachable
  125228  6535102 DROP       all  --  br0    enp1s0  192.168.111.101      0.0.0.0/0
141958610 234949440837 ACCEPT     all  --  enp1s0 br0     0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
95521717 19505234955 ACCEPT     all  --  br0    enp1s0  0.0.0.0/0            0.0.0.0/0
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            LOG flags 0 level 6 prefix "FCATCH:"
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0
```

But say I wanted to acquire more information about my main windows computer at 192.168.111.122. I add these 2 iptables rules:

```
sudo iptables -I FORWARD 15 -s 192.168.111.122 -i br0 -o enp1s0 -j ACCEPT
sudo iptables -I FORWARD 15 -d 192.168.111.122 -i enp1s0 -o br0 -m state --state ESTABLISHED,RELATED -j ACCEPT
```

And now have this:

```
Chain FORWARD (policy DROP 6 packets, 302 bytes)
    pkts      bytes target     prot opt in     out     source               destination
       0        0 DROP       udp  --  *      enp1s0  0.0.0.0/0            0.0.0.0/0            udp dpt:137
     474    47608 LOG        all  --  *      enp1s0  0.0.0.0/0            192.168.0.0/16       LOG flags 0 level 6 prefix "F192:"
     474    47608 DROP       all  --  *      enp1s0  0.0.0.0/0            192.168.0.0/16
      60     4800 LOG        all  --  *      enp1s0  0.0.0.0/0            10.0.0.0/8           LOG flags 0 level 6 prefix "F10:"
      60     4800 DROP       all  --  *      enp1s0  0.0.0.0/0            10.0.0.0/8
      10      810 LOG        all  --  *      enp1s0  0.0.0.0/0            172.16.0.0/12        LOG flags 0 level 6 prefix "F172:"
      10      810 DROP       all  --  *      enp1s0  0.0.0.0/0            172.16.0.0/12
       0        0 LOG        all  --  *      enp1s0  0.0.0.0/0            224.0.0.0/4          LOG flags 0 level 6 prefix "F224:"
       0        0 DROP       all  --  *      enp1s0  0.0.0.0/0            224.0.0.0/4
       0        0 LOG        all  --  *      enp1s0  0.0.0.0/0            240.0.0.0/5          LOG flags 0 level 6 prefix "F240:"
       0        0 DROP       all  --  *      enp1s0  0.0.0.0/0            240.0.0.0/5
       2      225 LOG        all  --  *      enp1s0  0.0.0.0/0            169.254.0.0/16       LOG flags 0 level 6 prefix "F169:"
       2      225 DROP       all  --  *      enp1s0  0.0.0.0/0            169.254.0.0/16
   38171  1859576 REJECT     all  --  br0    *       0.0.0.0/0            0.0.0.0/0            state INVALID reject-with icmp-port-unreachable
[COLOR="#FF0000"]      66    18660 ACCEPT     all  --  enp1s0 br0     0.0.0.0/0            192.168.111.122      state RELATED,ESTABLISHED
     192    63904 ACCEPT     all  --  br0    enp1s0  192.168.111.122      0.0.0.0/0[/COLOR]
  125228  6535102 DROP       all  --  br0    enp1s0  192.168.111.101      0.0.0.0/0
141964212 234954601348 ACCEPT     all  --  enp1s0 br0     0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
95526529 19506658298 ACCEPT     all  --  br0    enp1s0  0.0.0.0/0            0.0.0.0/0
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            LOG flags 0 level 6 prefix "FCATCH:"
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0
```

---

