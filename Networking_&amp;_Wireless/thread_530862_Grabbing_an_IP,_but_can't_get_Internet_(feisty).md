---
title: "Grabbing an IP, but can't get Internet (feisty)"
date: 2007-08-20
forum: Networking &amp; Wireless
---

### Post by fortenbt on 2007-08-20
Hello all; I just signed up here but I've been following the forums for awhile now.  This is the first problem I've had where I couldn't find the solution here or somewhere else.

I'm running Feisty (7.04) on my athlon 3200+ desktop system.  This system has 3 network cards--two on the motherboard and one pci.  All of them are recognized and work correctly by ubuntu.

I'm set up in university housing with ethernet ports in our room that lead to a modem that is directly connected to fiber provided by Time Warner.

eth2 is connected directly to the port on the wall and grabs an external IP using DHCP.
eth0 is forwarding internet to the uplink of my dlink DI-524 router and is statically set at 192.168.0.1.
eth1 is connected to a port on my router and is assigned 192.168.1.101.
(This may seem like an odd setup; it is.  My university does not allow routers to be directly connected to the ports, so I have to share internet to them, and then connect other devices to my router)

In order to forward Internet, I followed [_this_]("http://ubuntuforums.org/showthread.php?t=91370") guide on setting up internet connection sharing.

The problem is that sometimes I can't get to the Internet.  Every now and then, and very rarely, I open up firefox and, voila, it works.  Most of the time, I can't ping external sites, I can't navigate to websites using firefox, etc.  The confusing part about this is that I get the external IP and it even sees the correct DNS servers the university uses and everything.  And the worst part is that I don't change anything (that I know of) and it miraculously works sometimes.

I should add that I have the same setup in windows (directly connected to the wall with one nic, forwarding that internet to my router with another, and connected to that router with the third), and everything works perfectly.

I'm not too familiar with iptables and nat and masquerading (I just followed that guide like a sheep ;)), so my first guess would be it has something to do with that.

Sorry for the long post, but I was hoping to explain my strange setup and the problem as accurately as possible.  Any help is much appreciated.

Thanks,
Ben

---

### Post by AcworthJack on 2007-08-20
Can you post the results from the following:
ifconfig -a
netstat -r
iptables -L
and your /etc/sysctl.conf file

Thanks

---

### Post by fortenbt on 2007-08-20
Edit: I should add that as I ran these commands, my Internet actually works.  If the next time I get on it does not, I'll rerun them and see if there are any differences.

**_ifconfig -a output_**
```
eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx 
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:eaff:feeb:1e6c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8227 (8.0 KiB)  TX bytes:3637 (3.5 KiB)
          Interrupt:16 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2a0:c9ff:fee0:1500/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:130 errors:0 dropped:0 overruns:0 frame:0
          TX packets:101 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:32240 (31.4 KiB)  TX bytes:12734 (12.4 KiB)

eth2      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx
          inet addr:64.93.153.123  Bcast:64.93.155.255  Mask:255.255.252.0
          inet6 addr: fe80::20f:eaff:feea:4ede/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1697 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:360411 (351.9 KiB)  TX bytes:4927 (4.8 KiB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:740 (740.0 b)  TX bytes:740 (740.0 b)

```

**_netstat -r output_**
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     *               255.255.255.0   U         0 0          0 eth1
192.168.0.0     *               255.255.255.0   U         0 0          0 eth0
64.93.152.0     *               255.255.252.0   U         0 0          0 eth2
link-local      *               255.255.0.0     U         0 0          0 eth0
default         64.93.152.1     0.0.0.0         UG        0 0          0 eth2
default         192.168.1.1     0.0.0.0         UG        0 0          0 eth1
```

**_iptables -L output_**
```
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     0    --  anywhere             anywhere            
LOG        0    --  127.0.0.0/8          anywhere            LOG level warning 
DROP       0    --  127.0.0.0/8          anywhere            
ACCEPT     0    --  anywhere             255.255.255.255     
ACCEPT     0    --  192.168.0.0/24       anywhere            
ACCEPT    !tcp  --  anywhere             BASE-ADDRESS.MCAST.NET/4 
LOG        0    --  192.168.0.0/24       anywhere            LOG level warning 
DROP       0    --  192.168.0.0/24       anywhere            
LOG        0    --  192.168.0.0/24       anywhere            LOG level warning 
DROP       0    --  192.168.0.0/24       anywhere            
ACCEPT     0    --  anywhere             255.255.255.255     
ACCEPT     0    --  anywhere             255.255.255.255     
ACCEPT     0    --  anywhere             192.168.1.101       
ACCEPT     0    --  anywhere             192.168.1.255       
ACCEPT     0    --  anywhere             64.93.153.123       
ACCEPT     0    --  anywhere             64.93.155.255       
DROP       0    --  anywhere             ALL-SYSTEMS.MCAST.NET 
LOG        0    --  anywhere             anywhere            LOG level warning 
DROP       0    --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     0    --  192.168.0.0/24       anywhere            
ACCEPT     0    --  192.168.0.0/24       anywhere            
ACCEPT     0    --  anywhere             anywhere            state RELATED,ESTABLISHED 
LOG        0    --  anywhere             192.168.0.0/24      LOG level warning 
DROP       0    --  anywhere             192.168.0.0/24      
LOG        0    --  anywhere             192.168.0.0/24      LOG level warning 
DROP       0    --  anywhere             192.168.0.0/24      
DROP       0    --  anywhere             ALL-SYSTEMS.MCAST.NET 
LOG        0    --  anywhere             anywhere            LOG level warning 
DROP       0    --  anywhere             anywhere            

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     0    --  anywhere             anywhere            
ACCEPT     0    --  anywhere             255.255.255.255     
ACCEPT     0    --  anywhere             192.168.0.0/24      
ACCEPT    !tcp  --  anywhere             BASE-ADDRESS.MCAST.NET/4 
LOG        0    --  anywhere             192.168.0.0/24      LOG level warning 
DROP       0    --  anywhere             192.168.0.0/24      
LOG        0    --  anywhere             192.168.0.0/24      LOG level warning 
DROP       0    --  anywhere             192.168.0.0/24      
ACCEPT     0    --  anywhere             255.255.255.255     
ACCEPT     0    --  anywhere             255.255.255.255     
ACCEPT     0    --  192.168.1.101        anywhere            
ACCEPT     0    --  192.168.1.255        anywhere            
ACCEPT     0    --  64.93.153.123        anywhere            
ACCEPT     0    --  64.93.155.255        anywhere            
DROP       0    --  anywhere             ALL-SYSTEMS.MCAST.NET 
LOG        0    --  anywhere             anywhere            LOG level warning 
DROP       0    --  anywhere             anywhere         
```

**_/etc/sysctl.conf file_**
```
net.ipv4.ip_forward = 1
#
# /etc/sysctl.conf - Configuration file for setting system variables
# See sysctl.conf (5) for information.
#

#kernel.domainname = example.com
#net/ipv4/icmp_echo_ignore_broadcasts=1

# the following stops low-level messages on console
kernel.printk = 4 4 1 7

##############################################################3
# Functions previously found in netbase
#

# Uncomment the next line to enable Spoof protection (reverse-path filter)
#net.ipv4.conf.default.rp_filter=1

# Uncomment the next line to enable TCP/IP SYN cookies
#net.ipv4.tcp_syncookies=1

# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.conf.default.forwarding=1

# Uncomment the next line to enable packet forwarding for IPv6
#net.ipv6.conf.default.forwarding=1
```

---

### Post by fortenbt on 2007-08-21
Well, I got it to stop working this morning.

I've been messing around with my ati drivers--specifically, with the /etc/X11/xorg.conf file to get the drivers working correctly.  After I edited that file this morning (while the Internet was still working), I restarted the x server by hitting ctrl-alt-backspace.  When it tried to restart, there was a parse error with the xorg.conf file, so I just logged into the first console (ctrl-alt-f1) to fix the issue.  From there I ran "startx" and logged back into ubuntu.

That's when the Internet was not working.  I ran all those commands again and compared them to what I had when it was working, and the only differences were in my iptables.  I posted those below and highlighted the differences in red.

I thought restarting the x server had nothing to do with networking, so I was surprised to see that it must have done something.

**_iptables -L output when not working_**
```
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     0    --  anywhere             anywhere            
LOG        0    --  127.0.0.0/8          anywhere            LOG level warning 
DROP       0    --  127.0.0.0/8          anywhere            
ACCEPT     0    --  anywhere             255.255.255.255     
ACCEPT     0    --  192.168.0.0/24       anywhere            
ACCEPT    !tcp  --  anywhere            [COLOR="Red"]** 224.0.0.0/4**[/COLOR]         
LOG        0    --  192.168.0.0/24       anywhere            LOG level warning 
DROP       0    --  192.168.0.0/24       anywhere            
LOG        0    --  192.168.0.0/24       anywhere            LOG level warning 
DROP       0    --  192.168.0.0/24       anywhere            
ACCEPT     0    --  anywhere             255.255.255.255     
ACCEPT     0    --  anywhere             255.255.255.255     
ACCEPT     0    --  anywhere             192.168.1.101       
ACCEPT     0    --  anywhere             192.168.1.255       
ACCEPT     0    --  anywhere             64.93.153.123       
ACCEPT     0    --  anywhere             64.93.155.255       
DROP       0    --  anywhere             [COLOR="Red"]**224.0.0.1**[/COLOR]           
LOG        0    --  anywhere             anywhere            LOG level warning 
DROP       0    --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     0    --  192.168.0.0/24       anywhere            
ACCEPT     0    --  192.168.0.0/24       anywhere            
ACCEPT     0    --  anywhere             anywhere            state RELATED,ESTABLISHED 
LOG        0    --  anywhere             192.168.0.0/24      LOG level warning 
DROP       0    --  anywhere             192.168.0.0/24      
LOG        0    --  anywhere             192.168.0.0/24      LOG level warning 
DROP       0    --  anywhere             192.168.0.0/24      
DROP       0    --  anywhere             [COLOR="Red"]**224.0.0.1 **[/COLOR]          
LOG        0    --  anywhere             anywhere            LOG level warning 
DROP       0    --  anywhere             anywhere            

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     0    --  anywhere             anywhere            
ACCEPT     0    --  anywhere             255.255.255.255     
ACCEPT     0    --  anywhere             192.168.0.0/24      
ACCEPT    !tcp  --  anywhere             [COLOR="Red"]**224.0.0.0/4**[/COLOR]         
LOG        0    --  anywhere             192.168.0.0/24      LOG level warning 
DROP       0    --  anywhere             192.168.0.0/24      
LOG        0    --  anywhere             192.168.0.0/24      LOG level warning 
DROP       0    --  anywhere             192.168.0.0/24      
ACCEPT     0    --  anywhere             255.255.255.255     
ACCEPT     0    --  anywhere             255.255.255.255     
ACCEPT     0    --  192.168.1.101        anywhere            
ACCEPT     0    --  192.168.1.255        anywhere            
ACCEPT     0    --  64.93.153.123        anywhere            
ACCEPT     0    --  64.93.155.255        anywhere            
DROP       0    --  anywhere             [COLOR="Red"]**224.0.0.1**[/COLOR]           
LOG        0    --  anywhere             anywhere            LOG level warning 
DROP       0    --  anywhere             anywhere            

```

---

### Post by fortenbt on 2007-08-21
After reading a lot about iptables, I still haven't figured out exactly how to configure it, but it looks like iptables acts as a firewall.  If nothing else, I would just want to get it set back to normal so I can have Internet on the Ubuntu machine without having it forward the Internet to my router.

---

### Post by fortenbt on 2007-08-22
bump

Anyone?

---

