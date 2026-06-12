---
title: "File transfer faster when monitored with ethstatus"
date: 2007-11-21
forum: Networking &amp; Wireless
---

### Post by wittewim on 2007-11-21
I am running an Ubuntu server 7.10 (Linux xServer01 2.6.22-14-server #1 SMP Sun Oct 14 23:34:23 GMT 2007 i686 GNU/Linux). It has one NIC (eth0).

When i transfer a file from my Windows XP workstation or OS X workstation the transfer speed is very poor (~ 800KB/s). If i open an ssh connection to the server and run "ethstatus eth0" the file transfer speed increases to ~ 30MB/s. So the hardware is working fine i think. It must be some configuration problem.

When i download a file from the server there is no difference in speed when monitored with ethstatus. Transfer speed is always ~30MB/s.

I've tried to change many configuration settings in the smb.conf. None of them seems to make a relevant difference.

I enabled/disabled promiscuous mode on the network card with "ifconfig eth0 promisc" and "ifconfig eth0 -promisc". It makes no difference.

Ethstatus does something with the NIC to increase it's performance. I want it enabled all the time. Leave ethstatus running is not an option :)

[lspci -v]
```
02:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 025c
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
	I/O ports at 9800 [size=256]
	Memory at f3001000 (32-bit, non-prefetchable) [size=256]
	[virtual] Expansion ROM at 70000000 [disabled] [size=128K]
	Capabilities: [dc] Power Management version 2
```

[ifconfig eth0]
```
eth0      Link encap:Ethernet  HWaddr 00:11:09:E9:68:44  
          inet addr:192.168.254.10  Bcast:192.168.254.255  Mask:255.255.255.0
          inet6 addr: fe80::211:9ff:fee9:6844/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:112758749 errors:0 dropped:84 overruns:0 frame:0
          TX packets:106788022 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3380692059 (3.1 GB)  TX bytes:2913750408 (2.7 GB)
          Interrupt:22
```

[ethtool eth0]
```
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 1000Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000033 (51)
	Link detected: yes
```

[netperf -H mythtv] - to my MythTv machine
```
TCP STREAM TEST from 0.0.0.0 (0.0.0.0) port 0 AF_INET to mythtv.wittesaele.grp (192.168.254.50) port 0 AF_INET
Recv   Send    Send                          
Socket Socket  Message  Elapsed              
Size   Size    Size     Time     Throughput  
bytes  bytes   bytes    secs.    10^6bits/sec  

 87380  16384  16384    10.00     625.26
```

[netperf -H xserver01] - from my MythTv to xServer01
```
TCP STREAM TEST from 0.0.0.0 (0.0.0.0) port 0 AF_INET to xserver01.wittesaele.grp (192.168.254.10) port 0 AF_INET
Recv   Send    Send                          
Socket Socket  Message  Elapsed              
Size   Size    Size     Time     Throughput  
bytes  bytes   bytes    secs.    10^6bits/sec  

 87380  16384  16384    10.01     669.21 
```

[smb.conf]
```
[global]
        workgroup = WITTESAELE.GRP
        wins support = true
        domain master = yes
        preferred master = yes
        local master = yes
        os level = 255
        server string = %h server
        security = user
        encrypt passwords = true
        obey pam restrictions = Yes
        passdb backend = tdbsam
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword$
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        panic action = /usr/share/samba/panic-action %d
        printing = cups
        printcap name = cups
        load printers = yes
        lpq command = %p
        lprm command =
        socket options = TCP_NODELAY
```

---

