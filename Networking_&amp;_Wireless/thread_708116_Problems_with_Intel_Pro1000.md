---
title: "Problems with Intel Pro/1000"
date: 2008-02-26
forum: Networking &amp; Wireless
---

### Post by dea_jul on 2008-02-26
Hey there,

I'm new to Ubuntu, and linux in general... so please excuse any ignorance. ;)

I just recently got a new Lenovo T60P, and decided to put Ubuntu 7.10 on it, instead of windows. But, I'm having the hardest time getting any connection to the internet. I've looked around google, and these forums for days, and I can't find anything that solves my problem.

If anyone could help, or give me any advice at all, that'd really be great. I'd really love to stick this out, but I'm having the hardest time. :(

Since I don't have an internet connection, it's hard to post the output of lengthy commands, but I've manually typed in a few of the shorter ones, in case they are useful...

```
ifconfig -a
irda0       Link encap:IrLAP HWaddr 00:00:00:00
               NOARP MTU:2048 Metric:1
              RX packets:0 errors:0 dropped:0 overruns:0 frame:0
             TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
             collisions:0 txqueue1en:8
            RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
lo         Link encap:Local Loopback
           inet addr: 127.0.0.1 Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
           UP LOOPBACK RUNNING MTU:16436 Metric:1
              RX packets:68 errors:0 dropped:0 overruns:0 frame:0
             TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
             collisions:0 txqueue1en:8
            RX bytes:5460 (5.3 KB) TX bytes:5460 (5.3 KB)
```

```

iwconfig
lo           No wireless extensions.
irda0      No wireless extensions.
```

```
lspci | grep Wireless
03:00.0 Network controller: Atheros Communications, Inc. AR5418 801.11a/b/g/n Wireless PCI Express Adapter (rev 01)
```

```

dmesg | grep Network
[    3.5000000] Intel(R) PRO/1000 Network Driver - version 7.3.20-k2-NAPI
```

```
lshw -c network
       *-network UNCLAIMED
              description: Ethernet controller
             product: 82573: Gigabit Ethernet Controller
            vendor: Intel Corporation
            physical id: 0
            bus info: pci@0000:02:00.0
           version 00
           width 32 bits
           clock 33MHz
          capabilities: pm msi pciexpress cap_list
          configuration: latency=0
      *-network UNCLAIMED
          description: Network controller
          product: AR5418 802.11a/b/g/n Wireless PCI  Express Adapter
          vendor: Atheros Communications, Inc
            physical id: 0
            bus info: pci@0000:03:00.0
           version 01
           width 64 bits
           clock 33MHz
          capabilities: pm msi pciexpress msix bus_master cap_list
          configuration: latency=0
```

```
cat /etc/network/interfaces
auto lo
iface lo inet loopback
```

I've gathered, from browsing around, that I don't have something configured properly, but I'm not wholly sure how to go about configuring it. Any help would be HUGELY appreciated! Really! And if you're ever in New York, I'll buy you a cup of coffee. I promise! :)

I'm new to this, so if you need any other information, I can pull it up and type it in. 

Thanks!!
   -Jules

---

### Post by dea_jul on 2008-02-26
Hey there,

I'm still having some trouble... but, in browsing around, I found a number of other messages in dmesg that might indicate problems. After the "Intel(R) PRO/1000 Network Driver" line, there are a couple like:
ACPI: PCI Interrupt 0000:00:id.1[B] -> GSI 17 (level, low) -> IRQ 21
And a couple others that are a bit similar. 

If the contents of dmesg would be helpful to anyone, I can burn it to a cd so I can post it here. That's not a problem. I'd just appreciate the help.

Thanks everyone!,
   -Jules

---

### Post by Fire_Chief on 2008-02-27
Hi Jules,

I have a T60 running Ubuntu 7.10 with the same wired controller (Intel Pro/1000). My dmesg output when grepping for Network shows an additional line.```
[    3.456000] Intel(R) PRO/1000 Network Driver - version 7.3.20-k2-NAPI
[    7.012000] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection

```
For some reason, your 7.10 install did not auto-detect and install the e1000 driver for your wired network card. I'm not really sure why that is since mine was working out of the box.

Are you using NetworkManager to handle the network connections or trying to configure manually?

For your wireless, verify that you have the linux-restricted-modules packages installed.
You can also check out some possible solutions [here]("http://ubuntuforums.org/showthread.php?t=668590&highlight=AR5418") and [here]("http://www.thinkwiki.org/wiki/ThinkPad_11a/b/g/n_Wireless_LAN_Mini_Express_Adapter").

Cheers

---

