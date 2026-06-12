---
title: "Ubuntu Server eth0 got missing"
date: 2015-10-21
forum: Networking &amp; Wireless
---

### Post by vnish11 on 2015-10-21
Ubuntu Server eth0 & eth1 got missing after restart and prior to restart controller is with DPDK not with kernel.

**Here is detailed of a problem...**

Till yesterday everything was working fine. My machine has ubuntu server 15.04 having 4 Network adapter.

In one of the demo program of DPDK, i assigned eth0 and eth1 to DPDK, till this point i had no issue. After that i restarted system without moving back NIC to kernel and from that time, i am unable to see my eth0 and eth1.

--
ls -c network

root@ubuntu-1:~# lshw -C network
*-network
description: Ethernet interface
product: NetXtreme II BCM5708 Gigabit Ethernet
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:03:00.0
logical name: eth2
version: 12
serial: 00:24:81:a5:8f:30
size: 1Gbit/s
capacity: 1Gbit/s
width: 64 bits
clock: 66MHz
capabilities: pcix pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=bnx2 driverversion=2.2.5 duplex=full firmware=bc 1.9.6 ip=10.101.31.100 latency=64 link=yes mingnt=64 multicast=yes port=twisted pair speed=1Gbit/s
resources: irq:28 memory:f8000000-f9ffffff
*-network DISABLED
description: Ethernet interface
product: NetXtreme II BCM5708 Gigabit Ethernet
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:05:00.0
logical name: eth3
version: 12
serial: 00:24:81:a5:7e:ee
capacity: 1Gbit/s
width: 64 bits
clock: 66MHz
capabilities: pcix pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=bnx2 driverversion=2.2.5 duplex=half firmware=bc 1.9.6 latency=64 link=no mingnt=64 multicast=yes port=twisted pair
resources: irq:19 memory:fa000000-fbffffff
*-network DISABLED
description: Ethernet interface
physical id: 1
logical name: virbr0-nic
serial: 52:54:00:12:4b:df
size: 10Mbit/s
capabilities: ethernet physical
configuration: autonegotiation=off broadcast=yes driver=tun driverversion=1.6 duplex=full link=no multicast=yes port=twisted pair speed=10Mbit/s
==
(It is not showing the device in pci list.)
lspci -nn | grep Ethernet
03:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme II BCM5708 Gigabit Ethernet [14e4:164c] (rev 12)
05:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme II BCM5708 Gigabit Ethernet [14e4:164c] (rev 12)

One other machine with everything working fine has output like
[
lspci -nn | grep Ethernet
03:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme II BCM5708 Gigabit Ethernet [14e4:164c] (rev 12)
05:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme II BCM5708 Gigabit Ethernet [14e4:164c] (rev 12)
0b:00.0 Ethernet controller [0200]: Intel Corporation 82571EB Gigabit Ethernet Controller [8086:105e] (rev 06)
0b:00.1 Ethernet controller [0200]: Intel Corporation 82571EB Gigabit Ethernet Controller [8086:105e] (rev 06)
]
--
sudo modprobe e1000e
**doesn't show anything.
--

Please suggest what to do ?


I really appreciate.

---

### Post by chili555 on 2015-10-21
I am not at all familiar with DPDK. I haven't any idea what it is or how it works. I suggest you check the message log for clues:```
dmesg | grep - e eth -e bnx2
```I suggest you also retrace the process you followed here:> In one of the demo program of DPDK, i assigned eth0 and eth1 to DPDK,I'd probably also check the documentation for DPDK for any hints about networking.

Finally, I suggest you either amend the title of this thread to reference DPDK or start a new thread so that DPDK is in the thread title. I hope it will catch the eye of someone who knows something about DPDK. I know nothing.

I wish I could be of more assistance.

---

### Post by vnish11 on 2015-10-21
OK here is the output of command 
------
dmesg | grep -e eth -e bnx2

[    0.140005] ACPI Error: Method parse/execution failed [\_SB_._OSC] (Node ffff88012f4a7190), AE_AML_BUFFER_LIMIT (20141107/psparse-536)
[    5.835709] bnx2: QLogic NetXtreme II Gigabit Ethernet Driver bnx2 v2.2.5 (December 20, 2013)
[    6.516367] bnx2 0000:03:00.0 eth0: Broadcom NetXtreme II BCM5708 1000Base-T (B2) PCI-X 64-bit 133MHz found at mem f8000000, IRQ 18, node addr 00:24:81:a5:8f:30
[    6.996383] bnx2 0000:05:00.0 eth1: Broadcom NetXtreme II BCM5708 1000Base-T (B2) PCI-X 64-bit 133MHz found at mem fa000000, IRQ 19, node addr 00:24:81:a5:7e:ee
[   15.739606] bnx2 0000:03:00.0 eth2: renamed from eth0
[   15.764341] bnx2 0000:05:00.0 eth3: renamed from eth1
[   19.276046] bnx2 0000:03:00.0 eth2: using MSI
[   19.276126] IPv6: ADDRCONF(NETDEV_UP): eth2: link is not ready
[   22.450384] bnx2 0000:03:00.0 eth2: NIC Copper Link is Up, 1000 Mbps full duplex
[   22.450472] IPv6: ADDRCONF(NETDEV_CHANGE): eth2: link becomes ready


==> Let me simplify my question.
What I have to do, if my Network adapter is not visible to kernel itself.
As I have checked lshw and lspci, their is no information that I am looking for, also in BIOS I am not getting any entry related to Intel Gigabyte Ethernet Controller.

---

### Post by michi1983 on 2015-10-22
I would say you did something wrong when configuring DPDK.
Regarding [this document]("https://gist.github.com/ConradIrwin/9077440") I would first try to unload the modules you loaded or even better restore your system to the point **before **you played around with DPDK.

And another advise:
I would really think about why you use Ubuntu 15.04 for a server environment. It's almost out of date already because 15.10 is just around the corner.
I would rather stick to a LTS version of Ubuntu (currently 14.04).

I extracted the source of DPDK for you and found a script with which you seem to bind the interfaces.
```
/tools/pci_unbind.py
```
Within this script there are some examples how to use them:
```
Examples:
---------
    
To display current device status:
        %(argv0)s --status
        
To bind eth1 from the current driver and move to use igb_uio
        %(argv0)s --bind=igb_uio eth1
        
To unbind 0000:01:00.0 from using any driver
        %(argv0)s -u 0000:01:00.0
        
To bind 0000:02:00.0 and 0000:02:00.1 to the ixgbe kernel driver
        %(argv0)s -b ixgbe 02:00.0 02:00.1
```
So first thing I would try is unbind the interfaces you binded.
```
./tools/pci_unbind.py -u eth1
``` for eth1 and 
```
./tools/pci_unbind.py -u eth0
``` for eth0.
Reboot and see if they are back.

---

### Post by vnish11 on 2015-10-22
I love to unbind, if i can. 
Now in current state, eth0 and eth1 is not visible. Nor DPDK neither Kernel able to detect anything like eth0 and eth1

Just for sake i am posting output...
 ./dpdk_nic_bind.py --status

Network devices using DPDK-compatible driver
============================================
<none>

Network devices using kernel driver
===================================
0000:03:00.0 'NetXtreme II BCM5708 Gigabit Ethernet' if=eth2 drv=bnx2 unused=igb_uio *Active*
0000:05:00.0 'NetXtreme II BCM5708 Gigabit Ethernet' if=eth3 drv=bnx2 unused=igb_uio

Other network devices
=====================
<none>
----------------------------------------------

So, how can i unbind i NIC that is not shown as bind. Secondly if forcefully i tried to execute the command, here is what i got.
Unknown device: 0000:0b:00.0. Please specify device in "bus:slot.func" format

---

### Post by michi1983 on 2015-10-22
Please post the output of```
sudo lsmod
```

---

### Post by vnish11 on 2015-10-22
Michi... here is the output.

root@ubuntu-1:~# lsmod
Module                  Size  Used by
xt_CHECKSUM            16384  1
iptable_mangle         16384  1
ipt_MASQUERADE         16384  3
nf_nat_masquerade_ipv4    16384  1 ipt_MASQUERADE
iptable_nat            16384  1
nf_nat_ipv4            16384  1 iptable_nat
nf_nat                 28672  2 nf_nat_ipv4,nf_nat_masquerade_ipv4
nf_conntrack_ipv4      16384  2
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
xt_conntrack           16384  1
nf_conntrack          106496  5 nf_nat,nf_nat_ipv4,xt_conntrack,nf_nat_masquerade_ipv4,nf_conntrack_ipv4
ipt_REJECT             16384  2
nf_reject_ipv4         16384  1 ipt_REJECT
xt_tcpudp              16384  6
bridge                110592  0
stp                    16384  1 bridge
llc                    16384  2 stp,bridge
ebtable_filter         16384  0
ebtables               36864  1 ebtable_filter
ip6table_filter        16384  0
ip6_tables             28672  1 ip6table_filter
iptable_filter         16384  1
ip_tables              28672  3 iptable_filter,iptable_mangle,iptable_nat
x_tables               36864  11 ip6table_filter,xt_CHECKSUM,ip_tables,xt_tcpudp,ipt_MASQUERADE,xt_conntrack,iptable_filter,ebtables,ipt_REJECT,iptable_mangle,ip6_tables
ipmi_ssif              24576  0
amdkfd                 81920  1
amd_iommu_v2           20480  1 amdkfd
radeon               1556480  1
gpio_ich               16384  0
coretemp               16384  0
lpc_ich                24576  0
ttm                    98304  1 radeon
kvm                   483328  0
serio_raw              16384  0
drm_kms_helper        122880  1 radeon
drm                   344064  4 ttm,drm_kms_helper,radeon
i5000_edac             20480  0
hpilo                  20480  0
i2c_algo_bit           16384  1 radeon
edac_core              53248  2 i5000_edac
i5k_amb                16384  0
shpchp                 40960  0
ipmi_si                57344  0
8250_fintek            16384  0
ipmi_msghandler        49152  2 ipmi_ssif,ipmi_si
mac_hid                16384  0
autofs4                40960  2
hpsa                   81920  0
psmouse               118784  0
pata_acpi              16384  0
bnx2                   86016  0
cciss                 118784  3

---

### Post by vnish11 on 2015-10-22
In Addition to that i like to share two pics of BIOS with all of you.
1. Good-Mac
2. Bad-Mac

In Good Machine, i am able to see all 4 NIC interface but in Bad one i am able to see only two. My intention to share the image is to give as much information as i can to resolve the issue.

[ATTACH=CONFIG]265094[/ATTACH]


[ATTACH=CONFIG]265095[/ATTACH]

---

