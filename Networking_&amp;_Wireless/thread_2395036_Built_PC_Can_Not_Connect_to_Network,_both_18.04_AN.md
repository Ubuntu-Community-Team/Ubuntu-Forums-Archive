---
title: "Built PC Can Not Connect to Network, both 18.04 AND 16.04 (Hardline)"
date: 2018-06-24
forum: Networking &amp; Wireless
---

### Post by muddpup64 on 2018-06-24
Hello!

I just built my first computer and am putting Ubuntu on it! We are having some major problems however...

I can not connect to the internet via ethernet. It first started with the built in LAN supported chip provided by the motherboard. Ten hours of work later and no progress, so I went out and bought a PCIe Gigabit NIC. And guess what?! It doesn't work either.. I just so happen to have two drives with two different OS's (16.04, 18.04) in the machine and neither can connect, both show the same symptoms. I can confirm without a shadow of a doubt this is a problem with my computer and not the network it is tied to. Furthermore, I have tried this on multiple networks with he same result. Here is the motherboard I am using: [https://www.asus.com/us/Motherboards/TUF-X299-MARK-2/](https://www.asus.com/us/Motherboards/TUF-X299-MARK-2/)

This is what I have worked out so far;

ifconfig -a
```
 enp0s31f6 Link encap:Ethernet  HWaddr 18:31:bf:6d:3f:3c  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:100 errors:0 dropped:9 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12841 (12.8 KB)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:92f00000-92f20000 

enp23s0   Link encap:Ethernet  HWaddr 00:e0:4c:89:20:45  
          inet6 addr: fe80::be61:d815:c5fc:11c2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:164 errors:0 dropped:9 overruns:0 frame:0
          TX packets:364 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:63818 (63.8 KB)  TX bytes:69682 (69.6 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:17150 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17150 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:10541135 (10.5 MB)  TX bytes:10541135 (10.5 MB) 
```

*Note* Sometimes the inet6 line will appear, sometimes not. It depends on which ethernet connection the computer is trying to connect to at that moment in time. This is in regards to "enp0s31f6" and "enp23s0". Again, the outcomes for both connections are the same. I simply am adding them both in the print out to save time.

lspci -nnk | grep 0200 -A2
```
 00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I219-V [8086:15b8]
    Subsystem: ASUSTeK Computer Inc. Ethernet Connection (2) I219-V [1043:8672]
    Kernel driver in use: e1000e
--
17:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:0123]
    Kernel driver in use: r8169  
```

dmesg | grep e100
```
 [    0.901950] e1000e: Intel(R) PRO/1000 Network Driver - 3.2.6-k
[    0.901951] e1000e: Copyright(c) 1999 - 2015 Intel Corporation.
[    0.952298] e1000e 0000:00:1f.6: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    1.300354] e1000e 0000:00:1f.6 eth0: registered PHC clock
[    1.300356] e1000e 0000:00:1f.6 eth0: (PCI Express:2.5GT/s:Width x1) 18:31:bf:6d:3f:3c
[    1.300357] e1000e 0000:00:1f.6 eth0: Intel(R) PRO/1000 Network Connection
[    1.300441] e1000e 0000:00:1f.6 eth0: MAC: 12, PHY: 12, PBA No: FFFFFF-0FF
[    1.301790] e1000e 0000:00:1f.6 enp0s31f6: renamed from eth0
[   53.429975] e1000e: enp0s31f6 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[   53.429977] e1000e 0000:00:1f.6 enp0s31f6: 10/100 speed: disabling TSO  
```

*Note* As far as I can tell, in these last two lines, I establish a connection and then it fails shortly after. 

In summary, both devices on both OS's and two different networks perform exactly the same with the same symptoms. From what I can tell both devices make an attempt at connection and then fall short. As for why, I have no idea. I am not sure where to go from where I am at other than to boot the system on Windows and see if there is a change. But this is Ubuntu Forums, I'm sure we can figure it out before I succumb to the dark side. &#128539;

Any and all help is appreciated. I am banging my head against a wall over here and until this problem is solved all I have is a $2,000 paper weight. 

Thanks,
  Matt

---

### Post by muddpup64 on 2018-06-25
Bump

This expensive paper weight is kicking my ass. I posted this here in hopes it would have more eyes on it. If it needs to be moved to a more appropriate section, can a mod please do so?

---

### Post by wildmanne39 on 2018-06-25
*Thread moved to **Networking & Wireless for a more appropriate fit**.*

---

### Post by oldfred on 2018-06-25
My Asus motherboard is older. But same kernel driver, but using e1000e, but no mention of the r8169. Do  you have dual ports with different drivers? Perhaps conflicts?

> [    1.008442] e1000e: Intel(R) PRO/1000 Network Driver - 3.2.6-k
[    1.008442] e1000e: Copyright(c) 1999 - 2015 Intel Corporation.
[    1.008618] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    1.080961] e1000e 0000:00:19.0 0000:00:19.0 (uninitialized): registered PHC clock
[    1.149682] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) 10:c3:7b:6e:0c:af
[    1.149683] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    1.149711] e1000e 0000:00:19.0 eth0: MAC: 11, PHY: 12, PBA No: FFFFFF-0FF
[    1.150227] e1000e 0000:00:19.0 eno1: renamed from eth0
[    7.606202] e1000e: eno1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx

---

### Post by muddpup64 on 2018-06-25
> **oldfred said:**
> My Asus motherboard is older. But same kernel driver, but using e1000e, but no mention of the r8169. Do  you have dual ports with different drivers? Perhaps conflicts?

The r8169 is the driver for a second PCIe NIC I installed. After no success with the native LAN I bought it in hopes I could get it to work. Here it the print out after I remove the second NIC:

```
 muddpup@********:~$ ifconfig -a
enp0s31f6 Link encap:Ethernet  HWaddr xx:xx
          inet6 addr: fe80::653e:c5c5:c0b:eba0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8965 (8.9 KB)  TX bytes:7063 (7.0 KB)
          Interrupt:20 Memory:92f00000-92f20000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:10297 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10297 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:2758010 (2.7 MB)  TX bytes:2758010 (2.7 MB)  
```


Woah, one of my print outs changed. Check this out:

```
 muddpup@********:~$ dmesg | grep e1000
[    0.913898] e1000e: Intel(R) PRO/1000 Network Driver - 3.2.6-k
[    0.913899] e1000e: Copyright(c) 1999 - 2015 Intel Corporation.
[    0.947540] e1000e 0000:00:1f.6: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    1.260728] e1000e 0000:00:1f.6 eth0: registered PHC clock
[    1.260729] e1000e 0000:00:1f.6 eth0: (PCI Express:2.5GT/s:Width x1) 18:31:bf:6d:3f:3c
[    1.260730] e1000e 0000:00:1f.6 eth0: Intel(R) PRO/1000 Network Connection
[    1.260800] e1000e 0000:00:1f.6 eth0: MAC: 12, PHY: 12, PBA No: FFFFFF-0FF
[    1.262135] e1000e 0000:00:1f.6 enp0s31f6: renamed from eth0
[  192.682984] e1000e: enp0s31f6 NIC Link is Down
[  236.770497] e1000e: enp0s31f6 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[  236.770504] e1000e 0000:00:1f.6 enp0s31f6: 10/100 speed: disabling TSO
[  245.277787] e1000e: enp0s31f6 NIC Link is Down
[  250.146240] e1000e: enp0s31f6 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[  250.146247] e1000e 0000:00:1f.6 enp0s31f6: 10/100 speed: disabling TSO
[  272.573177] e1000e: enp0s31f6 NIC Link is Down
[  275.474131] e1000e: enp0s31f6 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[  275.474138] e1000e 0000:00:1f.6 enp0s31f6: 10/100 speed: disabling TSO  
```

Correct me if I'm wrong, but isn't it making multiple attempts at a connection and then failing? The ending is the same as before however: " e1000e 0000:00:1f.6 enp0s31f6: 10/100 speed: disabling TSO "
But ya oldfred, my on board NIC using the same driver as yours, "e1000e".

---

### Post by muddpup64 on 2018-06-25
I had a suspicion it is attempting to only connect via IPv6. I did an experiment with a know good machine and it turns out both networks I tested on have no IPv6 support.

So, is there any thing I can do to give my machine IPv4 support? 

Or is this on a hardware level? I would not think so. I bought another NIC (which I have mentioned) and it did not work either.

---

### Post by oldfred on 2018-06-25
Best not to post MAC.

Do you have Internet icon in upper right corner.
Does it show IP4?
Or edit connections.

They changed, and I do not know details of new way of configuring Internet. 
Mine just worked.

---

### Post by muddpup64 on 2018-06-26
The top right corner of the desktop gui? No, it just has the normal ethernet symbol.

I know for sure one of the networks only supports IPv4 because it's owner set it up that way. As for the other network, I attempted to connect while forcing IPv6 and was unable to connect. As soon as you turn on IPv4, it works again.

I do have the option to edit connection however. If that is what you are asking.

I can send screenshot later tonight but I am at work right now.

---

### Post by oldfred on 2018-06-26
Then is router set to restrict who can connect and your system is not in list that works?

---

### Post by muddpup64 on 2018-06-26
I forgot to mention a crucial piece of information. The machine I was able to connect with IPv4 is NOT the same machine I am having problems with. It is a separate device whose only purpose is to act as a known good. The machine I am having problems with won't connect AT ALL.

As for a system blacklist, ya, there is no such thing on both networks.

---

### Post by oldfred on 2018-06-26
On the system that does not work, can you use the Internet Icon in upper right corner to edit connections?

Did you do any manual Internet configuration? 
All my recent systems have just worked, but I understand that using different configuration methods can create conflicts.
In old days we used ifconfig, but then they said the then new gui config conflicted with that. Or ifconfig was only for servers.
Now there is even a newer way to config, not sure if just icon in upper right corner. Or if system settings network is different.

---

### Post by muddpup64 on 2018-06-26
Yes, both 16.04 and 18.04 have an icon that let's me change the connection(s). 


It might be worth noting that I spend most of my time in 16.04 side of things. It is an old drive out of my laptop and has a bunch of troubleshooting utilities that I would otherwise have to install on 18.04. Ya know on a computer that has no internet access. (see title)

---

### Post by oldfred on 2018-06-26
Since two different NIC do not work, I am thinking it may be a setting in router or bad wire to router.
Does router see computer?

---

### Post by muddpup64 on 2018-06-26
> **oldfred said:**
> Since two different NIC do not work, I am thinking it may be a setting in router or bad wire to router.
Does router see computer?

While my box is attempting to connect to the network, it grabs a 30 second DHCP lease on the router. It does this about 3 times before it just gives up. SO the router can see it. For very brief moments.

I checked my lease renewal time in my syslog. It is within what I would consider normal. (34260 seconds to be percise)

---

### Post by oldfred on 2018-06-26
My older Asus has a network stack enable/disable, with default of enabled.
Check UEFI settings. You may have more with a newer system.

You may need a boot parameter. My system does not and most Intel based do not. But many AMD system need boot parameters for various things to work.

Found this also:
       Asus Prime Z270-A  Ethernet patch
[URL="https://ubuntuforums.org/showthread.php?t=2351572"]https://ubuntuforums.org/showthread.php?t=2351572

      [/URL]
 Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown and other boot parameters
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset. 
    [URL="https://ubuntuforums.org/showthread.php?t=2351572"]
[/URL]

---

### Post by Dennis N on 2018-06-26
Did you try connecting ethernet cable directly from modem to computer without router?

FYI, This computer has same ethernet controller details:

```
dmn@Roxanne:~$ inxi -n
Network:   Card-1: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169
           IF: enp2s0 state: up speed: 1000 Mbps duplex: full
           mac: xx
           Card-2: ASUSTek 802.11n Network Adapter driver: rt2800usb
           IF: wlxe0b9a5079265 state: N/A mac: N/A

```

---

### Post by muddpup64 on 2018-06-26
> **oldfred said:**
> My older Asus has a network stack enable/disable, with default of enabled.
Check UEFI settings. You may have more with a newer system.

You may need a boot parameter. My system does not and most Intel based do not. But many AMD system need boot parameters for various things to work.

Found this also:
       Asus Prime Z270-A  Ethernet patch
[URL="https://ubuntuforums.org/showthread.php?t=2351572"]https://ubuntuforums.org/showthread.php?t=2351572

      [/URL]
 Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown and other boot parameters
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset. 
    [URL="https://ubuntuforums.org/showthread.php?t=2351572"]
[/URL]

So I took a look in the bios and found my network stack disabled. This is weird not only because me and my buddy's dad (who knows way more about this than me) had both been in there looking for such a thing BUT when I enabled it, nothing changed.
Furthmore, this link ( [https://ubuntuforums.org/showthread.php?t=2351572](https://ubuntuforums.org/showthread.php?t=2351572) ). I had seen this post and was working to install a driver update. However I could not figure out how to install the damn thing. I eventually got distracted down another potential fix.

Here is what I don't understand in the README file; ```

5. To assign an IP address to the interface, enter the following:

   ifconfig em<interface_num> <IP_address>
```

What is the interface number and what IP address am I supposed to use? The MAC address?

---

### Post by noah31 on 2018-06-26
I've got a really dumb suggestion, try swapping ethernet cables. I've had a few go bad on me, they will sometimes show symptoms similar to yours.

---

### Post by muddpup64 on 2018-06-26
> **noah31 said:**
> I've got a really dumb suggestion, try swapping ethernet cables. I've had a few go bad on me, they will sometimes show symptoms similar to yours.

Done that.

---

### Post by oldfred on 2018-06-26
The old ifconfig commands are still available.
Not sure if they conflict with the gui methods. Last I saw posted was they may, but since my system works, I did not pay close attention.

This shows your connections:
ifconfig -v
More info on ifconfig
man ifconfig

Interfaces have changed, used to be eth0, but now mine is eno1.
Now with most routers you set the ip in the router. And have to be careful not to use any DHCP.
My older routers used a range for DHCP. My newer routers use everything for DHCP, and you have to set the ip in the router.

fred@bionic-z97:~$ ifconfig -v
eno1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 10.0.0.36  netmask 255.255.255.0  broadcast 10.0.0.255
And lots of inet6 info & other data.

Even if I shutdown & reboot my router now seems to always use 10.0.0.36 although not specifically set as a fixed address (I do not think?)

---

### Post by muddpup64 on 2018-06-27
> **oldfred said:**
> The old ifconfig commands are still available.
Not sure if they conflict with the gui methods. Last I saw posted was they may, but since my system works, I did not pay close attention.

This shows your connections:
ifconfig -v
More info on ifconfig
man ifconfig

Interfaces have changed, used to be eth0, but now mine is eno1.
Now with most routers you set the ip in the router. And have to be careful not to use any DHCP.
My older routers used a range for DHCP. My newer routers use everything for DHCP, and you have to set the ip in the router.

fred@bionic-z97:~$ ifconfig -v
eno1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 10.0.0.36  netmask 255.255.255.0  broadcast 10.0.0.255
And lots of inet6 info & other data.

Even if I shutdown & reboot my router now seems to always use 10.0.0.36 although not specifically set as a fixed address (I do not think?)

Getting this error in the make process: ```
Makefile:3: *** missing separator. Stop.
```

I assume there is an error on line three in the make file?

---

### Post by muddpup64 on 2018-06-30
So the driver I got from intel is written for BSD. I did some fiddling to get rid of my missing separator error but the build is dependent on some BSD libraries. Is there a way to convert this to something my system can understand?

muddpup@*****:~*******/em-7.7.4/src$ make
```
Makefile:34: bsd.kmod.mk: No such file or directory
make: *** No rule to make target 'bsd.kmod.mk'.  Stop.

```


Here is the make file after my edits:
```
#$FreeBSD$
.PATH:  ${.CURDIR}

KMOD    = if_em
KMODDIR ?= /boot/kernel
SRCS    = device_if.h bus_if.h pci_if.h
SRCS    += $(CORE_SRC) $(COMMON_SHARED) $(LEGACY_SHARED) $(PCIE_SHARED)
CORE_SRC = if_em.c if_lem.c e1000_osdep.c em_compat.c
# Shared
COMMON_SHARED = e1000_api.c e1000_phy.c e1000_nvm.c e1000_mac.c e1000_manage.c
PCIE_SHARED = e1000_80003es2lan.c e1000_ich8lan.c e1000_82571.c
LEGACY_SHARED = e1000_82540.c e1000_82542.c e1000_82541.c e1000_82543.c

# These flags are only used when in a standalone tarball build
CFLAGS  += -DINET -DINET6 -DEM_STANDALONE_BUILD

# Uncomment this to disable Fast interrupt handling.
#CFLAGS  += -DEM_LEGACY_IRQ

# DEVICE_POLLING for a non-interrupt-driven method
#CFLAGS  += -DDEVICE_POLLING

# Uncomment this to enable the stack multiqueue routines
# with this driver you do not get multiple tx queues,
# but it does provide input queuing. Testing has shown
# some stability issues so its off by default.
# NOTE: it has been found that UDP intensive traffic
#       actually does better with the old stack interface
#       and so it seems better to have this off by default.
#       however it works fine, and some workloads may benefit
#       having it on.
#CFLAGS  += -DEM_MULTIQUEUE

include    bsd.kmod.mk
```

I was also told to see if there is a conflict in the modules.I go this:

grep "e100" /proc/modules
```
e1000e 237568 0 - Live 0x0000000000000000
ptp 20480 1 e1000e, Live 0x0000000000000000

```

grep -i "e100" /etc/modprobe.d/*
```
blacklist.conf:# replaced by e100 
```

My thoughts on these print out, "Wow, great. What do they mean and how are they useful?"

Help.

---

### Post by oldfred on 2018-06-30
Since my system with similar hardware & driver works, I doubt tying to compile something from BSD will work.
Not sure if updated driver in 18.10, yet or if newer driver downloaded since I had Internet?

Does your motherboard also have wireless?

---

### Post by muddpup64 on 2018-07-01
> **oldfred said:**
> Since my system with similar hardware & driver works, I doubt tying to compile something from BSD will work.
Not sure if updated driver in 18.10, yet or if newer driver downloaded since I had Internet?

Does your motherboard also have wireless?


I'm sorry, I did not post a reply as I was being a grumpy ******* at the time. I solved the issue.

My system clock was set about 100 years in the future. This discrepancy created a scenario where my rig thought everything was an un-secure connection. It would then proceed to run around with it's hair on fire. I never would have thought to even look there honestly.

We started by creating a connection by manually setting the IP address AND the DNS. That got us connected and updating the kernel. I had set the IP before, but not until I also set the DNS did this work. Those updates did not fix the issue however. Only after I started using a web browser and seeing expired certificates (expiration date 2020, btw), did I even remotely think to look there. Went into the BIOS, set the correct time, deleted the IP and DNS, set it to full auto, and everything runs great now! Spread the word of (in)correct system clocks, it's what Jesus would want.
 :guitar:

---

