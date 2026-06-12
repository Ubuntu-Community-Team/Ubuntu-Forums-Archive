---
title: "Two network cards, one machine, same network....help please!"
date: 2013-11-08
forum: Networking &amp; Wireless
---

### Post by mahalos on 2013-11-08
Hey 
I have just added a gigabit PCI network card to my server as the onboard wasn't gigabit.
 I use wakeonlan daily to wake up the server for various things, but cant get it working with the PCI card (motherboard limitation i think). 
So i have re-enabled the onboard NIC in the hope of using it just for WOL and the new gigabit PCI card for all traffic. 

I have both NICs working ....despite the "waiting for network configuration"....on boot up
```
eth0      Link encap:Ethernet  HWaddr 00:11:11:f1:cc:32  
          inet addr:192.168.1.200  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:11ff:fef1:cc32/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:258 errors:0 dropped:0 overruns:0 frame:0
          TX packets:129 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24941 (24.9 KB)  TX bytes:15686 (15.6 KB)

eth1      Link encap:Ethernet  HWaddr 64:66:b3:03:90:3a  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::6666:b3ff:fe03:903a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:230 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20685 (20.6 KB)  TX bytes:468 (468.0 B)
          Interrupt:22 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

```

Im not sure where to go from here...
ip route shows eth0 as being the default device
```
default via 192.168.1.1 dev eth0  metric 100 
192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.200 
192.168.1.0/24 dev eth1  proto kernel  scope link  src 192.168.1.100 
```

here's my /etc/network/interfaces
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.200
netmask 255.255.255.0
gateway 192.168.1.1

#tp-link gigbit pci card
auto eth1
iface eth1 inet static
address 192.168.1.100
netmask 255.255.255.0
gateway 192.168.1.1

```

If someone can help to get it setup so all traffic goes through eth1 whilst eth0 just sits there is used for WOL it's be most appreciated

Thanks

---

### Post by TheFu on 2013-11-08
Does WOL need an IP at all?  Here, WOL only uses the MAC.

Having 2 IPs on the same subnet is usually a bad idea, with limited network knowledge.
I would remove the eth0 stanza and try WOL.

Otherwise, I would read the interfaces man page (**man interfaces**) to find how to remove the automatic routing - might be as simple as removing the "gateway" line for that adapter - I don't know.  The post-up command can certainly be used to remove the routing for that specific interface.

---

### Post by mahalos on 2013-11-08
Thanks for the reply.

You are correct, WOL does not need an IP. It uses MAC addresses. WOL will work on the onboard NIC (eth0) but I can't get it working on the PCI NIC (eth1). 

Things seem to be working with both cards installed with different IPs, and I can use WOL to wake the server up, I just want to be sure that all normal network traffic is being routed through the gigabit NIC (eth1)

---

### Post by SeijiSensei on 2013-11-08
Just make sure that your default gateway is connected to eth1.  That should be all you need.

---

### Post by TheFu on 2013-11-08
> **mahalos said:**
> You are correct, WOL does not need an IP. It uses MAC addresses. WOL will work on the onboard NIC (eth0) but I can't get it working on the PCI NIC (eth1). 


Perhaps I was not obvious?  Just because a NIC is there and there is a cable connected, that does NOT mean you must give it an IP or any network traffic. - remove the eth0 stanza from your "interfaces" file, but leave it connected. After a reboot, eth0 will not have an IP, but will still work for WoL needs.  Without an IP, there won't be any routing issues, so eth1 will get all the traffic.

Hope that wasn't unclear AND that it works.

---

