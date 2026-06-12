---
title: "Destination Host Unreachable"
date: 2015-06-22
forum: Networking &amp; Wireless
---

### Post by Curtis_G_Hanson on 2015-06-22
I installed Server 14.04 and for the life of me, cannot see what I've done wrong.

I am using a static IP from Comcast and have my server plugged directly into the SMC modem.

Here's what I got:

ifconfig -a

```

eth0      Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          inet addr:173.164.126.170  Bcast:173.164.126.175  Mask:255.255.255.248
          inet6 addr: fe80::214:22ff:fe22:5191/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:246 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:63 (63.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:567 errors:0 dropped:0 overruns:0 frame:0
          TX packets:567 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:143991 (143.9 KB)  TX bytes:143991 (143.9 KB)

```

route -n

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         173.164.126.174 0.0.0.0         UG    0      0        0 eth0
173.164.126.168 0.0.0.0         255.255.255.248 U     0      0        0 eth0


```

netstat -r

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
default         173.164.126.174 0.0.0.0         UG        0 0          0 eth0
173.164.126.168 *               255.255.255.248 U         0 0          0 eth0



```

cat /etc/network/interfaces

```
# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth0
iface eth0 inet static
address 173.164.126.170/29
gateway 173.164.126.174
dns-search fartinginelevators.com
dns-nameservers 75.75.75.75 75.75.76.76

```

cat /etc/hosts

```
127.0.0.1       localhost
173.164.126.170 fartinginelevators.com fartinginelevators


```

cat /etc/resolv.conf

```
nameserver 75.75.75.75
nameserver 75.75.76.76
search fartinginelevators.com


```

ip addr

```

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 00:00:00:0:00:00 brd ff:ff:ff:ff:ff:ff
    inet 173.164.126.170/29 brd 173.164.126.175 scope global eth0
       valid_lft forever preferred_lft forever
    inet6 fe80::214:22ff:fe22:5191/64 scope link 
       valid_lft forever preferred_lft forever

```

ip route

```

default via 173.164.126.174 dev eth0 
173.164.126.168/29 dev eth0  proto kernel  scope link  src 173.164.126.170


```

If I try to ping the gateway: 173.164.126.174

```

PING 173.164.126.174 (173.164.126.174) 56(84) bytes of data.
From 173.164.126.170 icmp_seq=1 Destination Host Unreachable

```

I have 5 static IPs from Comcast in the 173.164.126.174/29 block.
What have I possibly missed? I have double checked and triple checked the physical cable to the modem and I checked that switch controls on the SMC were opened as well.

Edit: Added ip commands and responses

---

### Post by TheFu on 2015-06-22
I have a similar setup - same router, same subnet /29.

```
Address:     	173.164.126.170       	10101101.10100100.01111110.10101 010
Netmask: 	255.255.255.248 = 29 	11111111.11111111.11111111.11111 000
Wildcard: 	0.0.0.7 	00000000.00000000.00000000.00000 111
=>
Network:     	173.164.126.168/29    	10101101.10100100.01111110.10101 000
HostMin: 	173.164.126.169 	10101101.10100100.01111110.10101 001
HostMax: 	173.164.126.174 	10101101.10100100.01111110.10101 110
Broadcast: 	173.164.126.175 	10101101.10100100.01111110.10101 111
Hosts/Net: 	6 	Class B
```

I'm using a router connected to their router. All my systems are behind different NAT LANs - each for a different public IP.

The first IP you can use is .169.  The .174 IP is your gateway address.

 /etc/network/interfaces has a mistake in the "address" line. Remove the /29.

I think you'll want/need to add a separate stanza to have each IP.  Might make more sense to setup virtual machines and assign 1 IP to each which runs a specific service on a port that cannot easily be shared with another system.  For example, "https" ... of course, you can use name-based virtualhosts for most web services and have a reverse proxy to handle the HTTPS parts and send the traffic to any number of "back-end" processes (up to you how many are desired).

I'd have to look up the exact format of the stanzas for the virtual interfaces.  Don't want physical machines to talk directly on the internet. Much prefer to have the VMs behind some hardware port filters myself.

**EDIT: From the interfaces manpage**, ```

              address address
                     Address (dotted quad/netmask) required
```
**So it seems I was wrong. Your settings should work.**

Anyway, hope this helps.

---

### Post by PaulBx on 2015-06-22
Did you get into the modem and verify that it was set up as 173.164.126.174/29?
Do you have the leds on when you plug the cable between the two machines in?

I wonder what the significance of the all 0's HWaddr is.

BTW I believe the first IP he can use is .168, not .169 unless I am mistaken...

---

### Post by TheFu on 2015-06-22
I'm absolutely positive about the 1st IP.  With comcast biz and a /29, we get 5 usable IPs. The last 1 is for THEIR router/gateway.

---

### Post by Curtis_G_Hanson on 2015-06-23
Thanks everyone for the help.

I fixed that error in my /etc/network/interface file:

```

# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth0
iface eth0 inet static
address 173.164.126.170
netmask 255.255.255.248
gateway 173.164.126.174
dns-search fartinginelevators.com
dns-nameservers 75.75.75.75 75.75.76.76

```

Aside from that, my setup was correct.

It turns out it was a hardware and BIOS issue.

My motherboard, GIGABYTE GA-990FXA-UD3, has an apparent problem with Ubuntu installations.

In the BIOS, there is an option for [IOMMU]("https://en.wikipedia.org/wiki/IOMMU") and it needs to be set to Enabled.

I didn't think it was a hardware issue since I first installed Ubuntu using that Ethernet port on my local network. After installation, I installed more packages successfully connecting to the internet. It all started when I assigned it a static IP and connected it to the SMC modem directly. I couldn't find anything in syslog nor was there anything in dmesg. Since I don't know enough about this subject, I'll call my fix good.

Edit: grammar.

---

### Post by TheFu on 2015-06-23
So the issue was the /etc/network/interfaces  "address" line. Remove the "/29"?  It isn't clear.

Also, please mark the thread "solved" to help the rest of the community.

---

### Post by Curtis_G_Hanson on 2015-06-23
No.

The CIDR notation correction in the /etc/network/interfaces file wasn't the resolution.

In fact, you are permitted to use CIDR notation in that file. Read the manpage for it: [http://manpages.ubuntu.com/manpages/precise/man5/interfaces.5.html](http://manpages.ubuntu.com/manpages/precise/man5/interfaces.5.html).

Shown below is the text from the page:

```
**The** **static** **Method**
       This  method  may be used to define ethernet interfaces with statically
       allocated IPv4 addresses.

       **Options**

              **address** _address_
                     Address (dotted quad/netmask) **required**
```

This is why I got no errors for it to begin with. 

**The resolution was changing the IOMMU setting to Enabled in the BIOS.**

---

### Post by TheFu on 2015-06-23
Thanks for clarifying.  When I looked at the last version of the file - the /29 had been removed and the statement that the interfaces file was "fixed" through me off.

I didn't know that IOMMU wasn't just for virtual machine HW passthru. Good to know. Thanks!

---

