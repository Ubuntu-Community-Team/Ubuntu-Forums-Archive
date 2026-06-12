---
title: "Ethernet Not Working on Ubuntu 14.04 LTS"
date: 2015-10-03
forum: Networking &amp; Wireless
---

### Post by Devgaze on 2015-10-03
HI everyone,

it seams I am in the same situation but still don't see an answer in this thread. 

I'll just continue from the previous post...

My wireless is not visible and through cable I don't get any connection.

**ifconfig**
```

eth0       Link encap:Ethernet  HWaddr 00:17:08:4a:d8:71
             inet6 adr: fe80::217:8ff:fe4a:d871/64 Scope:Link
             UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
             RX packets:517 errors:0 dropped:0 overruns:0 frame:0
             TX packets:573 errors:0 dropped:0 overruns:0 carrier:0
             collisions:0 txqueuelen:1000
             RX bytes:134577 (134.5 KB) TX bytes:151577 (151.5 KB)
             Interrupts:23

lo          Link encap:Local Loopback
            inet addr:127.0.0.1 Mask:255.0.0.0
            inet6 addr: ::1/128 Scope:Host
            UP LOOPBACK RUNNING MTU:65536 Metric:1
            RX packets:384 errors:0 dropped:0 overruns:0 frame:0
            TX packets:384 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:0
            RX bytes:31128 (31.1 KB) TX bytes:31128 (31.1 KB)

```

[B]cat /etc/NetworkManager/NetworkManager.conf
[/B]```

[main]
plugins=ifupdown, keyfile, ofono
dns=dnsmasq

[ifupdown]
managed=true

```

So if anyone can help I would really appreciate it.

Cheers!

---

### Post by howefield on 2015-10-03
Hello and welcome to the forums,

Thread moved to own thread, much better than tacking on to an old thread.

---

### Post by Devgaze on 2015-10-04
Oh, I wondered where it has disappeared.

@howefield thanks for the welcome ;). 

Ok so @Bashing-om asked me ([here]("http://ubuntuforums.org/showthread.php?t=2222204&page=2&p=13367203#post13367203")) to provide the output for[B] cat /etc/network/interfaces
[/B]
So here it goes:

```

#interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

# default settgins are above, I added below snippet while trying other recommendation from the internet, but it didn't work and I forgot to remove it!
iface eth0 inet dhcp
        pre-up ifconfig $IFACE up
        pre-up ethtool --change eth0 speed 1000 duplex full autoneg off

```


After removing this thread it kinda lost its context, so let me explain what's going on. I have found my old laptop HP Compaq nx6325 and just wanted to refresh him with fresh install of Ubuntu. 
The problem is I am seeing my eth0, but I can't establish a connection and wireless card is not visible. I've seen on the internet that many of users have same/similar issues but non of proposed solutions work for me.
So here I am :), hopefully this community will help me sort it out.

Cheers!

---

### Post by Bashing-om on 2015-10-04
Devgaze; Hi once more;

OK, this config setting tells the system networking will be configured elsewhere:
> 
[ifupdown]
managed=true

That elsewhere is in the /etc/network/interfaces file.
Maybe something like this will work in your case:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

```
Which will identify to the system eth0 as the interface, and as well that the network is dynamic and Domain Name Services are provided . If your network is "static" additional/other settings will be required. ( /etc/resolv.conf for one instance )

depending;
[INDENT][INDENT][INDENT]maybe yes
[/INDENT][/INDENT][/INDENT]

---

### Post by Devgaze on 2015-10-04
Yeah, I did try that previously, and right now once again, but no luck.

---

### Post by Bashing-om on 2015-10-04
Devgaze; K;

Then tell us about your network .
Router ?
ISP ?
cable ?

Are you getting out of house ? 
what returns:
```

ping -c3 8.8.8.8

```
see if you see google's server response . - As 1 place to start troubleshooting -

[INDENT][INDENT]all is in the process
[/INDENT][/INDENT]

---

### Post by Devgaze on 2015-10-04
Alright, I got cable network in my house and everything is fine on my iMac. But when I plug the cable in my old laptop it doesn't get connection.

I did try to ping google servers, and as output I get this message

```

devgaze@~$ ping -c3 8.8.8.8
connect: Network is unreachable

```

So I use the same cable, when I try other devices (wife's laptop) on that cable it works too.
Usually I am using my iMac as an AP for home WiFi (through shared connection), that's how we connect all other devices (iPad, iPhone's, laptop) and the idea is that one day this old laptop will do the same.

But for now I would just like to be able to get a connection through direct cable input.

---

### Post by Bashing-om on 2015-10-04
Devgaze; Yuk;

OK. let's find out the why.
Is the hardware identified by the system ?
```

lspci | grep Ethernet

```
Is a driver loaded ?
```

sudo lshw -C network

```
How is DNS resolution handled ?
```

cat /etc/resolv.conf
ls -l /etc/resolv.conf

```
What does the system tell us when the interface is activated ?
```

ifconfig eth0 up

```

[INDENT][INDENT]these gotta point us somewhere 
[/INDENT][/INDENT]

---

### Post by Devgaze on 2015-10-04
**lspci | grep Ethernet**
```

02:01:0 Ethernet controller: Broadcom Corporation NetXtreme BCM5788 Gigabit Ehternet (rev 03)

```

**sudo lshw -C network**
```

  *-network
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:30:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:c4000000-c4003fff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5788 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 03
       serial: 00:17:08:4a:d8:71
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 duplex=full firmware=5788-v3.26 latency=64 link=yes mingnt=64 multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:23 memory:d0000000-d000ffff



```

**cat /etc/resolv.conf**
```

# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN

```

**ls -l /etc/resolv.conf**
```

lrwxrwxrwx 1 root root 29 Ožu 22 20:17 /etc/resolv.conf -> ../run/resolvconf/resolv.conf

```

**ifconfig eth0 up**
```

SIOCSIFFLAGS: Operation not permitted

```

When I try the last one with `sudo` it doesn't output anything.

---

### Post by Bashing-om on 2015-10-04
Devgaze; Welp;

Broadcom ! Has it ups and downs.

What returns:
```

lspci -vvnn | grep -A 9 Network

```
And let's find us a driver .

[INDENT][INDENT]it can be done
[/INDENT][/INDENT]

---

### Post by Devgaze on 2015-10-04
[B]lspci -vvnn | grep -A 9 Network
[/B]
```

    30:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Hewlett-Packard Company BCM4311 802.11b/g Wireless LAN Controller [103c:1364]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 18
    Region 0: Memory at c4000000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: b43-pci-bridge

```

I like the sound of "it can be done" \\:D/

---

### Post by Bashing-om on 2015-10-04
Devgaze; Hey:

Yeah .. rather than me taking all the credit .. here is the how-to:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Maybe a bit of a pain; 
> 
STA - No Internet access
If you do not have any other means of Internet access on your computer, you can install the bcmwl-kernel-source package from the restricted folder under ../pool/restricted/b/bcmwl on the Ubuntu install media


If you run into problems, I will not have you have all the fun to yourself.

[INDENT][INDENT]do'n what I can to help
[/INDENT][/INDENT]

---

### Post by Devgaze on 2015-10-06
So I went with Bashing-om advice and followed instructions from [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA_-_No_Internet_access"). 
I manually downloaded on USB and installed (in this order) following packages:

[http://packages.ubuntu.com/trusty/all/dkms/download](http://packages.ubuntu.com/trusty/all/dkms/download)
[http://packages.ubuntu.com/trusty/i386/patch/download](http://packages.ubuntu.com/trusty/i386/patch/download)
[http://packages.ubuntu.com/trusty/i386/libfakeroot/download](http://packages.ubuntu.com/trusty/i386/libfakeroot/download) (<< this one will complain on untrusty source; I ignored it)
[http://packages.ubuntu.com/trusty/i386/fakeroot/download](http://packages.ubuntu.com/trusty/i386/fakeroot/download) (<< the same as the previous one)
[http://packages.ubuntu.com/trusty/i386/bcmwl-kernel-source/download](http://packages.ubuntu.com/trusty/i386/bcmwl-kernel-source/download) 

After that I try the same thing and it didn't work. Then I tried to put in static IP and DNS, like so:

```

iface eth0 inet static
    address 109.60.61.140
    netmask 255.255.252.0
    gateway 109.60.60.1
    dns-nameservers 83.139.104.2 83.139.105.2

``` 

So than I tried to restart the network-manager
```

sudo service network-manager restart

stop: Unknown instance:
network-manager start/running, process 2190

```

And nothing happened. Then I tried (I am really lost here :D) :

```

devgaze@~$ sudo ifdown eth0
RTNETLINK answers: No such process
RTNETLINK answers: No such process

devgaze@~$ sudo ifup eth0
devgaze@~$ 

```

And nothing. Then I started to spin around myself once again


```

devgaze@~$ sudo ifdown eth0
RTNETLINK answers: No such process
RTNETLINK answers: No such process

devgaze@~$ sudo service network-manager restart
devgaze@~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:17:08:4a:d8:71  
          inet6 addr: fe80::217:8ff:fe4a:d871/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6952 (6.9 KB)  TX bytes:7822 (7.8 KB)
          Interrupt:23 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:264 errors:0 dropped:0 overruns:0 frame:0
          TX packets:264 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:21700 (21.7 KB)  TX bytes:21700 (21.7 KB)


```

Then I started to write this reply and at one point (few minutes after) I realised there is a connection, so I ran last command once again

```

devgaze@~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:17:08:4a:d8:71  
          **inet addr:109.60.61.140**  Bcast:109.60.63.255  Mask:255.255.252.0
          inet6 addr: fe80::217:8ff:fe4a:d871/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:216 errors:0 dropped:0 overruns:0 frame:0
          TX packets:322 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:50450 (50.4 KB)  TX bytes:63022 (63.0 KB)
          Interrupt:23 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:540 errors:0 dropped:0 overruns:0 frame:0
          TX packets:540 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:45758 (45.7 KB)  TX bytes:45758 (45.7 KB)

```

So what happened in those few minutes remains a mystery to me. Anyway so I proceed with:

```

devgaze@~$ ping 8.8.8.8

PING 8.8.8.8 (8.8.8.8) 56(84) nytes of data.
From 109.60.61.140 icmp_seq=1 Destination Host Unreacheable
From 109.60.61.140 icmp_seq=2 Destination Host Unreacheable
From 109.60.61.140 icmp_seq=3 Destination Host Unreacheable

```

And this is how far did I go.

Cheers!

---

### Post by Bashing-om on 2015-10-06
Devgaze; Welp;

My thought, one has to decide how Networking is going to be managed - There can be only 1 way , and proper settings must be set up for the chosen method.
In your case I do suggest that Network-Manager be that controlling authority.
To that end .. tell the system so by editing /etc/NetworkManager/NetworkManager.conf .
change 
```

[ifupdown]
managed=false

```
to true .
And edit /etc/network/interfaces back to the default:
```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

``` as Network-Manager manages the network, all that is configured in this file is the LOcal loopback .

And IF Network manager is installed and we are going to use it: What is in this file ?
```

cat /var/lib/NetworkManager/dhclient-eth0.conf

```

Domain Name Resolution: What is in:
```

cat /etc/resolv.conf

```
(is your router handing out leases or is DNS via your ISP ?)

When ready to "try" again:
```

sudo ifdown eth0 && sudo ifup -v eth0

```

Mind you I do not use Network-Manager as my set up is very simple . My knowledge base of Network-Manager is sorta scanty. But we will work through this.
see:
[https://help.ubuntu.com/community/NetworkManager#Editing_Network_Settings_in_nm-connection-editor](https://help.ubuntu.com/community/NetworkManager#Editing_Network_Settings_in_nm-connection-editor) 

Hopefully we are not back at square one, getting a driver loaded ; all we are looking at now is configuration (?) ,

[INDENT][INDENT][INDENT]maybe YES
[/INDENT][/INDENT][/INDENT]

---

