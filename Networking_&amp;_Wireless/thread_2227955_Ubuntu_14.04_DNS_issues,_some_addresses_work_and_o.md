---
title: "Ubuntu 14.04 DNS issues, some addresses work and others do not"
date: 2014-06-04
forum: Networking &amp; Wireless
---

### Post by Steve_Daubs on 2014-06-04
This is my first Ubuntu install for myself although I generally work with older LINUX versions at work so I *thought* I knew what I was doing but it is clear that I do not. I installed Ubuntu 14.04 Desktop on a newly built PC with no other OS on it. The DNS lookup has been inconsistent and I'm tried to follow various fixes on this forum which has likely left me with one or two messed up configuration files. The shorter version of what is happening is that if I try to go to google.com in Firefox, it cannot find the web site. If I go to 190.167.241.187, the google.com web site appears and allows me to search until I try to click on one of the links which will fail again. If I try to go to my ISP's web site, it does work ([www.mtco.com]("http://www.mtco.com")) as does other sites hosted on it (which makes perfect sense to me). A handful of nearby businesses also load while others will not which implies that my ISP isn't hosting them or at least isn't finding them in some way. Now none of this is an issue on the Win7 machines attached to the same network and that the Ubuntu computer and the Win7 machines can see each other on the network and share files using samba.

Here's some of the files/data that I've seen requested so I hope that this helps:

```

uname -a
Linux ubuntu-storage 3.13.0-27-generic #50-Ubuntu SMP Thu May 15 18:06:16 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```

```

nm-tool -a



NetworkManager Tool


State: connected (global)


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        E0:3F:49:AB:B4:1F


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.1.37
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             8.8.8.8
    DNS:             192.168.1.1
    DNS:             4.4.4.4
    DNS:             208.67.222.222
    DNS:             208.67.220.220





```

```
ifconfig -a

eth0      Link encap:Ethernet  HWaddr e0:3f:49:ab:b4:1f  
          inet addr:192.168.1.37  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fd85:2f46:5909:1:e23f:49ff:feab:b41f/64 Scope:Global
          inet6 addr: fd85:2f46:5909:1:4189:17c:57e1:3e6/64 Scope:Global
          inet6 addr: fe80::e23f:49ff:feab:b41f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6681 errors:0 dropped:1 overruns:0 frame:0
          TX packets:1112 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:902379 (902.3 KB)  TX bytes:193004 (193.0 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:273 errors:0 dropped:0 overruns:0 frame:0
          TX packets:273 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30725 (30.7 KB)  TX bytes:30725 (30.7 KB)



```

```
ping google.com

PING google.com (74.125.225.8) 56(84) bytes of data.
From 192.168.1.37 icmp_seq=1 Destination Port Unreachable
From 192.168.1.37 icmp_seq=2 Destination Port Unreachable
From 192.168.1.37 icmp_seq=3 Destination Port Unreachable
From 192.168.1.37 icmp_seq=4 Destination Port Unreachable


--- google.com ping statistics ---
4 packets transmitted, 0 received, +4 errors, 100% packet loss, time 3001ms



```

```
ping 190.167.241.187

PING 190.167.241.187 (190.167.241.187) 56(84) bytes of data.
64 bytes from 190.167.241.187: icmp_seq=1 ttl=48 time=106 ms
64 bytes from 190.167.241.187: icmp_seq=2 ttl=48 time=79.9 ms
64 bytes from 190.167.241.187: icmp_seq=3 ttl=48 time=80.0 ms
64 bytes from 190.167.241.187: icmp_seq=4 ttl=48 time=80.2 ms


--- 190.167.241.187 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3003ms
rtt min/avg/max/mdev = 79.947/86.731/106.714/11.537 ms



```

```
grep -i error syslog

Jun  4 19:54:51 ubuntu-storage NetworkManager[31447]: <error> [1401929691.382983] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Jun  4 20:07:49 ubuntu-storage NetworkManager[31826]: <error> [1401930469.607260] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Jun  4 20:12:14 ubuntu-storage NetworkManager[32298]: <error> [1401930734.617787] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Jun  4 20:14:35 ubuntu-storage NetworkManager[32572]: <error> [1401930875.41609] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Jun  4 20:19:10 ubuntu-storage kernel: [    4.557604] EXT4-fs (sdd1): re-mounted. Opts: errors=remount-ro
Jun  4 20:19:13 ubuntu-storage NetworkManager[1172]: <error> [1401931153.643999] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Jun  4 20:30:15 ubuntu-storage NetworkManager[3430]: <error> [1401931815.449475] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Jun  4 20:50:03 ubuntu-storage NetworkManager[4051]: <error> [1401933003.799760] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Jun  4 21:02:11 ubuntu-storage kernel: [    4.387545] EXT4-fs (sdd1): re-mounted. Opts: errors=remount-ro
Jun  4 21:02:14 ubuntu-storage NetworkManager[1229]: <error> [1401933734.777434] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Jun  4 21:06:58 ubuntu-storage NetworkManager[3442]: <error> [1401934018.792370] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Jun  4 21:25:09 ubuntu-storage kernel: [    4.647486] EXT4-fs (sdd1): re-mounted. Opts: errors=remount-ro
Jun  4 21:25:13 ubuntu-storage NetworkManager[1277]: <error> [1401935113.788933] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name



```

```
route

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0



```

```
lshw -class network

  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 09
       serial: e0:3f:49:ab:b4:1f
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168f-1_0.0.5 06/18/12 ip=192.168.1.37 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:50 ioport:e000(size=256) memory:d0004000-d0004fff memory:d0000000-d0003fff



```

```
nslookup ubuntu.com

Server:        208.67.222.222
Address:    208.67.222.222#53


Non-authoritative answer:
Name:    ubuntu.com
Address: 91.189.94.156



```

```
nslookup google.com

Server:        208.67.222.222
Address:    208.67.222.222#53


Non-authoritative answer:
Name:    google.com
Address: 173.194.43.71
Name:    google.com
Address: 173.194.43.72
Name:    google.com
Address: 173.194.43.66
Name:    google.com
Address: 173.194.43.65
Name:    google.com
Address: 173.194.43.69
Name:    google.com
Address: 173.194.43.67
Name:    google.com
Address: 173.194.43.68
Name:    google.com
Address: 173.194.43.70
Name:    google.com
Address: 173.194.43.78
Name:    google.com
Address: 173.194.43.64
Name:    google.com
Address: 173.194.43.73



```

```
cat /etc/resolv.conf

# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN


#nameserver 8.8.8.8
nameserver 208.67.222.222
nameserver 208.67.220.220




nameserver 127.0.1.1
search zyxel.com



```

```
cat /etc/network/interfaces

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


auto eth0
iface eth0 inet static
address 192.168.1.37
netmask 255.255.255.0
gateway 192.168.1.1


search ns.mtco.com ns2.mtco.com
dns-nameserver 127.0.1.1











```

And in case it helps, the ipconfig/all on my windows 7 PC (just a computer on the same LAN as the Ubuntu computer):
```
ipconfig /all



Windows IP Configuration


   Host Name . . . . . . . . . . . . : Main-Steve-PC
   Primary Dns Suffix  . . . . . . . : 
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No
   DNS Suffix Search List. . . . . . : zyxel.com


Ethernet adapter Local Area Connection 2:


   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : TAP-Win32 Adapter V9
   Physical Address. . . . . . . . . : 00-FF-F4-27-FC-E1
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes


Ethernet adapter Local Area Connection:


   Connection-specific DNS Suffix  . : zyxel.com
   Description . . . . . . . . . . . : Realtek PCIe GBE Family Controller
   Physical Address. . . . . . . . . : 1C-6F-65-AC-5A-37
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   IPv6 Address. . . . . . . . . . . : fd85:2f46:5909:1:781c:c99e:8bc3:7941(Preferred) 
   Temporary IPv6 Address. . . . . . : fd85:2f46:5909:1:68d5:947d:7fb5:ecb1(Preferred) 
   Link-local IPv6 Address . . . . . : fe80::781c:c99e:8bc3:7941%11(Preferred) 
   IPv4 Address. . . . . . . . . . . : 192.168.1.46(Preferred) 
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : Sunday, June 01, 2014 8:43:51 AM
   Lease Expires . . . . . . . . . . : Thursday, June 05, 2014 5:50:33 PM
   Default Gateway . . . . . . . . . : 192.168.1.1
   DHCP Server . . . . . . . . . . . : 192.168.1.1
   DNS Servers . . . . . . . . . . . : 192.168.1.1
   NetBIOS over Tcpip. . . . . . . . : Enabled


Tunnel adapter isatap.{78AADCF8-8903-44AA-828C-BE166B53D0AC}:


   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes


Tunnel adapter Teredo Tunneling Pseudo-Interface:


   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes



```

---

### Post by steeldriver on 2014-06-05
Hello and welcome to the forums

Based on your ping and nslookup results, this looks more like a routing issue than a DNS issue. Regardless, you seem to have a bit of a dog's breakfast of a configuration there so my suggestion would be to set everything back to square one and then try to troubleshoot from there.

1. edit your /etc/network/interfaces file back to the default localhost-only configuration - this will let the GUI networkmanager take full control again (it can cause conflicts if both networkmanager and the server-style networking service are trying to configure the same interface)
```

auto lo
iface lo inet loopback

```

2. reconfigure the reolvconf package
```

sudo dpkg-reconfigure resolvconf

```
It will present you with a question about preparing /etc/resolv.conf for dynamic updates - answer "Yes". It may also present you with another question about temporarily appending your existing config to the dynamic one - I suggest answering "No" to that one. 

3. set up a plain vanilla DHCP connection via the networkmanager GUI (either by clicking on the desktop icon, or by running nm-connection-editor from a terminal). It should look like the attached screenshot except select **Automatic (DHCP)** instead of Manual

If that doesn't work, next step would be to try **Automatic (DHCP) address only** and enter DNS addresses manually, however based on the ipconfig from your Windows box it seems that works OK without explicit DNS server specification.

---

### Post by Steve_Daubs on 2014-06-07
steeldriver,

Firstly, thanks for the welcome and the reply. Secondly, thank you for the new-to-me phrase of dog's breakfast. I'm going to working that into my conversations asap.

So I've tried to do the various fixes/ideas in the post and I'm still seeing the same basic error of some local domains (hosted by my ISP basically) working and most others failing. My current Wired Connection is configured as Automatic (DHCP) address only using just 208.67.222.222 as the DNS entry

My current /etc/networking/interfaces
```
# interfaces(5) file used by ifup(8) and ifdown(8)auto lo
iface lo inet loopback



```

My current /etc/resolv.conf
```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN


nameserver 127.0.1.1



```

route
```
Kernel IP routing tableDestination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     *               255.255.255.0   U     1      0        0 eth0



```

nm-tool -a
```


NetworkManager Tool


State: connected (global)


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        E0:3F:49:AB:B4:1F


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.1.37
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             208.67.222.222





```

Any other ideas to try? Or any other logs/tools to add to this reply?

---

### Post by steeldriver on 2014-06-07
Is

```
# interfaces(5) file used by ifup(8) and ifdown(8)auto lo
iface lo inet loopback
```

just a transcription error? the 'auto lo' part needs to be separated from the comment line i.e.

```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
```

Apart from that, everything looks OK - you appear to have a valid IPv4 address (192.168.1.37) and DNS server (208.67.222.222 - OpenDNS?). If you're still having webiste loading problems then the 2 things that come to mind are

1. the chosen IP is not unique on your LAN i.e. there is another device also assigned that address

2. (more likely, since you appear to be using DHCP not static addressing) it is some kind of MTU issue

Here's a little one-liner you can run to test the maximum non-fragmenting MTU:

```
size=1272; while ping -s $size -c1 -M do google.com >&/dev/null; do ((size+=4)); done; echo "Max MTU size: $((size-4+28))"
```

If it comes back with a number less than 1500 (which iirc is the default automatic choice) we can try setting a manual value for the connection and see if that helps

---

### Post by Steve_Daubs on 2014-06-07
Thank you for the reply. 

Yea, that was a small issue on my copy & paste. The /etc/network/interfaces file is as such:

```


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback



```

So I ran the short script that you sent. When I ran it using google.com, it returned a Max MTU size of 1296 immediately. As I cannot connect to google.com by domain, I tried it with an address that I did have access to ([www.mtco.com]("http://www.mtco.com")) and that returned as 1452. And yes, that one DNS is OpenDNS's first/Primary DNS. I was having problems pinging 8.8.8.8 so I tried the next one that would ping properly.

I opened the Wired Connection 1 setup in Ubuntu and changed the Ethernet MTU setting to 1452. I've rebooted and it is still acting the same way. IP address of 192.168.1.37, connecting to locally-hosted by my ISP sites, connecting by IP addresses, not connecting to yahoo, google, or bing by domain name.

Next suggestion?

---

### Post by steeldriver on 2014-06-07
Hmm... you could try a *really* small MTU (in the 100's) - or even re-running the max MTU one-liner on google.com but starting from size=0 ?

---

### Post by Steve_Daubs on 2014-06-07
> **steeldriver said:**
> Hmm... you could try a *really* small MTU (in the 100's) - or even re-running the max MTU one-liner on google.com but starting from size=0 ?

Just tried both. With google.com and starting at zero, I got a Max MTU size of 24. Starting at zero and going to [www.mtco.com]("http://www.mtco.com") instead, I got a Max MTU of 1452 (which I think is the same number I got the first time)

---

### Post by steeldriver on 2014-06-07
Well that sounds like something very wrong - either a very sick network card, or intermediate router - what does

```

tracepath google.com

```

say? it may take some time, and you may want to kill it with Ctrl-C once you get down to a whole lot of 'no reply' responses

---

### Post by Steve_Daubs on 2014-06-08
steeldriver,

Sorry I didn't reply. Work and family called (literally in one case) and I just got back to this. I have reset the eth0 connection to automatic (DHCP) and removed any additional DNS servers. I'm hoping that is issue is not the ethernet card as I've already had to replace the original MSI motherboard with this ASUS one.

I've tried running tracepath and its Windows 7 equivalent pathping to see if there are any useful details in this:

**Ubuntu 14.04**

```


steve@ubuntu-storage:~$ steve@ubuntu-storage:~$ tracepath google.com
 1?: [LOCALHOST]                                         pmtu 1452
 1:  192.168.1.37                                          0.314ms reached
 1:  192.168.1.37                                          0.251ms reached
     Resume: pmtu 1452 hops 1 back 1

```

```

steve@ubuntu-storage:~$ tracepath mtco.com
 1?: [LOCALHOST]                                         pmtu 1452
 1:  NBG-419N.zyxel.com                                    0.870ms
 1:  NBG-419N.zyxel.com                                    0.740ms
 2:  207-179-210-1.mtco.com                                3.276ms
 3:  marsbb1-eth-1-21.mtco.com                             4.296ms
 4:  metabb1-ve-201.mtco.com                               9.057ms
 5:  ghillsbb1-ve-202.mtco.com                             5.244ms
 6:  ghillser1-ve-211.mtco.com                             5.649ms
 7:  no reply
 8:  no reply
 9:  no reply
^C
steve@ubuntu-storage:~$

```


And an odd one, I tried cat.com vs [www.cat.com]("http://www.cat.com") and saw this:

```

steve@ubuntu-storage:~$ tracepath cat.com
 1?: [LOCALHOST]                                         pmtu 1452
 1:  192.168.1.37                                          0.121ms reached
 1:  192.168.1.37                                          0.266ms reached
     Resume: pmtu 1452 hops 1 back 1
steve@ubuntu-storage:~$ tracepath www.cat.com
 1?: [LOCALHOST]                                         pmtu 1452
 1:  192.168.1.1                                           0.840ms
 1:  192.168.1.1                                           0.616ms
 2:  207-179-210-1.mtco.com                                4.048ms
 3:  marsbb1-eth-1-21.mtco.com                             3.848ms
 4:  metabb1-ve-201.mtco.com                               5.565ms
 5:  ghillsbb1-ve-202.mtco.com                             5.686ms
 6:  ghillser1-ve-211.mtco.com                             5.595ms
 7:  akamai.mtco.com                                       6.173ms reached
     Resume: pmtu 1452 hops 7 back 7



```

**Windows 7**

I did not include the stats for any of pathping commands. 
```

C:\Windows>pathping www.gooogle.com


Tracing route to www.gooogle.com [74.125.225.88]
over a maximum of 30 hops:
  0  Main-Steve-PC.zyxel.com [192.168.1.46]
  1  NBG-419N.zyxel.com [192.168.1.1]
  2  207-179-210-1.mtco.com [207.179.210.1]
  3  marsbb1-eth-1-21.mtco.com [207.179.252.105]
  4  chibb1-ve-207.mtco.com [207.179.253.58]
  5  208.68.86.197
  6  xe-5-1-0.er2.ord2.us.above.net [208.185.185.65]
  7  ae15.cr2.ord2.us.above.net [64.125.24.149]
  8  ae11.cr1.ord2.us.above.net [64.125.20.245]
  9  ae5.er1.ord7.us.above.net [64.125.20.38]
 10  72.14.217.53
 11  209.85.254.128
 12  209.85.250.30
 13  ord08s07-in-f24.1e100.net [74.125.225.88]


Computing statistics for 325 seconds...

```

```
C:\Users\Steve>pathping www.mtco.com

Tracing route to www.mtco.com [207.179.255.20]
over a maximum of 30 hops:
  0  Main-Steve-PC.zyxel.com [192.168.1.46]
  1  NBG-419N.zyxel.com [192.168.1.1]
  2  207-179-210-1.mtco.com [207.179.210.1]
  3  marsbb1-eth-1-21.mtco.com [207.179.252.105]
  4  metabb1-ve-201.mtco.com [207.179.252.246]
  5  ghillsbb1-ve-202.mtco.com [207.179.252.253]
  6  ghillser1-ve-211.mtco.com [207.179.250.42]
  7  lb1.mtco.com [207.179.255.17]
  8  www.mtco.com [207.179.255.20]


Computing statistics for 200 seconds...
```

```
C:\Users\Steve>pathping cat.com

Tracing route to cat.com [192.56.231.67]
over a maximum of 30 hops:
  0  Main-Steve-PC.zyxel.com [192.168.1.46]
  1  NBG-419N.zyxel.com [192.168.1.1]
  2  207-179-210-1.mtco.com [207.179.210.1]
  3  marsbb1-eth-1-21.mtco.com [207.179.252.105]
  4  chibb1-ve-207.mtco.com [207.179.253.58]
  5  208.68.86.197
  6  xe-11-3-2.edge2.Chicago2.Level3.net [4.35.104.53]
  7  vl-3504-ve-118.ebr1.Chicago2.Level3.net [4.69.158.14]
  8  ae-1-51.edge3.Chicago3.Level3.net [4.69.138.136]
  9  sl-st20-chi-10-0-0.sprintlink.net [144.232.8.113]
 10  sl-crs2-chi-0-12-2-0.sprintlink.net [144.232.19.145]
 11  sl-cater3-605169-0.sprintlink.net [144.228.150.198]
 12     *        *        *
Computing statistics for 275 seconds...
```

---

### Post by steeldriver on 2014-06-08
Hmm.. I had kind of dismissed DNS as an issue since names appeared to be resolving - but perhaps we should look at what they're resolving *to*

```

dig +short cat.com

dig +short www.cat.com

dig @8.8.8.8 +short cat.com

dig @8.8.8.8 +short www.cat.com
```

and

```

nmcli dev list iface eth0 | grep 'DNS'
```

---

### Post by Steve_Daubs on 2014-06-08
OK,

Here's the results of each command:

```
root@ubuntu-storage:~# dig +short cat.com
192.56.231.67
root@ubuntu-storage:~# dig +short www.cat.com
www.cat.com.edgesuite.net.
a871.g.akamai.net.
165.254.94.123
165.254.94.155
root@ubuntu-storage:~# dig @8.8.8.8 +short cat.com
192.56.231.67
root@ubuntu-storage:~# dig @8.8.8.8 +short www.cat.com
www.cat.com.edgesuite.net.
a871.g.akamai.net.
165.254.94.123
165.254.94.155
root@ubuntu-storage:~# nmcli dev list iface eth0 | grep 'DNS'
IP4.DNS[1]:                             8.8.8.8
IP4.DNS[2]:                             192.168.1.1
root@ubuntu-storage:~#



```

I'm a little surprised to the see the 8.8.8.8 DNS in the list as I thought that I got rid of all of files that referenced it.

---

### Post by steeldriver on 2014-06-08
I think I'm ready to throw in the towel here - sorry. We've tried everything I can think of.

---

