---
title: "Can't get my laptop and desktop to communicate"
date: 2005-11-25
forum: Networking &amp; Wireless
---

### Post by inha on 2005-11-25
Hello all. 

I've got my desktop connected to the internet via dhcp using eth0 and I've got an ethernet card at eth2 and it's connected to my laptops eth0 via a crossover cable. I gave eth2 a static ip and a subnet mask , another ip for my laptop's eth 0 and the desktop's static ip as it's gateway. 

But something seems to be missing from my equation because the laptop and the desktop can't communicate with eachother.  

I tried to use firestarter to manage the connection between the machines but that doesn't seem to work either. If I set at my desktop's firestarter that eth0 is the internet conn and eth2 the local conn, enable conn sharing and enable dhcp for the local server the firewall won't even start.

Where should I start in finding the problem (and what extra info do you guys need)?

---

### Post by xristos on 2005-11-25
In the desktop computer you must enable port forwarding .
What OS does the desktop have ?

---

### Post by mips on 2005-11-26
For both machines:

Lets see your **/etc/network/interfaces** file
Lets see output of **ifconfig -a** command
Lets see output of **mii-diag** command
Lets see output of **mii-tool** command
Lets see output of **route -n** command

---

### Post by inha on 2005-11-26
Both are running ubuntu.

Desktop:

interfaces

```
# The primary network interface
iface eth0 inet dhcp

iface eth2 inet static
address 192.168.1.1
netmask 255.255.255.0

auto eth2

auto eth0

```

ifconfig -a 

```
eth0      Link encap:Ethernet  HWaddr 00:07:E9:AE:06:3A
          inet addr:193.229.102.227  Bcast:193.229.103.255  Mask:255.255.252.0
          inet6 addr: fe80::207:e9ff:feae:63a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2057627 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2866593 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:315732832 (301.1 MiB)  TX bytes:3500259494 (3.2 GiB)

eth2      Link encap:Ethernet  HWaddr 00:50:BF:A5:6A:E8
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:bfff:fea5:6ae8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2591 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:156324 (152.6 KiB)  TX bytes:2174 (2.1 KiB)
          Interrupt:21 Base address:0xde00

```


mii-diag gives an error 

```

Using the default interface 'eth0'.
SIOCGMIIPHY on eth0 failed: Operation not supported

```

mii-tool gives the same for a bunch of ethn.

route -n

```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth2
193.229.100.0   0.0.0.0         255.255.252.0   U     0      0        0 eth0
0.0.0.0         193.229.100.1   0.0.0.0         UG    0      0        0 eth0

```

I'll post the laptop's outputs in a while from it to avoid a gigantic typing task.

---

### Post by inha on 2005-11-26
Now I'll have to get creative. I opened up this thread and now I'll put the nonworking config back on , c/p the outputs here,  then connect this one back to the internets and post this message. 

laptop:

interfaces file

```

# The primary network interface
iface eth0 inet static
address 196.168.1.2
netmask 255.255.255.0
gateway 196.168.1.1

auto eth0

```

ifconfig -A

```

eth0      Link encap:Ethernet  HWaddr 00:13:D4:9A:84:27
          inet addr:80.186.106.107  Bcast:80.186.127.255  Mask:255.255.224.0
          inet6 addr: fe80::213:d4ff:fe9a:8427/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1495 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1699 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1419462 (1.3 MiB)  TX bytes:231097 (225.6 KiB)
          Interrupt:16

```

mii-stuff gives the same errors. It was operation not permitted instead of suppoerted on the mii-tool on both computers though.

route -n

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
80.186.96.0     0.0.0.0         255.255.224.0   U     0      0        0 eth0
0.0.0.0         80.186.96.1     0.0.0.0         UG    0      0        0 eth0

```

---

### Post by mips on 2005-11-26
First, stop Firestarter.

Can you ping from the Laptop to Eth2 and vice versa using the IP address ?

---

### Post by inha on 2005-11-26
[QUOTE=mips]First, stop Firestarter.

Can you ping from the Laptop to Eth2 and vice versa using the IP address ?[/QUOTE]

I didn't even have it running.

ping from laptop gives: Destination host unreachable
desktop: Destination net unreachable

---

### Post by mips on 2005-11-26
```

eth0      Link encap:Ethernet  HWaddr 00:13:D4:9A:84:27
          inet addr:**[COLOR="Red"]80.186.106.107[/COLOR]**  Bcast:80.186.127.255  Mask:255.255.224.0
          inet6 addr: fe80::213:d4ff:fe9a:8427/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1495 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1699 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1419462 (1.3 MiB)  TX bytes:231097 (225.6 KiB)
          Interrupt:16

```

What happened to 196.168.1.2 ???


```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
[COLOR="Red"]80.186.96.0[/COLOR]     0.0.0.0         255.255.224.0   U     0      0        0 eth0
0.0.0.0         [COLOR="Red"]80.186.96.1[/COLOR]     0.0.0.0         UG    0      0        0 eth0

```

Is this with the config changed ? Bit confusing.

---

### Post by inha on 2005-11-26
[QUOTE=mips]```

eth0      Link encap:Ethernet  HWaddr 00:13:D4:9A:84:27
          inet addr:**[COLOR="Red"]80.186.106.107[/COLOR]**  Bcast:80.186.127.255  Mask:255.255.224.0
          inet6 addr: fe80::213:d4ff:fe9a:8427/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1495 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1699 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1419462 (1.3 MiB)  TX bytes:231097 (225.6 KiB)
          Interrupt:16

```

What happened to 196.168.1.2 ???


```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
[COLOR="Red"]80.186.96.0[/COLOR]     0.0.0.0         255.255.224.0   U     0      0        0 eth0
0.0.0.0         [COLOR="Red"]80.186.96.1[/COLOR]     0.0.0.0         UG    0      0        0 eth0

```

Is this with the config changed ? Bit confusing.[/QUOTE]


woops. I think I forgot to restart networking in between configs so those may be messed up.

a rerun of ifconfig gives 196.168.1.2 as the ip and route gives the same output.

---

### Post by mips on 2005-11-26
The routes should not stay the same. What happens when you reboot the Laptop ?

---

### Post by mips on 2005-11-26
Your laptops route -n output should look like this:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
[COLOR="Red"]196.168.1.0[/COLOR]     0.0.0.0         [COLOR="Red"]255.255.255.0[/COLOR]   U     0      0        0 eth0
0.0.0.0         196.168.1.1     0.0.0.0         UG    0      0        0 eth0
```

---

### Post by inha on 2005-11-26
route still gives the same ips.

---

### Post by inha on 2005-11-26
[QUOTE=mips]Your laptops route -n output should look like this:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
[COLOR="Red"]196.168.1.0[/COLOR]     0.0.0.0         [COLOR="Red"]255.255.255.0[/COLOR]   U     0      0        0 eth0
0.0.0.0         196.168.1.1     0.0.0.0         UG    0      0        0 eth0
```[/QUOTE]

That's exactly what it gives.

---

### Post by mips on 2005-11-26
Do you have skype, MSN or ICQ on a working machine ? If you do PM me your contact details.

I see you are online, might go faster if we have a direct realtime line of comms.

---

### Post by inha on 2005-11-26
None of those, sorry.

---

### Post by mips on 2005-11-26
Start XChat IRC on the desktop join the ubuntu channel or simply go /join #mips for my channel.

1. Sure the cable is a X-over ?
2. Firestarter is shut down/not running/disabled ?
3. You cannot ping 196.168.1.1 from the laptop ?
4. You cannot ping 196.168.1.2 from the pc ?
5. Can you ping 127.0.0.1 from the laptop ?

---

### Post by inha on 2005-11-26
I'll be there in 10 minutes or so. I've got to run out to the store.

---

### Post by mips on 2005-11-26
Problem solved! inha will report back with the steps followed.

---

### Post by inha on 2005-11-26
Indeed. As a desperate final measure mips suggested that I'd turn apic and apci off and that did the trick. Then further testing showed that disabling apic is enough.

So the solution for me was to add apic=off into the kernel entry in the grub configuration file /boot/grub/menu.lst.

One final thanks to mips! This double interwebbing stuff is off the hook!

---

