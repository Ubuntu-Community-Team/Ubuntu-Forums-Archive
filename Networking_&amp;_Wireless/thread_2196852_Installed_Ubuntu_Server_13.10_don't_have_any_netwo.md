---
title: "Installed Ubuntu Server 13.10 don't have any network connection at all"
date: 2013-12-31
forum: Networking &amp; Wireless
---

### Post by tomasdepriede on 2013-12-31
Hey Guys, 

 I spend the last two days trying to fix this issue by myself using the info that is in this forum but I didn't have success. 
Let me explain my situation. 

Just installed a fresh ubuntu server 13.10 in a machine with a Realtek Semiconductor RTL-8139 Ethernet card, that had internet in the installation, lost all the internet connectivity after being installed.

My router is on 192.168.4.1
I have a MacBook Pro that is using dhcp (like any other device here) in 192.168.4.203
My ubuntu server gets the 192.168.2.3 by dhcp why??? The ubuntu is getting internet by a wired connection to my MBP using internet sharing. That was working with the previous Windows installed in that machine. But now is failing. If I do a direct connection from the ubuntu to the router the ip is 192.168.4.20X but I still have no internet at all. 

Please let me know what can I do. I also tried setting a static ip, but cannot ping the router.

Thanks!

---

### Post by monkeybrain20122 on 2013-12-31
Ubuntu 13.04 will reach end of life the end of january, not a good time to install it now.

---

### Post by tomasdepriede on 2013-12-31
Sorry, my bad. The version installed is the 13.10

---

### Post by Iowan on 2013-12-31
The MacBook may be issuing the 192.168.2.X address.
When connected to router with DHCP address, can you ping the router?
How about pinging internet by IP address?

---

### Post by tomasdepriede on 2013-12-31
Thanks for the answer. Last time I tested I couldn't ping the router. 
But about pinging the internet, you say something like ping OpenDNS servers?

---

### Post by Iowan on 2013-12-31
If you can't ping the router, you won't be able to reach the Internet.
(But yes, 8.8.8.8, etc.)
Can you verify that **route -n** shows the router as the gateway (when connectedto it)
It may show the MBP when connected to it.

---

### Post by praseodym on 2014-01-01
Please show the following outputs:
```

lspci -nnk | grep -iA2 net
ifconfig -a
cat /etc/network/interfaces
cat /etc/resolv.conf
route -n
```
Is there a GUI installed or do you want to configure manually? Static IPs?

---

### Post by tomasdepriede on 2014-01-01
Hi Praseodym. Thanks for your answer and Happy new year!

There is no GUI installed and I prefer to do it manually because my ATI Radeon XPress 200 is not a good ally of Ubuntu GUI.
 I always had issues with that graphic card and linux.
I will prefer a configuration with static ips for that server. But for now is the same. I want network there first [IMG]http://ubuntuforums.org/webkit-fake-url://23D27F99-552B-4436-A06E-D97159BE6C15/icon_smile.gif[/IMG]

Currenty it is configured a static IP but maybe is something wrong:
Here is the output of those commands connected to the MBP But if you also need, I can connect to the router and do the same output: 
cat /etc/network/interfaces
```

# The loopback network interface. I disabled this one.
#auto lo 
#iface lo inet loopback 

# The primary network interface 
auto eth0
iface eth0 inet static
address 192.168.4.101   (My mac ip is 192.168.4.203)
netmask 255.255.255.0
gateway 192.168.4.1
broadcast 192.168.4.255
dns-nameservers 208.67.222.222 208.67.220.220
hwaddress 04:06:FF:AA:22:33

```

cat /etc/resolv.conf
```

nameserver 208.67.222.222
nameserver 208.67.220.220

```
route -n
```

Kernel IP routing table
Destination     Gateway          Genmask          Flags     Metric     Ref    Use    Iface
0.0.0.0           192.168.4.1     0.0.0.0             UG         0           0         0      eht0
192.168.4.0     0.0.0.0           255.255.255.0  U           0           0         0      eht0

```
ifconfig -a
```

eth0   Link encamp:Ethernet HWaddr 04:06:ff:aa22:33
        inet addr:192.168.4.101 Bcast:192.168.4.255 Mask:255.255.255.0
        UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
        RX packets:2 errors:0 dropped:0 overruns:0 frame:0
        TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueueln:1000
        RX Bytes:684 (684.0 B) TX bytes:600 (600.0 B)]

lo     Link encamp:Local Loopback
        inet addr:127.0.0.1 Mask:255.0.0.0
        UP LOOBACK RUNNING MTU:65536 Metric:1
        RX packets:48 errors:0 dropped:0 overruns:0 frame:0
        TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueueln:0
        RX Bytes:4336 (4.3 KB) TX bytes:4336 (4.3 KB)

```

lspci -nnk | grep -iA2 net
```

02:02.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
        Subsystem: Intel Corporation Device [8086:d601]
        Kernel driver in use: 8139too

```

Thanks!

---

### Post by praseodym on 2014-01-01
This device is known to load two drivers: 8130too (right one) amd 8139cp (wrong one). Blacklist the wrong one and un-uncomment both "lo" lines in the "interfaces"!!! Reboot after that

---

### Post by tomasdepriede on 2014-01-01
I will search it about how to blacklist the wrong one. And uncomment the "lo" lines. Will post after that. 
Thanks you!

---

### Post by praseodym on 2014-01-01
```
echo "blacklist 8139cp" | sudo tee /etc/modprobe.d/blacklist-8139cp.conf
```
does the trick

---

### Post by tomasdepriede on 2014-01-01
[FONT=verdana, arial, sans-serif][COLOR=#000000]Sorry just see your post. I will try it[/COLOR][/FONT]

---

### Post by tomasdepriede on 2014-01-01
Ok I connected my machine to the router. No success.
Used your command to blacklist. Reboot. No success. 
I checked with lsmod and still can see the two drivers. 

Also I tested the following:
[COLOR=#000000][FONT=Consolas]rmmod 8139cp[/FONT][/COLOR]
[COLOR=#000000][FONT=Consolas]rmmod 8139too[/FONT][/COLOR]
[COLOR=#000000][FONT=Consolas]rmmod mii[/FONT][/COLOR]
[COLOR=#000000][FONT=Consolas]modprobe 8139too[/FONT][/COLOR]
[COLOR=#000000][FONT=Consolas]modprobe mii[/FONT][/COLOR]
[COLOR=#000000][FONT=Consolas]service networking restart
no success.

[/FONT][/COLOR]The ping to the router still have all the packet loss. 
Thanks!

---

### Post by praseodym on 2014-01-01
Add the router IP as a nameserver in the "interfaces" and the "resolv.conf"

---

### Post by tomasdepriede on 2014-01-01
Still no success :-(

Added to the dns-nameservers in the interfaces. Restarted network services. Checked in the resolv.conf that the router is there. Rebooted ubuntu. And when pinging the router still has Destination Host Unreachable.

Thanks for your help!

---

### Post by praseodym on 2014-01-01
Router-reset?

---

### Post by tomasdepriede on 2014-01-01
Just rebooted ubuntu and reset'ed the router. No success.

---

### Post by praseodym on 2014-01-01
Lets see:
```

ifconfig -a
cat /etc/udev/rules.d/70-persistent-net.rules
cat /etc/resolv.conf
cat /etc/network/interfaces
route -n
dmesg | grep 8139
```

---

