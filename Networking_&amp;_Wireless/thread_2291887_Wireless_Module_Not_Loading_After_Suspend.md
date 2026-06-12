---
title: "Wireless Module Not Loading After Suspend"
date: 2015-08-23
forum: Networking &amp; Wireless
---

### Post by Gotit on 2015-08-23
Hi,
I've spent a few days searching this an other forums, but can't find a solution that seems to work for me, so giving it a post.

Wireless on my laptop running 12.04 is fine about 60% of the time.  However, about every 7th - 12th time I resume from suspend, it appears the wireless module doesn't load and I can't load it by hand either.

Here are some particulars: 

```
**uname -r**
3.2.0-88-generic-pae

**ifconfig**
eth1      Link encap:Ethernet  HWaddr 00:a0:d1:94:1d:a1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:181 errors:0 dropped:0 overruns:0 frame:0
          TX packets:339 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24311 (24.3 KB)  TX bytes:57174 (57.1 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7516 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7516 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:640763 (640.7 KB)  TX bytes:640763 (640.7 KB)


**iwconfig**
lo        no wireless extensions.

eth1      no wireless extensions.



**nmcli nm**
RUNNING         STATE           WIFI-HARDWARE   WIFI       WWAN-HARDWARE   WWAN      
running         connected       enabled         enabled    enabled         disabled  


**sudo lshw -C network**
  *-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 14
       serial: 00:a0:d1:94:1d:a1
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 duplex=full firmware=N/A latency=0 link=no multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:46 memory:f0000000-f0003fff ioport:2000(size=256)
  *-network UNCLAIMED
       description: Network controller
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:f1000000-f1000fff


**rfkill list all**
8: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

**lspci -nnk | grep -iA2 net**
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller [11ab:4353] (rev 14)
	Subsystem: Toshiba America Info Systems Device [1179:ff10]
	Kernel driver in use: sky2
--
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
	Subsystem: Intel Corporation Device [8086:1040]
	Kernel modules: iwl3945


**lsmod | grep iwl***
iwl_legacy             71334  0 
mac80211              436544  1 iwl_legacy
cfg80211              178877  2 iwl_legacy,mac80211


**nm-tool**
NetworkManager Tool

State: disconnected

- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             unavailable
  Default:           no
  HW Address:        00:A0:D1:94:1D:A1

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


**sudo iwlist wlan0 scanning**
wlan0     Interface doesn't support scanning.


```

When I tried to install the wireless module 
```
sudo modprobe iwl3945
```

Syslog shows:
```
Aug 23 13:28:19 i5-Toshiba kernel: [12493.157820] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
Aug 23 13:28:19 i5-Toshiba kernel: [12493.157825] iwl3945: Copyright(c) 2003-2011 Intel Corporation
Aug 23 13:28:19 i5-Toshiba kernel: [12493.157915] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Aug 23 13:28:19 i5-Toshiba kernel: [12493.157949] iwl3945 0000:03:00.0: setting latency timer to 64
Aug 23 13:28:19 i5-Toshiba kernel: [12493.160012] iwl3945 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Aug 23 13:28:19 i5-Toshiba kernel: [12493.184229] iwl3945 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Aug 23 13:28:19 i5-Toshiba kernel: [12493.206010] iwl3945 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Aug 23 13:28:19 i5-Toshiba kernel: [12493.227704] iwl3945 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Aug 23 13:28:19 i5-Toshiba kernel: [12493.249404] iwl3945 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Aug 23 13:28:19 i5-Toshiba kernel: [12493.271118] iwl3945 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Aug 23 13:28:19 i5-Toshiba kernel: [12493.288914] iwl3945 0000:03:00.0: bad EEPROM signature,EEPROM_GP=0x00000007
Aug 23 13:28:19 i5-Toshiba kernel: [12493.288920] iwl3945 0000:03:00.0: EEPROM not found, EEPROM_GP=0xffffffff
Aug 23 13:28:19 i5-Toshiba kernel: [12493.288959] iwl3945 0000:03:00.0: Unable to init EEPROM
Aug 23 13:28:19 i5-Toshiba kernel: [12493.289026] iwl3945 0000:03:00.0: PCI INT A disabled
Aug 23 13:28:19 i5-Toshiba kernel: [12493.289053] iwl3945: probe of 0000:03:00.0 failed with error -2
```

Any ideas on how to get the wireless module re-installed and running without a reboot?
Thanks!

---

