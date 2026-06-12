---
title: "Ethernet and Wireless &quot;Network Unclaimed&quot; on New Install of Ubuntu 14.04"
date: 2017-12-25
forum: Networking &amp; Wireless
---

### Post by ublazay on 2017-12-25
Hello all,

I am a new Ubuntu user who recently installed Ubuntu 14.04 to dual boot with Windows 10. My issue is that neither the wireless nor ethernet menu's are showing up so I cannot establish an internet connection. This is essential to doing anything so it's the first thing I'd like to take care of. Both ethernet and wireless work in windows so I know the router isn't the problem. I've done a bit of searching and it seems like this is due to me not having the right drivers installed but I don't know where to get them. I've seen people with similar issues get their problems solved so I've copied some of the outputs some people have asked them to post on their threads. Hopefully this will expedite my debugging process.

Please note that I'm as new as a user as possible so detailed instructions would be greatly appreciated. Also, keep in mind that I DO NOT HAVE INTERNET. Most of the solutions I've seen online ask you to "download" this or "apt-get" that. I can download something in Windows and access it from Ubuntu but please don't suggest things that require me to have internet within Ubuntu.

Below, I have the output to certain commands (in bold) that I've seen other people ask for:
**ifconfig**
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:181 errors:0 dropped:0 overruns:0 frame:0
          TX packets:181 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:13024 (13.0 KB)  TX bytes:13024 (13.0 KB)

**sudo lshw -C network**
  *-network UNCLAIMED     
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 78
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:ec000000-ec001fff
  *-network UNCLAIMED
       description: Ethernet controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 1f.6
       bus info: pci@0000:00:1f.6
       version: 21
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: latency=0
       resources: memory:ec100000-ec11ffff

**uname -r**
4.4.0-31-generic

**lspci**
00:00.0 Host bridge: Intel Corporation Device 5904 (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Device 5916 (rev 02)
00:14.0 USB controller: Intel Corporation Device 9d2f (rev 21)
00:14.2 Signal processing controller: Intel Corporation Device 9d31 (rev 21)
00:16.0 Communication controller: Intel Corporation Device 9d3a (rev 21)
00:17.0 SATA controller: Intel Corporation Device 9d03 (rev 21)
00:1c.0 PCI bridge: Intel Corporation Device 9d10 (rev f1)
00:1c.6 PCI bridge: Intel Corporation Device 9d16 (rev f1)
00:1d.0 PCI bridge: Intel Corporation Device 9d18 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Device 9d58 (rev 21)
00:1f.2 Memory controller: Intel Corporation Device 9d21 (rev 21)
00:1f.3 Audio device: Intel Corporation Device 9d71 (rev 21)
00:1f.4 SMBus: Intel Corporation Device 9d23 (rev 21)
00:1f.6 Ethernet controller: Intel Corporation Device 15d8 (rev 21)
04:00.0 Network controller: Intel Corporation Device 24fd (rev 78)

**arch**
x86_64

Any help would be greatly appreciated! Thanks in advance

---

### Post by jeremy31 on 2017-12-25
Good info provided, try Ubuntu 16.04.3 and at least the wifi should work.  Your hardware is too new for Ubuntu 14.04

---

### Post by ublazay on 2017-12-25
I was previously using Ubuntu 16.04 but reverted to 14.04 for a host of reasons related to the work I'm going to be doing/compatibility issues. Switching back to 16.04 would have to be a worst case scenario. Are you saying it's outright impossible to use 14.04 with my hardware or that it's just going to be a hassle? I'd really like to find a way.

---

### Post by jeremy31 on 2017-12-26
A temporary workaround is at [https://askubuntu.com/a/859263/300665](https://askubuntu.com/a/859263/300665)
If the linux-firmware download is not available, use [http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.157.14_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.157.14_all.deb)

---

### Post by ublazay on 2017-12-26
Yes! This worked for me. Thanks! But why is this a "temporary" workaround?

---

### Post by jeremy31 on 2017-12-26
The kernel itself is no longer supported but we can use it to download things that are supported.  Please post results for ```
lspci -nnk | grep -iA3 net
```

---

