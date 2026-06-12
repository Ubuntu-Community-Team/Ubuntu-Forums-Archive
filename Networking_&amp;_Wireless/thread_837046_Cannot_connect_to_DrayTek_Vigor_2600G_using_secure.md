---
title: "Cannot connect to DrayTek Vigor 2600G using secure wireless"
date: 2008-06-22
forum: Networking &amp; Wireless
---

### Post by philip_bretton on 2008-06-22
Hi

I am using an Asus W5F laptop with an Intel 3945ABG wireless network adpater. I have used it at various sites and have had no problems connecting to WEP and WPA encrypted wireless networks. 

I recently purchased a DrayTek Vigor 2600G wireless router. Using a wired connection I can connect successfully. If I disabled all wireless security then I can connect successfully to the router. With WEP or WPA enabled I can connect successfully from Windows but cannot connect from Ubuntu.

```
sudo modinfo iwl3945

filename:       /lib/modules/2.6.24-18-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl3945.ko
license:        GPL
author:         Copyright(c) 2003-2007 Intel Corporation
version:        1.2.0
description:    Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux
srcversion:     8E95C617988943846696F97
alias:          pci:v00008086d00004227sv*sd*bc*sc*i*
alias:          pci:v00008086d00004222sv*sd*bc*sc*i*
depends:        iwlwifi_mac80211
vermagic:       2.6.24-18-generic SMP mod_unload 586 
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           disable:manually disable the radio (default 0 [radio on]) (int)
parm:           hwcrypto:using hardware crypto engine (default 0 [software])
 (int)
parm:           debug:debug output mask (int)
parm:           disable_hw_scan:disable hardware scanning (default 0) (int)
parm:           queues_num:number of hw queues. (int)
parm:           qos_enable:enable all QoS functionality (int)

sudo lspci --vvnn

07:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4222] (rev 02)
	Subsystem: Intel Corporation Unknown device [8086:1001]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 221
	Region 0: Memory at fe7ff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [c8] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
		Address: 00000000fee0300c  Data: 4132
	Capabilities: [e0] Express Legacy Endpoint IRQ 0
		Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
		Device: Latency L0s <512ns, L1 unlimited
		Device: AtnBtn- AtnInd- PwrInd-
		Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
		Device: RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
		Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
		Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s L1, Port 0
		Link: Latency L0s <128ns, L1 <64us
		Link: ASPM Disabled RCB 64 bytes CommClk+ ExtSynch-
		Link: Speed 2.5Gb/s, Width x1
```

Below is the relevant section from the daemon.log file when I try to connect:
```
Jun 21 18:28:40 brett-laptop NetworkManager: <info>  Activation (eth1) started... 
Jun 21 18:28:40 brett-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Jun 21 18:28:40 brett-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Jun 21 18:28:40 brett-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Jun 21 18:28:40 brett-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Jun 21 18:28:40 brett-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Jun 21 18:28:40 brett-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'Deerwood' is encrypted, and a key exists.  No new key needed. 
Jun 21 18:28:42 brett-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant0^I' 
Jun 21 18:28:42 brett-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jun 21 18:28:42 brett-laptop NetworkManager: <info>  kernel_driver for non broadcast check: iwl3945 (has_scan_capa_ssid=0) 
Jun 21 18:28:42 brett-laptop NetworkManager: <info>  using has_buggy_apscan_2 fix for iwl3945 
Jun 21 18:28:42 brett-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Jun 21 18:28:42 brett-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jun 21 18:28:42 brett-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Jun 21 18:28:42 brett-laptop NetworkManager: <info>  SUP: response was '0' 
Jun 21 18:28:42 brett-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 44656572776f6f64' 
Jun 21 18:28:42 brett-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jun 21 18:28:42 brett-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 scan_ssid 1' 
Jun 21 18:28:42 brett-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jun 21 18:28:42 brett-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 proto WPA' 
Jun 21 18:28:42 brett-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jun 21 18:28:42 brett-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt WPA-PSK' 
Jun 21 18:28:42 brett-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jun 21 18:28:42 brett-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 psk <key>' 
Jun 21 18:28:42 brett-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jun 21 18:28:42 brett-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 pairwise TKIP' 
Jun 21 18:28:42 brett-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jun 21 18:28:42 brett-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 group TKIP' 
Jun 21 18:28:42 brett-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jun 21 18:28:42 brett-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Jun 21 18:28:42 brett-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jun 21 18:28:42 brett-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Jun 21 18:28:42 brett-laptop NetworkManager: <debug> [1214069322.296831] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:00:00:00:00:00 to 00:13:D3:00:1E:77 on wireless network 'Deerwood' 
Jun 21 18:28:42 brett-laptop NetworkManager: <debug> [1214069322.308932] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'Deerwood' 
Jun 21 18:28:42 brett-laptop NetworkManager: <debug> [1214069322.309189] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'Deerwood' 
Jun 21 18:28:42 brett-laptop NetworkManager: <debug> [1214069322.309367] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'Deerwood' 
Jun 21 18:28:42 brett-laptop NetworkManager: <debug> [1214069322.309541] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'Deerwood' 
Jun 21 18:28:42 brett-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Jun 21 18:28:45 brett-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Jun 21 18:28:52 brett-laptop NetworkManager: <info>  Supplicant state changed: 0 
Jun 21 18:29:04 brett-laptop NetworkManager: <WARN>  request_and_convert_scan_results(): card took too much time scanning.  Get a better one. 
Jun 21 18:29:10 brett-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Jun 21 18:29:12 brett-laptop NetworkManager: <info>  Activation (eth1/wireless): disconnected during association, asking for new key. 
Jun 21 18:29:12 brett-laptop NetworkManager: <info>  Activation (eth1) New wireless user key requested for network 'Deerwood'. 
Jun 21 18:29:35 brett-laptop NetworkManager: <WARN>  request_and_convert_scan_results(): card took too much time scanning.  Get a better one. 
Jun 21 18:29:38 brett-laptop NetworkManager: <info>  Activation (eth1) New wireless user key for network 'Deerwood' received. 
Jun 21 18:29:38 brett-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Jun 21 18:29:38 brett-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Jun 21 18:29:38 brett-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Jun 21 18:29:38 brett-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Jun 21 18:29:38 brett-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Jun 21 18:29:38 brett-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'Deerwood' is encrypted, and a key exists.  No new key needed. 
Jun 21 18:29:40 brett-laptop NetworkManager: <info>  retry to connect to global supplicant socket (try=1) 
Jun 21 18:29:40 brett-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant0^I' 
Jun 21 18:29:40 brett-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jun 21 18:29:40 brett-laptop NetworkManager: <info>  kernel_driver for non broadcast check: iwl3945 (has_scan_capa_ssid=0) 
Jun 21 18:29:40 brett-laptop NetworkManager: <info>  using has_buggy_apscan_2 fix for iwl3945 
Jun 21 18:29:40 brett-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Jun 21 18:29:40 brett-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jun 21 18:29:40 brett-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Jun 21 18:29:40 brett-laptop NetworkManager: <info>  SUP: response was '0' 
Jun 21 18:29:40 brett-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 44656572776f6f64' 
Jun 21 18:29:40 brett-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jun 21 18:29:40 brett-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 scan_ssid 1' 
Jun 21 18:29:40 brett-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jun 21 18:29:40 brett-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 proto WPA' 
Jun 21 18:29:40 brett-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jun 21 18:29:40 brett-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt WPA-PSK' 
Jun 21 18:29:40 brett-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jun 21 18:29:40 brett-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 psk <key>' 
Jun 21 18:29:40 brett-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jun 21 18:29:40 brett-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 pairwise TKIP' 
Jun 21 18:29:40 brett-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jun 21 18:29:40 brett-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 group TKIP' 
Jun 21 18:29:40 brett-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jun 21 18:29:40 brett-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Jun 21 18:29:40 brett-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jun 21 18:29:40 brett-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Jun 21 18:29:45 brett-laptop NetworkManager: <WARN>  request_and_convert_scan_results(): card took too much time scanning.  Get a better one. 
Jun 21 18:29:51 brett-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Jun 21 18:30:01 brett-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Jun 21 18:30:15 brett-laptop NetworkManager: <WARN>  request_and_convert_scan_results(): card took too much time scanning.  Get a better one. 

```

I have tried connecting through the GUI and using the command line with the same results:
```
brett@brett-laptop:~$ sudo ifconfig eth1 down
brett@brett-laptop:~$ sudo dhclient -r eth1
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth1/00:13:02:18:79:11
Sending on   LPF/eth1/00:13:02:18:79:11
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.0.1 port 67
brett@brett-laptop:~$ sudo ifconfig eth1 up
brett@brett-laptop:~$ sudo iwconfig eth1 essid "Deerwood"
brett@brett-laptop:~$ sudo iwconfig eth1 key s:012EE8322D7E7
brett@brett-laptop:~$ sudo iwconfig eth1 key open
brett@brett-laptop:~$ sudo iwconfig eth1 mod Managed
iwconfig: command "mod" is ambiguous
brett@brett-laptop:~$ sudo iwconfig eth1 mode Managed
brett@brett-laptop:~$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth1/00:13:02:18:79:11
Sending on   LPF/eth1/00:13:02:18:79:11
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
brett@brett-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

eth1      IEEE 802.11g  ESSID:"Deerwood"  Nickname:""
          Mode:Managed  Frequency:2.472 GHz  Access Point: 00:13:D3:00:1E:77   
          Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Link quality shows 0 and yet the GUI interface shows a near 100% signal strength.

---

### Post by chili555 on 2008-06-22
Does your card respond correctly to scan requests?```
sudo iwlist eth1 scan
```Does:```
dmesg | grep eth1
```tell us anything interesting? From your log:> request_and_convert_scan_results(): card took too much time scanning.  Get a better one.I will be fascinated to see the scan!

---

### Post by philip_bretton on 2008-06-22
Nothing really interesting from either unfortunately:

<code>
brett@brett-laptop:/usr/src/alsa/alsa-utils-1.0.16# sudo iwlist eth1 scan
eth1      No scan results

brett@brett-laptop:/usr/src/alsa/alsa-utils-1.0.16# dmesg | grep eth1
[   45.732909] udev: renamed network interface wlan0 to eth1
[   97.458089] ADDRCONF(NETDEV_UP): eth1: link is not ready
[11292.582994] udev: renamed network interface wlan0 to eth1
[11292.602337] ADDRCONF(NETDEV_UP): eth1: link is not ready
</code>

---

### Post by chili555 on 2008-06-22
Please see this: [https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/176602](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/176602)

I suggest:```
sudo apt-get install linux-backports-modules-hardy-generic
```It will upgrade your driver to version 1.2.25. Let us know.

---

### Post by philip_bretton on 2008-06-23
No, Unfortunately that does not work either. Its wierd because when I use the GUI to connect to the wireless network it prompts me for the WEP password and then I would expect the icon in the systray to show one green light as it negotiates and then the next green light to come on when connected. But it just sits with no green lights and the thingy going round and round.

Sorry about the delay in getting back to you but I am babysitting my niece and nephew for the week and things get a little hectic sometimes!

---

