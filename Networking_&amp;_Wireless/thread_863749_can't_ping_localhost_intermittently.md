---
title: "can't ping localhost intermittently"
date: 2008-07-18
forum: Networking &amp; Wireless
---

### Post by myst123 on 2008-07-18
Hi All,

I'm having a weird problem with my wired network connection after upgrading to Hardy...

Randomly it seems to just die, to the point that I cannot connect to anything, ping anything on my local network, can't even ping localhost.

Tried unloading and reloading the forcedeth module, looked at iptables, syslog, ifconfig, everything to no avail.

Only a reboot will fix it.

```

$ lspci | grep -i ethernet
00:05.0 Bridge: nVidia Corporation CK8S Ethernet Controller (rev a2)

$ sudo ethtool eth0
Settings for eth0:
	Supported ports: [ MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 1
	Transceiver: external
	Auto-negotiation: on
	Supports Wake-on: g
	Wake-on: d
	Link detected: yes

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0f:ea:37:4d:06  
          inet addr:192.168.0.123  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:eaff:fe37:4d06/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:214664 errors:0 dropped:0 overruns:0 frame:0
          TX packets:170559 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:203423501 (193.9 MB)  TX bytes:14159916 (13.5 MB)
          Interrupt:16 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1886 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1886 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:97042 (94.7 KB)  TX bytes:97042 (94.7 KB)


$ ping 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted

--- 127.0.0.1 ping statistics ---
2 packets transmitted, 0 received, 100% packet loss, time 1008ms


$ sudo ping 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted

--- 127.0.0.1 ping statistics ---
2 packets transmitted, 0 received, 100% packet loss, time 1008ms

```

Any ideas?? driving me nuts.

Thanks

---

