---
title: "Internet stops working automatically even if status says Ethernet is conected"
date: 2018-06-19
forum: Networking &amp; Wireless
---

### Post by nikhil12 on 2018-06-19
This has been happening for few hours. One of the Ubuntu servers is losing internet connectivity suddenly every ~15 minutes. The network manager shows that the cable is connected correctly. All the other systems on the same network are working correctly without any issues.

I tried a fix related to `avahai-deamon` as mentioned [here]("https://ubuntu-mate.community/t/stop-network-disconnecting-in-ubuntu/829") but that did not make any changes related to this.

Any help to debug this would be appreciated.

Here is some information related to the system

Output of [COLOR=#000000][FONT=&amp]lspci -nnk | grep -iA2 net[/FONT][/COLOR]

```

02:00.0 Ethernet controller [0200]: Intel Corporation 82574L Gigabit Network Connection [8086:10d3]
    DeviceName: NIC Port 1
    Subsystem: Hewlett-Packard Company NC112i 1-port Ethernet Server Adapter [103c:1785]
    Kernel driver in use: e1000e
    Kernel modules: e1000e

```

Output of [COLOR=#000000][FONT=&amp]lsmod[/FONT][/COLOR]

```

Module                  Size  Used by
joydev                 20480  0
binfmt_misc            20480  1
gpio_ich               16384  0
ipmi_ssif              24576  0
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
kvm_intel             172032  0
kvm                   548864  1 kvm_intel
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
aesni_intel           167936  0
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
cryptd                 20480  3 ghash_clmulni_intel,aesni_intel,ablk_helper
input_leds             16384  0
serio_raw              16384  0
hpilo                  20480  0
lpc_ich                24576  0
ie31200_edac           16384  0
shpchp                 36864  0
edac_core              53248  1 ie31200_edac
ipmi_si                57344  0
ipmi_msghandler        49152  2 ipmi_ssif,ipmi_si
mac_hid                16384  0
ip6t_REJECT            16384  1
nf_reject_ipv6         16384  1 ip6t_REJECT
nf_log_ipv6            16384  5
xt_hl                  16384  22
ip6t_rt                16384  3
nf_conntrack_ipv6      20480  8
nf_defrag_ipv6         36864  1 nf_conntrack_ipv6
ipt_REJECT             16384  1
nf_reject_ipv4         16384  1 ipt_REJECT
nf_log_ipv4            16384  5
nf_log_common          16384  2 nf_log_ipv4,nf_log_ipv6
xt_LOG                 16384  10
xt_limit               16384  13
xt_tcpudp              16384  50
xt_addrtype            16384  4
nf_conntrack_ipv4      20480  8
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
xt_conntrack           16384  16
ip6table_filter        16384  1
ip6_tables             28672  1 ip6table_filter
nf_conntrack_netbios_ns    16384  0
nf_conntrack_broadcast    16384  1 nf_conntrack_netbios_ns
nf_nat_ftp             16384  0
nf_nat                 28672  1 nf_nat_ftp
nf_conntrack_ftp       20480  1 nf_nat_ftp
nf_conntrack          106496  8 nf_nat_ftp,nf_conntrack_netbios_ns,nf_nat,xt_conntrack,nf_conntrack_broadcast,nf_conntrack_ftp,nf_conntrack_ipv4,nf_conntrack_ipv6
iptable_filter         16384  1
ip_tables              24576  1 iptable_filter
x_tables               36864  13 ip6table_filter,xt_hl,ip_tables,xt_tcpudp,xt_limit,xt_conntrack,xt_LOG,iptable_filter,ip6t_rt,ipt_REJECT,ip6_tables,xt_addrtype,ip6t_REJECT
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
hid_generic            16384  0
usbhid                 49152  0
hid                   122880  2 hid_generic,usbhid
e1000e                241664  0
psmouse               131072  0
ahci                   36864  3
libahci                32768  1 ahci
ptp                    20480  1 e1000e
pps_core               20480  1 ptp
fjes                   28672  0

```


Output of [COLOR=#000000][FONT=&amp]ifconfig[/FONT][/COLOR]

```

eth0      Link encap:Ethernet  HWaddr 9c:b6:54:0b:ab:e4
          inet addr:192.168.1.115  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::9eb6:54ff:fe0b:abe4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33039 errors:0 dropped:2 overruns:0 frame:0
          TX packets:43373 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:6035745 (6.0 MB)  TX bytes:27603279 (27.6 MB)
          Interrupt:16 Memory:fbfe0000-fc000000


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:7512 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7512 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1
          RX bytes:591594 (591.5 KB)  TX bytes:591594 (591.5 KB)

```

More hardware information. Outtput of [COLOR=#111111][FONT=Consolas]lspci[/FONT][/COLOR]

```

00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v2/Ivy Bridge DRAM Controller (rev 09)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b5)
00:1c.7 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 8 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation C204 Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family SATA AHCI Controller (rev 05)
01:00.0 System peripheral: Hewlett-Packard Company Integrated Lights-Out Standard Slave Instrumentation & System Support (rev 05)
01:00.1 VGA compatible controller: Matrox Electronics Systems Ltd. MGA G200EH
01:00.2 System peripheral: Hewlett-Packard Company Integrated Lights-Out Standard Management Processor Support and Messaging (rev 05)
01:00.4 USB controller: Hewlett-Packard Company Integrated Lights-Out Standard Virtual USB Controller (rev 02)
02:00.0 Ethernet controller: Intel Corporation 82574L Gigabit Network Connection

```

I have updated the intel driver e1000e to latest version sttill the problem exists.

---

