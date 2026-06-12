---
title: "No network access, can't ping the router"
date: 2006-07-22
forum: Networking &amp; Wireless
---

### Post by flo2771 on 2006-07-22
Hi!
I installed Xubuntu 6.06 yesterday and it's a great system, except that I don't have access to my LAN nor to the internet, which is behind our (linux) router.

When I run windows on the same machine, LAN and everything works, so there is not a problem with the cables...
My system's NIC is a 3COM 900B, connected to our old house-network still using the old coax (bnc) cables.

All the hosts in our LAN have static IP addresses. (192.168.99.101 - my machine, 192.168.99.10 the router).

Some system output (translated from German)

IFCONFIG

```


eth0      Protocol:Ethernet  Hardware address 00:50:04:EC:3D:46  
          inet address:192.168.99.101  Bcast:192.168.99.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Collisions:0 Length of queue:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:5 Base-address:0x4000 

lo        Protocol:Loopback Device
          inet address:127.0.0.1  mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:47 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47 errors:0 dropped:0 overruns:0 carrier:0
          Collisions:0 Length of queue:0 
          RX bytes:4296 (4.1 KiB)  TX bytes:4296 (4.1 KiB)


```

ROUTE  (hangs after printing the info below, only to be canceled with ctrl+c)
```


Dest           Router      Genmask           Flags      Metric     Ref     Use     Iface
localnet        *         255.255.255.0        U           0          0        0        eth0


```

/etc/network/interfaces
```

#...#
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address 192.168.99.101
	netmask 255.255.255.0
	network 192.168.99.0
	broadcast 192.168.99.255
	gateway 192.168.99.10
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 192.168.99.10

```

LSMOD grep 3c
```

3c59x                  45608  0 
mii                     5888  1 3c59x

```

MII-DIAG eth0
```

Basic registers of MII PHY #24:  0000 1809 0000 0000 0061 0000 0000 0000.
 Basic mode control register 0x0000: Auto-negotiation disabled, with
 Speed fixed at 10 mbps, half-duplex.
 Basic mode status register 0x1809 ... 1809.
   Link status: not established.
 Link partner information is not exchanged when in fixed speed mode.
   End of basic transceiver information.

```

Here it says "link status: not established". However, as it works under windows and as I've read something about some drivers reporting "no link" whether there is one or not, that could also be a driver bug. I also ran the DOS-Configtool, but there it all says "auto detection"...

I really need help, thanks in advance!!!

---

