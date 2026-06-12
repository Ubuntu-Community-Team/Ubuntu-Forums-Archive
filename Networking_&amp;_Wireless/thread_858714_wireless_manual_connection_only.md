---
title: "wireless manual connection only"
date: 2008-07-13
forum: Networking &amp; Wireless
---

### Post by karlatsaic on 2008-07-13
I shouldn't complain too much as my wireless is working just fine under Hardy 8.04 on my old Compaq Presario 2100. However, if I set "Roaming enabled" for my connection, it evidently cannot WEP authenticate (evidence in /var/log/syslog). It does work just fine under Manual Configuration as I write this. Before I get too detailed, I was just wondering if this makes sense to anyone with more experience. I am using network-manager (gnome nm-applet) (please don't suggest wicd as I have a VPN requirement which also works beautifully). I also had to install linux-backports-modules-hardy to get my current setup to work at all. Also, under the nm-applet, it shows TWO wireless connnections, wlan0 and wifi0 (note that when working manually, only wlan0 is manually configured with wifi0 set with "roaming enabled") . wifi0 represents the physical connection, but I reference the logical wlan0 everywhere for doing things manually. I'm wondering if I can get that wifi0 to disappear from the nm-applet that may do the trick but I do not know how to do that. I am also using a Linksys WRT160N router, with WEP for now. I also can connect with roaming enabled on my 64-bit work laptop - Dell XPS M1330 with Hardy 8.04 also, using iwl3945 driver for Intel Pro 3945ABG so I think my router setup is just fine. [EDIT: also on my work laptop, only ONE connection shows in the nm-applet, wlan0, while the physical connection, wmaster0, only shows up under ifconfig, but NOT in Network Settings, as I would think is correct].

output of lshw - C network
```

  *-network:0             
       description: Wireless interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: wifi0
       version: 01
       serial: 00:02:8a:7a:11:fa
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list logical wireless ethernet physical
       configuration: broadcast=yes driver=hostap firmware=1.4.9 ip=192.168.1.102 latency=64 module=hostap_pci multicast=yes wireless=IEEE 802.11b
  *-network:1
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 00
       serial: 00:0b:cd:34:d3:67
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=natsemi driverversion=2.1 latency=90 maxlatency=52 mingnt=11 module=natsemi multicast=yes

```Output of ifconfig while my manual configuration is working:
```
eth0      Link encap:Ethernet  HWaddr 00:0b:cd:34:d3:67  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0x6000 

eth0:avahi Link encap:Ethernet  HWaddr 00:0b:cd:34:d3:67  
          inet addr:169.254.7.145  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:11 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1838 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1838 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:92204 (90.0 KB)  TX bytes:92204 (90.0 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-02-8A-7A-11-FA-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10523 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2977 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4685824 (4.4 MB)  TX bytes:964444 (941.8 KB)
          Interrupt:10 

wlan0     Link encap:Ethernet  HWaddr 00:02:8a:7a:11:fa  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::202:8aff:fe7a:11fa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10523 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2977 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4496410 (4.2 MB)  TX bytes:964444 (941.8 KB)
          Interrupt:10 

```Thanks for any help - not too desperate as things work nicely. Just want roaming someday for those rare times when I have this old laptop out of my house.

---

### Post by karlatsaic on 2008-07-13
**Details**: If I switch to "Roaming enabled" while the manually configured connection is alive, my wlan0 connection works for about 30-60 seconds, then it is lost, and I get the dialogue to re-enter my WEP key. It never connects again. For the patient, my /var/log/syslog has these entries during the transition from manual to roaming...
```

karl@hplaptop:~$ sudo tail -200 /var/log/syslog
[sudo] password for karl: 
Jul 13 18:34:30 hplaptop kernel: [12152.688395] wlan0: hfa384x_set_rid: CMDCODE_ACCESS_WRITE failed (res=127, rid=fc04, len=34)
Jul 13 18:34:30 hplaptop NetworkManager: <info>  /etc/network/interface changed: rebuilding the device list. 
Jul 13 18:34:30 hplaptop NetworkManager: <info>  Recreating the device list. 
Jul 13 18:34:30 hplaptop kernel: [12152.873453] wifi0: hfa384x_setup_bap - offset error (0,0x041a5,0); reg=0x4000
Jul 13 18:34:30 hplaptop kernel: [12152.873472] wifi0: prism2_tx_80211 - to BAP0 failed
Jul 13 18:34:30 hplaptop NetworkManager: <info>  wlan0: Device is fully-supported using driver 'hostap_pci'. 
Jul 13 18:34:30 hplaptop kernel: [12152.873711] wifi0: scheduled card reset
Jul 13 18:34:30 hplaptop kernel: [12152.873717] hostap_pci: wifi0: resetting card
Jul 13 18:34:30 hplaptop kernel: [12152.873723] wifi0: Original COR value: 0x0
Jul 13 18:34:30 hplaptop kernel: [12152.879137] wlan0: hfa384x_cmd_issue: cmd reg was busy for 758 usec
Jul 13 18:34:30 hplaptop kernel: [12152.879883] prism2_hw_init: initialized in 0 ms
Jul 13 18:34:30 hplaptop kernel: [12152.879893] prism2_enable_aux_port: was not disabled!?
Jul 13 18:34:30 hplaptop kernel: [12152.880471] wifi0: CMD=0x000a => res=0x7f
Jul 13 18:34:30 hplaptop kernel: [12152.880473] wifi0: cannot allocate fid, len=2364
Jul 13 18:34:30 hplaptop kernel: [12152.880511] wifi0: CMD=0x000a => res=0x7f
Jul 13 18:34:30 hplaptop kernel: [12152.880514] wifi0: cannot allocate fid, len=1600
Jul 13 18:34:30 hplaptop kernel: [12152.880516] hostap_pci: Initialization failed
Jul 13 18:34:30 hplaptop kernel: [12152.977321] wifi0: prism2_tx_80211: hw not ready - skipping
Jul 13 18:34:31 hplaptop kernel: [41028.169044] wifi0: prism2_tx_80211: hw not ready - skipping
Jul 13 18:34:32 hplaptop avahi-daemon[4865]: Registering new address record for fe80::202:8aff:fe7a:11fa on wlan0.*.
Jul 13 18:34:32 hplaptop kernel: [12153.856585] wifi0: prism2_tx_80211: hw not ready - skipping
Jul 13 18:34:32 hplaptop NetworkManager: <info>  wlan0: driver supports SSID scans (scan_capa 0x01). 
Jul 13 18:34:32 hplaptop kernel: [12153.964435] wlan0: hfa384x_cmd: entry still in list? (entry=e02d9cc0, type=0, res=0)
Jul 13 18:34:32 hplaptop kernel: [12153.964453] wlan0: hfa384x_cmd: command was not completed (res=0, entry=e02d9cc0, type=0, cmd=0x0021, param0=0xfdc6, EVSTAT=8000 INTEN=0000)
Jul 13 18:34:32 hplaptop kernel: [12153.964459] wlan0: hfa384x_get_rid: CMDCODE_ACCESS failed (res=-110, rid=fdc6, len=12)
Jul 13 18:34:32 hplaptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Jul 13 18:34:32 hplaptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Jul 13 18:34:32 hplaptop NetworkManager: <info>  Now managing wireless (802.11) device 'wlan0'. 
Jul 13 18:34:32 hplaptop NetworkManager: <info>  Deactivating device wlan0. 
Jul 13 18:34:32 hplaptop avahi-daemon[4865]: Withdrawing address record for fe80::202:8aff:fe7a:11fa on wlan0.
Jul 13 18:34:34 hplaptop kernel: [41032.912726] wlan0: hfa384x_cmd: entry still in list? (entry=e02d9280, type=0, res=0)
Jul 13 18:34:34 hplaptop kernel: [41032.912758] wlan0: hfa384x_cmd: command was not completed (res=0, entry=e02d9280, type=0, cmd=0x0121, param0=0xfc02, EVSTAT=8010 INTEN=0000)
Jul 13 18:34:34 hplaptop kernel: [41032.912770] wlan0: interrupt delivery does not seem to work
Jul 13 18:34:34 hplaptop kernel: [41032.912782] wlan0: hfa384x_set_rid: CMDCODE_ACCESS_WRITE failed (res=-110, rid=fc02, len=34)
Jul 13 18:34:34 hplaptop kernel: [41032.912794] hostap_pci: wlan0: resetting card
Jul 13 18:34:34 hplaptop kernel: [41032.912807] wifi0: Original COR value: 0xa
Jul 13 18:34:34 hplaptop kernel: [12154.838726] prism2_hw_init: initialized in 200 ms
Jul 13 18:34:34 hplaptop NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Invalid argument 
Jul 13 18:34:34 hplaptop NetworkManager: <info>  Device list recreated successfully. 
Jul 13 18:34:34 hplaptop NetworkManager: <info>  Going to sleep. 
Jul 13 18:34:34 hplaptop kernel: [12154.926249] wifi0: TXEXC - status=0x0004 ([Discon]) tx_control=000c
Jul 13 18:34:34 hplaptop kernel: [12154.926296]    retry_count=0 tx_rate=0 fc=0x00c0 (Mgmt::12)
Jul 13 18:34:34 hplaptop kernel: [12154.926302]    A1=00:21:29:63:78:1c A2=00:02:8a:7a:11:fa A3=00:21:29:63:78:1c A4=00:00:00:00:00:00
Jul 13 18:34:35 hplaptop NetworkManager: <info>  Waking up from sleep. 
Jul 13 18:34:35 hplaptop NetworkManager: <info>  Deactivating device wlan0. 
Jul 13 18:34:35 hplaptop kernel: [12155.069907] wifi0: TXEXC - status=0x0004 ([Discon]) tx_control=000c
Jul 13 18:34:35 hplaptop kernel: [12155.069920]    retry_count=0 tx_rate=0 fc=0x0108 (Data::0 ToDS)
Jul 13 18:34:35 hplaptop kernel: [12155.069926]    A1=00:21:29:63:78:1c A2=00:02:8a:7a:11:fa A3=33:33:00:00:00:16 A4=00:00:00:00:00:00
Jul 13 18:34:35 hplaptop NetworkManager: <info>  wlan0: Device is fully-supported using driver 'hostap_pci'. 
Jul 13 18:34:35 hplaptop NetworkManager: <info>  wlan0: driver supports SSID scans (scan_capa 0x01). 
Jul 13 18:34:35 hplaptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Jul 13 18:34:35 hplaptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Jul 13 18:34:35 hplaptop NetworkManager: <info>  Now managing wireless (802.11) device 'wlan0'. 
Jul 13 18:34:35 hplaptop NetworkManager: <info>  Deactivating device wlan0. 
Jul 13 18:34:35 hplaptop kernel: [12155.114131] wifi0: LinkStatus=2 (Disconnected)
Jul 13 18:34:35 hplaptop kernel: [12155.114604] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
Jul 13 18:34:35 hplaptop kernel: [12155.566985] wifi0: LinkStatus=1 (Connected)
Jul 13 18:34:35 hplaptop kernel: [12155.567460] wifi0: LinkStatus: BSSID=00:21:29:63:78:1c
Jul 13 18:34:35 hplaptop kernel: [12155.568875] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jul 13 18:34:37 hplaptop avahi-daemon[4865]: Registering new address record for fe80::202:8aff:fe7a:11fa on wlan0.*.
Jul 13 18:34:45 hplaptop NetworkManager: <info>  SWITCH: no current connection, found better connection 'wlan0'. 
Jul 13 18:34:45 hplaptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
Jul 13 18:34:45 hplaptop NetworkManager: <info>  Will activate connection 'wlan0/SanPat'. 
Jul 13 18:34:45 hplaptop NetworkManager: <info>  Device wlan0 activation scheduled... 
Jul 13 18:34:45 hplaptop NetworkManager: <info>  Activation (wlan0) started... 
Jul 13 18:34:45 hplaptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Jul 13 18:34:45 hplaptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Jul 13 18:34:45 hplaptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Jul 13 18:34:45 hplaptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Jul 13 18:34:45 hplaptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Jul 13 18:34:45 hplaptop NetworkManager: <info>  Activation (wlan0/wireless): access point 'SanPat' is encrypted, but NO valid key exists.  New key needed. 
Jul 13 18:34:45 hplaptop NetworkManager: <info>  Activation (wlan0) New wireless user key requested for network 'SanPat'. 
Jul 13 18:34:45 hplaptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Jul 13 18:34:45 hplaptop NetworkManager: <info>  Activation (wlan0) New wireless user key for network 'SanPat' received. 
Jul 13 18:34:45 hplaptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Jul 13 18:34:45 hplaptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Jul 13 18:34:45 hplaptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Jul 13 18:34:45 hplaptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Jul 13 18:34:45 hplaptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Jul 13 18:34:45 hplaptop NetworkManager: <info>  Activation (wlan0/wireless): access point 'SanPat' is encrypted, and a key exists.  No new key needed. 
Jul 13 18:34:46 hplaptop kernel: [41052.218745] wlan0: no IPv6 routers present
Jul 13 18:34:47 hplaptop NetworkManager: <info>  retry to connect to global supplicant socket (try=1) 
Jul 13 18:34:47 hplaptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan0^I^Iwext^I/var/run/wpa_supplicant0^I' 
Jul 13 18:34:47 hplaptop NetworkManager: <info>  SUP: response was 'OK' 
Jul 13 18:34:47 hplaptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Jul 13 18:34:47 hplaptop NetworkManager: <info>  SUP: response was 'OK' 
Jul 13 18:34:47 hplaptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Jul 13 18:34:47 hplaptop NetworkManager: <info>  SUP: response was '0' 
Jul 13 18:34:47 hplaptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 53616e506174' 
Jul 13 18:34:47 hplaptop NetworkManager: <info>  SUP: response was 'OK' 
Jul 13 18:34:47 hplaptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Jul 13 18:34:47 hplaptop NetworkManager: <info>  SUP: response was 'OK' 
Jul 13 18:34:47 hplaptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_key0 <key>' 
Jul 13 18:34:47 hplaptop NetworkManager: <info>  SUP: response was 'OK' 
Jul 13 18:34:47 hplaptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0' 
Jul 13 18:34:47 hplaptop NetworkManager: <info>  SUP: response was 'OK' 
Jul 13 18:34:47 hplaptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Jul 13 18:34:47 hplaptop NetworkManager: <info>  SUP: response was 'OK' 
Jul 13 18:34:47 hplaptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Jul 13 18:34:53 hplaptop kernel: [12163.050788] wifi0: CMD=0x0121 => res=0x7f, resp0=0x0004
Jul 13 18:34:53 hplaptop kernel: [12163.050798] wifi0: hfa384x_set_rid: CMDCODE_ACCESS_WRITE failed (res=127, rid=fc24, len=6)
Jul 13 18:34:53 hplaptop kernel: [12163.050802] Could not set key 0 (len=6)
Jul 13 18:34:53 hplaptop kernel: [12163.050804] wifi0: encryption setup failed
Jul 13 18:34:53 hplaptop kernel: [12163.051805] wifi0: CMD=0x0121 => res=0x7f, resp0=0x0004
Jul 13 18:34:53 hplaptop kernel: [12163.051810] wifi0: hfa384x_set_rid: CMDCODE_ACCESS_WRITE failed (res=127, rid=fc48, len=2)
Jul 13 18:34:53 hplaptop kernel: [12163.052168] wlan0: CMD=0x0121 => res=0x7f, resp0=0x0004
Jul 13 18:34:53 hplaptop kernel: [12163.052172] wlan0: hfa384x_set_rid: CMDCODE_ACCESS_WRITE failed (res=127, rid=fc03, len=2)
Jul 13 18:34:53 hplaptop kernel: [12163.052626] wlan0: CMD=0x0121 => res=0x7f, resp0=0x0004
Jul 13 18:34:53 hplaptop kernel: [12163.052631] wlan0: hfa384x_set_rid: CMDCODE_ACCESS_WRITE failed (res=127, rid=fc04, len=34)
Jul 13 18:34:53 hplaptop kernel: [12163.052665] wlan0: Preferred AP (SIOCSIWAP) is used only in Managed mode when host_roaming is enabled
Jul 13 18:34:53 hplaptop NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
Jul 13 18:34:58 hplaptop kernel: [12165.669974] wifi0: CMD=0x0121 => res=0x7f, resp0=0x0004
Jul 13 18:34:58 hplaptop kernel: [12165.669988] wifi0: hfa384x_set_rid: CMDCODE_ACCESS_WRITE failed (res=127, rid=fc24, len=6)
Jul 13 18:34:58 hplaptop kernel: [12165.669991] Could not set key 0 (len=6)
Jul 13 18:34:58 hplaptop kernel: [12165.669993] wifi0: encryption setup failed
Jul 13 18:34:58 hplaptop kernel: [12165.671061] wifi0: CMD=0x0121 => res=0x7f, resp0=0x0004
Jul 13 18:34:58 hplaptop kernel: [12165.671066] wifi0: hfa384x_set_rid: CMDCODE_ACCESS_WRITE failed (res=127, rid=fc48, len=2)
Jul 13 18:34:58 hplaptop kernel: [12165.671422] wlan0: CMD=0x0121 => res=0x7f, resp0=0x0004
Jul 13 18:34:58 hplaptop kernel: [12165.671427] wlan0: hfa384x_set_rid: CMDCODE_ACCESS_WRITE failed (res=127, rid=fc03, len=2)
Jul 13 18:34:58 hplaptop kernel: [12165.671980] wlan0: CMD=0x0121 => res=0x7f, resp0=0x0004
Jul 13 18:34:58 hplaptop kernel: [12165.671984] wlan0: hfa384x_set_rid: CMDCODE_ACCESS_WRITE failed (res=127, rid=fc04, len=34)
Jul 13 18:34:58 hplaptop kernel: [12165.672020] wlan0: Preferred AP (SIOCSIWAP) is used only in Managed mode when host_roaming is enabled
Jul 13 18:34:58 hplaptop NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
Jul 13 18:35:04 hplaptop NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
Jul 13 18:35:09 hplaptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Jul 13 18:35:09 hplaptop NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
Jul 13 18:35:14 hplaptop NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
Jul 13 18:35:15 hplaptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Jul 13 18:35:20 hplaptop NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
Jul 13 18:35:25 hplaptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Jul 13 18:35:25 hplaptop NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
Jul 13 18:35:31 hplaptop NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
Jul 13 18:35:35 hplaptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Jul 13 18:35:36 hplaptop NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
Jul 13 18:35:40 hplaptop dhclient: No DHCPOFFERS received.
Jul 13 18:35:40 hplaptop dhclient: No working leases in persistent database - sleeping.
Jul 13 18:35:41 hplaptop kernel: [41125.215490] wifi0: CMD=0x0121 => res=0x7f, resp0=0x0004
Jul 13 18:35:41 hplaptop kernel: [41125.215512] wifi0: hfa384x_set_rid: CMDCODE_ACCESS_WRITE failed (res=127, rid=fc24, len=6)
Jul 13 18:35:41 hplaptop kernel: [41125.215523] Could not set key 0 (len=6)
Jul 13 18:35:41 hplaptop kernel: [41125.215530] wifi0: encryption setup failed
Jul 13 18:35:41 hplaptop kernel: [41125.217931] wifi0: CMD=0x0121 => res=0x7f, resp0=0x0004
Jul 13 18:35:41 hplaptop kernel: [41125.217947] wifi0: hfa384x_set_rid: CMDCODE_ACCESS_WRITE failed (res=127, rid=fc48, len=2)
Jul 13 18:35:41 hplaptop kernel: [41125.218847] wlan0: CMD=0x0121 => res=0x7f, resp0=0x0004
Jul 13 18:35:41 hplaptop kernel: [41125.218863] wlan0: hfa384x_set_rid: CMDCODE_ACCESS_WRITE failed (res=127, rid=fc03, len=2)
Jul 13 18:35:41 hplaptop kernel: [41125.219928] wlan0: CMD=0x0121 => res=0x7f, resp0=0x0004
Jul 13 18:35:41 hplaptop kernel: [41125.219940] wlan0: hfa384x_set_rid: CMDCODE_ACCESS_WRITE failed (res=127, rid=fc04, len=34)
Jul 13 18:35:41 hplaptop kernel: [41125.220056] wlan0: Preferred AP (SIOCSIWAP) is used only in Managed mode when host_roaming is enabled
Jul 13 18:35:41 hplaptop NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
Jul 13 18:35:47 hplaptop NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
Jul 13 18:35:47 hplaptop NetworkManager: <info>  Activation (wlan0/wireless): association took too long (>60s), asking for new key. 
Jul 13 18:35:47 hplaptop NetworkManager: <info>  Activation (wlan0) New wireless user key requested for network 'SanPat'. 
Jul 13 18:36:29 hplaptop NetworkManager: <info>  Activation (wlan0) New wireless user key for network 'SanPat' received. 
Jul 13 18:36:29 hplaptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Jul 13 18:36:29 hplaptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Jul 13 18:36:29 hplaptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Jul 13 18:36:29 hplaptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Jul 13 18:36:29 hplaptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Jul 13 18:36:30 hplaptop NetworkManager: <info>  Activation (wlan0/wireless): access point 'SanPat' is encrypted, and a key exists.  No new key needed. 
Jul 13 18:36:31 hplaptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan0^I^Iwext^I/var/run/wpa_supplicant0^I' 
Jul 13 18:36:31 hplaptop NetworkManager: <info>  SUP: response was 'OK' 
Jul 13 18:36:31 hplaptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Jul 13 18:36:31 hplaptop NetworkManager: <info>  SUP: response was 'OK' 
Jul 13 18:36:31 hplaptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Jul 13 18:36:31 hplaptop NetworkManager: <info>  SUP: response was '0' 
Jul 13 18:36:31 hplaptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 53616e506174' 
Jul 13 18:36:31 hplaptop NetworkManager: <info>  SUP: response was 'OK' 
Jul 13 18:36:31 hplaptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Jul 13 18:36:31 hplaptop NetworkManager: <info>  SUP: response was 'OK' 
Jul 13 18:36:31 hplaptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_key0 <key>' 
Jul 13 18:36:31 hplaptop NetworkManager: <info>  SUP: response was 'OK' 
Jul 13 18:36:31 hplaptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0' 
Jul 13 18:36:31 hplaptop NetworkManager: <info>  SUP: response was 'OK' 
Jul 13 18:36:31 hplaptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Jul 13 18:36:31 hplaptop NetworkManager: <info>  SUP: response was 'OK' 
Jul 13 18:36:31 hplaptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Jul 13 18:36:31 hplaptop kernel: [41185.760825] wifi0: CMD=0x0121 => res=0x7f, resp0=0x0004
Jul 13 18:36:31 hplaptop kernel: [41185.760847] wifi0: hfa384x_set_rid: CMDCODE_ACCESS_WRITE failed (res=127, rid=fc24, len=6)
Jul 13 18:36:31 hplaptop kernel: [41185.760857] Could not set key 0 (len=6)
Jul 13 18:36:31 hplaptop kernel: [41185.760864] wifi0: encryption setup failed
Jul 13 18:36:31 hplaptop kernel: [41185.763074] wifi0: CMD=0x0121 => res=0x7f, resp0=0x0004
Jul 13 18:36:31 hplaptop kernel: [41185.763090] wifi0: hfa384x_set_rid: CMDCODE_ACCESS_WRITE failed (res=127, rid=fc48, len=2)
Jul 13 18:36:31 hplaptop kernel: [41185.763888] wlan0: CMD=0x0121 => res=0x7f, resp0=0x0004
Jul 13 18:36:31 hplaptop kernel: [41185.763902] wlan0: hfa384x_set_rid: CMDCODE_ACCESS_WRITE failed (res=127, rid=fc03, len=2)
Jul 13 18:36:31 hplaptop kernel: [41185.765278] wlan0: CMD=0x0121 => res=0x7f, resp0=0x0004
Jul 13 18:36:31 hplaptop kernel: [41185.765293] wlan0: hfa384x_set_rid: CMDCODE_ACCESS_WRITE failed (res=127, rid=fc04, len=34)
Jul 13 18:36:31 hplaptop kernel: [41185.765396] wlan0: Preferred AP (SIOCSIWAP) is used only in Managed mode when host_roaming is enabled
Jul 13 18:36:31 hplaptop NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
Jul 13 18:36:48 hplaptop last message repeated 3 times
Jul 13 18:36:53 hplaptop kernel: [41216.276915] wifi0: CMD=0x0121 => res=0x7f, resp0=0x0004
Jul 13 18:36:53 hplaptop kernel: [41216.276937] wifi0: hfa384x_set_rid: CMDCODE_ACCESS_WRITE failed (res=127, rid=fc24, len=6)
Jul 13 18:36:53 hplaptop kernel: [41216.276948] Could not set key 0 (len=6)
Jul 13 18:36:53 hplaptop kernel: [41216.276954] wifi0: encryption setup failed
Jul 13 18:36:53 hplaptop kernel: [41216.279344] wifi0: CMD=0x0121 => res=0x7f, resp0=0x0004
Jul 13 18:36:53 hplaptop kernel: [41216.279360] wifi0: hfa384x_set_rid: CMDCODE_ACCESS_WRITE failed (res=127, rid=fc48, len=2)
Jul 13 18:36:53 hplaptop kernel: [41216.280128] wlan0: CMD=0x0121 => res=0x7f, resp0=0x0004
Jul 13 18:36:53 hplaptop kernel: [41216.280143] wlan0: hfa384x_set_rid: CMDCODE_ACCESS_WRITE failed (res=127, rid=fc03, len=2)
Jul 13 18:36:53 hplaptop kernel: [41216.281591] wlan0: CMD=0x0121 => res=0x7f, resp0=0x0004
Jul 13 18:36:53 hplaptop kernel: [41216.281606] wlan0: hfa384x_set_rid: CMDCODE_ACCESS_WRITE failed (res=127, rid=fc04, len=34)
Jul 13 18:36:53 hplaptop kernel: [41216.281718] wlan0: Preferred AP (SIOCSIWAP) is used only in Managed mode when host_roaming is enabled
Jul 13 18:36:53 hplaptop NetworkManager: <info>  Old device 'wlan0' activating, won't change. 

```

---

### Post by karlatsaic on 2008-10-24
I did an intrepid 8.10 (not quite ready) upgrade in hopes that the new kernel, mods and NetworkManager 0.7 would help. Now, I don't seem to be able to have the "Manual Configuration" option in the previous nm-applet. My current /var/log/syslog, while trying to make the connection, looks like:
```

Oct 24 08:19:10 hplaptop NetworkManager: <info>  Activation (wlan0) starting connection 'Auto SanPat' 
Oct 24 08:19:10 hplaptop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 
Oct 24 08:19:10 hplaptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 24 08:19:10 hplaptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Oct 24 08:19:10 hplaptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Oct 24 08:19:10 hplaptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Oct 24 08:19:10 hplaptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Oct 24 08:19:10 hplaptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Oct 24 08:19:10 hplaptop NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto SanPat' requires no security.  No secrets needed. 
Oct 24 08:19:10 hplaptop NetworkManager: <info>  Config: added 'ssid' value 'SanPat' 
Oct 24 08:19:10 hplaptop NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Oct 24 08:19:10 hplaptop NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE' 
Oct 24 08:19:10 hplaptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Oct 24 08:19:10 hplaptop NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 0 
Oct 24 08:19:10 hplaptop NetworkManager: <info>  Config: set interface ap_scan to 1 
Oct 24 08:19:10 hplaptop NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 2 
Oct 24 08:19:15 hplaptop NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 3 
Oct 24 08:19:15 hplaptop kernel: [ 4349.472077] wifi0: CMD=0x0121 => res=0x7f, resp0=0x0004
Oct 24 08:19:15 hplaptop kernel: [ 4349.472093] wifi0: hfa384x_set_rid: CMDCODE_ACCESS_WRITE failed (res=127, rid=fc48, len=2)
Oct 24 08:19:15 hplaptop kernel: [ 4349.474902] wlan0: CMD=0x0121 => res=0x7f, resp0=0x0004
Oct 24 08:19:15 hplaptop kernel: [ 4349.474910] wlan0: hfa384x_set_rid: CMDCODE_ACCESS_WRITE failed (res=127, rid=fc03, len=2)
Oct 24 08:19:15 hplaptop kernel: [ 4349.477790] wlan0: CMD=0x0121 => res=0x7f, resp0=0x0004
Oct 24 08:19:15 hplaptop kernel: [ 4349.477797] wlan0: hfa384x_set_rid: CMDCODE_ACCESS_WRITE failed (res=127, rid=fc04, len=34)
Oct 24 08:19:15 hplaptop kernel: [ 4349.477837] wlan0: Preferred AP (SIOCSIWAP) is used only in Managed mode when host_roaming is enabled
Oct 24 08:19:20 hplaptop NetworkManager: <info>  (wlan0): supplicant connection state change: 3 -> 0 
Oct 24 08:19:20 hplaptop NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 2 
Oct 24 08:19:25 hplaptop NetworkManager: <info>  wlan0: link timed out. 

```This looks close. I turned encryption off on my router while I am diagnosing this. I am presuming there is just some configuration setting somewhere, but I'm not aware of all the required conf files, etc. This is a trusty old Compaq Presario 2100 and the output of "lshw -C network" shows:
```

  *-network:0             
       description: Wireless interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: wifi0
       version: 01
       serial: 00:02:8a:7a:11:fa
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list logical wireless ethernet physical
       configuration: broadcast=yes driver=hostap firmware=1.4.9 latency=64 module=hostap_pci multicast=yes wireless=IEEE 802.11b
  *-network:1
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 00
       serial: 00:0b:cd:34:d3:67
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=full ip=192.168.1.101 latency=90 link=yes maxlatency=52 mingnt=11 module=natsemi multicast=yes port=twisted pair speed=100MB/s

```
Any help, clues, pointers, ... are greatly appreciated.

---

### Post by karlatsaic on 2008-11-04
The problem was simply the driver. After installing off the alternate iso and upgrading the kernel to 2.6.27-7 the hostap wifi driver was selected for my Intersil Prism 2.5 wireless chipset. I accidentally stuck in the live iso while testing this out and noticed that the orinoco driver was selected. I simply blacklisted the hostap driver by adding the following lines to /etc/modprobe.d/blacklist:
```

# prefer the orinoco wifi driver
blacklist hostap
blacklist hostap_pci

```I rebooted and, I also have to say, I really like the new Network Manager 0.7. It gives me lots more control, keeps wired and wireless alive simultaneously, and has the vpn features I need.

---

