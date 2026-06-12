---
title: "Ingress redirect to ifb not working ubuntu 14.04."
date: 2016-08-25
forum: Networking &amp; Wireless
---

### Post by stuartjk1606 on 2016-08-25
I have a slightly more compex network setup at home than usual but still quite a simple one but after recent purchases of a couple of Xbox Ones, the entire household is struggling to share my 3mb downlink. My current setup is...

Broadband modem (192.168.1.254) downlink ~3.2mbps uplink 799kpbs
|-TP-Link Downstairs switch and wifi AP (192.168.1.252)
| |-Ubuntu server 14.04 dnsserver and default gateway (192.168.1.250 eth2) for selected machines routing traffic to 192.168.1.254 through secondary NIC 192.168.1.249 (eth0)
|-TP-Link Upstairs switch and wifi AP (192.168.1.251)

*.250 is running dnsmasq which routes all traffic from household game consoles, smart tvs and physical PCs through itself as the client default gateway, and all others to *.254.
*.254 is the default gateway for all other machines (mobile devices, EXSi host and guests) as well as 192.168.1.249.
*.250 does not have a default gateway set

path of heavy users:

    [xbox]-[*.250-dnsserver-*.249]-[*.254-router-WAN]

path of light users:

    [phone]-[*.254-router-WAN]

My aim is to limit traffic for heavy users to 2.5mbps down 512 up so allowing light users to use what is left to share between them, I can then easily tweak the limit on heavy users without affecting others too much. This also means that light uses have access to the lot if no heavy users are running.

I have it set this way because *.254 has no Qos capabilities and the ISP does not play well with consumer routers whereas Ubuntu allows me to split traffic out easily so my only concern now is limiting.

I have limited the upstream traffic on 192.168.1.249 so the network hungry machines do not saturate my uplink successfully with:
```
tc qdisc add dev eth0 root tbf rate 512kbit latency 50ms burst 1540
```

My problem is coming when I try to limit the downlink.

I have tried setting a rate on the egress traffic of *.250 this appeared to do nothing.
```
tc qdisc add dev eth2 root tbf rate 512kbit latency 50ms burst 1540
```

I have also set up an ifb redirect on *.249
 ```
modprobe ifb numifbs=1
ip link set dev ifb0 up
```

Then setting ingress traffic on eth0 to redirect through ifb0
```
tc qdisc add dev eth0 ingress handle ffff:
tc filter add dev eth0 parent ffff: protocol ip u32 match u32 0 0 action mirred egress redirect dev ifb0
```

output from tc qdisc: (eth1 is an internal only management network so can be ignored)
```
qdisc tbf 8002: dev eth0 root refcnt 2 rate 512000bit burst 1539b lat 50.0ms
qdisc ingress ffff: dev eth0 parent ffff:fff1 ----------------
qdisc pfifo_fast 0: dev eth1 root refcnt 2 bands 3 priomap  1 2 2 2 1 2 0 0 1 1 1 1 1 1 1 1
qdisc tbf 8004: dev eth2 root refcnt 2 rate 512000bit burst 1539b lat 50.0ms
qdisc tbf 8001: dev ifb0 root refcnt 2 rate 512000bit burst 1539b lat 50.0ms
```

output from tc filter show dev eth0 parent ffff:
```
filter protocol ip pref 49152 u32
filter protocol ip pref 49152 u32 fh 800: ht divisor 1
filter protocol ip pref 49152 u32 fh 800::800 order 2048 key ht 800 bkt 0 terminal flowid ???
   match 00000000/00000000 at 0
        action order 1: mirred (Egress Redirect to device ifb0) stolen
        index 1 ref 1 bind 1
```

However the filter does not seem to be matching.

I have set to 512kbit on both sides so I can see the limiting in action however nothing seems to be working.

As visible from the show filter, nothing is being matched in the filter, so nothing is passing to ifb0. Doing a tracert on a windows box going through dnsserver does show it is taking the planned route.
```
1    <1 ms    <1 ms    <1 ms  UNKNOWN [192.168.1.249]
2     1 ms    <1 ms    <1 ms  *** [192.168.1.254]
3   ...
```

I have a general understanding of what these commands are doing but reading up on tc is like knitting fog so I copied these from other peoples solutions online.

I have tried wondershaper but it seems to cause problems with uplink and also does not seem to do anything specific on downlink exibiting similar behaviour to my own manual solution.

I am more than willing to route everything through dnsserver and use virtual interfaces to split the traffic there but until I can control the traffic I am not going to delve any further.

Anyway, does anyone have any ideas why either egress on eth2 or ingress redirect on eth0 is not working and how can I accomplish this?

I have tried every "quick win" solution I can find and nothing seems to work. I am after overall reduction in throughput on all avaialble traffic so nothing too complex, just a bit annoyed it is getting nowhere.

My initial thought is because all machines are on the same subnet. Could it be I need to have eth0 on dnsserver and the router on a seperate subnet? Not ideal as I would then need to move port forwarding to dnsserver which I don't want to risk. Alternatively is there something else I am missing?

A bit more info:

output from ip route on dnsserver:
```
default via 192.168.1.254 dev eth0
192.168.0.0/24 dev eth1  proto kernel  scope link  src 192.168.0.250
192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.249
192.168.1.0/24 dev eth2  proto kernel  scope link  src 192.168.1.250
```

I have also tried limiting ingress traffic directly with:
```
tc filter add dev eth0 parent ffff: protocol ip u32 match ip src 0.0.0.0/0 flowid :1 police rate 512kbit mtu 10000 burst 10k drop
```

with no success but once again this may be because the filter is not getting hit.

---

