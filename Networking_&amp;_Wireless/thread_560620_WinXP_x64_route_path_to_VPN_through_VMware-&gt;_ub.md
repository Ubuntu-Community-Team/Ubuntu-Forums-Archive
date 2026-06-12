---
title: "WinXP x64 route path to VPN through VMware-&gt; ubu server"
date: 2007-09-26
forum: Networking &amp; Wireless
---

### Post by LandRover on 2007-09-26
Hey,

This one is a little complicated and I've been cracking my head over it for a while. Right about now I'm crying out for help.

This is the deal, I got cisco vpn to connect to the office but unfortunately I got XP x64 and cisco cant seem to provide a proper client for x64 OS' so far.   I don't want to reinstall my computer therefore I found a creative solution.

I decided to install VMware server(which is free now! woohoo) and setup up a light weight ubu-server to run 'VPNC' client to connect to the VPN. So far, so good. 
It kinda works, I can access the VPN from the VMware guest hosted ubu, I can ping the local VPN addresses.

The main idea of this solution is to keep the VMware host with the guest ubu minimized, connected to the VPN permanently and route all the traffic from the VPN directly to the host machine.

_**The VMware GUEST (ubu-server) set with 2 NiCs:**_ [list][*] VMnet0 - Bridged connection 
[list]
[*] IP: 10.0.0.13 / 255.0.0.0
[*] Gateway: 10.0.0.138
[/list]
[*] VMnet1 - Host only
[list]
[*] IP: 192.168.0.2 / 255.255.255.0
[*] Gateway: - [/list]

[*] VPN TUNNEL-00
[list]
[*] IP: 172.21.32.39 / 255.255.255.255 (auto assigned by the CISCO PIX)
[*] Gateway: - [/list][/list]

_**The VMware HOST (Winxp x64) network settings:**_ 
[list][*] Local Area Connection #1 [list]
[*] IP: 10.0.0.1 / 255.0.0.0
[*] Gateway: 10.0.0.138[/list]
[*] VMnet1 - Host only
[list]
[*] IP: 192.168.0.1 / 255.255.255.0
[*] Gateway: -[/list][/list]

The IP I'm trying to access over the VPN is: **172.31.110.244**.
From the GUEST machine it works at this point.

On the XP I did a route command to flow all the related traffic through the guest's ip.
[list][*] route add 172.31.0.0 MASK 255.255.0.0 10.0.0.13 METRIC 1
[*] route add 172.31.0.0 MASK 255.255.0.0 192.168.0.2 METRIC 1[/list]

Tried these two one by one but it didn't come up well.
ping timed out and tracert failed to complete a single hop.

I decided to try bridging the interfaces on the guest, between the gateway associated and the host only. 
The script I used to bridge with: ```
    brctl addbr br0;
    brctl stp br0 on;
    brctl addif br0 eth0;
    brctl addif br0 eth1;
    (ifdown eth0 1>/dev/null 2>&1;);
    (ifdown eth1 1>/dev/null 2>&1;);
    ifconfig eth0 0.0.0.0 up;
    ifconfig eth1 0.0.0.0 up;
    ifconfig br0 10.0.0.50 broadcast 10.255.255.255 netmask 255.0.0.0 up
    route add default gw 10.0.0.138;
    for file in br0 eth0 eth1;
    do
      echo "1" > /proc/sys/net/ipv4/conf/${file}/proxy_arp;
      echo "1" > /proc/sys/net/ipv4/conf/${file}/forwarding;
    done;
    echo "1" > /proc/sys/net/ipv4/ip_forward;
```

The br0 interface ip I got: **10.0.0.50**.
I've also added some iptables rules to monitor the logs and accept forwarding:
```
iptables -P FORWARD ACCEPT
iptables -F FORWARD
iptables -I FORWARD -j ACCEPT
iptables -I FORWARD -j LOG
```

I've also updated the route command at the XP to this following:
[list][*] route add 172.31.0.0 MASK 255.255.0.0 10.0.0.50 METRIC 1[/list]

at this point it looked much better, I tried to ping the destination ip on the host ip and could see the trace log of the iptables which means the traffic from the host goes trough the guest.

also the tracert made a single hop:```
C:\>tracert 172.31.110.244
Tracing route to 172.31.110.244 over a maximum of 30 hops

  1    <1 ms    <1 ms    <1 ms  10.0.0.50
  2     *        *        *     Request timed out.
  .....
  30    *        *        *     Request timed out.
```

syslog at the same point of the trace on the guest machine: ```
Sep 26 23:57:11 ubu-vpnc kernel: IN=br0 OUT=tun0 PHYSIN=eth0 SRC=10.0.0.1 DST=172.31.110.244 LEN=78 TOS=0x00 PREC=0x00 TTL=127 ID=16734 PROTO=UDP SPT=137 DPT=137 LEN=58
Sep 26 23:57:12 ubu-vpnc kernel: IN=br0 OUT=tun0 PHYSIN=eth0 SRC=10.0.0.1 DST=172.31.110.244 LEN=78 TOS=0x00 PREC=0x00 TTL=127 ID=16735 PROTO=UDP SPT=137 DPT=137 LEN=58
Sep 26 23:57:14 ubu-vpnc kernel: IN=br0 OUT=tun0 PHYSIN=eth0 SRC=10.0.0.1 DST=172.31.110.244 LEN=78 TOS=0x00 PREC=0x00 TTL=127 ID=16736 PROTO=UDP SPT=137 DPT=137 LEN=58
Sep 26 23:57:23 ubu-vpnc kernel: IN=br0 OUT=tun0 PHYSIN=eth0 SRC=10.0.0.1 DST=172.31.110.244 LEN=78 TOS=0x00 PREC=0x00 TTL=127 ID=16746 PROTO=UDP SPT=137 DPT=137 LEN=58
Sep 26 23:57:24 ubu-vpnc kernel: IN=br0 OUT=tun0 PHYSIN=eth0 SRC=10.0.0.1 DST=172.31.110.244 LEN=78 TOS=0x00 PREC=0x00 TTL=127 ID=16747 PROTO=UDP SPT=137 DPT=137 LEN=58
Sep 26 23:57:26 ubu-vpnc kernel: IN=br0 OUT=tun0 PHYSIN=eth0 SRC=10.0.0.1 DST=172.31.110.244 LEN=78 TOS=0x00 PREC=0x00 TTL=127 ID=16748 PROTO=UDP SPT=137 DPT=137 LEN=58
```

Sigh! At this point, I don't have any more ideas how to fix the routes to make it work properly.
Any ideas are welcome (not ideas to drop the solution but how to make the route thing work, I also would like to learn from this something :) )

Regards,
Oleg G.

[landroverz.com]("http://landroverz.com/")

---

### Post by LandRover on 2007-09-28
Yey! I've solved it.
took a while.. but its a working gateway for a cisco vpn via x64 xp!

```
C:\>tracert 172.31.110.244

Tracing route to APP-SAFE [172.31.110.244]
over a maximum of 30 hops:

  1    <1 ms    <1 ms    <1 ms  192.168.2.2
  2    50 ms    53 ms    55 ms  APP-SAFE [172.31.110.244]

Trace complete.
```

If anyone comes across something like this in the future the light could be found here: [http://tldp.org/HOWTO/IP-Masquerade-HOWTO/](http://tldp.org/HOWTO/IP-Masquerade-HOWTO/)

google4life :)

---

