---
title: "lose network connection booting into Xen"
date: 2006-11-29
forum: Networking &amp; Wireless
---

### Post by kpm on 2006-11-29
Hi, I am attempting to set up an Ubuntu server running Xen for the first time.  First I installed a basic 6.10 server, can run apt and ping etc.  Then, I set up the Xen hypervisor following these instructions:
[https://help.ubuntu.com/community/XenVirtualMachine/XenOnUbuntuEdgy](https://help.ubuntu.com/community/XenVirtualMachine/XenOnUbuntuEdgy)
but on reboot, I loose network connection, can't ping.

Anyone have any suggestions??

Thanks

---

### Post by trubblemaker on 2006-11-29
I"m not sure how bad xen messing things up, I can help with network connectioins but never used xen.  Lets start with the basics:
```

lspci
cat /etc/network/interfaces
ifconfig

```
should give me a head start on where to go.
also run this for me
```

sudo ifdown eth0
sudo ifup eth0

```

---

### Post by kpm on 2006-11-29
> **trubblemaker said:**
> I"m not sure how bad xen messing things up, I can help with network connectioins but never used xen.  Lets start with the basics:
```

lspci
cat /etc/network/interfaces
ifconfig

```
should give me a head start on where to go.
also run this for me
```

sudo ifdown eth0
sudo ifup eth0

```

Result of lspci:
00:010.0 PCI Bridge: Via Techologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev c4)
00:0b.0 Ethernet Controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)

Result of cat /etc/network/interfaces:
auto eth0
iface eth0 inet static
address 192.168.1.200
netmask 255.255.255.0
gateway 192.168.1.1

Result of ifconfig:
eth0
Link encap.ethernet HWaddr FE:FF:FF:FF:FF:FF
inet addr:192.168.1.200 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::fcff:ffff:feff:ffff/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:59427 errors:0 dropped:0 overruns:0 frame:0
TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txquelen:0
RX bytes:9454477 (9.0 MiB) TX bytes:1476 (1.4 KiB)

lo
Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:8 errors:0 dropped:0 overruns:0 frame:0
TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txquelen:0
RX bytes:772 (772.0 b) TX bytes:772 (772.0 b)

peth0
Link encap.ethernet HWaddr FE:FF:FF:FF:FF:FF
inet6 addr: fe80::fcff:ffff:feff:ffff/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:60340 errors:0 dropped:0 overruns:0 frame:0
TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txquelen:1000
RX bytes:9596517 (9.1 MiB) TX bytes:2495 (2.4 KiB)
Interrupt:11 Base address:0xd800

vif0.0
Link encap.ethernet HWaddr FE:FF:FF:FF:FF:FF
inet6 addr: fe80::fcff:ffff:feff:ffff/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:30 errors:0 dropped:0 overruns:0 frame:0
TX packets:59427 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txquelen:1000
RX bytes:1476 (1.4 KiB) TX bytes:9454477 (9.0 MiB)
Interrupt:11 Base address:0xd800

xenbr0
Link encap.ethernet HWaddr FE:FF:FF:FF:FF:FF
inet6 addr: fe80::200:ff:fe00:0/64 Scope:Link
UP BROADCAST RUNNING NOARP MTU:1500 Metric:1
RX packets:59481 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txquelen:0
RX bytes:8624659 (8.2 MiB) TX bytes:0 (0.0 b)
Interrupt:11 Base address:0xd800


For sudo ifdown eth0:
interface eth0 not configured

For sudo ifup eth0 (i ran the command, nothing happened so ran it again and got):
intercace eth0 already configured

Thanks for the help!

---

### Post by trubblemaker on 2006-11-29
so I see you have an ip address, your up and running again?

---

### Post by kpm on 2006-11-30
> **trubblemaker said:**
> I"m not sure how bad xen messing things up, I can help with network connectioins but never used xen.  Lets start with the basics:
```

lspci
cat /etc/network/interfaces
ifconfig

```
should give me a head start on where to go.
also run this for me
```

sudo ifdown eth0
sudo ifup eth0

```

> **trubblemaker said:**
> so I see you have an ip address, your up and running again?

Nope, still not able to connect when booted into Xen (the boot/grub/menu.lst was edited so that the machine boots into Xen, but I can tell it to boot into the Ubuntu 6.10 kernel and then my connections work... None of the howtos, faqs, or support sites for getting Xen up and running mention anything about this situation, they just continue on with the steps as though a network conection is available...

The concept of virtualization is so appealing, I had to give it a try on my old test machine. I read up on the different types, and then learned Ubuntu would support Xen in edgy (I tried in Dapper with no luck previusly) so thought my luck would change with it, but it still appears to be out of my reach...

---

### Post by trubblemaker on 2006-11-30
try
```
sudo dhclient wlan0
```

---

### Post by kpm on 2006-11-30
> **trubblemaker said:**
> try
```
sudo dhclient wlan0
```

response to dhclient wlan0:
SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device

thanks

---

### Post by chewie124 on 2006-11-30
When xend starts up with the default network configuration (network-bridge), your eth0 becomes like a virtual switch, rendering it's actual network connection unavailable.  At least, that's the way I understand it.  I believe you would need to setup your dom0 on some kind of virtual network interface to actually restore network connectivity from dom0.

However, when you start up your domU & get the networking configured on there, your domU machines will be able to connect, no problem.  Or, it should be that way. ;)

For more details, check here:
[http://wiki.xensource.com/xenwiki/XenNetworking](http://wiki.xensource.com/xenwiki/XenNetworking)

---

### Post by trubblemaker on 2006-11-30
ah that would be it
also I meant to say
```

sudo dhclient eth0

```

---

### Post by kpm on 2006-12-01
> **chewie124 said:**
> When xend starts up with the default network configuration (network-bridge), your eth0 becomes like a virtual switch, rendering it's actual network connection unavailable.  At least, that's the way I understand it.  I believe you would need to setup your dom0 on some kind of virtual network interface to actually restore network connectivity from dom0.

However, when you start up your domU & get the networking configured on there, your domU machines will be able to connect, no problem.  Or, it should be that way. ;)

For more details, check here:
[http://wiki.xensource.com/xenwiki/XenNetworking](http://wiki.xensource.com/xenwiki/XenNetworking)

Yes, I originally thought that even if I lost the network on Dom0, I could get it up and running on a DomU as soon as an image was mounted.  But, I am stuck in that the next steps in any howto for getting Xen running requires 'sudo apt-get install debootstrap' the old catch 22, without a live connection to the sources, I am dead in the water.  I can somewhat wrap my head around the networking magic that xen does, but I simply do not have the knowledge to sort out whatever I need to do to get the Dom0 connected... and I can't seem to find an assumptionless 'howto' anywhere that does not skip this very crucial component of getting Xen connected. sigh.

---

### Post by kpm on 2006-12-01
> **trubblemaker said:**
> ah that would be it
also I meant to say
```

sudo dhclient eth0

```

for what its worth... the output:

Listening on LPF/eth0/fe:ff:ff:ff:ff:ff
Sending on LPF/eth0/fe:ff:ff:ff:ff:ff
Sending on Socket/fallback
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.102 -- renewal in 35259 seconds.

---

### Post by trubblemaker on 2006-12-01
well there is always a work around for you,

if you need to install something like that use your 6.10 to download it for you and then you can later install the deb with dpkg.  obviously you'll need to download all the packages you need first then install them all.  apt-get has a just download only feature, then later you could install the downloads.  Just some ideas,

---

### Post by kpm on 2006-12-02
> **trubblemaker said:**
> well there is always a work around for you,

if you need to install something like that use your 6.10 to download it for you and then you can later install the deb with dpkg.  obviously you'll need to download all the packages you need first then install them all.  apt-get has a just download only feature, then later you could install the downloads.  Just some ideas,

Hmmm, interesting... I just booted into 6.10, apt-got debootstrap, then booted back into xen and ran the next step in the howto, apt-get install debootstrap, and it installed!  So apt must somehow be interacting with the original 6.10 base install.

Anyway, that brings me a step closer to being able to install a domU, but next up in the howto is to then run "sudo debootstrap edgy /mnt" which then attempts to retrieve the release but again needs network access to do so ("Failed getting release file [http://archive.ubutu.com/ubuntu/dists/edgy/Release)](http://archive.ubutu.com/ubuntu/dists/edgy/Release)).

So I suppose I will have to figure out how to point deebootstrap to the installation cd... but I foresee endless Xen pain simply because I cannot seem to get Dom0 to access the internet, something every howto simply assumes it does... very annoying... time to give up and look back at Xen next year or so to see if a) the howtos are written more to my level of understanding, or b) I get a better grounding in the netwroking behind Xen to do the proper configuration.  For now, life is to short to be spending endless fruitless hours... back to a standalone LAMP server for now.
Regradless, thanks much for all the help.
Cheers.

---

### Post by Andrew Stone on 2008-02-06
I have the exact same problem.  I noticed that dhclient actually works to assign IP addresses to the various interfaces peth0, vethbr, etc.  So this means that ethernet (layer 1) communications work.  Unfortunately, there is such a mess of virtual interfaces routes and default routes that I can't figure out what was intended without delving into the source code.

Instead I commented out the bridging (in xend-config.sxp) and instead used routing:
(network-script network-route)
(network-script vif-route)

When I rebooted, the interface table was much cleaner, with just a single additional virtual interface "vif3".  IP worked out of dom0.  However, domU's (a guest) ethernet did not work.  I noticed that the IP address assigned to vif3 was in the same subnet as eth0.  This doesn't make sense because we are using routing now.  I assigned vif3 and the guest's eth0 to a different subnet and could ping between them.
(dom0 eth0 is on subnet 192.168.1.x)
guest: ifconfig eth0 192.168.2.180 netmask 255.255.255.0
dom0: ifconfig vif3 192.168.2.1 netmask 255.255.255.0

However, the dom0 was not routing between the subnets.  That is, I couldn't ping from the guest to 192.168.1.1.  Since I have never configured linux to route between interfaces, it is probably a simple routing config problem...

on dom0:
root@stone-desktop:~# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 vif3.0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
root@stone-desktop:~# ip route list
192.168.2.0/24 dev vif3.0  proto kernel  scope link  src 192.168.2.1 
192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.103 
169.254.0.0/16 dev eth0  scope link  metric 1000 
default via 192.168.1.1 dev eth0 

on guest:
root@xen1:~# ip route list
192.168.2.0/24 dev eth0  proto kernel  scope link  src 192.168.2.180 
default via 192.168.2.1 dev eth0 
root@xen1:~# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0
root@xen1:~# 

Any help is appreciated!

---

