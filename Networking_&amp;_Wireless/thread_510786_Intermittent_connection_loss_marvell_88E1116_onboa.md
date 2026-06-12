---
title: "Intermittent connection loss: marvell 88E1116 onboard nic"
date: 2007-07-27
forum: Networking &amp; Wireless
---

### Post by charlesg3 on 2007-07-27
I'm having trouble with the aforementioned NIC (marvell 88E1116). I see the connection disconnect every 10-20 minutes. When it disconnects, it stays down for ~20 seconds then comes back up. When I try to ping google continuously, I get this during the disconnection period:
```

...
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=331 ttl=243 time=59.7 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=332 ttl=243 time=58.8 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=333 ttl=243 time=60.1 ms
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
From bonham32.local (169.254.8.136) icmp_seq=341 Destination Host Unreachable
From bonham32.local (169.254.8.136) icmp_seq=342 Destination Host Unreachable
From bonham32.local (169.254.8.136) icmp_seq=343 Destination Host Unreachable
ping: sendmsg: Network is unreachable
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=345 ttl=243 time=64.1 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=346 ttl=243 time=59.0 ms
...

```

Note that I have several computers on my lan, and I have verified that two other computers can communicate continuously without a problem, which makes me believe the problem is not in the router. Additionally, the ip address doesn't change during these 

I have the following motherboard:[Gigabyte GA-M57SLI-S4]("http://www.gigabyte.com.tw/Products/Motherboard/Products_Spec.aspx?ClassValue=Motherboard&ProductID=2287&ProductName=GA-M57SLI-S4")


Here is ifconfig while the network was down


```
charles@bonham32:~/src$ ifconfig -a
eth1      Link encap:Ethernet  HWaddr 00:1A:4D:7B:FB:7E
          inet6 addr: fe80::21a:4dff:fe7b:fb7e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:203495 errors:0 dropped:0 overruns:0 frame:0
          TX packets:184712 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:258661416 (246.6 MiB)  TX bytes:14400036 (13.7 MiB)
          Interrupt:17 Base address:0x2000

eth1:avah Link encap:Ethernet  HWaddr 00:1A:4D:7B:FB:7E
          inet addr:169.254.8.136  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0x2000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:52 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5652 (5.5 KiB)  TX bytes:5652 (5.5 KiB)

```

I am using ubuntu fiesty - 2.6.20-16-generic

---

### Post by charlesg3 on 2007-07-28
Bump... Does anyone have any suggestions for how to obtain more diagnostic information, perhaps from the module?

---

### Post by noob12 on 2007-07-29
Do you normally have an IPV4 address associated with eth1?  Because **ifconfiig** isn't showing it.

Are you seeing DHCP requests/offers during this time in **/var/log/syslog**?

---

### Post by charlesg3 on 2007-07-29
Yes, this nic is receiving an ipv4 ip address, I posted the result of ifconfig while it was down (and restablishing), here's ifconfig while it is up..

```
charles@bonham32:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:1A:4D:7B:FB:7E
          inet addr:10.1.1.15  Bcast:10.1.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:4dff:fe7b:fb7e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2744450 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2375383 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2635809959 (2.4 GiB)  TX bytes:1184621098 (1.1 GiB)
          Interrupt:17 Base address:0x2000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4209 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4209 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:639462 (624.4 KiB)  TX bytes:639462 (624.4 KiB)

```


Also, here's output from syslog during one of these failures...

```
Jul 29 11:39:24 bonham32 last message repeated 3 times
Jul 29 11:39:35 bonham32 avahi-daemon[4946]: Withdrawing address record for 10.1.1.15 on eth1.
Jul 29 11:39:35 bonham32 avahi-daemon[4946]: Leaving mDNS multicast group on interface eth1.IPv4 with address 10.1.1.15.
Jul 29 11:39:35 bonham32 avahi-daemon[4946]: Interface eth1.IPv4 no longer relevant for mDNS.
Jul 29 11:39:35 bonham32 avahi-autoipd(eth1)[27442]: Found user 'avahi-autoipd' (UID 111) and group 'avahi-autoipd' (GID 116).
Jul 29 11:39:35 bonham32 avahi-autoipd(eth1)[27442]: Successfully called chroot().
Jul 29 11:39:35 bonham32 avahi-autoipd(eth1)[27442]: Successfully dropped root privileges.
Jul 29 11:39:35 bonham32 avahi-autoipd(eth1)[27442]: fopen() failed: Permission denied
Jul 29 11:39:35 bonham32 avahi-autoipd(eth1)[27442]: Starting with address 169.254.8.136
Jul 29 11:39:35 bonham32 avahi-autoipd(eth1)[27442]: Got SIGTERM, quitting.
Jul 29 11:39:35 bonham32 NetworkManager: <information>^IDHCP daemon state is now 10 (unknown) for interface eth1
Jul 29 11:39:36 bonham32 dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Jul 29 11:39:36 bonham32 dhclient: DHCPOFFER from 10.1.1.1
Jul 29 11:39:36 bonham32 dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Jul 29 11:39:36 bonham32 dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Jul 29 11:39:36 bonham32 NetworkManager: <information>^IDHCP daemon state is now 1 (starting) for interface eth1
Jul 29 11:39:36 bonham32 dhclient: DHCPACK from 10.1.1.1
Jul 29 11:39:36 bonham32 avahi-daemon[4946]: Joining mDNS multicast group on interface eth1.IPv4 with address 10.1.1.15.
Jul 29 11:39:36 bonham32 avahi-daemon[4946]: New relevant interface eth1.IPv4 for mDNS.
Jul 29 11:39:36 bonham32 avahi-daemon[4946]: Registering new address record for 10.1.1.15 on eth1.IPv4.
Jul 29 11:39:36 bonham32 avahi-daemon[4946]: Withdrawing address record for 10.1.1.15 on eth1.
Jul 29 11:39:36 bonham32 avahi-daemon[4946]: Leaving mDNS multicast group on interface eth1.IPv4 with address 10.1.1.15.
Jul 29 11:39:36 bonham32 avahi-daemon[4946]: Interface eth1.IPv4 no longer relevant for mDNS.
Jul 29 11:39:36 bonham32 avahi-daemon[4946]: Joining mDNS multicast group on interface eth1.IPv4 with address 10.1.1.15.
Jul 29 11:39:36 bonham32 avahi-daemon[4946]: New relevant interface eth1.IPv4 for mDNS.
Jul 29 11:39:36 bonham32 avahi-daemon[4946]: Registering new address record for 10.1.1.15 on eth1.IPv4.
Jul 29 11:39:36 bonham32 dhclient: bound to 10.1.1.15 -- renewal in 277 seconds.
Jul 29 11:39:36 bonham32 dhclient: DHCPOFFER from 10.1.1.1
Jul 29 11:39:36 bonham32 dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Jul 29 11:39:36 bonham32 dhclient: DHCPACK from 10.1.1.1
Jul 29 11:39:36 bonham32 NetworkManager: <information>^IDHCP daemon state is now 2 (bound) for interface eth1
Jul 29 11:39:36 bonham32 dhclient: bound to 10.1.1.15 -- renewal in 295 seconds.

```

---

### Post by noob12 on 2007-07-29
It looks like you're getting very short DHCP lease times (295 seconds!), about 5 minutes.  Is it a local gateway router that you control?  Is this intentional? Can you set this higher?

---

### Post by noob12 on 2007-07-29
Also, are you using NetworkManager to configure this card.  Can you show us /etc/network/interfaces?

> 
cat /etc/network/interfaces


---

### Post by charlesg3 on 2007-07-29
Yes, I manage the dhcp server, I can up the times a bit, but I wonder why only this machine is being affected (I have other machines getting leases from the same dhcp server which don't seem to cutout at the end of the lease). Is there something about this driver which makes this transition not seamless?

Here's /network/interfaces, everything is setup for dhcp...


```
charles@bonham32:~/backgrounds$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```

---

### Post by charlesg3 on 2007-07-30
I changed the dhcp lease to be 1 hour instead of 10 minutes, this seemed to work for a while, however when I woke up this morning, it seemed like NIC was stuck in it's down state with the following output from ifconfig:

```
charles@bonham32:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:1A:4D:7B:FB:7E
          inet6 addr: fe80::21a:4dff:fe7b:fb7e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3707 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13935 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1851420 (1.7 MiB)  TX bytes:1170471 (1.1 MiB)
          Interrupt:17 Base address:0xa000

eth1:avah Link encap:Ethernet  HWaddr 00:1A:4D:7B:FB:7E
          inet addr:169.254.8.136  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0xa000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3982 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3982 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:382349 (373.3 KiB)  TX bytes:382349 (373.3 KiB)

charles@bonham32:~$
```

And the following output from syslog:
```

Jul 30 03:34:41 bonham32 last message repeated 4 times
Jul 30 03:35:52 bonham32 last message repeated 5 times
Jul 30 03:36:48 bonham32 last message repeated 4 times
Jul 30 03:37:39 bonham32 last message repeated 4 times
Jul 30 03:38:08 bonham32 last message repeated 2 times
Jul 30 03:38:22 bonham32 dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Jul 30 03:38:38 bonham32 dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Jul 30 03:39:48 bonham32 last message repeated 5 times
Jul 30 03:40:46 bonham32 last message repeated 4 times
Jul 30 03:41:49 bonham32 last message repeated 4 times
Jul 30 03:42:40 bonham32 last message repeated 3 times
Jul 30 03:43:42 bonham32 last message repeated 4 times
Jul 30 03:44:47 bonham32 last message repeated 5 times
Jul 30 03:45:45 bonham32 last message repeated 5 times
Jul 30 03:45:49 bonham32 avahi-daemon[5004]: Withdrawing address record for 10.1.1.6 on eth1.
Jul 30 03:45:49 bonham32 avahi-daemon[5004]: Leaving mDNS multicast group on interface eth1.IPv4 with address 10.1.1.6.
Jul 30 03:45:49 bonham32 avahi-daemon[5004]: Interface eth1.IPv4 no longer relevant for mDNS.
Jul 30 03:45:49 bonham32 avahi-autoipd(eth1)[18091]: Found user 'avahi-autoipd' (UID 111) and group 'avahi-autoipd' (GID 116).
Jul 30 03:45:49 bonham32 avahi-autoipd(eth1)[18091]: Successfully called chroot().
Jul 30 03:45:49 bonham32 avahi-autoipd(eth1)[18091]: Successfully dropped root privileges.
Jul 30 03:45:49 bonham32 avahi-autoipd(eth1)[18091]: fopen() failed: Permission denied
Jul 30 03:45:49 bonham32 avahi-autoipd(eth1)[18091]: Starting with address 169.254.8.136
Jul 30 03:45:53 bonham32 avahi-autoipd(eth1)[18091]: Callout BIND, address 169.254.8.136 on interface eth1
Jul 30 03:45:53 bonham32 avahi-daemon[5004]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.8.136.
Jul 30 03:45:53 bonham32 avahi-daemon[5004]: New relevant interface eth1.IPv4 for mDNS.
Jul 30 03:45:53 bonham32 avahi-daemon[5004]: Registering new address record for 169.254.8.136 on eth1.IPv4.
Jul 30 03:45:57 bonham32 avahi-autoipd(eth1)[18091]: Successfully claimed IP address 169.254.8.136
Jul 30 03:45:57 bonham32 avahi-autoipd(eth1)[18091]: fopen() failed: Permission denied
Jul 30 03:45:57 bonham32 NetworkManager: <information>^IDHCP daemon state is now 10 (unknown) for interface eth1
Jul 30 03:45:57 bonham32 avahi-autoipd(eth1)[18091]: Got SIGTERM, quitting.
Jul 30 03:45:57 bonham32 avahi-autoipd(eth1)[18091]: Callout STOP, address 169.254.8.136 on interface eth1
Jul 30 03:45:57 bonham32 avahi-daemon[5004]: Withdrawing address record for 169.254.8.136 on eth1.
Jul 30 03:45:57 bonham32 avahi-daemon[5004]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.8.136.
Jul 30 03:45:57 bonham32 avahi-daemon[5004]: Interface eth1.IPv4 no longer relevant for mDNS.
Jul 30 03:45:57 bonham32 avahi-autoipd(eth1)[18092]: client: RTNETLINK answers: No such process
Jul 30 03:45:59 bonham32 dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Jul 30 03:45:59 bonham32 NetworkManager: <information>^IDHCP daemon state is now 1 (starting) for interface eth1
Jul 30 03:46:04 bonham32 dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Jul 30 03:46:09 bonham32 dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
Jul 30 03:46:22 bonham32 dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Jul 30 03:46:30 bonham32 dhclient: No DHCPOFFERS received.
Jul 30 03:46:30 bonham32 avahi-autoipd(eth1)[18120]: Found user 'avahi-autoipd' (UID 111) and group 'avahi-autoipd' (GID 116).
Jul 30 03:46:30 bonham32 avahi-autoipd(eth1)[18120]: Successfully called chroot().
Jul 30 03:46:30 bonham32 avahi-autoipd(eth1)[18120]: Successfully dropped root privileges.
Jul 30 03:46:30 bonham32 avahi-autoipd(eth1)[18120]: fopen() failed: Permission denied
Jul 30 03:46:30 bonham32 avahi-autoipd(eth1)[18120]: Starting with address 169.254.8.136
Jul 30 03:46:35 bonham32 avahi-autoipd(eth1)[18120]: Callout BIND, address 169.254.8.136 on interface eth1
Jul 30 03:46:35 bonham32 avahi-daemon[5004]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.8.136.
Jul 30 03:46:35 bonham32 avahi-daemon[5004]: New relevant interface eth1.IPv4 for mDNS.
Jul 30 03:46:35 bonham32 avahi-daemon[5004]: Registering new address record for 169.254.8.136 on eth1.IPv4.
Jul 30 03:46:39 bonham32 avahi-autoipd(eth1)[18120]: Successfully claimed IP address 169.254.8.136
Jul 30 03:46:39 bonham32 avahi-autoipd(eth1)[18120]: fopen() failed: Permission denied
Jul 30 03:46:39 bonham32 NetworkManager: <information>^IDHCP daemon state is now 9 (fail) for interface eth1

```

Running dhclient3 manually resolved the issue, but now I'm curious why the NIC ever got in this state and how to prevent this from happening in the future.

---

### Post by noob12 on 2007-07-30
OK.  For some reason it thinks it is sending out requests, but it isn't receiving a DHCP offer response or maybe it isn't really getting the request out.  

More diagnostic ideas:

Do the link state LEDs on the card and the switch to which it is connected look normal at the time of the DHCP renewal?

I suspect the requests are not really getting out or not getting to the server; maybe there is a problem with the card, cable, or driver.  Can you let us know what driver is associated by posting **lshw -C network** output?  

Install **ethtool** if you don't already have it and run **ethtool eth1**.  Ideally we could run this during a failed renewal.

Can you look on the server during this process or in logs to see if it thinks it has received a request from this client's MAC address?

Can you run a sniffer (tcpdump, ethereal or something) on a host on the same net as this DHCP client during the renewal?

As a temporary workaround you could try to raise the timeout on the client.  The default on Feisty is set to 30 seconds in the config. Apparently it is not getting a response in 30 seconds.  You can find and raise this in **/etc/dhcp3/dhclient.conf**.  Look for the **timeout** line.  Be careful not to remove the semi-colon at the end of the line.

---

### Post by charlesg3 on 2007-07-31
relevant information from lshw, note that this is identified as a bridge device on this computer

```
  *-bridge
       description: Ethernet interface
       product: MCP55 Ethernet
       vendor: nVidia Corporation
       physical id: 8
       bus info: pci@00:08.0
       logical name: eth1
       version: a2
       serial: 00:1a:4d:7b:fb:7e
       width: 32 bits
       clock: 66MHz
       capabilities: bridge bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.59 ip=10.1.1.6 latency=0 maxlatency=20 mingnt=1 multicast=yes
       resources: iomemory:fb103000-fb103fff ioport:e000-e007 iomemory:fb104000-fb1040ff iomemory:fb105000-fb10500f irq:17

```

The link state line remains on throughout the disconnection process.

I checked ethtool while the connection was down, I didn't notice any changes compared to when the connection was up, heres the output:


```
charles@bonham32:~$ sudo ethtool eth1
Settings for eth1:
        Supported ports: [ MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 1
        Transceiver: external
        Auto-negotiation: on
        Supports Wake-on: g
        Wake-on: d
        Link detected: yes

```


This is what I continuously see on the server's syslog, however it looks like the same text comes out during a connection loss as when the connection is up...

```
Jul 31 09:56:23 localhost dhcpd: DHCPREQUEST for 10.1.1.6 from 00:1a:4d:7b:fb:7e (bonham32) via eth1
Jul 31 09:56:23 localhost dhcpd: DHCPACK on 10.1.1.6 to 00:1a:4d:7b:fb:7e (bonham32) via eth1
Jul 31 09:56:23 localhost dhcpd: send_packet: Operation not permitted

```

(note this computer changed ip's from 10.1.1.15 to 10.1.1.6). Let me know if I should pursue ethereal from another computer.

---

### Post by noob12 on 2007-07-31
This suggests the DHCP server is getting the request but bonham32 is not getting the response.

By any chance do you have a firewall running on the client host (bonham32)?  Can you verify that it is allowing incoming UDP traffic on port 68?

---

### Post by noob12 on 2007-08-01
If you're sure you're not running a firewall, I'd try doing the scan with ethereal or tcpdump and a separate host on the net.  We want to know if the DHCP response is actually coming back or not.


If it is not, I'd look further into this line from your server's log
> 
dhcpd: send_packet: Operation not permitted

in your message. This suggests outbound firewalling on the server may be preventing DHCP ACKs (typically renewal responses) from getting out the gate.  That's also something to look at.

---

### Post by charlesg3 on 2007-08-01
It seems I was missing an entry in iptables

```

# dhcp
iptables -A INPUT -p UDP -i $LAN_IF --dport 67 --sport 68 -j ACCEPT

```

to fix that message... I'll post whether this resolves the error.

---

### Post by noob12 on 2007-08-01
If this is on the client, then the rule has to accept traffic *into* UDP port 68, not 67. 

Furthermore, strictly speaking, the source port on the response from the server is not guaranteed to be 67, thought it may be conventionally.  You may be able to filter on source IP address if you really want some restriction.

```

iptables -A INPUT -p UDP -i $LAN_IF [COLOR="Red"]--dport 68[/COLOR] -j ACCEPT

```

---

### Post by charlesg3 on 2007-08-03
The problem now seems to be solved, the above listed iptables entry was on the gateway/dhcp server (thus the reversal of dest/src). Let me know if you think I should make any changes in light of where the firewall is.

Thanks again for all the help.

---

### Post by noob12 on 2007-08-03
OK. And on the server, make sure that the iptables OUTPUT chain also allows the output message.  If your OUTPUT chain is already empty with a policy of ACCEPT, then you're fine.  Otherwise, make sure you have a rule like this

```

iptables -A OUTPUT -p UDP --dport 68 -j ACCEPT

```

The send_packet on DHCP ACKs should not fail as indicated in that one server log snippet.  If you still see that message logged then you still need to look at the firewall rules.

I'll watch the thread another day or two, in case there's an issue, but I think it's basically the firewall, and if you get that set up right, things should work normally.

---

### Post by charlesg3 on 2007-08-21
For some reason, this problem seems to have popped up again. This time the ip address keeps changing after the connection goes down.

This is the output from syslog:

```
Aug 21 20:16:05 localhost last message repeated 2 times
Aug 21 20:16:07 localhost avahi-daemon[4835]: Withdrawing address record for 10.1.1.47 on eth1.
Aug 21 20:16:07 localhost avahi-daemon[4835]: Leaving mDNS multicast group on interface eth1.IPv4 with address 10.1.1.47.
Aug 21 20:16:07 localhost avahi-daemon[4835]: Interface eth1.IPv4 no longer relevant for mDNS.
Aug 21 20:16:07 localhost avahi-autoipd(eth1)[10962]: Found user 'avahi-autoipd' (UID 111) and group 'avahi-autoipd' (GID 116).
Aug 21 20:16:07 localhost avahi-autoipd(eth1)[10962]: Successfully called chroot().
Aug 21 20:16:07 localhost avahi-autoipd(eth1)[10962]: Successfully dropped root privileges.
Aug 21 20:16:07 localhost avahi-autoipd(eth1)[10962]: fopen() failed: Permission denied
Aug 21 20:16:07 localhost avahi-autoipd(eth1)[10962]: Starting with address 169.254.8.136
Aug 21 20:16:11 localhost avahi-autoipd(eth1)[10962]: Callout BIND, address 169.254.8.136 on interface eth1
Aug 21 20:16:11 localhost avahi-daemon[4835]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.8.136.
Aug 21 20:16:11 localhost avahi-daemon[4835]: New relevant interface eth1.IPv4 for mDNS.
Aug 21 20:16:11 localhost avahi-daemon[4835]: Registering new address record for 169.254.8.136 on eth1.IPv4.
Aug 21 20:16:15 localhost avahi-autoipd(eth1)[10962]: Successfully claimed IP address 169.254.8.136
Aug 21 20:16:15 localhost avahi-autoipd(eth1)[10962]: fopen() failed: Permission denied
Aug 21 20:16:15 localhost avahi-autoipd(eth1)[10962]: Got SIGTERM, quitting.
Aug 21 20:16:15 localhost avahi-autoipd(eth1)[10962]: Callout STOP, address 169.254.8.136 on interface eth1
Aug 21 20:16:15 localhost avahi-daemon[4835]: Withdrawing address record for 169.254.8.136 on eth1.
Aug 21 20:16:15 localhost avahi-daemon[4835]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.8.136.
Aug 21 20:16:15 localhost avahi-daemon[4835]: Interface eth1.IPv4 no longer relevant for mDNS.
Aug 21 20:16:15 localhost avahi-autoipd(eth1)[10963]: client: RTNETLINK answers: No such process
Aug 21 20:16:16 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Aug 21 20:16:17 localhost dhclient: DHCPOFFER from 10.1.1.1
Aug 21 20:16:17 localhost dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Aug 21 20:16:17 localhost dhclient: DHCPACK from 10.1.1.1
Aug 21 20:16:17 localhost avahi-daemon[4835]: Joining mDNS multicast group on interface eth1.IPv4 with address 10.1.1.46.
Aug 21 20:16:17 localhost avahi-daemon[4835]: New relevant interface eth1.IPv4 for mDNS.
Aug 21 20:16:17 localhost avahi-daemon[4835]: Registering new address record for 10.1.1.46 on eth1.IPv4.
Aug 21 20:16:17 localhost avahi-daemon[4835]: Withdrawing address record for 10.1.1.46 on eth1.
Aug 21 20:16:17 localhost avahi-daemon[4835]: Leaving mDNS multicast group on interface eth1.IPv4 with address 10.1.1.46.
Aug 21 20:16:17 localhost avahi-daemon[4835]: Interface eth1.IPv4 no longer relevant for mDNS.
Aug 21 20:16:17 localhost avahi-daemon[4835]: Joining mDNS multicast group on interface eth1.IPv4 with address 10.1.1.46.
Aug 21 20:16:17 localhost avahi-daemon[4835]: New relevant interface eth1.IPv4 for mDNS.
Aug 21 20:16:17 localhost avahi-daemon[4835]: Registering new address record for 10.1.1.46 on eth1.IPv4.
Aug 21 20:16:17 localhost dhclient: bound to 10.1.1.46 -- renewal in 129 seconds.

```

The output from the gateway's syslog looks like the following:

```
Aug 21 19:15:25 localhost dhcpd: DHCPACK on 10.1.1.47 to 00:1a:4d:7b:fb:7e (bonham32) via eth1
Aug 21 19:15:37 localhost dhcpd: DHCPREQUEST for 10.1.1.46 from 00:1a:4d:7b:fb:7e (bonham32) via eth1
Aug 21 19:15:37 localhost dhcpd: DHCPACK on 10.1.1.46 to 00:1a:4d:7b:fb:7e (bonham32) via eth1
Aug 21 19:15:51 localhost dhcpd: DHCPREQUEST for 10.1.1.46 from 00:1a:4d:7b:fb:7e (bonham32) via eth1
Aug 21 19:15:51 localhost dhcpd: DHCPACK on 10.1.1.46 to 00:1a:4d:7b:fb:7e (bonham32) via eth1
Aug 21 19:16:03 localhost dhcpd: DHCPREQUEST for 10.1.1.46 from 00:1a:4d:7b:fb:7e (bonham32) via eth1
Aug 21 19:16:03 localhost dhcpd: DHCPACK on 10.1.1.46 to 00:1a:4d:7b:fb:7e (bonham32) via eth1
Aug 21 19:16:14 localhost dhcpd: DHCPREQUEST for 10.1.1.46 from 00:1a:4d:7b:fb:7e (bonham32) via eth1
Aug 21 19:16:14 localhost dhcpd: DHCPACK on 10.1.1.46 to 00:1a:4d:7b:fb:7e (bonham32) via eth1
Aug 21 19:16:27 localhost dhcpd: DHCPREQUEST for 10.1.1.46 from 00:1a:4d:7b:fb:7e (bonham32) via eth1
Aug 21 19:16:27 localhost dhcpd: DHCPACK on 10.1.1.46 to 00:1a:4d:7b:fb:7e (bonham32) via eth1
Aug 21 19:16:28 localhost dhcpd: DHCPREQUEST for 10.1.1.49 from 00:40:05:60:fa:e2 (DI-614+) via eth1
Aug 21 19:16:28 localhost dhcpd: DHCPACK on 10.1.1.49 to 00:40:05:60:fa:e2 (DI-614+) via eth1
Aug 21 19:16:41 localhost dhcpd: DHCPREQUEST for 10.1.1.46 from 00:1a:4d:7b:fb:7e (bonham32) via eth1
Aug 21 19:16:41 localhost dhcpd: DHCPACK on 10.1.1.46 to 00:1a:4d:7b:fb:7e (bonham32) via eth1
Aug 21 19:16:50 localhost dhcpd: DHCPREQUEST for 10.1.1.5 from 00:40:63:e5:bf:24 (biggiesmalls) via eth1
Aug 21 19:16:50 localhost dhcpd: DHCPACK on 10.1.1.5 to 00:40:63:e5:bf:24 (biggiesmalls) via eth1
Aug 21 19:16:55 localhost dhcpd: DHCPREQUEST for 10.1.1.46 from 00:1a:4d:7b:fb:7e (bonham32) via eth1
Aug 21 19:16:55 localhost dhcpd: DHCPACK on 10.1.1.46 to 00:1a:4d:7b:fb:7e (bonham32) via eth1
Aug 21 19:17:07 localhost dhcpd: DHCPDISCOVER from 00:1a:4d:7b:fb:7e (bonham32) via eth1
Aug 21 19:17:07 localhost dhcpd: DHCPOFFER on 10.1.1.46 to 00:1a:4d:7b:fb:7e (bonham32) via eth1
Aug 21 19:17:07 localhost dhcpd: DHCPREQUEST for 10.1.1.46 (10.1.1.1) from 00:1a:4d:7b:fb:7e (bonham32) via eth1
Aug 21 19:17:07 localhost dhcpd: DHCPACK on 10.1.1.46 to 00:1a:4d:7b:fb:7e (bonham32) via eth1
Aug 21 19:17:30 localhost dhcpd: DHCPREQUEST for 10.1.1.47 from 00:1a:4d:7b:fb:7e (bonham32) via eth1
Aug 21 19:17:30 localhost dhcpd: DHCPACK on 10.1.1.47 to 00:1a:4d:7b:fb:7e (bonham32) via eth1

```

Note that the following line no longer appears which makes me think this problem is different from the previous (iptables) problem.
```

Jul 31 09:56:23 localhost dhcpd: send_packet: Operation not permitted
```

---

