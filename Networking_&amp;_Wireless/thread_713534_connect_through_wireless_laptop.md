---
title: "connect through wireless laptop"
date: 2008-03-02
forum: Networking &amp; Wireless
---

### Post by supersonicdarky on 2008-03-02
I have 2 laptops, both running 7.10. One has wirelss + ethernet, the other only ethernet. Is it possible to connect the wired one to the internet though the wireless one? I have both regular and crossover cables handy. This isn't an issue in any way, just an experiment (proof of concept if you may).

---

### Post by SpaceTeddy on 2008-03-03
yes, it is.

i'm going to give a **very** quick rundown on what to do... if you need more detailed instructions or want to make the setting permanent, then you would need to take more steps. everything done here is temporary and will be reset upon rebooting.

i will assume that eth0 is the ethernet card in both laptops, eth1 is the wireless card in the one laptop that is the router.
LT1 is the laptop with two network cards
LT2 is the laptop with ethernet only


Prerequisite:
LT1 has full internet access

1.) enable ip forwarding
on LT1, issue the following commands to enable port forwarding and allowing passthrough traffic
```
sudo su
echo 1 > /proc/sys/net/ipv4/ip_forward
iptables -A FORWARD -j ACCEPT
```
NOTE: all following commands on LT1 should be done in this terminal, since this is now root. if you run them in a different terminal, put sudo infront

2.) set a static ip for eth0(cable network)
on LT1, configure your networkcard to have an ip address that is NOT in the subnet of eth1. let's use the 192.168.178.0/24 network.
```
ifconfig eth0 192.168.178.1
```

3.) Enable masquerading
on LT1, issue this command to enable masquerading of all networks behind this machine . This will make LT1 rewrite all packets so that it looks like the laptop itself sent them
```
iptables --table nat -A POSTROUTING -o eth1 -j MASQUERADE
```

4.) configure LT2 network
Disable the network manager on LT2 !
on LT2 configure the network card to reach LT1 with an ip address from the same subnet
```
sudo ifconfig eth0 192.168.178.2
```
you should now be able to ping the computers repectivly.
on LT1
```
ping -c4 192.168.178.2
```
on LT2
```
ping -c4 192.168.178.1
```

5.) set the default route for LT2
In order for LT2 to find the internet, we need to tell it where to send its pakets. this is done via
```
sudo route add default gw 192.168.178.1
```

6.)Nameserver for LT2
last thing that is needed for LT2 is a nameserver.
the easiest way is to copy the settings from LT1 to LT2 by copying the nameserver statements from the file /etc/resolv.conf
on LT1:
```
cat /etc/resolv.conf
```
on LT2:
> gksu gedit /etc/resolf.conf

LT2 should now have internet access (if i didn't forget anything and everything worked)
This is a VERY basic rundown on just the commands. there is way more to the whole issue at hand, but i know that getting something to work is sometimes the best to start figuring stuff out.

---

### Post by supersonicdarky on 2008-03-03
I get stuck on step 4.

You haven't specified which cable to use, so I tried both.

Ping from L1 to L2 && L2 to L1 using crossover cable = fail
Ping from L1 to L2 (once network manager connects using eth0) using regular cable = successful
Ping from L2 to L1 in the same configuration (no network manager) = fail

I don't think I got anything wrong.

[size=1]since the original post I have installed Arch on the wired laptop, but there's no reason why it should make a difference[/size]

---

### Post by SpaceTeddy on 2008-03-04
for a direct connection between two computer both having 100Mbit cards or less you need a crossover.

if there is a switch/hub inbetween you need two patchcables

as soon as one of the machines hab Gbit Ethernet the cable type does not matter anymore - the card will figure it out itself.

also, i am unsure how nm can connect to anything on LT2 since there should be no dhcp server or anything running... or so i assumed :) The reason why i said disable network manager is because it usually gets in the way when you are trying to do manual network configurations with ifconfig - it overwrites them on a regular basis. If you can get it to work with nm - then do so...

also, can you please give me (after you have configured the devices) an output of ```
ifconfig
``` from both machines ?

---

### Post by supersonicdarky on 2008-03-04
looking at htop, it seems something related to dhcp is running. I don't know if it's a server though.

```
/sbin/dhcpcd -t 30 -h arch eth0
```

and ifconfig
L1: (ignore the eth2, it's just an old pcmcia network card that i'm using to prevent dust/dirt from getting into the slot)
```
root@laptop:~# ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:C0:9F:E8:82:50  
          inet addr:192.168.178.1  Bcast:192.168.178.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 Base address:0x1800 

eth1      Link encap:Ethernet  HWaddr 00:14:A4:47:25:79  
          inet addr:192.168.1.99  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:a4ff:fe47:2579/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12389 errors:0 dropped:1609 overruns:0 frame:0
          TX packets:8882 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13560314 (12.9 MB)  TX bytes:582081870 (555.1 MB)
          Interrupt:4 Base address:0x4000 

eth2      Link encap:Ethernet  HWaddr 00:60:97:93:EF:03  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:90 (90.0 b)
          Interrupt:19 Base address:0x300 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:101 errors:0 dropped:0 overruns:0 frame:0
          TX packets:101 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8494 (8.2 KB)  TX bytes:8494 (8.2 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:192.168.254.1  Bcast:192.168.254.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:88 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:172.16.156.1  Bcast:172.16.156.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:88 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

L2:
```
[root@arch ~]# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:D0:59:11:87:C3  
          inet addr:192.168.178.2  Bcast:192.168.178.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:94 errors:0 dropped:0 overruns:0 frame:0
          TX packets:94 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9968 (9.7 Kb)  TX bytes:9968 (9.7 Kb)

```

---

### Post by SpaceTeddy on 2008-03-05
if the two eth0 are connected via a cross-over cable, then this setup should work. The devices are configured correctly and should be able to talk to each other.

you might want to kill that dhcpcd process on eth0 zero, since that one is set (by it's commandline parameters) to try to get a new IP every 30 minutes if there is none assigned to it. This would mean that it overwrites the current configuration that you made.
i have no idea where it comes from... and i have not seen that process/programm run anywhere before...

---

