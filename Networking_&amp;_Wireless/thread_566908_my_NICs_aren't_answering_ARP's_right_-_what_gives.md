---
title: "my NICs aren't answering ARP's right - what gives?"
date: 2007-10-04
forum: Networking &amp; Wireless
---

### Post by wideLoad on 2007-10-04
I've got a 6.10 server w/ two NICs, both on the same subnet.  The problem is that when the router does an ARP request to see which mac is tied to an IP, my server answers inconsistently!

So sometimes I will see that my 10.0.102.11 -and- 10.0.102.12 IPs both have the same MAC in my routers ARP cache (and i'm using two NIC's w/ different macs obviously).  Clearing the routers cache doesn't help -- my Ubuntu server is not answering the ARP requests correctly.

Other times, it will work correctly and answer the ARP's OK -- all without power cycling or changing anything.

Clearly, I don't have something configured correctly in my networking stuff.  Does anyone have experience w/ multihomed boxes? 

I've played w/ my /etc/network/interfaces file and /etc/iftab significantly.  Nothing seems to make this prob go away.  Here are the current versions:

------------------------------------------
/etc/network/interfaces (it looks indented incorrectly but it is in the real file  -- if that matters)
------------------------------------------
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
        address 10.0.102.11
        netmask 255.255.255.0
        network 10.0.102.0
        broadcast 10.0.102.255
        gateway 10.0.102.1
        dns-nameservers 10.0.102.1

auto eth1
iface eth1 inet static
        address 10.0.102.12
        netmask 255.255.255.0
        network 10.0.102.0
        broadcast 10.0.102.255
        gateway 10.0.102.1
        dns-nameservers 10.0.102.1


------------------------------------------
/etc/fstab -- is currently **empty**.  But i tried this before, and lots of other variations, all to no avail.
------------------------------------------
eth0 mac 00:13:72:2f:4b:4d arp 1
eth1 mac 00:A0:C9:C6:F4:26 arp 1

I've also tried adding "hwaddress ether" option to "hardcode" my mac for each NIC.  I even tried creating the "/etc/udev/rules.d/70-persistent-net.rules" file (and since removed).  I have no idea why my server is not responding to ARP's correctly.  

Hopefully there's something obvious i'm not doing correctly.  Please give me a clue!! Thanks
w

---

### Post by noob12 on 2007-10-04
Can you post the output of these:

```

lspci -nn

sudo lshw -C network

```

---

### Post by wideLoad on 2007-10-04
I'm thrilled to post the output of those commands.  Lemme know if u see something funky, i'm pretty sure that i'm just not setting an important var in one the configs.  There's a ton of info online about adding a new NIC to ubuntu, but not nearly as much about multihoming a linux box, especially when it's NOT a router, just two connections to the LAN on the same subnet.  Here's the output and thanks for the rsp.

root@crawler:~# lspci -nn
00:00.0 0600: 8086:2778
00:01.0 0604: 8086:2779
00:1c.0 0604: 8086:27d0 (rev 01)
00:1c.4 0604: 8086:27e0 (rev 01)
00:1c.5 0604: 8086:27e2 (rev 01)
00:1d.0 0c03: 8086:27c8 (rev 01)
00:1d.1 0c03: 8086:27c9 (rev 01)
00:1d.2 0c03: 8086:27ca (rev 01)
00:1d.3 0c03: 8086:27cb (rev 01)
00:1d.7 0c03: 8086:27cc (rev 01)
00:1e.0 0604: 8086:244e (rev e1)
00:1f.0 0601: 8086:27b8 (rev 01)
00:1f.1 0101: 8086:27df (rev 01)
00:1f.2 0101: 8086:27c0 (rev 01)
00:1f.3 0c05: 8086:27da (rev 01)
04:00.0 0200: 14e4:167a (rev 02)
05:02.0 0200: 8086:1229 (rev 04)
05:07.0 0300: 1002:515e (rev 02)

root@crawler:~# lshw -C network
  *-network
       description: Ethernet interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@04:00.0
       logical name: eth0
       version: 02
       serial: 00:13:72:2f:4b:4d
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=tg3 driverversion=3.59.1 duplex=full firmware=5754-v3.12 ip=10.0.102.11 link=yes multicast=yes port=twisted pair speed=1GB/s
       resources: iomemory:efcf0000-efcfffff irq:74
  *-network
       description: Ethernet interface
       product: 82557/8/9 [Ethernet Pro 100]
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@05:02.0
       logical name: eth1
       version: 04
       serial: 00:a0:c9:c6:f4:26
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=e100 driverversion=3.5.10-k2-NAPI duplex=full firmware=N/A ip=10.0.102.12 link=yes multicast=yes port=MII speed=100MB/s
       resources: iomemory:e8000000-e8000fff ioport:d8e0-d8ff iomemory:efa00000-efafffff irq:58


w

---

### Post by netztier on 2007-10-04
> **wideLoad said:**
> I've got a 6.10 server w/ two NICs, both on the same subnet.  The problem is that when the router does an ARP request to see which mac is tied to an IP, my server answers inconsistently!


Two NICs in the same Subnet is a bad thing to have (if you don't take precautions). The main problems that arise are MAC- and ARP related, just like the ones you are experiencing, because it is not clearly defined which interface should answer an ARP request or which interface to use to start a connection to some other host. Network confusion is the general result.

> **wideLoad said:**
>  Clearly, I don't have something configured correctly in my networking stuff.  Does anyone have experience w/ multihomed boxes? 

If you want to have two interfaces in the same subnet, you should configure **bonding**. The individual interfaces won't have IP parameters anymore, but a new virtual interface (generally called **bond0**) will be created and will get the IP configuration parameters. Depending on what your LAN switch is capable of, several modes of bonding are possible - you'll find info about this in the different threads in the forum and in the documents they link to.

A starting point for reading: [http://ubuntuforums.org/showthread.php?t=283113&highlight=bonding](http://ubuntuforums.org/showthread.php?t=283113&highlight=bonding)

Also use "bonding" as search keyword in "search this forum" and you'll get a lot of threads around the topic.


best regards

Marc

---

### Post by noob12 on 2007-10-04
A common solution to this is to enable arp filtering.  You can try that.

You can do it either via /proc or sysctl 

e.g. **as root**
```

echo "1" > /proc/sys/net/ipv4/conf/all/arp_filter

```

To make it permanent

```

echo "net.ipv4.conf.default.arp_filter=1" | sudo tee -a /etc/sysctl.conf

```

Reboot.

Note that your neighboring host arp caches may need flushing.


Ref:
[http://linux-ip.net/html/ether-arp.html](http://linux-ip.net/html/ether-arp.html)
[http://downloadmirror.intel.com/5154/ENG/e100.htm](http://downloadmirror.intel.com/5154/ENG/e100.htm)

---

### Post by wideLoad on 2007-10-05
I need to keep these seperate interfaces for traffic shaping purposes, so noob12's option is the only way forward.  So those links are awesome, and i defintely need to use the arp_filter option which is designed exactly for this problem.

Unfortunately, it is not as simple as setting
echo "1" > /proc/sys/net/ipv4/conf/all/arp_filter

You have to make routing changes so that whatever IP was ARP'd, the kernel can lookup in the route tables and see if it would send an reply via that interface to the arp'd IP, and only then will it reply.  So i'm having a heck of a time doing just that.

Apparently, you have to do some magic with source IP routing vs destination, and i'm an old school user of the "route" command, not "ip route" -- so its proving troublesome.

Per this link:
[http://mailman.ds9a.nl/pipermail/lartc/2005q2/015790.html](http://mailman.ds9a.nl/pipermail/lartc/2005q2/015790.html)

I found an example that I thought would help me, but everytime i execute these commands, the network connection dies on me, and i have to go the servers terminal to restart it.

ip rule add from 10.0.102.11 lookup 10
ip route add table 10 default src 10.0.102.11 dev eth0

ip rule add from 10.0.102.12 lookup 11
ip route add table 11 default src 10.0.102.12 dev eth1

Anybody know why those rules would kill connectivity to the server immediately?

Maybe this would all be easier if i just go a different way ... like turning off arp completely via the ifconfig -arp command, and then using some other tool for arp responses.  I'm kind of shocked that it is this hard to get two IP's onto the same subnet.  I've been playing w/ this for days now.  

Thanks again for previous posts, those definitely got me in the right direction at least.

---

### Post by wideLoad on 2007-10-05
Just as some background on my IP setup.  The nics are 10.0.102.12 and 10.0.102.11, 255.255.255.0   The default gateway is 10.0.102.1

The "working" routing table is this:
ip route show
10.0.102.0/24 dev eth0  proto kernel  scope link  src 10.0.102.11
10.0.102.0/24 dev eth1  proto kernel  scope link  src 10.0.102.12
default via 10.0.102.1 dev eth1
default via 10.0.102.1 dev eth0


Which works, but doesn't have the source routing setup as described previously to get the arps working properly.  Once I execute this:

ip rule add from 10.0.102.11 lookup 10
ip route add table 10 default src 10.0.102.11 dev eth0

ip rule add from 10.0.102.12 lookup 11
ip route add table 11 default src 10.0.102.12 dev eth1

The connectivity is killed and the routing table is...
ip route show:
10.0.102.12 dev eth1  scope link  (NEW)
10.0.102.11 dev eth0  scope link   (NEW)
10.0.102.0/24 dev eth0  proto kernel  scope link  src 10.0.102.11
10.0.102.0/24 dev eth1  proto kernel  scope link  src 10.0.102.12
default via 10.0.102.1 dev eth1
default via 10.0.102.1 dev eth0

If anybody can shed some light on how i can change those ip rule and ip route add commands, that would be great.   Thanks again.

w

---

### Post by wideLoad on 2007-10-05
Ok, i got it.  Thanks previous posters for pointing me in the right direction.  For future reference here is how i got two NIC's working on the same subnet.

Background info:
1) IP's were 10.0.102.11 and 10.0.102.12
2) 255.255.255.0
3) gateway is 10.0.102.1

Steps:
1) echo 1 > /proc/sys/net/ipv4/conf/all/arp_filter
2) now you must change the routing tables so the kernel has a reason to always send .11 out eth0, and .12 out eth1.  I accomplished this by executing the following:
  >ip rule add from 10.0.102.11 lookup 10
  >ip route add table 10 default via 10.0.102.1 src 10.0.102.11 dev eth0
 
  >ip rule add from 10.0.102.12 lookup 11
  >ip route add table 11 default via 10.0.102.1 src 10.0.102.12 dev eth1

Steps to make it permanent if those steps above work:
changed /etc/network/interfaces to the following:
iface eth0 inet static
        post-up /sbin/ip rule add from 10.0.102.11 lookup 10
        post-up /sbin/ip route add table 10 default via 10.0.102.1 src 10.0.102.11 dev eth0
        address 10.0.102.11
        netmask 255.255.255.0
        network 10.0.102.0
        broadcast 10.0.102.255
        gateway 10.0.102.1
        dns-nameservers 10.0.102.1

iface eth1 inet static
        post-up /sbin/ip rule add from 10.0.102.12 lookup 11
        post-up /sbin/ip route add table 11 default via 10.0.102.1 src 10.0.102.12 dev eth1
        address 10.0.102.12
        netmask 255.255.255.0
        network 10.0.102.0
        broadcast 10.0.102.255
        gateway 10.0.102.1
        dns-nameservers 10.0.102.1

Put this line in /etc/sysctl.conf
net.ipv4.conf.all.arp_filter=1

Note that the line above is slightly different than the line that noob12 recommended using, which did not work for me on 6.10 server.  Thanks again everyone!
w

---

### Post by wideLoad on 2007-10-05
Hmmm, one last thing.  You probably want to change the 'post-up' commands to 'up' in the interfaces file above.  Otherwise, there's a chance you could spit back a nasty arp directly after the interface was brought up, but before the routing tables were altered.  Which would result in somebody storing the wrong MAC in the arp cache thereby causing more doom and suffering.

---

