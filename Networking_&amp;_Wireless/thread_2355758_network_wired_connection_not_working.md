---
title: "network wired connection not working"
date: 2017-03-16
forum: Networking &amp; Wireless
---

### Post by mailak on 2017-03-16
Hi, I am quite newbie to forum, Ubuntu and network connections and the problem is that after 1 day spent I cannot connect my Ubuntu 12.0.4 to wired connection even having read post threads like [https://ubuntuforums.org/showthread.php?t=2247351](https://ubuntuforums.org/showthread.php?t=2247351) still not being able to solve the problem.
What I have is:

1) sudo lshw -C network
 ```
 *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 78
       serial: 00:13:d3:c9:a9:09
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.5.0 duplex=half latency=32 link=no maxlatency=8 mingnt=3 multicast=yes port=MII speed=10Mbit/s
       resources: irq:23 ioport:ec00(size=256) memory:fc001000-fc0010ff
```

2) nm-tool
```
State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            via-rhine
  State:             unavailable
  Default:           no
  HW Address:        00:13:D3:C9:A9:09

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off
```

3) cat /etc/network/interfaces
```
auto lo
iface lo inet loopback
```

4) cat /etc/NetworkManager/NetworkManager.conf
```
[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=00:13:D3:C9:A9:09,

[ifupdown]
managed=false
```

5) cat /var/lib/NetworkManager/NetworkManager.state
```
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true
darek@Puchacz:/etc/network$
```

6) In Windows7 x64 connection is maybe not set perfectly but for sure working and Windows doesn't find any problems:

Connection-specific DNS Suffix: [www.huaweimobilewifi.com]("http://www.huaweimobilewifi.com")
Description: HUAWEI Mobile Connect - Network Card #3
Physical Address: &#8206;0C-5B-8F-27-9A-64
DHCP Enabled: Yes
IPv4 Address: 192.168.8.101
IPv4 Subnet Mask: 255.255.255.0
Lease Obtained: 16 marca 2017 12:50:23
Lease Expires: 17 marca 2017 12:50:23
IPv4 Default Gateway: 192.168.8.1
IPv4 DHCP Server: 192.168.8.1
IPv4 DNS Servers: 192.168.8.1, 192.168.8.1
IPv4 WINS Server: 
NetBIOS over Tcpip Enabled: Yes

I have turned on:
Client for Microsoft Networks
QoS Packet Scheduler
File and Printer Sharing for Microsoft Networks
Internet Protocol Version 4 (TCP/IPv4)
Link-Layer Topology Discovery Mapper I/O Driver
Link-Layer Topology Discovery Responder

---

### Post by SeijiSensei on 2017-03-16
Let's try something simple first.  What do you see if you run
```
sudo ifconfig eth0 up
```

If you can bring up the interface, then try
```
sudo ifconfig eth0 ip.addr.of.interface
```

What happens?

---

### Post by mailak on 2017-03-16
Hello, below is what I got:

sudo ifconfig eth0 up
```
I enter my password and no information is displayed
When repeated no password needed, no message displayed

```

sudo ifconfig eth0 ip.addr.of.interface
```
ip.addr.of.interface: Unknown host
ifconfig: `--help' gives usage information.
```

sudo ifconfig eth0
```
eth0      Link encap:Ethernet  HWaddr 00:13:d3:c9:a9:09
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0xc000
```

sudo ifconfig eth0 192.168.8.1
```
no response, no message displayed
```

sudo ifconfig eth0 192.168.8.101
```
no response, no message displayed
```

sudo ifconfig eth0 255.255.255.0
```
SIOCSIFADDR: Invalid argument
```

I tried also:

ping 192.168.8.1
```
PING 192.168.8.1 (192.168.8.1) 56(84) bytes of data.
From 192.168.8.101 icmp_seq=1 Destination Host Unreachable
From 192.168.8.101 icmp_seq=2 Destination Host Unreachable
From 192.168.8.101 icmp_seq=3 Destination Host Unreachable
From 192.168.8.101 icmp_seq=4 Destination Host Unreachable
From 192.168.8.101 icmp_seq=5 Destination Host Unreachable
From 192.168.8.101 icmp_seq=6 Destination Host Unreachable
From 192.168.8.101 icmp_seq=7 Destination Host Unreachable
```

netstat -at
```
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 localhost:ipp           *:*                     LISTEN
```

nslookup 134.170.185.46
```
no response, no message displayed, <Ctrl>+<C> to return to command line
```

traceroute google.com
```
The program 'traceroute' can be found in the following packages:
 * inetutils-traceroute
 * traceroute
Try: sudo apt-get install <selected package>
```

sudo apt-get install traceroute
```
[sudo] password for d****: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package traceroute is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package 'traceroute' has no installation candidate
```

sudo apt-get install inetutils-traceroute
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package inetutils-traceroute
```

I don't know either it matters but it seems that "Physical Address" seen by Windows7 (0C 5B 8F 27 9A 64) is different from MAC seen by Ubuntu 12.0.4 (00:13:d3:c9:a9:09)

Does all that mean someting?

---

### Post by mailak on 2017-03-23
C:\Users\...>ipconfig
```
C:\Users\D...>ipconfig

Windows IP Configuration


Ethernet adapter Local Area Connection 4:

   Connection-specific DNS Suffix  . : www.huaweimobilewifi.com
   IPv4 Address. . . . . . . . . . . : 192.168.8.101
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 192.168.8.1

Ethernet adapter Local Area Connection 3:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Tunnel adapter isatap.www.huaweimobilewifi.com:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Tunnel adapter isatap.{75A1928C-147C-464D-9308-121BA57B7746}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Tunnel adapter Teredo Tunneling Pseudo-Interface:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
```

C:\Users\D...>netstat
```
Active Connections

  Proto  Local Address          Foreign Address        State
  TCP    127.0.0.1:49171        Darco-PC:49172         ESTABLISHED
  TCP    127.0.0.1:49172        Darco-PC:49171         ESTABLISHED
  TCP    127.0.0.1:59361        Darco-PC:59362         ESTABLISHED
  TCP    127.0.0.1:59362        Darco-PC:59361         ESTABLISHED
  TCP    192.168.8.101:50954    r-149-58-45-5:http     ESTABLISHED
  TCP    192.168.8.101:59363    server-54-192-230-80:http  TIME_WAIT
  TCP    192.168.8.101:59395    waw02s08-in-f197:https  ESTABLISHED
  TCP    192.168.8.101:59451    lo-in-f189:https       ESTABLISHED
  TCP    192.168.8.101:59519    161.69.169.63:https    TIME_WAIT
  TCP    192.168.8.101:59774    r-172-58-45-5:http     TIME_WAIT
  TCP    192.168.8.101:59775    waw02s08-in-f206:https  ESTABLISHED
  TCP    192.168.8.101:59776    r-173-58-45-5:http     TIME_WAIT
```

---

### Post by chili555 on 2017-03-23
>  I cannot connect my Ubuntu 12.0.4 to wired connection Ubuntu 12.04 reaches end-of-life in a few weeks and will no longer receiver security updates.

Moreover, there has been so much progress in drivers, networking and drivers in the last five years. I urge you to upgrade to at least 16.04 LTS now.

Did I say soooo much progress?

---

