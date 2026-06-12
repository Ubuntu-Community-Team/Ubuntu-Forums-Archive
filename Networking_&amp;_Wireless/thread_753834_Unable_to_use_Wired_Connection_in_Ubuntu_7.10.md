---
title: "Unable to use Wired Connection in Ubuntu 7.10"
date: 2008-04-13
forum: Networking &amp; Wireless
---

### Post by vijeethvalsan on 2008-04-13
Hi, 
I am a Linux newbie and I started up with Ubuntu 7.10.

I have a strange problem. I installed ubuntu 7.10 on my machine.
Everything worked fine after installation - sound, video and all
except for network. 

When I connect to wired network, I do not get a ip from dhcp 
I have configured eth0 to `Automatic configuration (DHCP)` 
using the `network-admin` dialog.

I have also configured DNS servers using the same `network-admin` 
dialog.

The connection icon in system tray comes up but nothing happens 
after that. When I try to connect to any website - it waits for a 
while and then shows me the `page can not be displayed` message.

I am posting the result of all the configurations / commands below.
[ One of my friend who is a linux user helped me get these logs
  but he could not resolve the problem :-( ]

HELP! Please :(

Cheers,
Vijeeth

```

--------------- Machine Configuration ------------------
Ubuntu: 7.10 (Gutsy Gibbon)
Laptop: Compaq Presario C700
Model Number: C702TU
Intel(R) GM965 Express Chipset
Chipset Components
     Memory Controller: 82GM965
     I/O Controller: Intel(R) 82801HB/HR I/O controller hub (ICH8M)
     Integrated Graphics: Intel(R) 965GM Graphics And Memory Controller Hub(GMCH)

---------------- /etc/network/interfaces ----------------
root@Kulfi:/home/vijeeth# cat /etc/network/interfaces 
auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth0

--------------- /etc/resolv.conf ------------------------

root@Kulfi:/home/vijeeth# cat /etc/resolv.conf 
nameserver 220.225.236.84
nameserver 220.225.236.85

---------------- ifconfig --------------------------------

root@Kulfi:/home/vijeeth# ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:1B:38:7D:80:00  
          inet6 addr: fe80::21b:38ff:fe7d:8000/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8176 errors:0 dropped:0 overruns:0 frame:0
          TX packets:425 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:581146 (567.5 KB)  TX bytes:33898 (33.1 KB)
          Interrupt:21 Base address:0x6000 

eth0:avah Link encap:Ethernet  HWaddr 00:1B:38:7D:80:00  
          inet addr:169.254.4.3  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:21 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:184 errors:0 dropped:0 overruns:0 frame:0
          TX packets:184 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16528 (16.1 KB)  TX bytes:16528 (16.1 KB)
---------------------------------------------------------------

```

---

### Post by bLaCkMeTaLL on 2008-04-14
if you have a dhcp server configured on your network, you could set your network card to "auto"...
since I think you don't have such a thing, I suggest you use a static IP address.

For internet to work, you should also know your gateway address.

Supposing your gateway is 192.168.1.1, your subnet is 255.255.255.0, you could set your static address to your pc using such command:

```
sudo ifconfig eth0 192.168.1.2 netmask 255.255.255.0 up 
```
```
sudo route add default gw 192.168.1.1 eth0
```

by typing them into a teminal (Apps -> Acc -> Terminal)

---

### Post by Iowan on 2008-04-14
What *should* be providing DHCP?  The "eth0:avah" section suggests no offers were received.
Often the DHCP server will tell the client what to use for gateway.

---

### Post by vijeethvalsan on 2008-04-16
No use I am not able to still connect to the internet!!!  :(

---

