---
title: "Automatic connected to unknown tap/tun device, every day"
date: 2016-09-09
forum: Networking &amp; Wireless
---

### Post by briancloughley on 2016-09-09
Hi

After every restart I am automatically connected to an unknown network. It's apparently a tun or tap device according to nmcli and if config. It changes my ip address to somewhere in a different city (according to dns test websites). It's always the same ip address. It happens whether I attempt to connect to the internet wired or wirelessly. It always shows up Network Manager as 'unknown'. I can't connect to a VPS through it, so I have to disconnect from the unknown network using Network Manager whenever I want to use one. In fact I disconnect from this network every time I use it because I don't know what it is. What can this weird network thing be? Why am I being automatically routed to another city? Is this a security/hacking issue? Here is the relevant network on nmcli and ifconfig


```
tap0                          9ac922ff-2e20-41b9-adf4-d17ef3633c1d  tun              tap0
```

```
tap0      Link encap:Ethernet  HWaddr 92:58:2a:d1:3c:ed            inet addr:193.180.119.144  Bcast:193.180.119.191  Mask:255.255.255.192
          inet6 addr: fe80::9058:2aff:fed1:3ced/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3518 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3382 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:2057494 (2.0 MB)  TX bytes:454233 (454.2 KB)



```

---

### Post by reese1379 on 2016-09-16
[COLOR=#555555][FONT=monospace]# 
# [TUN/TAP]("https://www.kernel.org/doc/Documentation/networking/tuntap.txt") provides packet reception and transmission for user space programs ..
#
# try ..
#
sudo [COLOR=#333333][FONT=Verdana]ifconfig tap0 down
[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]sudo tunctl -d tap0
sudo ifconfig eth0 down
sudo dhclient eth0

# eth0 has been renamed enp0s7 on my system, maybe the same for yours.[/FONT][/COLOR]
#
# if it reappears then some user application is recreating it.[/FONT][/COLOR]

---

