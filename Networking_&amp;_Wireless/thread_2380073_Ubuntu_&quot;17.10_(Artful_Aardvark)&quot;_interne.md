---
title: "Ubuntu &quot;17.10 (Artful Aardvark)&quot; internet dropping out possible drivr issue? please h"
date: 2017-12-12
forum: Networking &amp; Wireless
---

### Post by gogogadget1 on 2017-12-12
SO i've been running ubuntu now for a month or two and noticed i get a little box in the bottom right hand corner telling me periodically that my internet has dropped out, after a few seconds it is back on and i can do things like normal, could anybody please help me find the cause, any help would be awesome.
[COLOR=#111111][FONT=Ubuntu]Some commands and the output I receive from Ubuntu:
[/FONT][/COLOR]```

in:
lspci | grep -i eth
output:
andy@andy-Aspire-VN7-792G:~/Downloads$ lspci | grep -i eth
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)

```

```

in:
ifconfig -a
output:
enp3s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 30:65:ec:a5:74:ed  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 14452  bytes 3053429 (3.0 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 14452  bytes 3053429 (3.0 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlp2s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 10.x.1.xxx  netmask 255.255.255.0  broadcast 10.x.1.xxx
        inet6 fe80::1d4d:9079:8f14:4b99  prefixlen 64  scopeid 0x20<link>
        ether c8:ff:28:3c:97:6b  txqueuelen 1000  (Ethernet)
        RX packets 6522740  bytes 3749657753 (3.7 GB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2095460  bytes 206963755 (206.9 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


```

```

in:
sudo lshw -C network
[sudo] password for andy: 
output:
  *-network                 
       description: Wireless interface
       product: QCA6174 802.11ac Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: 32
       serial: c8:ff:28:3c:97:6b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath10k_pci driverversion=4.13.0-19-generic firmware=WLAN.RM.4.4-00022-QCARMSWPZ-2 ip=10.x.1.xxx latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:127 memory:64000000-641fffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: enp3s0
       version: 15
       serial: 30:65:ec:a5:74:ed
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168h-2_0.0.2 02/26/15 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:124 ioport:3000(size=256) memory:64204000-64204fff memory:64200000-64203fff

```

```

in:
sudo lshw -C CPU
output:
  *-cpu                     
       description: CPU
       product: Intel(R) Core(TM) i7-6700HQ CPU @ 2.60GHz
       vendor: Intel Corp.
       physical id: 4
       bus info: cpu@0
       version: Intel(R) Core(TM) i7-6700HQ CPU @ 2.60GHz
       serial: To Be Filled By O.E.M.
       slot: U3E1
       size: 1475MHz
       capacity: 4005MHz
       width: 64 bits
       clock: 100MHz
       capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb intel_pt tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 hle avx2 smep bmi2 erms invpcid rtm mpx rdseed adx smap clflushopt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp cpufreq
       configuration: cores=4 enabledcores=4 threads=8




```

```

in:
sudo lshw -C network | grep -i driver
output:

       configuration: broadcast=yes driver=ath10k_pci driverversion=4.13.0-19-generic firmware=WLAN.RM.4.4-00022-QCARMSWPZ-2 ip=10.x.1.xxx latency=0 link=yes multicast=yes wireless=IEEE 802.11
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168h-2_0.0.2 02/26/15 latency=0 link=no multicast=yes port=MII speed=10Mbit/s

``````

in:
free -h
output:
              total        used        free      shared  buff/cache   available
Mem:            15G        3.1G        9.5G        154M        2.9G         12G
Swap:           18G          0B         18G

```

```

in:
ls -al /usr/src
output:
total 40
drwxr-xr-x 10 root root 4096 Dec  9 06:17 .
drwxr-xr-x 13 root root 4096 Nov 16 16:12 ..
drwxr-xr-x  2 root root 4096 Nov 14 22:05 bbswitch-0.8
drwxr-xr-x 27 root root 4096 Nov 14 08:38 linux-headers-4.13.0-16
drwxr-xr-x  7 root root 4096 Nov 14 08:38 linux-headers-4.13.0-16-generic
drwxr-xr-x 27 root root 4096 Nov 22 06:34 linux-headers-4.13.0-17
drwxr-xr-x  7 root root 4096 Nov 22 06:34 linux-headers-4.13.0-17-generic
drwxr-xr-x 27 root root 4096 Dec  9 06:17 linux-headers-4.13.0-19
drwxr-xr-x  7 root root 4096 Dec  9 06:17 linux-headers-4.13.0-19-generic
drwxr-xr-x  8 root root 4096 Nov 14 22:04 nvidia-384-384.90

```

---

### Post by teafx on 2017-12-12
^^^ Everything above is worthless [to me] in this instance.

This doesn't happen with any other computer, phone, etc?

I would try a different LAN cable if you're using that.

Could be a quick wifi drop out if you're using that due to fluctuating signal strength, competing with neighbours, or hardware going bad. So try a cable instead and see if it still happens.

The network drivers/Ubuntu side of things really shouldn't be the actual cause here. The reason being is that it comes back online without doing anything =)

In theory it could be stemming from the router too and only to that computer.

I would test everything there on the physical network side of things before deciding its Ubuntu. You haven't stated that you have done so and so you should do so imo.

---

### Post by DuckHook on 2017-12-12
> **teafx said:**
> ^^^ Everything above is worthless [to me] in this instance…
The OP's included info was anything but "worthless".

@gogogadget1

Firstly, welcome to the forums. Your initial post complete with system info is a model of how one should ask for help. If more forum members had the presence of mind to include as much info as you did, they would get their problems solved a lot more effectively.

I am no WIFI guru, but I'm sure one will be along to help at some point. In the meantime, I have moved your thread to the Networking and Wireless Forum which is more appropriate to your problem.

---

### Post by DuckHook on 2017-12-12
> **gogogadget1 said:**
> …i get a little box in the bottom right hand corner telling me periodically that my internet has dropped out, after a few seconds it is back on and i can do things like normal, could anybody please help me find the cause, any help would be awesome…
Since you've obviously a good familiarity with the command line, the next time you encounter such a drop, immediately afterwards, please open a terminal and post the results of:```
dmesg | tail -n 30
```

---

