---
title: "Unable to ping myself or get pinged from other boxes"
date: 2007-05-08
forum: Networking &amp; Wireless
---

### Post by marx2k on 2007-05-08
On my private net, I have one box (the one that I am typing on) which is unable to ping itself and doesnt send ping replies to other boxes.

From this box I am able to ping any of my other  boxes and am able to ping any external IP such as google or Yahoo.

It is a feisty box but was having the same issue as an Edgy box.

Firestarter is running but the same issue occurs when it is not.

ping 127.0.0.1 produces no results.
trying to ping this box (192.168.11.4) from another box on the network gets no results
pinging the router @ 192.168.11.1 gets results
ping another box on the network (192.168.11.7) gets results

I am able to SSH into this box, I am able to connect to this box with any other services but get no ping replies.
The only other thing I am unable to do is connect to this box via SAMBA or SMBTREE

```

        \\COMMODORE-64                  Commodore-64 server (Samba, Ubuntu)
cli_start_connection: failed to connect to COMMODORE-64<20> (0.0.0.0)

```

But I think that is a seperate issue.  

Can anyone suggest where to even begin?

---

### Post by .rdg on 2007-05-08
Hi,

  as usual for me - try typing in the console the following (after Firestarter is disabled):

sudo iptables -L

  it should print out the following:

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 

meaning you are not firewalling anything (accepting all connections). If so - then I'll have to digg further where could icmp (ping) be filtered (wrapper perhaps?).

Regards,
.rdg

---

### Post by marx2k on 2007-05-08
```

marx2k@Commodore-64:/etc/init.d$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
marx2k@Commodore-64:/etc/init.d$ ping 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.

--- 127.0.0.1 ping statistics ---
336 packets transmitted, 0 received, 100% packet loss, time 336294ms

```

Yeah, Im not sure what is going on here. 

Is this any help?

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.11.0    *               255.255.255.0   U     0      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         192.168.11.1    0.0.0.0         UG    0      0        0 eth1

```

```

eth1      Link encap:Ethernet  HWaddr 00:40:CA:70:19:A6  
          inet addr:192.168.11.4  Bcast:192.168.11.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1512348 errors:0 dropped:0 overruns:56 frame:0
          TX packets:979520 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1580733485 (1.4 GiB)  TX bytes:134572101 (128.3 MiB)
          Interrupt:17 Base address:0x8000 

```

---

### Post by .rdg on 2007-05-09
The routing table is no help - there won't be any route to 127.0.0.1/32 as it is a local address.

Could you show the entire code fo ifconfig? Also have a look at /etc/network/interfaces - the lo (local loopback) interface should be set to be up automatically. It should be set as:

```

auto lo
iface lo inet loopback

```

Regards,
.rdg

---

### Post by marx2k on 2007-05-14
```

marx2k@Commodore-64:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:40:CA:70:19:A6  
          inet addr:192.168.11.4  Bcast:192.168.11.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:76585691 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64624908 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1246507767 (1.1 GiB)  TX bytes:1263234086 (1.1 GiB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11336 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11336 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:874108 (853.6 KiB)  TX bytes:874108 (853.6 KiB)

```

And interfaces is: 
```

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

```

---

