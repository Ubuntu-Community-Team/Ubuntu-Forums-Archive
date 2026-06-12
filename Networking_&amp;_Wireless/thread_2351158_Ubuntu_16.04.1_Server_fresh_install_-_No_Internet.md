---
title: "Ubuntu 16.04.1 Server fresh install - No Internet"
date: 2017-01-31
forum: Networking &amp; Wireless
---

### Post by garciafan on 2017-01-31
Hello!

I am having difficulty connecting to the internet on a fresh install of Ubuntu Server 16.04.1 which is dual-booted with Windows 10 on a separate drive. I previously had a dual boot working before on this system with Windows 7 and Ubuntu 16.04 desktop. I decided to do fresh installs of both and here I am.

I tried to compile relevant info to help with the troubleshooting process.

**System Specs:**

    
[LIST]
[*]ASUS Maximus VI Hero 
[*]Intel i7 4770k 
[*]32 GB Corsair Vengeance DDR3 PC3-12800 
[*]ASUS GeForce GTX 970 
[*]256GB SSD - Windows 10 UEFI 
[*]512GB SSD - Ubuntu Server UEFI 
[/LIST]
 
I created the Bootable USB of Ubuntu 16.04.1-server-amd64.iso with Rufus.

Internet worked during install of Ubuntu then after reboot, nothing.

**lshw -c network**
```
*-network
       description: Ethernet interface
       product: Ethernet Connection I217-V
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eno1
       version: 05
       serial: *(mac address)*
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k duplex=full firmware=0.13-4 ip=192.168.1.101 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:28 memory:f7200000-f721ffff memory:f7238000-f7238fff ioport:f040(size=32)
```

**lspci -nnk | grep 0200 -A2**
```

00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection I217-V [8086:153b] (rev 05)
    DeviceName:  Onboard LAN
    Subsystem: ASUSTeK Computer Inc. Ethernet Connection I217-V [1043:859f]

```

**ip link**
```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP mode DEFAULT group default qlen 1000
    link/ether *(mac address)* brd ff:ff:ff:ff:ff:ff
```

**ifconfig -a**
```
eno1      Link encap:Ethernet  HWaddr *(mac address)*  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::e23f:49ff:fe19:ac40/64 Scope:Link
          inet6 addr: 2601:548:c101:cb70:e23f:49ff:fe19:ac40/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:479 errors:0 dropped:4 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:40883 (40.8 KB)  TX bytes:1146 (1.1 KB)
          Interrupt:20 Memory:f7200000-f7220000

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:5120 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5120 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1
          RX bytes:378880 (378.8 KB)  TX bytes:378880 (378.8 KB)
```

**dmesg | grep eno1**
```
[    0.903307] e1000e 0000:00:19.0 eno1: renamed from eth0
[    4.008665] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[    6.810431] e1000e: eno1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
[    6.810459] IPv6: ADDRCONF(NETDEV_CHANGE): eno1: link becomes ready
```
[B]
[www.google.com]("http://www.google.com") ping statistics[/B]
```
ping: unknown host www.google.com
```

**8.8.8.8 ping statistics**
```
3 packets transmitted, 0 received, 100% packet loss, time 2014ms
```

**192.168.1.1 ping statistics**
```
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2017ms
pipe 3
PING gaming (127.0.1.1) 56(84) bytes of data.
64 bytes from gaming (127.0.1.1): icmp_seq=1 ttl=64 time=0.011 ms
64 bytes from gaming (127.0.1.1): icmp_seq=2 ttl=64 time=0.023 ms
64 bytes from gaming (127.0.1.1): icmp_seq=3 ttl=64 time=0.025 ms
```
[B]
gaming ping statistics [/B](this pc's hostname = gaming)
```
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 0.011/0.019/0.025/0.008 ms
PING 192.168.1.101 (192.168.1.101) 56(84) bytes of data.
64 bytes from 192.168.1.101: icmp_seq=1 ttl=64 time=0.022 ms
64 bytes from 192.168.1.101: icmp_seq=2 ttl=64 time=0.020 ms
64 bytes from 192.168.1.101: icmp_seq=3 ttl=64 time=0.025 ms
```
[B]
/etc/network/interfaces[/B]
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
# This is an autoconfigured IPv6 interface
auto eno1
iface eno1 inet dhcp

```

It pauses at boot and says "A start job is running for Raise network interfaces [*time remaining* / 5min 1sec]"

So I tried to set it to static:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
# This is an autoconfigured IPv6 interface
auto eno1
iface eno1 inet static
    address 192.168.1.101
    netmask 255.255.255.0
    gateway 192.168.1.1
    dns-nameservers 75.75.75.75 76.76.76.76

```

I also tried using the router (192.168.1.1) as the DNS with no luck. 
**Router Settings:**
```
Linksys WRT 1900AC v1
IP Address: 192.168.1.1
Subnet Mask: 255.255.255.0
DNS1: 75.75.75.75
DNS2: 75.75.76.76

```

---

### Post by TheFu on 2017-01-31
Can you ping the router by IP?
If not, swap the port or cable.

You forgot to configure the DNS in the interface file. When you go static, the router doesn't pass that on. Add
```
   dns-nameservers 75.75.75.75 75.75.76.76
```
though I'd NOT use Comcast DNS for many reasons.

Don't put the static IP into a DHCP range controlled by the router.

The e1000e driver is pretty stable. Never had any issues with it.  It is seeing a GigE connection. That's a good sign.

I take it you've restarted the networking subsystem and verified the routes?

---

### Post by garciafan on 2017-01-31
You know, I did have the dns entries in the interface file but I must not have saved it over to put on here. I'll edit the op to reflect that. 

I figured that since the Windows install has internet working fine, that it wouldn't be an issue with cables/router ports. I ran DNS Bench and found a few better DNS addresses and entered them when I had DDWRT installed on this router. I flashed it back to stock thinking it may have been an issue with DDWRT. I was using the Comcast ones just to get things rolling.

Ok, switched ports on the router and still no luck.

---

### Post by TheFu on 2017-01-31
[http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking) is my troubleshooting article. The order is important. Where does it fail on your network?

---

### Post by garciafan on 2017-01-31
Not pinging router. 

Therefore, according to your site, it's a config/driver issue.

As stated in the op, I had internet during install. Something changed at reboot after installation, not sure what :/

Will boot into the Linux drive and test the other commands that I haven't posted already. 

Thanks

**route**
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.1.1     0.0.0.0         UG    0      0        0 eno1
192.168.1.0     *               255.255.255.0   U     0      0        0 eno1
```

**more /etc/resolv.conf**
```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 75.75.75.75
nameserver 75.75.76.76
```

**dmesg | grep eth[0-9]**
```
[    0.902475] e1000e 0000:00:19.0 eth0: registered PHC clock
[    0.902479] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) *(mac address)*
[    0.902483] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    0.902519] e1000e 0000:00:19.0 eth0: MAC: 11, PHY: 12, PBA No: FFFFFF-0FF
[    0.903313] e1000e 0000:00:19.0 eno1: renamed from eth0
```

---

### Post by TheFu on 2017-01-31
At this point, I'd boot up into the installation disc and after the networking gets setup, switch to a different console and look at the driver and settings being used. DO NOT reinstall.  Then compare those to the driver and settings from above.  What is different?

The other thing is to recheck for typos in the interfaces file - 0/O l/1, things like that. ;)  We've all done it.

---

### Post by garciafan on 2017-02-01
Just ran the installer, and it was not able to connect to the internet. 

I'm 100% sure that the internet works on this machine because I'm typing this response from the Windows drive.

I also have Windows 10 & Ubuntu Server on my laptop, but on one SSD and everything works fine.

---

### Post by TheFu on 2017-02-02
What about "try ubuntu" on a desktop install?
puppy linux?
Fedora?
others ...

---

### Post by garciafan on 2017-02-02
This all started when I was tried to install Arch. 

I figured that I'd give Arch a shot since I have been using Ubuntu for the past couple of years. I made it through the install and then had no internet. I re-installed it two more times with the same result. Figured I was doing something wrong so I came back to try Ubuntu since I had it working before. 

I guess I'll give another distro a shot and see what happens. 

Thanks for the assistance.

---

### Post by TheFu on 2017-02-02
Arch is a rolling release and probably has a newer kernel with different driver support.

Someone else here: [https://ubuntuforums.org/showthread.php?t=2280968](https://ubuntuforums.org/showthread.php?t=2280968) solved it for the same Intel I217-V. Might be helpful.

---

### Post by TheFu on 2017-02-02
Whoa!!!!  You were trying to make Arch work with Ubuntu commands?  This is an Ubuntu support forum, not for Arch.

BTW, network manager isn't part of Ubuntu Server and isn't needed/desired when running with static IPs configured via the interfaces file.  Also, you don't need any of the wpa stuff - you are running wired, not wifi.  No sure what 1fallen is thinking here.

---

### Post by #&amp;thj^% on 2017-02-02
> **TheFu said:**
> Whoa!!!!  You were trying to make Arch work with Ubuntu commands?  This is an Ubuntu support forum, not for Arch.

BTW, network manager isn't part of Ubuntu Server and isn't needed/desired when running with static IPs configured via the interfaces file.  Also, you don't need any of the wpa stuff - you are running wired, not wifi.  No sure what 1fallen is thinking here.

Please read my edited post again.

---

### Post by TheFu on 2017-02-02
> **1fallen said:**
> Please read my edited post again.

I figured that I'd missed something fundamental that you'd gotten correct. No worries. We're all just tryin' to help.

---

### Post by garciafan on 2017-02-02
Alright, I unplugged all other hard drives and installed OpenSuse. Booted up and the internet worked. Haven't tried since I plugged the Windows drive back in though.

I am going to wipe the SSD and try either Arch or Ubuntu Server again tomorrow after work. I'll keep the link you posted handy if I run into the problem again.

---

### Post by garciafan on 2017-02-02
I rebooted after plugging the Windows SSD in and OpenSuse has no internet now. 

It seems that Windows is somehow affecting the other installs. 

In my BIOS, I have the UEFI Boot settings set to "Other OS". Not sure what else it could be..

---

### Post by garciafan on 2017-02-03
I should also note that I shut down the computer when switching between OSes, not just restart.

---

### Post by TheFu on 2017-02-03
Please re-read #6 above. Seeing it work is when you need to gather that data. Without facts, we are lost.

---

### Post by garciafan on 2017-02-03
I was able to reconnect in OpenSuse by doing the steps outlined [here]("http://askubuntu.com/a/622151"). 

Windows 10 had an older driver (2015) installed for my network card installed by default. I updated it and shut down, then booted into OpenSuse. Still no internet. Back to Windows and did as suggested in the link above (unchecking all power saving options). Shut down then booted into OpenSuse. Obtained an IP and am replying from that OS now. 

So, to recap:
[LIST=1]
[*]Go to [Intel's website]("https://downloadcenter.intel.com/") and download the latest drivers for your card. 
[*]Uninstall current network driver. 
[*]Install new drivers. 
[*]Go to the Network Adapter's device properties then Power Options and un-check all options. 
[/LIST]

[IMAGE]("http://imgur.com/a/HAc6Y")


I am going to format the drive and attempt to reinstall Ubuntu Server and hopefully all goes well.

Thanks for the help!

---

