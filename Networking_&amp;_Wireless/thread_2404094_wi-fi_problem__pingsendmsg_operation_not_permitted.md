---
title: "wi-fi problem  ping:sendmsg: operation not permitted"
date: 2018-10-19
forum: Networking &amp; Wireless
---

### Post by jgw on 2018-10-19
logs keeps repeating:

dbus: failed to construct signal
receive_packet failed on wlx00a1b0c24593: network is down
bgscan simple. failed to enable signal strength monitoring
<error> [1539994860.6583] wifi-wext: (wlx00a1b0c24593) error setting powers

tried: sudo iptables -P OUTPUT ACCEPT - didn't work

It thinks that its connected

Thoughts?

---

### Post by jgw on 2018-10-20
This morning, when I check this system, my wifi was working just fine.  I did absolutely nothing and left the machine on all night long. 

I am going to mark this as solved although I have absolutely no idea how that happened.  

If anybody is interesting I have also posted my logs report from this morning:
[https://pastebin.com/v4v82Ly1](https://pastebin.com/v4v82Ly1) 

Below is my wifi stuff:
greg@movies:~$ sudo lshw -C network
  *-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: enp1s0
       version: 06
       serial: 40:8d:5c:4d:8d:8e
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:35 ioport:e000(size=256) memory:fea00000-fea00fff memory:d0800000-d0803fff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:3
       logical name: wlx00a1b0c24593
       serial: 00:a1:b0:c2:45:93
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8712u ip=192.168.0.42 multicast=yes wireless=IEEE 802.11bgn
greg@movies:~$
greg@movies:~$ modinfo r8169
filename:       /lib/modules/4.15.0-36-generic/kernel/drivers/net/ethernet/realtek/r8169.ko
firmware:       rtl_nic/rtl8107e-2.fw
firmware:       rtl_nic/rtl8107e-1.fw
firmware:       rtl_nic/rtl8168h-2.fw
firmware:       rtl_nic/rtl8168h-1.fw
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
srcversion:     5B51A62816D68383E8ADAE6
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
alias:          pci:v000010ECd00008161sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008136sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008129sv*sd*bc*sc*i*
depends:        mii
retpoline:      Y
intree:         Y
name:           r8169
vermagic:       4.15.0-36-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           use_dac:Enable PCI DAC. Unsafe on 32 bit PCI slot. (int)
parm:           debug:Debug verbosity level (0=none, ..., 16=all) (int)
greg@movies:~$

---

