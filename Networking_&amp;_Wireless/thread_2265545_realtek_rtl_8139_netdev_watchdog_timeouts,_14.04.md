---
title: "realtek rtl 8139 netdev watchdog timeouts, 14.04"
date: 2015-02-16
forum: Networking &amp; Wireless
---

### Post by Michael_Newman on 2015-02-16
Posted this over at askubuntu as well, but thinking this is probably a better spot for it.. 

Having some problems here I've been searching all over for but am yet to find a working answer for.

Notably, examples of this:

```
    Feb 16 09:10:37 trillian kernel: [45756.292178] ------------[ cut here ]------------
    Feb 16 09:10:37 trillian kernel: [45756.292205] WARNING: CPU: 1 PID: 0 at /build/buildd/linux-3.13.0/net/sched/sch_generic.c:264 dev_watchdog+0x276/0x280()
    Feb 16 09:10:37 trillian kernel: [45756.292220] NETDEV WATCHDOG: eth2 (8139cp): transmit queue 0 timed out
    Feb 16 09:10:37 trillian kernel: [45756.292223] Modules linked in: pci_stub vboxpci(OX) vboxnetadp(OX) vboxnetflt(OX) vboxdrv(OX) pppoe pppox snd_hda_codec_hdmi rfcomm snd_hda_codec_realtek bnep bluetooth binfmt_misc ipt_MASQUERADE iptable_nat nf_nat_ipv4 nf_nat xt_TCPMSS xt_tcpmss intel_rapl xt_connmark xt_mark xt_dscp iptable_mangle xt_tcpudp nf_conntrack_ipv4 nf_defrag_ipv4 xt_conntrack coretemp nf_conntrack iptable_filter ip_tables kvm_intel kvm x_tables crct10dif_pclmul crc32_pclmul ghash_clmulni_intel snd_hda_intel snd_hda_codec cryptd i915_bdw snd_hwdep snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq intel_ips drm_kms_helper snd_seq_device snd_timer drm snd mac_hid soundcore i2c_algo_bit serio_raw ppdev video lp parport_pc parport hid_generic usbhid hid psmouse 8139too 8139cp r8169 ahci mii libahci
    Feb 16 09:10:37 trillian kernel: [45756.292343] CPU: 1 PID: 0 Comm: swapper/1 Tainted: G           OX 3.13.0-45-generic #74-Ubuntu
    Feb 16 09:10:37 trillian kernel: [45756.292347] Hardware name: Gigabyte Technology Co., Ltd. To be filled by O.E.M./J1900N-D3V, BIOS F3 04/29/2014
    Feb 16 09:10:37 trillian kernel: [45756.292352]  0000000000000009 ffff88023fc83d98 ffffffff81720eb6 ffff88023fc83de0
    Feb 16 09:10:37 trillian kernel: [45756.292361]  ffff88023fc83dd0 ffffffff810677cd 0000000000000000 ffff880234256000
    Feb 16 09:10:37 trillian kernel: [45756.292369]  ffff880036e8d280 0000000000000001 0000000000000001 ffff88023fc83e30
    Feb 16 09:10:37 trillian kernel: [45756.292377] Call Trace:
    Feb 16 09:10:37 trillian kernel: [45756.292381]  <IRQ>  [<ffffffff81720eb6>] dump_stack+0x45/0x56
    Feb 16 09:10:37 trillian kernel: [45756.292398]  [<ffffffff810677cd>] warn_slowpath_common+0x7d/0xa0
    Feb 16 09:10:37 trillian kernel: [45756.292405]  [<ffffffff8106783c>] warn_slowpath_fmt+0x4c/0x50
    Feb 16 09:10:37 trillian kernel: [45756.292418]  [<ffffffff816457d6>] dev_watchdog+0x276/0x280
    Feb 16 09:10:37 trillian kernel: [45756.292425]  [<ffffffff81645560>] ? dev_graft_qdisc+0x80/0x80
    Feb 16 09:10:37 trillian kernel: [45756.292432]  [<ffffffff81074386>] call_timer_fn+0x36/0x100
    Feb 16 09:10:37 trillian kernel: [45756.292439]  [<ffffffff81645560>] ? dev_graft_qdisc+0x80/0x80
    Feb 16 09:10:37 trillian kernel: [45756.292446]  [<ffffffff8107531f>] run_timer_softirq+0x1ef/0x2f0
    Feb 16 09:10:37 trillian kernel: [45756.292454]  [<ffffffff8106cc1c>] __do_softirq+0xec/0x2c0
    Feb 16 09:10:37 trillian kernel: [45756.292462]  [<ffffffff8106d165>] irq_exit+0x105/0x110
    Feb 16 09:10:37 trillian kernel: [45756.292471]  [<ffffffff81733d55>] smp_apic_timer_interrupt+0x45/0x60
    Feb 16 09:10:37 trillian kernel: [45756.292478]  [<ffffffff817326dd>] apic_timer_interrupt+0x6d/0x80
    Feb 16 09:10:37 trillian kernel: [45756.292482]  <EOI>  [<ffffffff8104f596>] ? native_safe_halt+0x6/0x10
    Feb 16 09:10:37 trillian kernel: [45756.292497]  [<ffffffff8101caaf>] default_idle+0x1f/0xc0
    Feb 16 09:10:37 trillian kernel: [45756.292504]  [<ffffffff8101d376>] arch_cpu_idle+0x26/0x30
    Feb 16 09:10:37 trillian kernel: [45756.292512]  [<ffffffff810bef35>] cpu_startup_entry+0xc5/0x290
    Feb 16 09:10:37 trillian kernel: [45756.292520]  [<ffffffff810413fd>] start_secondary+0x21d/0x2d0
    Feb 16 09:10:37 trillian kernel: [45756.292525] ---[ end trace 070e538cd96c54b1 ]---
    Feb 16 09:10:37 trillian kernel: [45756.292543] 8139cp 0000:04:00.0 eth2: Transmit timeout, status  c   3b    0 80ff

```
I can't really trend it to any sort of trigger, though it may be related to network traffic - I noticed the kernel SYN flood protection kicking in in syslog immediately before one instance.

The interface in question is actually a PCI based ADSL2+ modem that's getting on a bit but has been perfectly functional for a lot of years.  Has its own chip for the ATM side to run the DSL line itself, a little processor and then presents out the PCI interface as a realtek 8139 100mbit ethernet card (has the realtek chip onboard).  I have the card configured as a simple bridge, and pppd handles the connection to drive my internet wan link via pppoe on that 'eth2' interface.  Long and short of it, the system sees it as an rtl8139 card, like so:

```

    04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter (rev 20)
            Subsystem: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
            Flags: bus master, medium devsel, latency 32, IRQ 18
            I/O ports at c000 [size=256]
            Memory at d0600000 (32-bit, non-prefetchable) [size=256]
            Capabilities: [50] Power Management version 2
            Kernel driver in use: 8139cp

```

When this event comes through, throughput on the card effectively ceases.  Small packets (pings, etc) can get through ok, but as size increases, they start getting dropped very rapidly.. doesn't seem like an MTU issue as it's not a hard cutoff, but even down at a few hundred bytes, it's losing packets.  Makes it effectively useless.  Only solution to it I've managed is a reboot (though I've since seen the option to ifdown/rmmod/modprobe/ifup, I'll try that one next time)

This has been running along very happily for years in an intel atom D525 mini-itx board running fedora without so much as a hiccup.  Problem started once I upgraded.

New board is a Gigabyte J1900-d3v (latest bios available) and running ubuntu 14.04 LTS, this one with a pair of Realtek 8168 GigE NICs onboard:

```
    01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
            Subsystem: Gigabyte Technology Co., Ltd Motherboard
            Flags: bus master, fast devsel, latency 0, IRQ 105
            I/O ports at e000 [size=256]
            Memory at d0804000 (64-bit, non-prefetchable) [size=4K]
            Memory at d0800000 (64-bit, prefetchable) [size=16K]
            Capabilities: [40] Power Management version 3
            Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
            Capabilities: [70] Express Endpoint, MSI 01
            Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
            Capabilities: [d0] Vital Product Data
            Capabilities: [100] Advanced Error Reporting
            Capabilities: [140] Virtual Channel
            Capabilities: [160] Device Serial Number 01-00-00-00-68-4c-e0-00
            Kernel driver in use: r8169
    
    02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
            Subsystem: Gigabyte Technology Co., Ltd Motherboard
            Flags: bus master, fast devsel, latency 0, IRQ 106
            I/O ports at d000 [size=256]
            Memory at d0704000 (64-bit, non-prefetchable) [size=4K]
            Memory at d0700000 (64-bit, prefetchable) [size=16K]
            Capabilities: [40] Power Management version 3
            Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
            Capabilities: [70] Express Endpoint, MSI 01
            Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
            Capabilities: [d0] Vital Product Data
            Capabilities: [100] Advanced Error Reporting
            Capabilities: [140] Virtual Channel
            Capabilities: [160] Device Serial Number 01-00-00-00-68-4c-e0-00
            Kernel driver in use: r8169


```
I know that the realtek drivers have a history of problems under linux, I'm wondering if the additional GigE interfaces (the old motherboard used an intel NIC onboard) is causing some sort of conflict?

I've seen mentions of IRQ conflicts (/proc/interrupts shows the 8139 eth2 on its own interrupt at 18, eth0 on 105, the other gig port eth1 is down)

I've tried adding the 'noapic' option to grub which I've also seen suggested, still failing (should I still see "IO-APIC-fasteoi" and the like in /proc/interrupts if that's the case?).. Have also seen suggestions of disabling autonegotiation, but the link fails to activate with it off.. I even tried using ndiswrapper to pull in the windows drivers but couldn't get it going.

System is as updated as I can get it.

uname -a shows:
Linux trillian 3.13.0-45-generic #74-Ubuntu SMP Tue Jan 13 19:36:28 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
r



Any help would be very much appreciated - any extra info I can provide, let me know.  Would rather not have to go buy an external modem when there's nothing wrong with the hardware I have.

**Also as a short term..** is there any way I can perhaps have that watchdog that's triggering also kick a script/execute a command so I can get it back up and going (either that interface drop & module unload or a full reboot if necessary) on its own rather than having to wait to discover it?


wireless script output:
```


########## wireless info START ##########

Report from: 16 Feb 2015 19:52 AEDT +1100

Booted last: 16 Feb 2015 19:43 AEDT +1100

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID: Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:        14.04
Codename:       trusty

##### kernel ############################

Linux 3.13.0-45-generic #74-Ubuntu SMP Tue Jan 13 19:36:28 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Could not be determined.

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
        Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
        Kernel driver in use: r8169

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
        Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
        Kernel driver in use: r8169

04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter [10ec:8139] (rev 20)
        Subsystem: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter [10ec:8139]
        Kernel driver in use: 8139cp

##### lsusb #############################

Bus 002 Device 002: ID 045b:0210 Hitachi, Ltd
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 046d:c505 Logitech, Inc. Cordless Mouse+Keyboard Receiver
Bus 001 Device 002: ID 045b:0209 Hitachi, Ltd
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

cfg80211              484040  0

##### interfaces ########################

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
mtu 9000
address 10.0.0.1
netmask 255.0.0.0
post-up /sbin/iptables-restore < /etc/iptables.rules

auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth2 up # line maintained by pppoeconf
provider dsl-provider
post-up /root/htb.sh
post-up /sbin/iptables-restore < /etc/iptables.rules

auto eth2
iface eth2 inet static
address 192.168.1.2
netmask 255.255.255.0

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>
          inet addr:10.0.0.1  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::76d4:35ff:feef:eb00/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:9000  Metric:1
          RX packets:3555 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3138 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:476648 (476.6 KB)  TX bytes:1358998 (1.3 MB)

eth1      Link encap:Ethernet  HWaddr <MAC 'eth1' [IF]>
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth2      Link encap:Ethernet  HWaddr <MAC 'eth2' [IF]>
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:faff:fe20:511/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14519 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20435 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2618520 (2.6 MB)  TX bytes:8273367 (8.2 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

eth1      no wireless extensions.

eth2      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        0.0.0.0         255.0.0.0       U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth2
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth2

##### resolv.conf #######################

##### nm-tool ###########################

./wireless_script: line 198: nm-tool: command not found

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

Acquisition of admin privileges failed.

##### iw reg get ########################

Region: Australia/Sydney (based on set time zone)

country 00:
        (2402 - 2472 @ 40), (3, 20)
        (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
        (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
        (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
        (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

eth1      no frequency information.

eth2      no frequency information.

lo        no frequency information.

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

eth2      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[cfg80211]
filename:       /lib/modules/3.13.0-45-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:
intree:         Y
vermagic:       3.13.0-45-generic SMP mod_unload modversions
signer:         Magrathea: Glacier signing key
sig_key:        34:99:21:39:F3:DA:40:B6:20:BD:55:17:59:7B:A8:5A:F5:79:7C:9A
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/qemu-system-x86.conf]
options kvm_intel nested=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth1' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0x8139 (8139cp)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth2' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"
# PCI device 0x10ec:0x8139 (ndiswrapper)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth2' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[    4.882792] 8139cp 0000:04:00.0 eth2: link up, 100Mbps, full-duplex, lpa 0x41E1 (repeated 2 times)

########## wireless info END ############


```

---

### Post by chili555 on 2015-02-16
Although this is a different NIC, the symptoms are identical: [https://bugs.launchpad.net/ubuntu/+source/linux-lts-trusty/+bug/1346828](https://bugs.launchpad.net/ubuntu/+source/linux-lts-trusty/+bug/1346828) Please see:> a workaround is to run

ethtool -K eth0 tso off
ethtool -K eth0 gso off

in /etc/rc.localAre the two new Realtek NIC's actually in use?> Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
            Subsystem: Gigabyte Technology Co., Ltd Motherboard
            Flags: bus master, fast devsel, latency 0, IRQ 105
            I/O ports at e000 [size=256]
            Memory at d0804000 (64-bit, non-prefetchable) [size=4K]
            Memory at d0800000 (64-bit, prefetchable) [size=16K]
            Capabilities: [40] Power Management version 3
            Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
            Capabilities: [70] Express Endpoint, MSI 01
            Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
            Capabilities: [d0] Vital Product Data
            Capabilities: [100] Advanced Error Reporting
            Capabilities: [140] Virtual Channel
            Capabilities: [160] Device Serial Number 01-00-00-00-68-4c-e0-00
            Kernel driver in use: r8169If not, you might also try blacklisting r8169 in case it is a conflict in some way with 8139cp.

Actually, my intuition/suspicion/sixth sense suggests to try only the blacklist step first.

---

### Post by Michael_Newman on 2015-02-16
Thanks for the response, very much appreciated.. I'd come across that bug report previously as well but had pretty much written it off (possibly incorrectly).

That said, both offloads are already turned off on all three controllers.  I'm in agreement on the suspicion of an 8169 issue there, but unfortunately I'm using one of them to connect back into the LAN (the box is effectively a router), so blacklisting isn't really an option.  No room for another NIC in the box (it's only a mini-itx thing, 1 PCI slot) and no USB NIC handy to test the theory with.


In other news though, it failed again overnight so I had the chance to try the 'alternate' recovery method.. dropping the ppp session & eth interface, removing & reloading the modules (8139cp & 8139too) seems to correct the issue, meaning a hardware reload isn't required & software does seem the culprit... some sort of buffer overflow?


FWIW:
```

root@trillian:~# ethtool -k eth2
Features for eth2:
rx-checksumming: on
tx-checksumming: off
        tx-checksum-ipv4: off
        tx-checksum-ip-generic: off [fixed]
        tx-checksum-ipv6: off [fixed]
        tx-checksum-fcoe-crc: off [fixed]
        tx-checksum-sctp: off [fixed]
scatter-gather: off
        tx-scatter-gather: off
        tx-scatter-gather-fraglist: off [fixed]
tcp-segmentation-offload: off
        tx-tcp-segmentation: off
        tx-tcp-ecn-segmentation: off [fixed]
        tx-tcp6-segmentation: off [fixed]
udp-fragmentation-offload: off [fixed]
generic-segmentation-offload: off
generic-receive-offload: on
large-receive-offload: off [fixed]
rx-vlan-offload: on
tx-vlan-offload: on
ntuple-filters: off [fixed]
receive-hashing: off [fixed]
highdma: on [fixed]
rx-vlan-filter: off [fixed]
vlan-challenged: off [fixed]
tx-lockless: off [fixed]
netns-local: off [fixed]
tx-gso-robust: off [fixed]
tx-fcoe-segmentation: off [fixed]
tx-gre-segmentation: off [fixed]
tx-ipip-segmentation: off [fixed]
tx-sit-segmentation: off [fixed]
tx-udp_tnl-segmentation: off [fixed]
tx-mpls-segmentation: off [fixed]
fcoe-mtu: off [fixed]
tx-nocache-copy: off
loopback: off [fixed]
rx-fcs: off [fixed]
rx-all: off [fixed]
tx-vlan-stag-hw-insert: off [fixed]
rx-vlan-stag-hw-parse: off [fixed]
rx-vlan-stag-filter: off [fixed]
l2-fwd-offload: off [fixed]


```

Not running any vlan config on it, so I suppose I could disable those ones.... actually.. 
```

root@trillian:/root# ethtool -K eth2 tx-vlan-offload off
ethtool: bad command line argument(s)
For more information run ethtool -h
root@trillian:/root# ethtool -K eth2 tvo off
ethtool: bad command line argument(s)
For more information run ethtool -h

```

Unless I'm getting the syntax wrong, no I can't.

---

### Post by Michael_Newman on 2015-02-17
I'm also wondering if & how I can trigger a script from that watchdog event so I might be able to recover it with minimal downtime. I'm presuming it's rtkit that's doing it (no hardware watchdog in there), but I can't seem to find anything about the watchdog side of things in the documentation of it..

---

### Post by chili555 on 2015-02-17
Frankly, I am just about stumped. This is the first issue of this kind that I've seen. As in many cases for me, it's a case of educated guesswork and Google. I'm not an 8139cp expert; I'm a generalist in a specialized field!

I am quite suprised that the parameters such as tx-vlan-offload that are not [fixed] and presumably manipulable, really are not. 

I wonder if manipulating a driver parameter or two might help us:```
modinfo 8139cp
<snip>
parm:           debug:8139cp: bitmapped message enable number (int)
parm:           multicast_filter_limit:8139cp: maximum number of filtered multicast addresses (int)

```I checked here: [http://lxr.free-electrons.com/source/drivers/net/ethernet/realtek/8139cp.c?v=3.13](http://lxr.free-electrons.com/source/drivers/net/ethernet/realtek/8139cp.c?v=3.13)  and I see:> 94  /* Maximum number of multicast addresses to filter (vs. Rx-all-multicast).
 95    The RTL chips use a 64 element hash table based on the Ethernet CRC.  */
 96 static int multicast_filter_limit = 32;
 97 module_param(multicast_filter_limit, int, 0);
 98 MODULE_PARM_DESC (multicast_filter_limit, "8139cp: maximum number of filtered multicast addresses");I suggest you experiment a bit:```
sudo -i
echo "options 8139cp multicast_filter_limit=16"  >  /etc/modprobe.d/8139cp.conf
modprobe -r 8139too
modprobe -r 8139cp
modprobe 8139cp
exit
```Of course, setting debug to 0 or 1 might be useful as well.

>  doesn't seem like an MTU issue as it's not a hard cutoff, Have you experimented? On my DSL connection, it seems to work best at 1492:```
sudo ifconfig eth2 mtu 1492
```

---

### Post by Michael_Newman on 2015-02-17
> **chili555 said:**
> Frankly, I am just about stumped.
Glad it's not just me!

I am quite suprised that the parameters such as tx-vlan-offload that are not [fixed] and presumably manipulable, really are not. 

[quoteI wonder if manipulating a driver parameter or two might help us:[/quote]

Worth a shot, I'll drop it in.

> Have you experimented? On my DSL connection, it seems to work best at 1492:```
sudo ifconfig eth2 mtu 1492
```
A 1492 MTU makes sense for the PPP interface, since the PPPoE header is taking those extra 8 bytes from the Ethernet payload for its own header.  The underlying Ethernet interface itself would still want to be at 1500 though, I'd think...

---

