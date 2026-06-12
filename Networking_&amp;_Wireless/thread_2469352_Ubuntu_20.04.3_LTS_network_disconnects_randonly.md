---
title: "Ubuntu 20.04.3 LTS network disconnects randonly"
date: 2021-11-26
forum: Networking &amp; Wireless
---

### Post by re8el on 2021-11-26
Hi,


I'm using Ubuntu full update, and from time to time, my network just gets disconnected and reconnected automagicly. Every 10min or 5min or 2min, or even stays ok for 30min and gets back to it randomly.


It happens with ethernet cable to the laptop or to the Dock Station also with wifi, the beaviaviour it's all the same.


OS: Ubuntu 20.04.3 LTS x64


My hardware:


Laptop - HP Zbook Power G7
i9-10885H
64 GB DDR4-3200
Intel UHD Graphics && NVIDIA Quadro T1000 with Max-Q Design (4 GB GDDR6 dedicated)
2x 1 TB PCIe NVMe M.2 SSD
Intel Wi-Fi 6 AX201 (2x2) and Bluetooth 5 combo, vPro
Intel I219-LM GbE, vPro
[https://support.hp.com/lt-en/document/c06931915](https://support.hp.com/lt-en/document/c06931915)


DockStatio - HP Thunderbolt Dock 230W G2 w/ Combo Cable
Front: 1 USB-C™ port with data and power out (15W); 1 USB-C™ cable to connect to host system (0.7 meter cable length); Side: 1 powered USB 3.0 port; 1 combo Audio Jack; 1 Kensington lock slot; Back: 1 Thunderbolt™ port; 1 USB-C™ DisplayPort™ data and power out (15W) port; 2 DisplayPort™ ports; 1 VGA port; 2 USB 3.0 ports; 1 RJ45 port; 1 AC Adapter connector
[https://www.hp.com/us-en/shop/pdp/hp-thunderbolt-dock-g2-with-combo-cable](https://www.hp.com/us-en/shop/pdp/hp-thunderbolt-dock-g2-with-combo-cable)


Can some please help troubleshoot this prob, just trow the commands need to get the info and i will post them.


Thks in advance.


r

---

### Post by re8el on 2021-11-26
Hi,

Some info...

sudo lshw -C network 
  *-network:0 DISABLED      
       description: Wireless interface
       product: Wi-Fi 6 AX201
       vendor: Intel Corporation
       physical id: 14.3
       bus info: pci@0000:00:14.3
       logical name: wlp0s20f3
       version: 00
       serial: xxxxxxxxx
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=5.11.0-40-generic firmware=59.601f3a66.0 QuZ-a0-hr-b0-59.u latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:16 memory:e9230000-e9233fff
  *-network:1
       description: Ethernet interface
       product: Ethernet Connection (10) I219-LM
       vendor: Intel Corporation
       physical id: 1f.6
       bus info: pci@0000:00:1f.6
       logical name: enp0s31f6
       version: 00
       serial: xxxxxxxxxxx
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=5.11.0-40-generic firmware=0.6-4 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:150 memory:e9200000-e921ffff
  *-network
       description: Ethernet interface
       physical id: 2
       bus info: usb@4:1.3.3
       logical name: enx50814088859e
       serial: xxxxxxxxx
       size: 1Gbit/s
       capacity: 1Gbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8152 driverversion=v1.11.11 duplex=full firmware=rtl8153a-3 v2 02/07/20 ip=xxxxxxxx link=yes multicast=yes port=MII speed=1Gbit/s






lspci | grep -i eth                                                                                                                                                     
00:1f.6 Ethernet controller: Intel Corporation Ethernet Connection (10) I219-LM






ifconfig                                                                                                                                                               
enp0s31f6: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether xxxxxxxxxxxx  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 16  memory 0xe9200000-e9220000  


enx50814088859e: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet xxxxxxxxx  netmask 255.255.255.0  broadcast 172.16.252.255
        inet6 fe80::5281:40ff:fe88:859e  prefixlen 64  scopeid 0x20<link>
        ether xxxxxx  txqueuelen 1000  (Ethernet)
        RX packets 20182956  bytes 27181128718 (27.1 GB)
        RX errors 0  dropped 37829  overruns 0  frame 0
        TX packets 5241372  bytes 1435653385 (1.4 GB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 10050  bytes 1026920 (1.0 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 10050  bytes 1026920 (1.0 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


vmnet1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet xxxxxxxxxx netmask 255.255.255.0  broadcast 172.16.78.255
        inet6 fe80::250:56ff:fec0:1  prefixlen 64  scopeid 0x20<link>
        ether 00:50:56:c0:00:01  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1928  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


vmnet8: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet xxxxxxxxxxx  netmask 255.255.255.0  broadcast 172.16.217.255
        inet6 fe80::250:56ff:fec0:8  prefixlen 64  scopeid 0x20<link>
        ether 00:50:56:c0:00:08  txqueuelen 1000  (Ethernet)
        RX packets 3582  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1928  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0




sudo lshw -C CPU                                                                                                                                                       
  *-cpu                     
       description: CPU
       product: Intel(R) Core(TM) i9-10885H CPU @ 2.40GHz
       vendor: Intel Corp.
       physical id: 15
       bus info: cpu@0
       version: Intel(R) Core(TM) i9-10885H CPU @ 2.40GHz
       serial: To Be Filled By O.E.M.
       slot: U3E1
       size: 3031MHz
       capacity: 5300MHz
       width: 64 bits
       clock: 100MHz
       capabilities: lm fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp x86-64 constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single ssbd ibrs ibpb stibp ibrs_enhanced tpr_shadow vnmi flexpriority ept vpid ept_ad fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp pku ospke md_clear flush_l1d arch_capabilities cpufreq
       configuration: cores=8 enabledcores=8 threads=16


sudo lshw -C network | grep -i driver
configuration: broadcast=yes driver=iwlwifi driverversion=5.11.0-40-generic firmware=59.601f3a66.0 QuZ-a0-hr-b0-59.u latency=0 link=no multicast=yes wireless=IEEE 802.11
configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=5.11.0-40-generic firmware=0.6-4 latency=0 link=no multicast=yes port=twisted pair
configuration: autonegotiation=on broadcast=yes driver=r8152 driverversion=v1.11.11 duplex=full firmware=rtl8153a-3 v2 02/07/20 ip=xxxxxxxxxx link=yes multicast=yes port=MII speed=1Gbit/s




free -h                                                                                                                                                                
              total        used        free      shared  buff/cache   available
Mem:           62Gi       6,8Gi       5,2Gi        12Gi        50Gi        42Gi
Swap:          46Gi       1,0Mi        46Gi




swapon -s                                                                                                                                                              
Filename                Type        Size    Used    Priority
/dev/nvme1n1p2                             partition    48828412    1280    -2






dkms status                                                                                                                                                            
nvidia, 495.44, 5.11.0-38-generic, x86_64: installed
nvidia, 495.44, 5.11.0-40-generic, x86_64: installed
veeamsnap, 5.0.1.4493, 5.11.0-38-generic, x86_64: installed
veeamsnap, 5.0.1.4493, 5.11.0-40-generic, x86_64: installed

uname -a                                                                                                                                                               
Linux 5.11.0-40-generic #44~20.04.2-Ubuntu SMP Tue Oct 26 18:07:44 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux


change

Any ideas?

tks

---

