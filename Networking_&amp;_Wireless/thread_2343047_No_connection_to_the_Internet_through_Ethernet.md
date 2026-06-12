---
title: "No connection to the Internet through Ethernet"
date: 2016-11-12
forum: Networking &amp; Wireless
---

### Post by kalojan_lm on 2016-11-12
Hello, everyone.
I use 32-bit Ubuntu 12.04(kernel 3.2.0-80-generic) on eMachines E725 laptop with Pentium Dual-Core CPU T4200 2.00GHz and 2,9&#8202;GiB of RAM. 
I have the following problem. When i connect network cable to the Internet, it gives me indication that connection is done, but i have no possibility to load any page. When i try to pinging the gateway, it gives me this:

```
kalojan@eMachines-E725:~$ ping 77.70.0.1
PING 77.70.0.1 (77.70.0.1) 56(84) bytes of data.
From 77.70.0.41 icmp_seq=6 Destination Host Unreachable
From 77.70.0.41 icmp_seq=20 Destination Host Unreachable
From 77.70.0.41 icmp_seq=23 Destination Host Unreachable




```

Here is the output of ```
lshw -c network
``` :
```
 *-network
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: c0
       serial: 00:23:5a:63:15:80
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:45 memory:d3500000-d353ffff ioport:1000(size=128)

```And here is the output of ```
ifconfig -a
``` for eth0 and lo interfaces:
```
eth0      Link encap:Ethernet  HWaddr 00:23:5a:63:15:80  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:5815 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31329 errors:0 dropped:0 overruns:0 carrier:6
          collisions:0 txqueuelen:1000 
          RX bytes:551437 (551.4 KB)  TX bytes:2329893 (2.3 MB)
          Interrupt:45 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:232959 errors:0 dropped:0 overruns:0 frame:0
          TX packets:232959 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13845697 (13.8 MB)  TX bytes:13845697 (13.8 MB)

```I'm also trying to reset the interface with```
 sudo /etc/init.d/networking restart  
``` and also with ifdown and ifup and ```
sudo service network-manager restart
``` without effect. I also try sudo ```
lshw -c network -sanitize 
``` and here is the output: 
```

*-network
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: c0
       serial: [REMOVED]
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:45 memory:d3500000-d353ffff ioport:1000(size=128) 



```
Here is my /etc/network/interfaces:
 ```
auto lo
iface lo inet loopback


auto eth0
iface eth0 inet static
address 77.70.0.41
netmask 255.255.255.0
gateway 77.70.0.1


dns-nameservers 89.190.192.247

```
From the output of arp -a:
```
kalojan@eMachines-E725:~$ sudo arp -a
? (77.70.0.1) at <incomplete> on eth0 (77.70.0.1 is the IP of my gateway!)

```
i see that there is incomplete MAC address for the gateway. But i don't think that the problem is in the cable or gateway itself, because i try to connect to the same network another laptop and it works. So, is there any ideas where may be the problem. Sorry for poor english skills, its not my native language, i am new to Linux also.
Thanks for the answers in advance!

---

### Post by SeijiSensei on 2016-11-12
Well, the results you post indicate the interface has not been assigned an Ethernet address.

Let's see how we fare if you set things up manually.  Try this:
```

sudo ifconfig eth0 77.70.0.41 netmask 255.255.255.0 broadcast 77.70.0.255
sudo ip route add default gw 77.70.0.1

```

Can you then ping 77.70.0.1?  How about external machines like 8.8.8.8?

---

### Post by kalojan_lm on 2016-11-12
Here is the output:
```
kalojan@eMachines-E725:~$ sudo ifconfig eth0 77.70.0.41 netmask 255.255.255.0 broadcast 77.70.0.255
[sudo] password for kalojan: 
kalojan@eMachines-E725:~$ sudo ip route add default gw 77.70.0.1
Error: either "to" is duplicate, or "gw" is a garbage.
kalojan@eMachines-E725:~$ 
```
77.70.0.1 is still unreachable.

---

### Post by kalojan_lm on 2016-11-12
I change "gw" to "via" and the output is:
```
kalojan@eMachines-E725:~$ sudo ip route add default via 77.70.0.1
RTNETLINK answers: File exists

```
The result of pinging:
```

kalojan@eMachines-E725:~$ ping 77.70.0.1
PING 77.70.0.1 (77.70.0.1) 56(84) bytes of data.
From 77.70.0.41 icmp_seq=3 Destination Host Unreachable
^C
--- 77.70.0.1 ping statistics ---
6 packets transmitted, 0 received, +1 errors, 100% packet loss, time 5026ms
```

---

### Post by SeijiSensei on 2016-11-12
Are you sure you're supposed to be using 77.70.0.41 as your IP address?  Is there any other machine on the network with that address?  Do you not have a firewalling router between yourself and the Interent?  When you connect with the laptop you mentioned what IP address does it get?  (If you're using Windows, click Start and type "cmd" in the program box.  In the terminal window that appears, type "ipconfig /all" to see what address the machine is assigned.)  Is it also in the 77.70.0.1-254 range?  Or is it a private address like 192.168.1.20?  Are you sure it's not the router with the 77 address on the outside masquerading a private subnet to which you are connecting?  What happens if you use
```

auto eth0
iface eth0 inet dhcp

```
instead of a static address in /etc/network/interfaces?

Sorry about the "gw" vs. "via" business.  Over the years I've used both the old "route" command which uses "gw" and the newer "ip route" command which uses "via".  Sometimes I get them confused.

---

### Post by kalojan_lm on 2016-11-12
My answers on the questions:
1. My IP is manually set and the machine worked with with it for 1 year( it is the same IP on the another machine which work without problem at the moment).
2. I personally don't know is there another machine on the network with such address.
3. No, there is no router between me and the network, it is direct connection.
4. I change the lines in the file and reset the network manager. Still no connection
5. > [COLOR=#000000]Are you sure it's not the router with the 77 address on the outside masquerading a private subnet to which you are connecting? [/COLOR] I don't know, but i don't think that this is the case.

---

### Post by SeijiSensei on 2016-11-12
If there is another machine with the same IP running on the network, then you cannot use the same IP on a different machine at the same time.  The upstream router will not know where to send packets for the .41 address.  Disconnect the other machine and try again with the static configuration you had before.

If you want to have multiple machines on this connection, then either you need to have your provider give you a "subnet," or you need to put a masquerading router between your local network and the 77.70.0.1 machine upstream.  A subnet would include a range of addresses in batches of (2^k-2) for k=2,3, ..., 8, i.e, two, six, fourteen, thirty, etc. hosts.  Subnets are costly and hard to obtain.  You're probably better off buying a cheap router.

---

### Post by kalojan_lm on 2016-11-12
Yes, there is another laptop in addititon to the first(this one with the problem discussed here), but they are not running at the same time. If i want to connect the first laptop, i must disconnect this from i writitng at the moment. Is it possible the problem to be with network adapter of the first laptop? How to check?

---

### Post by SeijiSensei on 2016-11-15
I really think your problems would be better solved by buying a router, connecting it to the Internet, and connecting the machines to it.  If everything is connected via Ethernet, you could use something like [http://www.newegg.com/Product/Product.aspx?Item=N82E16833704070](http://www.newegg.com/Product/Product.aspx?Item=N82E16833704070).  If you want to support wireless devices, you'll need a wifi router.

Furthermore, connecting any computer using any operating system directly to the Internet is dangerous unless you have a trustworthy firewall in place.  Using a router will provide greater security for your systems and network as well.

I doubt you're having a problem with the network adapter.

---

