---
title: "2200bg connection drops, intermittently"
date: 2007-05-22
forum: Networking &amp; Wireless
---

### Post by haywire on 2007-05-22
I installed a fresh copy of Feisty 7.04 and cant get my wireless 2200bg adapter to work properly, upon bootup i open the network manager and connect to my access point. and it connects fine, obtains an ip. (i am using an unsecured network while i am attempting to debug this issue)

once i have my address i can ping my local router and even external ip's and domain names. however if i leave it on pinging for a while it will just eventually stop.
or if i have it ping then try to open the internet, it instantly stops responding. page never loads and pings fail.

from the base install i updated the firmware and tried that, to no luck then i tried loading the updated drivers, ieee and firmware all still with no luck

how and where do i insert debug commands and what should it be so i can get more details on why the adapter is dropping the connection 

debug=0x400000 ? and where do i put this so i can see the syslogd messages


any help or ideas is appreciated 


the only way i can bring the interface back up so i can get a few ping packets through is w/ 
su
modprobe -r ipw2200
modprobe ipw2200

---

### Post by haywire on 2007-05-23
i was able to put my ipw2200 in debug mode

modprobe ipw2200 debug=0x43fff

i will append some debug and syslog messages

---

### Post by haywire on 2007-05-23
i also ran modprobe ieee80211 debug=0x43fff



message log

May 23 16:18:21 laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.domain_name
May 23 16:18:21 laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
May 23 16:18:21 laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
May 23 16:19:25 laptop kernel: [13911.172000] ACPI: PCI interrupt for device 0000:01:05.0 disabled
May 23 16:19:32 laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
May 23 16:19:32 laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain



syslog/debug log


May 23 16:17:35 laptop kernel: [13800.480000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:35 laptop kernel: [13800.580000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:35 laptop kernel: [13800.684000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:35 laptop kernel: [13800.736000] ipw2200: U ipw_wx_get_range GET Range
May 23 16:17:35 laptop kernel: [13800.736000] ipw2200: U ipw_wx_get_wap Getting WAP BSSID: 00:14:bf:39:22:40
May 23 16:17:35 laptop kernel: [13800.736000] ipw2200: U ipw_wx_get_name Name: IEEE 802.11g
May 23 16:17:35 laptop kernel: [13800.736000] ipw2200: U ipw_wx_get_freq GET Freq/Channel -> 6 
May 23 16:17:35 laptop kernel: [13800.736000] ipw2200: U ipw_wx_get_essid Getting essid: 'Galaxy'
May 23 16:17:35 laptop kernel: [13800.736000] ipw2200: U ipw_wx_get_mode Get MODE -> 2
May 23 16:17:35 laptop kernel: [13800.784000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:35 laptop kernel: [13800.888000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:35 laptop kernel: [13800.992000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:35 laptop kernel: [13801.092000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:35 laptop kernel: [13801.196000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:35 laptop kernel: [13801.296000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:36 laptop kernel: [13801.492000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:36 laptop kernel: [13801.504000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:36 laptop kernel: [13801.604000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:36 laptop kernel: [13801.708000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:36 laptop kernel: [13801.840000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:36 laptop kernel: [13801.912000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:36 laptop kernel: [13802.016000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:36 laptop kernel: [13802.116000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:36 laptop kernel: [13802.228000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:36 laptop kernel: [13802.320000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:37 laptop kernel: [13802.424000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:37 laptop kernel: [13802.732000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:37 laptop kernel: [13802.736000] ipw2200: U ipw_wx_get_range GET Range
May 23 16:17:37 laptop kernel: [13802.736000] ipw2200: U ipw_wx_get_wap Getting WAP BSSID: 00:14:bf:39:22:40
May 23 16:17:37 laptop kernel: [13802.736000] ipw2200: U ipw_wx_get_name Name: IEEE 802.11g
May 23 16:17:37 laptop kernel: [13802.736000] ipw2200: U ipw_wx_get_freq GET Freq/Channel -> 6 
May 23 16:17:37 laptop kernel: [13802.736000] ipw2200: U ipw_wx_get_essid Getting essid: 'Galaxy'
May 23 16:17:37 laptop kernel: [13802.736000] ipw2200: U ipw_wx_get_mode Get MODE -> 2
May 23 16:17:37 laptop kernel: [13802.832000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:37 laptop kernel: [13802.936000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:37 laptop kernel: [13803.040000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:37 laptop kernel: [13803.140000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:37 laptop kernel: [13803.244000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:37 laptop kernel: [13803.348000] ipw2200: I ipw_rx_notification type = 17 (8 bytes)
May 23 16:17:37 laptop kernel: [13803.348000] ipw2200: I ipw_handle_missed_beacon Missed beacon: 1
May 23 16:17:38 laptop kernel: [13803.448000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:38 laptop kernel: [13803.552000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:38 laptop kernel: [13803.652000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:38 laptop kernel: [13803.756000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:38 laptop kernel: [13803.856000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:38 laptop kernel: [13803.960000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:38 laptop kernel: [13804.064000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:38 laptop kernel: [13804.164000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:38 laptop kernel: [13804.268000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:38 laptop kernel: [13804.368000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:39 laptop kernel: [13804.472000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:39 laptop kernel: [13804.572000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:39 laptop kernel: [13804.676000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:39 laptop kernel: [13804.736000] ipw2200: U ipw_wx_get_range GET Range
May 23 16:17:39 laptop kernel: [13804.736000] ipw2200: U ipw_wx_get_wap Getting WAP BSSID: 00:14:bf:39:22:40
May 23 16:17:39 laptop kernel: [13804.736000] ipw2200: U ipw_wx_get_name Name: IEEE 802.11g
May 23 16:17:39 laptop kernel: [13804.736000] ipw2200: U ipw_wx_get_freq GET Freq/Channel -> 6 
May 23 16:17:39 laptop kernel: [13804.736000] ipw2200: U ipw_wx_get_essid Getting essid: 'Galaxy'
May 23 16:17:39 laptop kernel: [13804.736000] ipw2200: U ipw_wx_get_mode Get MODE -> 2
May 23 16:17:39 laptop kernel: [13804.780000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:39 laptop kernel: [13804.880000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:39 laptop kernel: [13804.984000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:39 laptop kernel: [13805.088000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:39 laptop kernel: [13805.188000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:39 laptop kernel: [13805.292000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:39 laptop kernel: [13805.392000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:40 laptop kernel: [13805.496000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:40 laptop kernel: [13805.600000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:40 laptop kernel: [13805.700000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:40 laptop kernel: [13805.804000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:40 laptop kernel: [13805.904000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:40 laptop kernel: [13806.008000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:40 laptop kernel: [13806.108000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:40 laptop kernel: [13806.212000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:40 laptop kernel: [13806.316000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:40 laptop kernel: [13806.416000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:41 laptop kernel: [13806.520000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:41 laptop kernel: [13806.620000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:41 laptop kernel: [13806.724000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:41 laptop kernel: [13806.736000] ipw2200: U ipw_wx_get_range GET Range
May 23 16:17:41 laptop kernel: [13806.736000] ipw2200: U ipw_wx_get_wap Getting WAP BSSID: 00:14:bf:39:22:40
May 23 16:17:41 laptop kernel: [13806.736000] ipw2200: U ipw_wx_get_name Name: IEEE 802.11g
May 23 16:17:41 laptop kernel: [13806.736000] ipw2200: U ipw_wx_get_freq GET Freq/Channel -> 6 
May 23 16:17:41 laptop kernel: [13806.736000] ipw2200: U ipw_wx_get_essid Getting essid: 'Galaxy'
May 23 16:17:41 laptop kernel: [13806.736000] ipw2200: U ipw_wx_get_mode Get MODE -> 2
May 23 16:17:41 laptop kernel: [13806.828000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:41 laptop kernel: [13806.928000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:41 laptop kernel: [13807.032000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:41 laptop kernel: [13807.132000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:41 laptop kernel: [13807.236000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:41 laptop kernel: [13807.340000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:42 laptop kernel: [13807.440000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:42 laptop kernel: [13807.544000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:42 laptop kernel: [13807.644000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:42 laptop kernel: [13807.748000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:42 laptop kernel: [13807.852000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:42 laptop kernel: [13807.952000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:42 laptop kernel: [13808.056000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:42 laptop kernel: [13808.156000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:42 laptop kernel: [13808.260000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:42 laptop kernel: [13808.364000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:43 laptop kernel: [13808.464000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:43 laptop kernel: [13808.568000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:43 laptop kernel: [13808.668000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:43 laptop kernel: [13808.736000] ipw2200: U ipw_wx_get_range GET Range
May 23 16:17:43 laptop kernel: [13808.736000] ipw2200: U ipw_wx_get_wap Getting WAP BSSID: 00:14:bf:39:22:40
May 23 16:17:43 laptop kernel: [13808.736000] ipw2200: U ipw_wx_get_name Name: IEEE 802.11g
May 23 16:17:43 laptop kernel: [13808.736000] ipw2200: U ipw_wx_get_freq GET Freq/Channel -> 6 
May 23 16:17:43 laptop kernel: [13808.736000] ipw2200: U ipw_wx_get_essid Getting essid: 'Galaxy'
May 23 16:17:43 laptop kernel: [13808.736000] ipw2200: U ipw_wx_get_mode Get MODE -> 2
May 23 16:17:43 laptop kernel: [13808.772000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:43 laptop kernel: [13808.876000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:43 laptop kernel: [13808.976000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:43 laptop kernel: [13809.080000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:43 laptop kernel: [13809.180000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:43 laptop kernel: [13809.284000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:43 laptop kernel: [13809.388000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:44 laptop kernel: [13809.488000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:44 laptop kernel: [13809.592000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:44 laptop kernel: [13809.692000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:44 laptop kernel: [13809.796000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:44 laptop kernel: [13809.900000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:44 laptop kernel: [13810.000000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:44 laptop kernel: [13810.104000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:44 laptop kernel: [13810.204000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:44 laptop kernel: [13810.308000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:44 laptop kernel: [13810.412000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:45 laptop kernel: [13810.512000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:45 laptop kernel: [13810.616000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:17:45 laptop kernel: [13810.696000] ipw2200: U ipw_deinit Disassociating during shutdown.
May 23 16:17:45 laptop kernel: [13810.696000] ipw2200: U ipw_send_disassociate Disassocation attempt from 00:14:bf:39:22:40 on channel 6.
May 23 16:17:45 laptop kernel: [13810.696000] 00000000 06 00 02 00 02 00 00 02  00 14 BF 39 22 40 1E 00   ........ ...9"@..
May 23 16:17:45 laptop kernel: [13810.696000] 00000010 00 00 E1 3B C6 A1 11 04  0A 00 64 00 00 14 BF 39   ...;.... ..d....9
May 23 16:17:45 laptop kernel: [13810.696000] 00000020 22 40 00 00 00 00 00 00                            "@......         
May 23 16:17:45 laptop kernel: [13810.700000] ipw2200: I ipw_rx_notification type = 10 (4 bytes)
May 23 16:17:45 laptop kernel: [13810.700000] ipw2200: I ipw_rx_notification association failed (0x0C20): Unknown status value.
May 23 16:17:45 laptop kernel: [13810.700000] ipw2200: I ipw_rx_notification disassociated: 'Galaxy' 00:14:bf:39:22:40 
May 23 16:17:45 laptop kernel: [13810.700000] ipw2200: U ipw_deinit Took 119ms to de-init
May 23 16:17:45 laptop kernel: [13810.700000] 00000000 00 00 00 00                                        ....             
May 23 16:17:45 laptop kernel: [13810.736000] ipw2200: U ipw_wx_get_range GET Range
May 23 16:17:45 laptop kernel: [13810.736000] ipw2200: U ipw_wx_get_wap Getting WAP BSSID: 00:14:bf:39:22:40
May 23 16:17:45 laptop kernel: [13810.736000] ipw2200: U ipw_wx_get_name Name: unassociated
May 23 16:17:45 laptop kernel: [13810.736000] ipw2200: U ipw_wx_get_freq GET Freq/Channel -> 6 
May 23 16:17:45 laptop kernel: [13810.736000] ipw2200: U ipw_wx_get_essid Getting essid: 'Galaxy'
May 23 16:17:45 laptop kernel: [13810.736000] ipw2200: U ipw_wx_get_mode Get MODE -> 2
May 23 16:17:45 laptop kernel: [13810.748000] ipw2200: U ipw_net_stop dev->close
May 23 16:17:45 laptop NetworkManager: <debug info>^I[1179951465.341138] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/net_00_0e_35_a9_97_37'). 
May 23 16:18:01 laptop kernel: [13827.392000] eth0: no IPv6 routers present
May 23 16:18:05 laptop kernel: [13830.492000] ipw2200: U ipw_pci_probe pci_resource_len = 0x00001000
May 23 16:18:05 laptop kernel: [13830.492000] ipw2200: U ipw_pci_probe pci_resource_base = dfbc4000
May 23 16:18:05 laptop kernel: [13830.492000] ipw2200: U ipw_sw_reset Hardware crypto [off]
May 23 16:18:05 laptop kernel: [13830.500000] ipw2200: U ipw_get_fw Read firmware 'ipw2200-bss.fw' image v3.0 (191126 bytes)
May 23 16:18:05 laptop kernel: [13830.524000] ipw2200: U ipw_load initial device response after 10ms
May 23 16:18:05 laptop kernel: [13830.524000] ipw2200: U ipw_stop_master stop master 0ms
May 23 16:18:05 laptop kernel: [13830.540000] ipw2200: U ipw_load_ucode Microcode OK, rev. 53594 (0xd15a) dev. 3 (0x3) of 11/22/04 20:27
May 23 16:18:05 laptop kernel: [13830.596000] ipw2200: U ipw_load device response after 50ms
May 23 16:18:05 laptop kernel: [13830.608000] ipw2200: U ipw_eeprom_init_sram Writing EEPROM data into SRAM
May 23 16:18:05 laptop kernel: [13830.608000] 00000000 0B 02 01 14 02 14 03 14  04 14 05 14 06 14 07 14   ........ ........
May 23 16:18:05 laptop kernel: [13830.608000] 00000010 08 14 09 14 0A 14 0B 14  00 00 00 00 00 00 00 00   ........ ........
May 23 16:18:05 laptop kernel: [13830.608000] 00000020 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00   ........ ........
May 23 16:18:05 laptop kernel: [13830.608000] 00000030 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00   ........ ........
May 23 16:18:05 laptop kernel: [13830.608000] 00000040 00 00 00 00 00 00 00 00  00 00 00 00               ........ ....    
May 23 16:18:05 laptop kernel: [13830.608000] 00000000 0B 01 01 14 02 14 03 14  04 14 05 14 06 14 07 14   ........ ........
May 23 16:18:05 laptop kernel: [13830.608000] 00000010 08 14 09 14 0A 14 0B 14  00 00 00 00 00 00 00 00   ........ ........
May 23 16:18:05 laptop kernel: [13830.608000] 00000020 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00   ........ ........
May 23 16:18:05 laptop kernel: [13830.608000] 00000030 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00   ........ ........
May 23 16:18:05 laptop kernel: [13830.608000] 00000040 00 00 00 00 00 00 00 00  00 00 00 00               ........ ....    
May 23 16:18:05 laptop kernel: [13830.612000] ipw2200: U ipw_send_adapter_address eth1: Setting MAC to 00:0e:35:a9:97:37
May 23 16:18:05 laptop kernel: [13830.612000] 00000000 00 0E 35 A9 97 37                                  ..5..7           
May 23 16:18:05 laptop kernel: [13830.612000] 00000000 00 00 00 00 01 00 01 00  01 00 00 00 00 00 00 1E   ........ ........
May 23 16:18:05 laptop kernel: [13830.612000] 00000010 00 00 01 00                                        ....             
May 23 16:18:05 laptop kernel: [13830.612000] 00000000 02 0C 01 00 82 84 0B 16  0C 12 18 24 30 48 60 6C   ........ ...$0H`l
May 23 16:18:05 laptop kernel: [13830.612000] 00000000 00 09 00 00                                        ....             
May 23 16:18:05 laptop kernel: [13830.612000] 00000000 0F 00 0F 00 0F 00 0F 00  FF 03 FF 03 FF 03 FF 03   ........ ........
May 23 16:18:05 laptop kernel: [13830.612000] 00000010 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00   ........ ........
May 23 16:18:05 laptop kernel: [13830.612000] 00000020 1F 00 1F 00 1F 00 1F 00  FF 03 FF 03 FF 03 FF 03   ........ ........
May 23 16:18:05 laptop kernel: [13830.612000] 00000030 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00   ........ ........
May 23 16:18:05 laptop kernel: [13830.612000] 00000040 0F 00 0F 00 0F 00 0F 00  FF 03 FF 03 FF 03 FF 03   ........ ........
May 23 16:18:05 laptop kernel: [13830.612000] 00000050 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00   ........ ........
May 23 16:18:05 laptop kernel: [13830.612000] 00000000 FB 2F 5C 0D                                        ./\.             
May 23 16:18:05 laptop kernel: [13830.612000] ipw2200: U ipw_up Configured device on count 0
May 23 16:18:05 laptop kernel: [13830.612000] 00000000 00 00 00 00 4B 01 02 03  04 05 06 07 08 09 0A 0B   ....K... ........
May 23 16:18:05 laptop kernel: [13830.612000] 00000010 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00   ........ ........
May 23 16:18:05 laptop kernel: [13830.612000] 00000020 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00   ........ ........
May 23 16:18:05 laptop kernel: [13830.612000] 00000030 00 00 00 00 00 00 00 00  00 00 03 33 33 33 33 33   ........ ...33333
May 23 16:18:05 laptop kernel: [13830.612000] 00000040 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00   ........ ........
May 23 16:18:05 laptop kernel: [13830.612000] 00000050 00 00 00 00 00 00 00 00  78 00 00 00 14 00 14 00   ........ x.......
May 23 16:18:05 laptop NetworkManager: <debug info>^I[1179951485.207569] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_0e_35_a9_97_37'). 
May 23 16:18:05 laptop kernel: [13830.640000] ipw2200: I ipw_rx_notification type = 20 (104 bytes)
May 23 16:18:05 laptop kernel: [13830.640000] ipw2200: I ipw_rx_notification TODO: Calibration
May 23 16:18:05 laptop kernel: [13830.652000] ipw2200: U ipw_wx_get_range GET Range
May 23 16:18:05 laptop kernel: [13830.652000] ipw2200: U ipw_wx_set_scan Start scan
May 23 16:18:05 laptop kernel: [13830.652000] ipw2200: U ipw_net_open dev->open
May 23 16:18:05 laptop kernel: [13830.660000] ipw2200: I ipw_net_hard_start_xmit Tx attempt while not associated.
May 23 16:18:05 laptop kernel: [13830.664000] ipw2200: U ipw_wx_get_mode Get MODE -> 2
May 23 16:18:05 laptop kernel: [13830.664000] ipw2200: U ipw_wx_set_mode Set MODE: 2
May 23 16:18:05 laptop kernel: [13830.664000] ipw2200: U ipw_wx_get_range GET Range
May 23 16:18:05 laptop kernel: [13830.664000] ipw2200: I ipw_rx_notification type = 12 (46 bytes)
May 23 16:18:05 laptop kernel: [13830.664000] ipw2200: I ipw_rx_notification Scan result for channel 1
May 23 16:18:05 laptop kernel: [13830.676000] ipw2200: U ipw_wx_get_mode Get MODE -> 2
May 23 16:18:05 laptop kernel: [13830.676000] ipw2200: U ipw_wx_get_mode Get MODE -> 2
May 23 16:18:05 laptop kernel: [13830.676000] ipw2200: U ipw_wx_set_mode Set MODE: 2
May 23 16:18:05 laptop kernel: [13830.676000] ipw2200: U ipw_wx_set_scan Start scan
May 23 16:18:05 laptop kernel: [13830.688000] ipw2200: I ipw_rx_notification type = 12 (46 bytes)
May 23 16:18:05 laptop kernel: [13830.688000] ipw2200: I ipw_rx_notification Scan result for channel 2
May 23 16:18:05 laptop kernel: [13830.712000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:18:05 laptop kernel: [13830.712000] ipw2200: I ipw_rx_notification type = 12 (46 bytes)
May 23 16:18:05 laptop kernel: [13830.712000] ipw2200: I ipw_rx_notification Scan result for channel 3
May 23 16:18:05 laptop kernel: [13830.720000] ipw2200: U ipw_wx_set_essid Setting ESSID: '<hidden>' (0)
May 23 16:18:05 laptop kernel: [13830.720000] ipw2200: U ipw_wx_set_essid [re]association triggered due to ESSID change.
May 23 16:18:05 laptop kernel: [13830.720000] ipw2200: U ipw_associate Not attempting association (scanning or not initialized)
May 23 16:18:05 laptop kernel: [13830.720000] ipw2200: U ipw_wx_get_mode Get MODE -> 2
May 23 16:18:05 laptop kernel: [13830.720000] ipw2200: U ipw_wx_set_mode Set MODE: 2
May 23 16:18:05 laptop kernel: [13830.724000] ipw2200: U ipw_wx_get_mode Get MODE -> 2
May 23 16:18:05 laptop kernel: [13830.724000] ipw2200: U ipw_wx_get_rate GET Rate -> 0 
May 23 16:18:05 laptop kernel: [13830.736000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:18:05 laptop kernel: [13830.736000] ipw2200: I ipw_rx_notification type = 12 (46 bytes)
May 23 16:18:05 laptop kernel: [13830.736000] ipw2200: I ipw_rx_notification Scan result for channel 4
May 23 16:18:05 laptop kernel: [13830.760000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:18:05 laptop kernel: [13830.760000] ipw2200: I ipw_rx_notification type = 12 (46 bytes)
May 23 16:18:05 laptop kernel: [13830.760000] ipw2200: I ipw_rx_notification Scan result for channel 5
May 23 16:18:05 laptop kernel: [13830.784000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:18:05 laptop kernel: [13830.784000] ipw2200: I ipw_rx_notification type = 12 (46 bytes)
May 23 16:18:05 laptop kernel: [13830.784000] ipw2200: I ipw_rx_notification Scan result for channel 6
May 23 16:18:05 laptop kernel: [13830.808000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:18:05 laptop kernel: [13830.808000] ipw2200: I ipw_rx_notification type = 12 (46 bytes)
May 23 16:18:05 laptop kernel: [13830.808000] ipw2200: I ipw_rx_notification Scan result for channel 7
May 23 16:18:05 laptop kernel: [13830.832000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:18:05 laptop kernel: [13830.832000] ipw2200: I ipw_rx_notification type = 12 (46 bytes)
May 23 16:18:05 laptop kernel: [13830.832000] ipw2200: I ipw_rx_notification Scan result for channel 8
May 23 16:18:05 laptop kernel: [13830.856000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:18:05 laptop kernel: [13830.856000] ipw2200: I ipw_rx_notification type = 12 (46 bytes)
May 23 16:18:05 laptop kernel: [13830.856000] ipw2200: I ipw_rx_notification Scan result for channel 9
May 23 16:18:05 laptop kernel: [13830.876000] ipw2200: I ipw_rx_notification type = 12 (46 bytes)
May 23 16:18:05 laptop kernel: [13830.876000] ipw2200: I ipw_rx_notification Scan result for channel 10
May 23 16:18:05 laptop kernel: [13830.900000] ipw2200: I ipw_rx_notification type = 12 (46 bytes)
May 23 16:18:05 laptop kernel: [13830.900000] ipw2200: I ipw_rx_notification Scan result for channel 11
May 23 16:18:05 laptop kernel: [13830.900000] ipw2200: I ipw_rx_notification type = 13 (4 bytes)
May 23 16:18:05 laptop kernel: [13830.900000] ipw2200: I ipw_rx_notification Scan completed: type 11, 11 channels, 1 status
May 23 16:18:05 laptop kernel: [13830.900000] ipw2200: U ipw_best_network Network 'Galaxy (00:14:bf:39:22:40)' excluded because of ESSID mismatch: '<hidden>'.
May 23 16:18:05 laptop kernel: [13830.900000] ipw2200: U ipw_debug_config Scan completed, no valid APs matched [CFG 0x00000342]
May 23 16:18:05 laptop kernel: [13830.900000] ipw2200: U ipw_debug_config Channel unlocked.
May 23 16:18:05 laptop kernel: [13830.900000] ipw2200: U ipw_debug_config ESSID locked to '<hidden>'
May 23 16:18:05 laptop kernel: [13830.900000] ipw2200: U ipw_debug_config BSSID unlocked.
May 23 16:18:05 laptop kernel: [13830.900000] ipw2200: U ipw_debug_config PRIVACY off
May 23 16:18:05 laptop kernel: [13830.900000] ipw2200: U ipw_debug_config RATE MASK: 0x00000FFF
May 23 16:18:05 laptop kernel: [13830.928000] ipw2200: U ipw_wx_get_mode Get MODE -> 2
May 23 16:18:05 laptop kernel: [13831.000000] 00000000 01 00 00 00 4B 01 02 03  04 05 06 07 08 09 0A 0B   ....K... ........
May 23 16:18:05 laptop kernel: [13831.000000] 00000010 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00   ........ ........
May 23 16:18:05 laptop kernel: [13831.000000] 00000020 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00   ........ ........
May 23 16:18:05 laptop kernel: [13831.000000] 00000030 00 00 00 00 00 00 00 00  00 00 04 44 44 44 44 44   ........ ...DDDDD
May 23 16:18:05 laptop kernel: [13831.000000] 00000040 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00   ........ ........
May 23 16:18:05 laptop kernel: [13831.000000] 00000050 00 00 00 00 00 00 00 00  78 00 00 00 14 00 14 00   ........ x.......
May 23 16:18:05 laptop kernel: [13831.024000] ipw2200: I ipw_rx_notification type = 12 (46 bytes)
May 23 16:18:05 laptop kernel: [13831.024000] ipw2200: I ipw_rx_notification Scan result for channel 1
May 23 16:18:05 laptop kernel: [13831.048000] ipw2200: I ipw_rx_notification type = 12 (46 bytes)
May 23 16:18:05 laptop kernel: [13831.048000] ipw2200: I ipw_rx_notification Scan result for channel 2
May 23 16:18:05 laptop kernel: [13831.072000] ipw2200: I ipw_rx_notification type = 12 (46 bytes)
May 23 16:18:05 laptop kernel: [13831.072000] ipw2200: I ipw_rx_notification Scan result for channel 3
May 23 16:18:05 laptop kernel: [13831.096000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:18:05 laptop kernel: [13831.096000] ipw2200: I ipw_rx_notification type = 12 (46 bytes)
May 23 16:18:05 laptop kernel: [13831.096000] ipw2200: I ipw_rx_notification Scan result for channel 4
May 23 16:18:05 laptop kernel: [13831.124000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:18:05 laptop kernel: [13831.124000] ipw2200: I ipw_rx_notification type = 12 (46 bytes)
May 23 16:18:05 laptop kernel: [13831.124000] ipw2200: I ipw_rx_notification Scan result for channel 5
May 23 16:18:05 laptop kernel: [13831.152000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:18:05 laptop kernel: [13831.152000] ipw2200: I ipw_rx_notification type = 12 (46 bytes)
May 23 16:18:05 laptop kernel: [13831.152000] ipw2200: I ipw_rx_notification Scan result for channel 6
May 23 16:18:05 laptop kernel: [13831.176000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:18:05 laptop kernel: [13831.176000] ipw2200: I ipw_rx_notification type = 12 (46 bytes)
May 23 16:18:05 laptop kernel: [13831.176000] ipw2200: I ipw_rx_notification Scan result for channel 7
May 23 16:18:05 laptop kernel: [13831.204000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:18:05 laptop kernel: [13831.204000] ipw2200: I ipw_rx_notification type = 12 (46 bytes)
May 23 16:18:05 laptop kernel: [13831.204000] ipw2200: I ipw_rx_notification Scan result for channel 8
May 23 16:18:05 laptop kernel: [13831.228000] ipw2200: I ipw_rx_notification type = 12 (46 bytes)
May 23 16:18:05 laptop kernel: [13831.228000] ipw2200: I ipw_rx_notification Scan result for channel 9
May 23 16:18:05 laptop kernel: [13831.252000] ipw2200: I ipw_rx_notification type = 12 (46 bytes)
May 23 16:18:05 laptop kernel: [13831.252000] ipw2200: I ipw_rx_notification Scan result for channel 10
May 23 16:18:05 laptop kernel: [13831.276000] ipw2200: I ipw_rx_notification type = 12 (46 bytes)
May 23 16:18:05 laptop kernel: [13831.276000] ipw2200: I ipw_rx_notification Scan result for channel 11
May 23 16:18:05 laptop kernel: [13831.276000] ipw2200: I ipw_rx_notification type = 13 (4 bytes)
May 23 16:18:05 laptop kernel: [13831.276000] ipw2200: I ipw_rx_notification Scan completed: type 11, 11 channels, 1 status
May 23 16:18:05 laptop kernel: [13831.276000] ipw2200: U ipw_best_network Network 'Galaxy (00:14:bf:39:22:40)' excluded because of ESSID mismatch: '<hidden>'.
May 23 16:18:05 laptop kernel: [13831.276000] ipw2200: U ipw_debug_config Scan completed, no valid APs matched [CFG 0x00000342]
May 23 16:18:05 laptop kernel: [13831.276000] ipw2200: U ipw_debug_config Channel unlocked.
May 23 16:18:05 laptop kernel: [13831.276000] ipw2200: U ipw_debug_config ESSID locked to '<hidden>'
May 23 16:18:05 laptop kernel: [13831.276000] ipw2200: U ipw_debug_config BSSID unlocked.
May 23 16:18:05 laptop kernel: [13831.276000] ipw2200: U ipw_debug_config PRIVACY off
May 23 16:18:05 laptop kernel: [13831.276000] ipw2200: U ipw_debug_config RATE MASK: 0x00000FFF
May 23 16:18:05 laptop kernel: [13831.376000] 00000000 02 00 00 00 4B 01 02 03  04 05 06 07 08 09 0A 0B   ....K... ........
May 23 16:18:05 laptop kernel: [13831.376000] 00000010 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00   ........ ........
May 23 16:18:05 laptop kernel: [13831.376000] 00000020 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00   ........ ........
May 23 16:18:05 laptop kernel: [13831.376000] 00000030 00 00 00 00 00 00 00 00  00 00 03 33 33 33 33 33   ........ ...33333
May 23 16:18:05 laptop kernel: [13831.376000] 00000040 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00   ........ ........
May 23 16:18:05 laptop kernel: [13831.376000] 00000050 00 00 00 00 00 00 00 00  78 00 00 00 14 00 14 00   ........ x.......
May 23 16:18:05 laptop kernel: [13831.396000] ipw2200: I ipw_rx_notification type = 12 (46 bytes)
May 23 16:18:05 laptop kernel: [13831.396000] ipw2200: I ipw_rx_notification Scan result for channel 1
May 23 16:18:05 laptop kernel: [13831.420000] ipw2200: I ipw_rx_notification type = 12 (46 bytes)
May 23 16:18:05 laptop kernel: [13831.420000] ipw2200: I ipw_rx_notification Scan result for channel 2
May 23 16:18:06 laptop kernel: [13831.444000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:18:06 laptop kernel: [13831.444000] ipw2200: I ipw_rx_notification type = 12 (46 bytes)
May 23 16:18:06 laptop kernel: [13831.444000] ipw2200: I ipw_rx_notification Scan result for channel 3
May 23 16:18:06 laptop kernel: [13831.468000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:18:06 laptop kernel: [13831.468000] ipw2200: I ipw_rx_notification type = 12 (46 bytes)
May 23 16:18:06 laptop kernel: [13831.468000] ipw2200: I ipw_rx_notification Scan result for channel 4
May 23 16:18:06 laptop kernel: [13831.496000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:18:06 laptop kernel: [13831.496000] ipw2200: I ipw_rx_notification type = 12 (46 bytes)
May 23 16:18:06 laptop kernel: [13831.496000] ipw2200: I ipw_rx_notification Scan result for channel 5
May 23 16:18:06 laptop kernel: [13831.520000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:18:06 laptop kernel: [13831.520000] ipw2200: I ipw_rx_notification type = 12 (46 bytes)
May 23 16:18:06 laptop kernel: [13831.520000] ipw2200: I ipw_rx_notification Scan result for channel 6
May 23 16:18:06 laptop kernel: [13831.544000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:18:06 laptop kernel: [13831.544000] ipw2200: I ipw_rx_notification type = 12 (46 bytes)
May 23 16:18:06 laptop kernel: [13831.544000] ipw2200: I ipw_rx_notification Scan result for channel 7
May 23 16:18:06 laptop kernel: [13831.568000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:18:06 laptop kernel: [13831.568000] ipw2200: I ipw_rx_notification type = 12 (46 bytes)
May 23 16:18:06 laptop kernel: [13831.568000] ipw2200: I ipw_rx_notification Scan result for channel 8
May 23 16:18:06 laptop kernel: [13831.592000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:18:06 laptop kernel: [13831.592000] ipw2200: I ipw_rx_notification type = 12 (46 bytes)
May 23 16:18:06 laptop kernel: [13831.592000] ipw2200: I ipw_rx_notification Scan result for channel 9
May 23 16:18:06 laptop kernel: [13831.616000] ipw2200: I ipw_rx_notification type = 12 (46 bytes)
May 23 16:18:06 laptop kernel: [13831.616000] ipw2200: I ipw_rx_notification Scan result for channel 10
May 23 16:18:06 laptop kernel: [13831.640000] ipw2200: I ipw_rx_notification type = 12 (46 bytes)
May 23 16:18:06 laptop kernel: [13831.640000] ipw2200: I ipw_rx_notification Scan result for channel 11
May 23 16:18:06 laptop kernel: [13831.640000] ipw2200: I ipw_rx_notification type = 13 (4 bytes)
May 23 16:18:06 laptop kernel: [13831.640000] ipw2200: I ipw_rx_notification Scan completed: type 11, 11 channels, 1 status
May 23 16:18:06 laptop kernel: [13831.640000] ipw2200: U ipw_best_network Network 'Galaxy (00:14:bf:39:22:40)' excluded because of ESSID mismatch: '<hidden>'.
May 23 16:18:06 laptop kernel: [13831.640000] ipw2200: U ipw_debug_config Scan completed, no valid APs matched [CFG 0x00000342]
May 23 16:18:06 laptop kernel: [13831.640000] ipw2200: U ipw_debug_config Channel unlocked.
May 23 16:18:06 laptop kernel: [13831.640000] ipw2200: U ipw_debug_config ESSID locked to '<hidden>'
May 23 16:18:06 laptop kernel: [13831.640000] ipw2200: U ipw_debug_config BSSID unlocked.
May 23 16:18:06 laptop kernel: [13831.640000] ipw2200: U ipw_debug_config PRIVACY off
May 23 16:18:06 laptop kernel: [13831.640000] ipw2200: U ipw_debug_config RATE MASK: 0x00000FFF
May 23 16:18:06 laptop kernel: [13831.740000] 00000000 03 00 00 00 4B 01 02 03  04 05 06 07 08 09 0A 0B   ....K... ........
May 23 16:18:06 laptop kernel: [13831.740000] 00000010 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00   ........ ........
May 23 16:18:06 laptop kernel: [13831.740000] 00000020 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00   ........ ........
May 23 16:18:06 laptop kernel: [13831.740000] 00000030 00 00 00 00 00 00 00 00  00 00 04 44 44 44 44 44   ........ ...DDDDD
May 23 16:18:06 laptop kernel: [13831.740000] 00000040 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00   ........ ........
May 23 16:18:06 laptop kernel: [13831.740000] 00000050 00 00 00 00 00 00 00 00  78 00 00 00 14 00 14 00   ........ x.......
May 23 16:18:06 laptop kernel: [13831.764000] ipw2200: I ipw_rx_notification type = 12 (46 bytes)
May 23 16:18:06 laptop kernel: [13831.764000] ipw2200: I ipw_rx_notification Scan result for channel 1
May 23 16:18:06 laptop kernel: [13831.788000] ipw2200: I ipw_rx_notification type = 12 (46 bytes)
May 23 16:18:06 laptop kernel: [13831.788000] ipw2200: I ipw_rx_notification Scan result for channel 2
May 23 16:18:06 laptop kernel: [13831.812000] ipw2200: I ipw_rx_notification type = 12 (46 bytes)
May 23 16:18:06 laptop kernel: [13831.812000] ipw2200: I ipw_rx_notification Scan result for channel 3
May 23 16:18:06 laptop kernel: [13831.836000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:18:06 laptop kernel: [13831.836000] ipw2200: I ipw_rx_notification type = 12 (46 bytes)
May 23 16:18:06 laptop kernel: [13831.836000] ipw2200: I ipw_rx_notification Scan result for channel 4
May 23 16:18:06 laptop kernel: [13831.864000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:18:06 laptop kernel: [13831.864000] ipw2200: I ipw_rx_notification type = 12 (46 bytes)
May 23 16:18:06 laptop kernel: [13831.864000] ipw2200: I ipw_rx_notification Scan result for channel 5
May 23 16:18:06 laptop kernel: [13831.888000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:18:06 laptop kernel: [13831.888000] ipw2200: I ipw_rx_notification type = 12 (46 bytes)
May 23 16:18:06 laptop kernel: [13831.888000] ipw2200: I ipw_rx_notification Scan result for channel 6
May 23 16:18:06 laptop kernel: [13831.912000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:18:06 laptop kernel: [13831.912000] ipw2200: I ipw_rx_notification type = 12 (46 bytes)
May 23 16:18:06 laptop kernel: [13831.912000] ipw2200: I ipw_rx_notification Scan result for channel 7
May 23 16:18:06 laptop kernel: [13831.940000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)
May 23 16:18:06 laptop kernel: [13831.940000] ipw2200: I ipw_rx_notification type = 12 (46 bytes)
May 23 16:18:06 laptop kernel: [13831.940000] ipw2200: I ipw_rx_notification Scan result for channel 8
May 23 16:18:06 laptop kernel: [13831.964000] ipw2200: I ipw_rx_notification type = 12 (46 bytes)
May 23 16:18:06 laptop kernel: [13831.964000] ipw2200: I ipw_rx_notification Scan result for channel 9
May 23 16:18:06 laptop kernel: [13831.988000] ipw2200: I ipw_rx_notification type = 12 (46 bytes)
May 23 16:18:06 laptop kernel: [13831.988000] ipw2200: I ipw_rx_notification Scan result for channel 10
May 23 16:18:06 laptop kernel: [13832.012000] ipw2200: I ipw_rx_notification type = 12 (46 bytes)
May 23 16:18:06 laptop kernel: [13832.012000] ipw2200: I ipw_rx_notification Scan result for channel 11
May 23 16:18:06 laptop kernel: [13832.012000] ipw2200: I ipw_rx_notification type = 13 (4 bytes)
May 23 16:18:06 laptop kernel: [13832.012000] ipw2200: I ipw_rx_notification Scan completed: type 11, 11 channels, 1 status
May 23 16:18:06 laptop kernel: [13832.012000] ipw2200: U ipw_best_network Network 'Galaxy (00:14:bf:39:22:40)' excluded because of ESSID mismatch: '<hidden>'.
May 23 16:18:06 laptop kernel: [13832.012000] ipw2200: U ipw_debug_config Scan completed, no valid APs matched [CFG 0x00000342]
May 23 16:18:06 laptop kernel: [13832.012000] ipw2200: U ipw_debug_config Channel unlocked.
May 23 16:18:06 laptop kernel: [13832.012000] ipw2200: U ipw_debug_config ESSID locked to '<hidden>'
May 23 16:18:06 laptop kernel: [13832.012000] ipw2200: U ipw_debug_config BSSID unlocked.
May 23 16:18:06 laptop kernel: [13832.012000] ipw2200: U ipw_debug_config PRIVACY off
May 23 16:18:06 laptop kernel: [13832.012000] ipw2200: U ipw_debug_config RATE MASK:

---

### Post by haywire on 2007-05-23
it appears to be a problem with wpa and the 2200bg.

ive tried the setup with an orinoco gold pcmcia and it works fine w/ wpa and everything
and i was mistaken before the 2200bg works fine with the Access point unsecured. 

which means it has to be the 2200bg and the wpasupplicant

---

