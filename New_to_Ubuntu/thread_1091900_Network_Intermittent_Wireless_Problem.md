---
title: "Network Intermittent Wireless Problem"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by dunbrokin on 2009-03-09
I keep getting logged out from the wireless router on an intermittent basis. When I get logged out (despite the fact that I have given my profile permission to connect to the wireless system under Users and Groups) I have to reboot my machine to reconnect. This happens to me on a regular basis ( a couple of times a week), but especially happens if I am downloading a big document etc.

Here is the log....hopefully somebody can make sense of this and explain what the problem is.

Mar 10 11:44:55 PJKING NetworkManager: <info>  (eth1): supplicant connection state change: 0 -> 2 
Mar 10 11:44:56 PJKING NetworkManager: <info>  (eth1): supplicant connection state change: 2 -> 3 
Mar 10 11:44:56 PJKING NetworkManager: <info>  (eth1): supplicant connection state change: 3 -> 4 
Mar 10 11:44:56 PJKING NetworkManager: <info>  (eth1): supplicant connection state change: 4 -> 7 
Mar 10 11:44:59 PJKING dhclient: DHCPREQUEST of 10.1.1.4 on eth1 to 10.1.1.1 port 67 
Mar 10 11:45:28 PJKING last message repeated 2 times 
Mar 10 11:46:36 PJKING last message repeated 5 times 
Mar 10 11:46:49 PJKING dhclient: DHCPREQUEST of 10.1.1.4 on eth1 to 10.1.1.1 port 67 
Mar 10 11:46:55 PJKING NetworkManager: <info>  (eth1): supplicant connection state change: 7 -> 0 
Mar 10 11:46:55 PJKING NetworkManager: <info>  (eth1): supplicant connection state change: 0 -> 2 
Mar 10 11:46:56 PJKING NetworkManager: <info>  (eth1): supplicant connection state change: 2 -> 3 
Mar 10 11:46:56 PJKING NetworkManager: <info>  (eth1): supplicant connection state change: 3 -> 4 
Mar 10 11:46:56 PJKING NetworkManager: <info>  (eth1): supplicant connection state change: 4 -> 7 
Mar 10 11:47:08 PJKING dhclient: DHCPREQUEST of 10.1.1.4 on eth1 to 10.1.1.1 port 67 
Mar 10 11:47:37 PJKING last message repeated 2 times 
Mar 10 11:47:53 PJKING dhclient: DHCPREQUEST of 10.1.1.4 on eth1 to 10.1.1.1 port 67 
Mar 10 11:48:14 PJKING dhclient: DHCPREQUEST of 10.1.1.4 on eth1 to 255.255.255.255 port 67 
Mar 10 11:48:52 PJKING last message repeated 3 times 
Mar 10 11:48:55 PJKING NetworkManager: <info>  (eth1): supplicant connection state change: 7 -> 0 
Mar 10 11:48:55 PJKING NetworkManager: <info>  (eth1): supplicant connection state change: 0 -> 2 
Mar 10 11:48:56 PJKING NetworkManager: <info>  (eth1): supplicant connection state change: 2 -> 3 
Mar 10 11:48:56 PJKING NetworkManager: <info>  (eth1): supplicant connection state change: 3 -> 4 
Mar 10 11:48:56 PJKING NetworkManager: <info>  (eth1): supplicant connection state change: 4 -> 7 
Mar 10 11:49:01 PJKING dhclient: DHCPREQUEST of 10.1.1.4 on eth1 to 255.255.255.255 port 67 
Mar 10 11:49:22 PJKING dhclient: DHCPREQUEST of 10.1.1.4 on eth1 to 255.255.255.255 port 67 
Mar 10 11:49:55 PJKING last message repeated 2 times 
Mar 10 11:49:58 PJKING NetworkManager: <info>  (eth1): device state change: 8 -> 3 
Mar 10 11:49:58 PJKING NetworkManager: <info>  (eth1): deactivating device (reason: 0). 
Mar 10 11:49:59 PJKING NetworkManager: <info>  eth1: canceled DHCP transaction, dhcp client pid 6099 
Mar 10 11:49:59 PJKING NetworkManager: <WARN>  check_one_route(): (eth1) error -34 returned from rtnl_route_del(): Sucess  
Mar 10 11:49:59 PJKING avahi-daemon[4878]: Withdrawing address record for 10.1.1.4 on eth1. 
Mar 10 11:49:59 PJKING avahi-daemon[4878]: Leaving mDNS multicast group on interface eth1.IPv4 with address 10.1.1.4. 
Mar 10 11:49:59 PJKING avahi-daemon[4878]: Interface eth1.IPv4 no longer relevant for mDNS. 
Mar 10 11:49:59 PJKING NetworkManager: <info>  Activation (eth1) starting connection 'Auto DLINK' 
Mar 10 11:49:59 PJKING NetworkManager: <info>  (eth1): device state change: 3 -> 4 
Mar 10 11:49:59 PJKING NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Mar 10 11:49:59 PJKING NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Mar 10 11:49:59 PJKING NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Mar 10 11:49:59 PJKING NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Mar 10 11:49:59 PJKING NetworkManager: <info>  (eth1): supplicant connection state change: 7 -> 0 
Mar 10 11:49:59 PJKING NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Mar 10 11:49:59 PJKING NetworkManager: <info>  (eth1): device state change: 4 -> 5 
Mar 10 11:49:59 PJKING NetworkManager: <info>  Activation (eth1/wireless): access point 'Auto DLINK' has security, but secrets are required. 
Mar 10 11:49:59 PJKING NetworkManager: <info>  (eth1): device state change: 5 -> 6 
Mar 10 11:49:59 PJKING NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Mar 10 11:50:01 PJKING NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Mar 10 11:50:01 PJKING NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Mar 10 11:50:01 PJKING NetworkManager: <info>  (eth1): device state change: 6 -> 4 
Mar 10 11:50:01 PJKING NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Mar 10 11:50:01 PJKING NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Mar 10 11:50:01 PJKING NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Mar 10 11:50:01 PJKING NetworkManager: <info>  (eth1): device state change: 4 -> 5 
Mar 10 11:50:01 PJKING NetworkManager: <info>  Activation (eth1/wireless): connection 'Auto DLINK' has security, and secrets exist.  No new secrets needed. 
Mar 10 11:50:01 PJKING NetworkManager: <info>  Config: added 'ssid' value 'DLINK' 
Mar 10 11:50:01 PJKING NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Mar 10 11:50:01 PJKING NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE' 
Mar 10 11:50:01 PJKING NetworkManager: <info>  Config: added 'auth_alg' value 'OPEN' 
Mar 10 11:50:01 PJKING NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>' 
Mar 10 11:50:01 PJKING NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '0' 
Mar 10 11:50:01 PJKING NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Mar 10 11:50:01 PJKING NetworkManager: <info>  Config: set interface ap_scan to 1 
Mar 10 11:50:01 PJKING NetworkManager: <info>  (eth1): supplicant connection state change: 0 -> 2 
Mar 10 11:50:02 PJKING NetworkManager: <info>  (eth1): supplicant connection state change: 2 -> 3 
Mar 10 11:50:02 PJKING NetworkManager: <info>  (eth1): supplicant connection state change: 3 -> 4 
Mar 10 11:50:02 PJKING NetworkManager: <info>  (eth1): supplicant connection state change: 4 -> 7 
Mar 10 11:50:02 PJKING NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'DLINK'. 
Mar 10 11:50:02 PJKING NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Mar 10 11:50:02 PJKING NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Mar 10 11:50:02 PJKING NetworkManager: <info>  (eth1): device state change: 5 -> 7 
Mar 10 11:50:02 PJKING NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Mar 10 11:50:02 PJKING NetworkManager: <info>  dhclient started with pid 17786 
Mar 10 11:50:02 PJKING NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Mar 10 11:50:02 PJKING dhclient: Internet Systems Consortium DHCP Client V3.1.1 
Mar 10 11:50:02 PJKING dhclient: Copyright 2004-2008 Internet Systems Consortium. 
Mar 10 11:50:02 PJKING dhclient: All rights reserved. 
Mar 10 11:50:02 PJKING dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 
Mar 10 11:50:02 PJKING dhclient: 
Mar 10 11:50:02 PJKING NetworkManager: <info>  DHCP: device eth1 state changed normal exit -> preinit 
Mar 10 11:50:02 PJKING dhclient: Listening on LPF/eth1/00:12:f0:95:49:5b 
Mar 10 11:50:02 PJKING dhclient: Sending on   LPF/eth1/00:12:f0:95:49:5b 
Mar 10 11:50:02 PJKING dhclient: Sending on   Socket/fallback 
Mar 10 11:50:04 PJKING dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6 
Mar 10 11:50:11 PJKING dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7 
Mar 10 11:50:18 PJKING dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 18 
Mar 10 11:50:35 PJKING dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 18 
Mar 10 11:50:47 PJKING NetworkManager: <info>  Device 'eth1' DHCP transaction took too long (>45s), stopping it. 
Mar 10 11:50:47 PJKING NetworkManager: <info>  eth1: canceled DHCP transaction, dhcp client pid 17786 
Mar 10 11:50:47 PJKING NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Mar 10 11:50:47 PJKING NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) started... 
Mar 10 11:50:47 PJKING NetworkManager: <info>  Activation (eth1/wireless): could not get IP configuration for connection 'Auto DLINK'. 
Mar 10 11:50:47 PJKING NetworkManager: <info>  (eth1): device state change: 7 -> 6 
Mar 10 11:50:47 PJKING NetworkManager: <info>  Activation (eth1/wireless): asking for new secrets 
Mar 10 11:50:47 PJKING NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) complete. 
Mar 10 11:50:52 PJKING NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Mar 10 11:50:52 PJKING NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Mar 10 11:50:52 PJKING NetworkManager: <info>  (eth1): device state change: 6 -> 4 
Mar 10 11:50:52 PJKING NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Mar 10 11:50:52 PJKING NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Mar 10 11:50:52 PJKING NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Mar 10 11:50:52 PJKING NetworkManager: <info>  (eth1): device state change: 4 -> 5 
Mar 10 11:50:52 PJKING NetworkManager: <info>  Activation (eth1/wireless): connection 'Auto DLINK' has security, and secrets exist.  No new secrets needed. 
Mar 10 11:50:52 PJKING NetworkManager: <info>  Config: added 'ssid' value 'DLINK' 
Mar 10 11:50:52 PJKING NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Mar 10 11:50:52 PJKING NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE' 
Mar 10 11:50:52 PJKING NetworkManager: <info>  Config: added 'auth_alg' value 'OPEN' 
Mar 10 11:50:52 PJKING NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>' 
Mar 10 11:50:52 PJKING NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '0' 
Mar 10 11:50:52 PJKING NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Mar 10 11:50:52 PJKING NetworkManager: <info>  Config: set interface ap_scan to 1 
Mar 10 11:50:52 PJKING NetworkManager: <info>  (eth1): supplicant connection state change: 7 -> 0 
Mar 10 11:50:52 PJKING NetworkManager: <info>  (eth1): supplicant connection state change: 0 -> 2 
Mar 10 11:50:53 PJKING NetworkManager: <info>  (eth1): supplicant connection state change: 2 -> 3 
Mar 10 11:50:53 PJKING NetworkManager: <info>  (eth1): supplicant connection state change: 3 -> 4 
Mar 10 11:50:53 PJKING NetworkManager: <info>  (eth1): supplicant connection state change: 4 -> 7 
Mar 10 11:50:53 PJKING NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'DLINK'. 
Mar 10 11:50:53 PJKING NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Mar 10 11:50:53 PJKING NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Mar 10 11:50:53 PJKING NetworkManager: <info>  (eth1): device state change: 5 -> 7 
Mar 10 11:50:53 PJKING NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Mar 10 11:50:53 PJKING dhclient: Internet Systems Consortium DHCP Client V3.1.1 
Mar 10 11:50:53 PJKING dhclient: Copyright 2004-2008 Internet Systems Consortium. 
Mar 10 11:50:53 PJKING dhclient: All rights reserved. 
Mar 10 11:50:53 PJKING dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 
Mar 10 11:50:53 PJKING dhclient: 
Mar 10 11:50:53 PJKING NetworkManager: <info>  dhclient started with pid 17865 
Mar 10 11:50:53 PJKING NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Mar 10 11:50:53 PJKING NetworkManager: <info>  DHCP: device eth1 state changed normal exit -> preinit 
Mar 10 11:50:53 PJKING dhclient: Listening on LPF/eth1/00:12:f0:95:49:5b 
Mar 10 11:50:53 PJKING dhclient: Sending on   LPF/eth1/00:12:f0:95:49:5b 
Mar 10 11:50:53 PJKING dhclient: Sending on   Socket/fallback 
Mar 10 11:50:54 PJKING dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7 
Mar 10 11:50:59 PJKING NetworkManager: <info>  (eth1): supplicant connection state change: 7 -> 0 
Mar 10 11:50:59 PJKING NetworkManager: <info>  (eth1): supplicant connection state change: 0 -> 2 
Mar 10 11:51:00 PJKING NetworkManager: <info>  (eth1): supplicant connection state change: 2 -> 3 
Mar 10 11:51:00 PJKING NetworkManager: <info>  (eth1): supplicant connection state change: 3 -> 4 
Mar 10 11:51:00 PJKING NetworkManager: <info>  (eth1): supplicant connection state change: 4 -> 7 
Mar 10 11:51:02 PJKING dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10

---

### Post by Nxion on 2009-03-10
Is this on your laptop or desktop? Also can you post the output of these commands:

```
sudo lspci
```

and

```
sudo lshw -C network
```

---

### Post by dunbrokin on 2009-03-10
Laptop.

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300]
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
03:01.0 CardBus bridge: Texas Instruments PCI6515 Cardbus Controller
03:01.5 Communication controller: Texas Instruments PCI6515 SmartCard Controller
03:03.0 Network controller: Intel Corporation PRO/Wireless 2915ABG [Calexico2] Network Connection (rev 05)


 *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:12:3f:10:d2:75
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 firmware=5751-v3.29a latency=0 link=no module=tg3 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: PRO/Wireless 2915ABG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:95:49:5b
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) ip=10.1.1.5 latency=64 link=yes maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 6e:f3:77:58:a3:6a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

