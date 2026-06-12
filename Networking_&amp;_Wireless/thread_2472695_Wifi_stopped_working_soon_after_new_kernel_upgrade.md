---
title: "Wifi stopped working soon after new kernel upgrade"
date: 2022-03-09
forum: Networking &amp; Wireless
---

### Post by RegUB on 2022-03-09
This morning I was running Kernel 5.4.0-100-generic on my laptop (Ubuntu 20.04 on a Lenovo Thinkbook 15-IIL). Software updater informed that 5.4.0-104-generic was available, so I installed that, but did not restart the system. After working OK for a while, the system suddenly froze completely, so I had to power off manually and restart, upon which Ubuntu does not provide any option to connect to WiFi. There is no wireless icon in the top right hand corner, and in Network Settings there is no mention of a wireless connection. I've tried using both kernels (5.4.0-100-generic & 5.4.0-104-generic). It is not a hardware problem, because if I boot the laptop into Windows it connects to WiFi OK.

I don't know whether it is just coincidence that this occurred not long after the software upgrade but it seems a bit suspicious. I am wondering if the device files have somehow been corrupted but don't know what to look for.

Any help appreciated.

---

### Post by slickymaster on 2022-03-09
Thread moved to **Networking & Wireless** for a better fit

---

### Post by RegUB on 2022-03-09
Have now found that the wireless adapter is UNCLAIMED. The ethernet adapter is OK. Below is the output from various commands that I have found on other threads on this subject. Can anyone advise?
```
reg:~$ sudo lshw -C network
  *-network UNCLAIMED       
       description: Network controller
       product: Killer Wi-Fi 6 AX1650i 160MHz Wireless Network Adapter (201NGW)
       vendor: Intel Corporation
       physical id: 14.3
       bus info: pci@0000:00:14.3
       version: 30
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
       resources: memory:81430000-81433fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: enp1s0
       version: 15
       serial: b4:a9:fc:a6:29:2b
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 duplex=full firmware=rtl8168h-2_0.0.2 02/26/15 ip=192.168.1.180 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:16 ioport:2000(size=256) memory:81304000-81304fff memory:81300000-81303fff

reg:~$ dpkg -l | grep linux-modules-extra
ii  linux-modules-extra-5.4.0-100-generic      5.4.0-100.113                               amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.4.0-104-generic      5.4.0-104.118                               amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP

reg:~$ sudo modprobe -n -v iwlwifi
insmod /lib/modules/5.4.0-104-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/5.4.0-104-generic/kernel/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko 

reg:~$ uname -r
5.4.0-104-generic


```

---

### Post by jeremy31 on 2022-03-09
Results for ```
sudo dmesg | grep iwl
```

---

### Post by RegUB on 2022-03-10
> **jeremy31 said:**
> Results for ```
sudo dmesg | grep iwl
```

```
reg:~$ sudo dmesg | grep iwl
[    9.132760] iwlwifi 0000:00:14.3: enabling device (0000 -> 0002)
[    9.142104] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-Qu-c0-hr-b0-50.ucode failed with error -2
[    9.143167] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-Qu-c0-hr-b0-49.ucode failed with error -2
[    9.146366] iwlwifi 0000:00:14.3: TLV_FW_FSEQ_VERSION: FSEQ Version: 43.2.23.17
[    9.146370] iwlwifi 0000:00:14.3: Found debug destination: EXTERNAL_DRAM
[    9.146371] iwlwifi 0000:00:14.3: Found debug configuration: 0
[    9.146739] iwlwifi 0000:00:14.3: loaded firmware version 48.4fa0041f.0 op_mode iwlmvm
[    9.193910] iwlwifi 0000:00:14.3: Detected Intel(R) Wi-Fi 6 AX201 160MHz, REV=0x338
[    9.202647] iwlwifi 0000:00:14.3: Applying debug destination EXTERNAL_DRAM
[    9.203691] iwlwifi 0000:00:14.3: Allocated 0x00400000 bytes for firmware monitor.
[    9.354213] iwlwifi 0000:00:14.3: base HW address: 3c:58:c2:b9:0e:e2
[    9.420910] iwlwifi 0000:00:14.3 wlp0s20f3: renamed from wlan0
[   10.717631] iwlwifi 0000:00:14.3: Applying debug destination EXTERNAL_DRAM
[   10.863370] iwlwifi 0000:00:14.3: FW already configured (0) - re-configuring
[   10.867501] iwlwifi 0000:00:14.3: BIOS contains WGDS but no WRDS
```

---

### Post by RegUB on 2022-03-10
Of the two firmware load errors shown below, /lib/firmware/iwlwifi-QuZ-a0-hr-b0-50.ucode exists on the system, but iwlwifi-QuZ-a0-hr-b0-49.ucode does not. Is this what is causing the problem?

> **RegUB said:**
> ```
reg:~$ sudo dmesg | grep iwl
[    9.132760] iwlwifi 0000:00:14.3: enabling device (0000 -> 0002)
[    9.142104] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-Qu-c0-hr-b0-50.ucode failed with error -2
[    9.143167] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-Qu-c0-hr-b0-49.ucode failed with error -2
[    9.146366] iwlwifi 0000:00:14.3: TLV_FW_FSEQ_VERSION: FSEQ Version: 43.2.23.17
[    9.146370] iwlwifi 0000:00:14.3: Found debug destination: EXTERNAL_DRAM
[    9.146371] iwlwifi 0000:00:14.3: Found debug configuration: 0
[    9.146739] iwlwifi 0000:00:14.3: loaded firmware version 48.4fa0041f.0 op_mode iwlmvm
[    9.193910] iwlwifi 0000:00:14.3: Detected Intel(R) Wi-Fi 6 AX201 160MHz, REV=0x338
[    9.202647] iwlwifi 0000:00:14.3: Applying debug destination EXTERNAL_DRAM
[    9.203691] iwlwifi 0000:00:14.3: Allocated 0x00400000 bytes for firmware monitor.
[    9.354213] iwlwifi 0000:00:14.3: base HW address: 3c:58:c2:b9:0e:e2
[    9.420910] iwlwifi 0000:00:14.3 wlp0s20f3: renamed from wlan0
[   10.717631] iwlwifi 0000:00:14.3: Applying debug destination EXTERNAL_DRAM
[   10.863370] iwlwifi 0000:00:14.3: FW already configured (0) - re-configuring
[   10.867501] iwlwifi 0000:00:14.3: BIOS contains WGDS but no WRDS
```

---

### Post by RegUB on 2022-03-19
This problem cured itself without me having to do anything. I noticed that the lshw command no longer showed the adapter as unclaimed, so I removed the ethernet plug and the laptop immediately connected to the Wifi. No further updates had been installed. Have left it a few days to check that it's still OK, and no further problems. A mystery!

---

