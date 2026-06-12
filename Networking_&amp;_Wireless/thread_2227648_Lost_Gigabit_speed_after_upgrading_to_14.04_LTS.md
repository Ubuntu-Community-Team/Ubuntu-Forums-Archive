---
title: "Lost Gigabit speed after upgrading to 14.04 LTS"
date: 2014-06-03
forum: Networking &amp; Wireless
---

### Post by rdege on 2014-06-03
I have an AsRock H77M MOBO with an onboard Realtek RTL8111E NIC.  While running 13.10, my system was connected at 1GB/s to a Netgear gigabit switch.  After upgrading to 14.04 LTS, it now connects at 100Mb/s.  From a hardware perspective, I changed RJ45 cables, and connected to a different port on the switch, but to no avail.  I tried using ethtool to force the gigabit connection, but it didnt' work.  Then I noticed that the r8169 module depends on mii (modinfo r8169).  So I tried using the mii-tool, but that didn't work either.  My system is up2date with all available packages, and my current kernel is 3.13.0-27-generic.  Is there something that I'm missing??


# lspci -v
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
    Subsystem: ASRock Incorporation Motherboard (one of many)
    Flags: bus master, fast devsel, latency 0, IRQ 43
    I/O ports at e000 [size=256]
    Memory at f0004000 (64-bit, prefetchable) [size=4K]
    Memory at f0000000 (64-bit, prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 01
    Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
    Capabilities: [d0] Vital Product Data
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 01-00-00-00-68-4c-e0-00
    Kernel driver in use: r8169


# modinfo r8169
filename:       /lib/modules/3.13.0-27-generic/kernel/drivers/net/ethernet/realtek/r8169.ko
firmware:       rtl_nic/rtl8168g-3.fw
firmware:       rtl_nic/rtl8168g-2.fw
firmware:       rtl_nic/rtl8106e-2.fw
firmware:       rtl_nic/rtl8106e-1.fw
firmware:       rtl_nic/rtl8411-2.fw
firmware:       rtl_nic/rtl8411-1.fw
firmware:       rtl_nic/rtl8402-1.fw
firmware:       rtl_nic/rtl8168f-2.fw
firmware:       rtl_nic/rtl8168f-1.fw
firmware:       rtl_nic/rtl8105e-1.fw
firmware:       rtl_nic/rtl8168e-3.fw
firmware:       rtl_nic/rtl8168e-2.fw
firmware:       rtl_nic/rtl8168e-1.fw
firmware:       rtl_nic/rtl8168d-2.fw
firmware:       rtl_nic/rtl8168d-1.fw
version:        2.3LK-NAPI
license:        GPL
description:    RealTek RTL-8169 Gigabit Ethernet driver
author:         Realtek and the Linux r8169 crew <netdev@vger.kernel.org>
srcversion:     2919113FB153E8A21A85604
alias:          pci:v00000001d00008168sv*sd00002410bc*sc*i*
alias:          pci:v00001737d00001032sv*sd00000024bc*sc*i*
alias:          pci:v000016ECd00000116sv*sd*bc*sc*i*
alias:          pci:v00001259d0000C107sv*sd*bc*sc*i*
alias:          pci:v00001186d00004302sv*sd*bc*sc*i*
alias:          pci:v00001186d00004300sv*sd*bc*sc*i*
alias:          pci:v00001186d00004300sv00001186sd00004B10bc*sc*i*
alias:          pci:v000010ECd00008169sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008168sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008167sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008136sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008129sv*sd*bc*sc*i*
depends:        mii
intree:         Y
vermagic:       3.13.0-27-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        23:98:4A:C2:03:78:43:25:CC:F7:B9:5B:51:F6:C1:19:38:0E:B9:33
sig_hashalgo:   sha512
parm:           use_dac:Enable PCI DAC. Unsafe on 32 bit PCI slot. (int)
parm:           debug:Debug verbosity level (0=none, ..., 16=all) (int)

---

### Post by TheFu on 2014-06-03
Are the cables CAT5e or better?
Please post **ifconfig**, **lshw -C network** and **route **output. It isn't that we don't trust you, but ...  plus I'd like to see some more of the card settings.

---

### Post by rdege on 2014-06-03
Never hurts to have a second set of eyes.  I'd rather the problem be easy (my fault), and not difficult (OS issue).  Both cables used/tested are CAT5e.  I do have CAT6 cables around, but I'm pretty sure the problem is not hardware related, given the issue didn't exist yesterday before the upgrade.

# ifconfig

eth0      Link encap:Ethernet  HWaddr bc:5f:f4:e0:45:1d  
          inet addr:192.168.1.21  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::be5f:f4ff:fee0:451d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:745273 errors:0 dropped:66 overruns:0 frame:0
          TX packets:643109 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:354426201 (354.4 MB)  TX bytes:502004531 (502.0 MB)


# lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 06
       serial: bc:5f:f4:e0:45:1d
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.1.21 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:e000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff


# route       
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     *               255.255.255.0   U     1      0        0 eth0

---

### Post by jimmy-jad on 2014-06-03
I had the same problem, and since i changed primary Ethernet cards, and i didnt pick my gigabyte, its disabled and i cant enable it.

---

### Post by TheFu on 2014-06-03
So - in short, I got nuthin', sorry.

That data tells me that your card WANTS to talk GigE, but something is preventing it.  I'd expect the cable or switch to be the issue.  CAT5e is well beyond what GigE requires for signaling - CAT6 is extreme overkill, but not enough for 10GigE connections - dead technology, sadly for me.  If it is easy to swap in a different system with GigE to test the cable/switch, I'd do that before going too far.

Sometimes NICs need special extra settings (though none of mine do anymore).  ethtool and mii are usually the way to handle those driver tweaks if options for the driver module can't be added to start options.  I have 1 Realtek port with the same driver, but stopped using it for ...

I've added extra NICs to most of my machines here - going with Intel PRO/1000 cards. They are cheap and THE industry standard. I get that it should work as is, but ... $25 to newegg can solve this, plus having a spare card is always nice.

Did a little searching - [http://ubuntuforums.org/showthread.php?t=2140170](http://ubuntuforums.org/showthread.php?t=2140170) might help troubleshoot more.  Maybe.  I still got nuffin'.

---

### Post by totor55 on 2014-10-04
Hi,
just wondering if you got anywhere?

I have the same issue, Gb ethernet only working on 100.
Tried with ethtool to force, only to have disconnection...

Thanks

---

### Post by tgalati4 on 2014-10-04
Were you running 1/2 duplex before at gigabit speeds and now perhaps you are running full duplex at 100 Mbit speeds?

For the realtek module, *r8169*, there is a debug switch.  Load the module with it and try to capture some log files.

> parm:           debug:Debug verbosity level (0=none, ..., 16=all)

If two users have experienced this regression while upgrading to 14.04, then perhaps one should file a bug against the kernel (3.13) and the r8169 module.  Let it get kicked around a bit.

---

### Post by rdege on 2014-10-04
I was able to resolve the problem with one of the two methods:

1) I unplugged / plugged the ethernet cable into the RJ45 port on the back of the computer (not sure how this would cause a gigabit connection to fail, but still provide a solid 100Mb/s connection)
2) I rebooted the computer (maybe some updates were installed that addressed the issue (newer kernel?))

-Robert

---

### Post by tgalati4 on 2014-10-04
A quick search shows that there are quite a few bugs against the r8169 module and gigabit speeds.  There are several work arounds and several different conditions that cause it.

---

