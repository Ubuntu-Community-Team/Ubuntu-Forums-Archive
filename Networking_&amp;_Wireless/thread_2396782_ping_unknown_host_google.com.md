---
title: "ping: unknown host google.com"
date: 2018-07-20
forum: Networking &amp; Wireless
---

### Post by Mark_in_Hollywood on 2018-07-20
I changed ISPs. The now modem, when run with a Ethernet cable directly to the 'puter works. When the same cable goes to a unmanaged switch, no 'net. Pinging returns: ```
ping: unknown host google.com
```


Searching for no eth0 exists. I see an edit of /ect/init/rc.conf where the OP adds eth0 to the runlevel. But looking at my rc.conf, I don't know where that would go.

1. Is this the correct fix, adding eth0? (that's a zero number, on-screen here it looks like: m,n,O --the letter).
2. I ask as Ubuntu (16.04) has assigned the wired interface name to be: enp6s0.
3. There is NO router here, only an unmanaged switch.
4. When the switch has an Ethernet cable from the modem to the switch, the 'net is enabled. When a (extra) cable runs from the switch to the 'puter, the entire net goes down. What is going on here and how do I correct this?

```
mark@Lexington:/etc/init$ cat rc.conf
# rc - System V runlevel compatibility
#
# This task runs the old System V-style rc script when changing between
# runlevels.

description	"System V runlevel compatibility"
author		"Scott James Remnant <scott@netsplit.com>"

emits deconfiguring-networking
emits unmounted-remote-filesystems

start on runlevel [0123456]
stop on runlevel [!$RUNLEVEL]

export RUNLEVEL
export PREVLEVEL

console output
env INIT_VERBOSE

task

script
if [ "$RUNLEVEL" = "0" -o "$RUNLEVEL" = "1" -o "$RUNLEVEL" = "6" ]; then
    status plymouth-shutdown 2>/dev/null >/dev/null && start wait-for-state WAITER=rc WAIT_FOR=plymouth-shutdown || :
fi
/etc/init.d/rc $RUNLEVEL
end script
```


```

mark@Lexington:/$ ip link show dev eth0
Device "eth0" does not exist.
mark@Lexington:/$ ip address show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp6s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 4c:cc:6a:63:b1:bf brd ff:ff:ff:ff:ff:ff
    inet6 2605:e000:9fc0:5:698b:36eb:4b96:35cf/128 scope global dynamic 
       valid_lft 604302sec preferred_lft 604302sec
    inet6 fe80::f35e:6ca9:b307:2f33/64 scope link 
       valid_lft forever preferred_lft forever
```

---

### Post by chili555 on 2018-07-20
Is this a desktop where Network Manager is running or is it, as I suspect, a server? If the latter, may we see:```
cat /etc/network/interfaces
```Are there other devices attached to the switch? What address range do they get?

Many dumb switches, like mine, do not like static IP addresses. If /etc/network/interfaces is set for a static address, I haven't any doubt that the switch balks.

---

### Post by Mark_in_Hollywood on 2018-07-20
This is a Desktop box. No server to my knowledge.

Other Devices address range? My magicjack phone connection (VOIP) works as long as the cable twixt the switch and computer isn't connected.  I'm confused as to addresses. You mean MAC addresses, I'm guessing. 

```
mark@Lexington:~$ sudo ifconfig -a
[sudo] password for mark: 
enp6s0    Link encap:Ethernet  HWaddr 4c:cc:6a:63:b1:bf  
          inet addr:76.90.233.80  Bcast:76.90.239.255  Mask:255.255.240.0
          inet6 addr: fe80::6661:94a9:182b:256/64 Scope:Link
          inet6 addr: 2605:e000:9fc0:5:698b:36eb:4b96:35cf/128 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19959 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5651 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5862598 (5.8 MB)  TX bytes:1176374 (1.1 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:5901 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5901 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:483088 (483.0 KB)  TX bytes:483088 (483.0 KB)
```

```
mark@Lexington:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
```

---

### Post by chili555 on 2018-07-20
> Other Devices address range?I meant the IP addresses. What IP addresses do other devices get connected to the switch? In the 76.90.233.xx range or what?

The data above suggests that the ethernet is directly connected to your Time-Warner modem.>  When the switch has an Ethernet cable from the modem to the switch, the 'net is enabled. When a (extra) cable runs from the switch to the 'puter, the entire net goes down. What is going on here and how do I correct this?Are there other devices that all work perfectly well as long as the Ubuntu computer is not connected?

Can the Ubuntu computer ping this?```
ping -c3 8.8.8.8
```

---

### Post by Mark_in_Hollywood on 2018-07-20
I'm confused. I've read that unmanaged switches have no IP addresses. If that is correct what addresses do you want? All of the devices on the switch? Just some? Sorry, I'm not a nutworking 'puter guy. Your kung fu is the best.

As far as I know, as long as the 'puter is not attached via Ethernet cable between computer Ethernet port and the unmanaged switch all is working. For instance, with no computer (Linux) connected, the (usually no powered) Windws comp had net access.

```
mark@Lexington:/$ ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=121 time=27.7 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=121 time=17.1 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=121 time=83.4 ms

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 17.182/42.778/83.423/29.061 ms
```

but the return on 8.8.8.8 is while the computer's ethernet port is cabled directly to ONLY the modem.

FWIW, I've tried one device at a time, re-booting the modem each time. So far no 'net.


FYI

```
mark@Lexington:/$ sudo arp-scan --interface=eth0 --localnet
ioctl: No such device
mark@Lexington:/$ sudo arp-scan --interface=enp6s0 --localnet
Interface: enp6s0, datalink type: EN10MB (Ethernet)
Starting arp-scan 1.8.1 with 4096 hosts (http://www.nta-monitor.com/tools/arp-scan/)
76.90.224.1	00:01:5c:6e:56:46	CADANT INC.
76.90.224.2	00:01:5c:6e:56:46	CADANT INC.
76.90.224.3	00:01:5c:6e:56:46	CADANT INC.
76.90.224.4	00:01:5c:6e:56:46	CADANT INC.
76.90.224.5	00:01:5c:6e:56:46	CADANT INC.
76.90.224.6	00:01:5c:6e:56:46	CADANT INC.
76.90.224.7	00:01:5c:6e:56:46	CADANT INC.
76.90.224.8	00:01:5c:6e:56:46	CADANT INC.
76.90.224.9	00:01:5c:6e:56:46	CADANT INC.
76.90.232.105	00:01:5c:6e:56:46	CADANT INC.
76.90.226.50	00:01:5c:6e:56:46	CADANT INC.
76.90.235.247	00:01:5c:6e:56:46	CADANT INC.

13 packets received by filter, 0 packets dropped by kernel
Ending arp-scan 1.8.1: 4096 hosts scanned in 16.716 seconds (245.03 hosts/sec). 12 responded
```

---

### Post by chili555 on 2018-07-20
>  I've read that unmanaged switches have no IP addresses. Indeed the switch itself has no address. However, the connected devices have and must have IP addresses. 

In my own case, for example, there is but one ethernet jack to my TV/music room. I use a switch to give the TV, Roku, etc. their own unique connections. All have their own IP addresses in the same range as all other devices in my home, including this very computer, 192.168.0.xxx.

Where I am going with this is that if the modem gives an IP address from Time-Warner (Spectrum??) in the range of 76.90.233.80, what does the switch do? Is the modem set to be a DHCP server; i.e. can it assign IP addresses to the switch?

Have you gotten the Internet from Spectrum --> modem --> switch --> computer, phone or tablet method to work before today?> mark@Lexington:/$ ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=121 time=27.7 msAhhh! You have internet access but have a DNS problem. Please try:```
sudo dpkg-reconfigure resolveconf
```Say 'yes' to accept and pinging Google should work again.> FWIW, I've tried one device at a time, re-booting the modem each time. So far no 'net.No internet is available for* any* device using the switch? Or what??

---

### Post by chili555 on 2018-07-20
> 76.90.224.1	00:01:5c:6e:56:46	CADANT INC.
76.90.224.2	00:01:5c:6e:56:46	CADANT INC.
76.90.224.3	00:01:5c:6e:56:46	CADANT INC.
76.90.224.4	00:01:5c:6e:56:46	CADANT INC.
76.90.224.5	00:01:5c:6e:56:46	CADANT INC.
76.90.224.6	00:01:5c:6e:56:46	CADANT INC.
76.90.224.7	00:01:5c:6e:56:46	CADANT INC.
76.90.224.8	00:01:5c:6e:56:46	CADANT INC.
76.90.224.9	00:01:5c:6e:56:46	CADANT INC.
76.90.232.105	00:01:5c:6e:56:46	CADANT INC.
76.90.226.50	00:01:5c:6e:56:46	CADANT INC.
76.90.235.247	00:01:5c:6e:56:46	CADANT INC.I don't understand this at all. This is, as you can see by the MAC address, one device. It evidently has eleven (!!!) IP addresses in different subnets!

Weird.

---

### Post by kazakore on 2018-07-21
76.90.x.x is not within the ipv4 private network ranges, seems very strange to me that your router would be issuing addresses in this range for local network purposes. Something seems fishy with that....

[https://en.wikipedia.org/wiki/Private_network](https://en.wikipedia.org/wiki/Private_network)

((EDIT: Looks to be Time Warner external IPs. Odd!

                    Source:                     whois.arin.net                
                                    IP Address:                     76.90.224.1                
                                                            Name:                         RRWE                    
                                            Handle:                         NET-76-80-0-0-1                    
                                            Registration Date:                         22/12/06                    
                                            Range:                         76.80.0.0-76.95.255.255                    
                                                                                            Org:                             Time Warner Cable Internet LLC                        
                                                    Org Handle:                             RRWE                        
                                                    Address:                             6399 S Fiddlers Green Circle
                        
                                                    City:                             Greenwood Village                        
                                                    State/Province:                             CO                        
                                                    Postal Code:                             80111                        
                                                    Country:                             United States                        
                                                                Name Servers: 


Is this maybe Spectrum VPN so you're treated as being part of their network???
))

You've mentioned phones and other devices which do work until you connect the Ubuntu machine. Are those other devices also communicating through the switch by cable, or directly into the modem router (eg wifi.)

---

### Post by Mark_in_Hollywood on 2018-07-23
The order of re-booting the devices matters. Go Figure!

With all devices powered off, the modem is first to be powered up. Then the switch, then the 'puter and anything else. Except the MagicJack phone service. It just won't work. I would re-boot the modem and computer, without touching the unmanaged switch, that is what failed.

Thank you, community.

---

