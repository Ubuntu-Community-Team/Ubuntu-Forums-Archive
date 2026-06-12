---
title: "Asus USB-AC65 Wireless AC1300 - Not Working"
date: 2016-05-07
forum: Networking &amp; Wireless
---

### Post by romeosidvicious on 2016-05-07
I picked up this adapter on sale, as ASUS lists it as having Linux support and haven't been able to get it up and running properly. I'm using Ubuntu 16.04 and have been through pretty much every page on the USB-AC65 I can find. I can get the OS to sort of see it, with some oddities, but cannot achieve a decent connection. When Network Manager sees it, it doesn't see recognize it as having a name of any sort and iwconfig shows it as "unassociated"
```

##### iwconfig ##########################


enp2s0    no wireless extensions.


lo        no wireless extensions.


wlp4s0    IEEE 802.11bgn  ESSID:"Ermahgerd Wer Fer!"
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'Ermahgerd Wer Fer!' [AC1]>
          Bit Rate=1 Mb/s   Tx-Power=16 dBm
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-36 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:5  Invalid misc:55367   Missed beacon:0


enx9c5c8eb3f374  unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=5.745 GHz  Access Point: Not-Associated
          Sensitivity:0/0
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

This is using the 8812au module from the repos (4.4.0-22-generic), as suggested by some of the pages I've found thus far. I am hoping this is something simple that I've missed as I've managed to get it to be seen, to connect to a network (albeit slowly) instead of something that make this adapted useless. I've attached wirelessinfo.tar.gz and am more than willing to try just about anything at this point.

What I've tired:

Compiling the 8812au module from: [https://github.com/abperiasamy/rtl8812AU_8821AU_linux](https://github.com/abperiasamy/rtl8812AU_8821AU_linux) - Compiled but didn't play nice
Installing the module from the ASUS site - Broke a lot of stuff
Using the module from the repos (The newest module I've found so far) - Best results, though not quite working

Actually I can get this to connect, using the driver from the repos, but it doesn't stay connected. While it's connected I get over 4x the speed of the 2.4 ghz connection. In Network Manager it shows up without a name and while it's connected there is a rather constant message in the logs as follows
```
ay 07 16:50:09 htpc NetworkManager[746]: <info>  [1462657809.1893] sup-iface[0x24a2410,enx9c5c8eb3f374]: config: set interface ap_scan to 1May 07 16:50:09 htpc NetworkManager[746]: <info>  [1462657809.2023] device (enx9c5c8eb3f374): supplicant interface state: disconnected -> scanning
May 07 16:50:11 htpc NetworkManager[746]: <info>  [1462657811.3781] device (enx9c5c8eb3f374): supplicant interface state: scanning -> associating
May 07 16:50:11 htpc NetworkManager[746]: <info>  [1462657811.5049] device (enx9c5c8eb3f374): supplicant interface state: associating -> associated
May 07 16:50:11 htpc NetworkManager[746]: <info>  [1462657811.5148] device (enx9c5c8eb3f374): supplicant interface state: associated -> 4-way handshake
May 07 16:50:11 htpc NetworkManager[746]: <info>  [1462657811.5258] device (enx9c5c8eb3f374): supplicant interface state: 4-way handshake -> completed
May 07 16:50:11 htpc NetworkManager[746]: <info>  [1462657811.5259] device (enx9c5c8eb3f374): Activation: (wifi) Stage 2 of 5 (Device Configure) successful.  Connected to wirele
May 07 16:50:11 htpc NetworkManager[746]: <info>  [1462657811.5259] device (enx9c5c8eb3f374): state change: config -> ip-config (reason 'none') [50 70 0]
May 07 16:50:11 htpc NetworkManager[746]: <info>  [1462657811.5264] dhcp4 (enx9c5c8eb3f374): activation: beginning transaction (timeout in 45 seconds)
May 07 16:50:11 htpc NetworkManager[746]: <info>  [1462657811.5277] dhcp4 (enx9c5c8eb3f374): dhclient started with pid 24192
May 07 16:50:22 htpc NetworkManager[746]: <info>  [1462657822.2730]   address 192.168.1.66
May 07 16:50:22 htpc NetworkManager[746]: <info>  [1462657822.2730]   plen 24 (255.255.255.0)
May 07 16:50:22 htpc NetworkManager[746]: <info>  [1462657822.2730]   gateway 192.168.1.1
May 07 16:50:22 htpc NetworkManager[746]: <info>  [1462657822.2730]   server identifier 192.168.1.1
May 07 16:50:22 htpc NetworkManager[746]: <info>  [1462657822.2730]   lease time 86400
May 07 16:50:22 htpc NetworkManager[746]: <info>  [1462657822.2731]   hostname 'htpc'
May 07 16:50:22 htpc NetworkManager[746]: <info>  [1462657822.2731]   nameserver '8.8.8.8'
May 07 16:50:22 htpc NetworkManager[746]: <info>  [1462657822.2731]   nameserver '192.168.1.1'
May 07 16:50:22 htpc NetworkManager[746]: <info>  [1462657822.2731] dhcp4 (enx9c5c8eb3f374): state changed unknown -> bound
May 07 16:50:22 htpc NetworkManager[746]: <info>  [1462657822.2753] device (enx9c5c8eb3f374): state change: ip-config -> ip-check (reason 'none') [70 80 0]
May 07 16:50:22 htpc NetworkManager[746]: <info>  [1462657822.2759] device (enx9c5c8eb3f374): state change: ip-check -> secondaries (reason 'none') [80 90 0]
May 07 16:50:22 htpc NetworkManager[746]: <info>  [1462657822.2762] device (enx9c5c8eb3f374): state change: secondaries -> activated (reason 'none') [90 100 0]
May 07 16:50:22 htpc NetworkManager[746]: <warn>  [1462657822.3575] (wlan0): error getting signal strength: No such device
May 07 16:50:22 htpc NetworkManager[746]: <info>  [1462657822.3603] dns-mgr: Writing DNS information to /sbin/resolvconf
May 07 16:50:22 htpc NetworkManager[746]: <info>  [1462657822.3656] device (enx9c5c8eb3f374): Activation: successful, device activated.
May 07 16:50:26 htpc NetworkManager[746]: <warn>  [1462657826.9568] (wlan0): error getting signal strength: No such device
May 07 16:50:32 htpc NetworkManager[746]: <warn>  [1462657832.9605] (wlan0): error getting signal strength: No such device
May 07 16:50:38 htpc NetworkManager[746]: <warn>  [1462657838.9580] (wlan0): error getting signal strength: No such device
May 07 16:50:44 htpc NetworkManager[746]: <warn>  [1462657844.9559] (wlan0): error getting signal strength: No such device
```

Please see the attached screenshot for the NM without a device name

[ATTACH=CONFIG]268902[/ATTACH]

I think I'm close but I'm running out ideas. It seems to work but it drops pretty quickly and the repeating error seems to be an issue.

---

### Post by jeremy31 on 2016-05-07
If you can change the SSID's of the networks you want to connect to, change them to something without spaces and see if that works better

You might have issues from a Network Manager bug in 16.04, see if the Device name appears after ```
systemctl restart NetworkManager.service
```

---

### Post by romeosidvicious on 2016-05-07
And that solved, I didn't have to change network names at all, simply restarting NetworkManager did the trick! I don't know why I hadn't bothered to do that. I'm guessing that'll need to be done each reboot? I'll test it and figure that out. Otherwise everything appears to be working just fine. No more error messages in the logs, it seems to be staying connected just fine. I do feel a little stupid now to have overlooked that, it seems so simple. Considering what I do for a living, I ought to be ashamed.

---

### Post by jeremy31 on 2016-05-07
It will likely have to be restarted after reboot, possibly after sleep.  Did the ```
iwconfig
``` result change after the Network Manager restart?  It showed enx9c5c8eb3f374  before and I suspect that is now different

---

### Post by romeosidvicious on 2016-05-08
iwconfig doesn't change, although sometime overnight the adapter disappeared, I just had to rmmod and modprobe 8812au and restart network manager and it's all back up and running. Apparently I was a little hasty in marking this solved. It survived a reboot last night and still showed a proper name in NetworkManager. Here's what I found in the logs:
```
May 08 01:43:25 htpc wpa_supplicant[946]: enx9c5c8eb3f374: WPA: Group rekeying completed with d0:17:c2:5f:c8:64 [GTK=CCMP]May 08 02:43:24 htpc wpa_supplicant[946]: enx9c5c8eb3f374: WPA: Group rekeying completed with d0:17:c2:5f:c8:64 [GTK=CCMP]
May 08 03:43:24 htpc wpa_supplicant[946]: enx9c5c8eb3f374: WPA: Group rekeying completed with d0:17:c2:5f:c8:64 [GTK=CCMP]
May 08 04:43:23 htpc wpa_supplicant[946]: enx9c5c8eb3f374: WPA: Group rekeying completed with d0:17:c2:5f:c8:64 [GTK=CCMP]
May 08 05:43:20 htpc wpa_supplicant[946]: enx9c5c8eb3f374: WPA: Group rekeying completed with d0:17:c2:5f:c8:64 [GTK=CCMP]
May 08 06:43:19 htpc wpa_supplicant[946]: enx9c5c8eb3f374: WPA: Group rekeying completed with d0:17:c2:5f:c8:64 [GTK=CCMP]
May 08 07:05:08 htpc kernel: RTL871X: linked_status_chk(enx9c5c8eb3f374) disconnect or roaming
May 08 07:05:13 htpc wpa_supplicant[946]: enx9c5c8eb3f374: CTRL-EVENT-DISCONNECTED bssid=d0:17:c2:5f:c8:64 reason=0
May 08 07:05:13 htpc NetworkManager[760]: <info>  [1462709113.1548] device (enx9c5c8eb3f374): supplicant interface state: completed -> disconnected
May 08 07:05:13 htpc NetworkManager[760]: <info>  [1462709113.2523] device (enx9c5c8eb3f374): supplicant interface state: disconnected -> scanning
May 08 07:05:28 htpc NetworkManager[760]: <warn>  [1462709128.5446] device (enx9c5c8eb3f374): link timed out.
May 08 07:05:28 htpc NetworkManager[760]: <info>  [1462709128.5447] device (enx9c5c8eb3f374): state change: activated -> failed (reason 'ssid-not-found') [100 120 53]
May 08 07:05:28 htpc NetworkManager[760]: <warn>  [1462709128.5798] device (enx9c5c8eb3f374): Activation: failed for connection 'You kids get off my LAN'
May 08 07:05:28 htpc NetworkManager[760]: <info>  [1462709128.5815] device (enx9c5c8eb3f374): state change: failed -> disconnected (reason 'none') [120 30 0]
May 08 07:05:28 htpc kernel: IPv6: ADDRCONF(NETDEV_UP): enx9c5c8eb3f374: link is not ready
May 08 07:05:28 htpc avahi-daemon[724]: Withdrawing address record for fe80::83fb:19d0:8eb2:cbc5 on enx9c5c8eb3f374.
May 08 07:05:28 htpc avahi-daemon[724]: Leaving mDNS multicast group on interface enx9c5c8eb3f374.IPv6 with address fe80::83fb:19d0:8eb2:cbc5.
May 08 07:05:28 htpc avahi-daemon[724]: Interface enx9c5c8eb3f374.IPv6 no longer relevant for mDNS.
May 08 07:05:28 htpc avahi-daemon[724]: Withdrawing address record for 192.168.1.220 on enx9c5c8eb3f374.
May 08 07:05:28 htpc avahi-daemon[724]: Leaving mDNS multicast group on interface enx9c5c8eb3f374.IPv4 with address 192.168.1.220.
May 08 07:05:28 htpc avahi-daemon[724]: Interface enx9c5c8eb3f374.IPv4 no longer relevant for mDNS.
May 08 07:05:28 htpc wpa_supplicant[946]: enx9c5c8eb3f374: Reject scan trigger since one is already pending
May 08 07:05:28 htpc nm-dispatcher[32121]: req:1 'down' [enx9c5c8eb3f374]: new request (1 scripts)
May 08 07:05:28 htpc nm-dispatcher[32121]: req:1 'down' [enx9c5c8eb3f374]: start running ordered scripts...
May 08 07:05:29 htpc NetworkManager[760]: <info>  [1462709129.7791] device (enx9c5c8eb3f374): supplicant interface state: scanning -> inactive
```

Nothing else until I did the rmmod and modprobe, the machine is set not to sleep at all and there wasn't a reboot. I'm looking at various settings at this point. I will admit to not being well versed in wireless or USB, much less USB3, so I am a little out of my depth. I can troubleshoot MPI issues, Inifiniband, set up node to use NUMA and can't figure this out. It's leaving me feeling a little stupid. ;)

---

### Post by jeremy31 on 2016-05-08
Can you post ```
modinfo -p 8812au
```

---

### Post by romeosidvicious on 2016-05-08
```

rtw_ips_mode:The default IPS mode (int)
rtw_usb_rxagg_mode: (int)
rtw_qos_opt_enable: (int)
ifname:The default name to allocate for first interface (charp)
if2name:The default name to allocate for second interface (charp)
rtw_initmac: (charp)
rtw_channel_plan: (int)
rtw_special_rf_path: (int)
rtw_chip_version: (int)
rtw_rfintfs: (int)
rtw_lbkmode: (int)
rtw_network_mode: (int)
rtw_channel: (int)
rtw_mp_mode: (int)
rtw_wmm_enable: (int)
rtw_vrtl_carrier_sense: (int)
rtw_vcs_type: (int)
rtw_busy_thresh: (int)
rtw_ht_enable: (int)
rtw_bw_mode: (int)
rtw_ampdu_enable: (int)
rtw_rx_stbc: (int)
rtw_ampdu_amsdu: (int)
rtw_vht_enable: (int)
rtw_lowrate_two_xmit: (int)
rtw_rf_config: (int)
rtw_power_mgnt: (int)
rtw_smart_ps: (int)
rtw_low_power: (int)
rtw_wifi_spec: (int)
rtw_antdiv_cfg: (int)
rtw_antdiv_type: (int)
rtw_enusbss: (int)
rtw_hwpdn_mode: (int)
rtw_hwpwrp_detect: (int)
rtw_hw_wps_pbc: (int)
rtw_max_roaming_times:The max roaming times to try (uint)
rtw_mc2u_disable: (int)
rtw_80211d:Enable 802.11d mechanism (int)
rtw_notch_filter:0:Disable, 1:Enable, 2:Enable only for P2P (uint)
rtw_hiq_filter:0:allow all, 1:allow special, 2:deny all (uint)
rtw_adaptivity_en:0:disable, 1:enable, 2:auto (uint)
rtw_adaptivity_mode:0:normal, 1:carrier sense (uint)
rtw_nhm_en:0:disable, 1:enable (uint)
rtw_amplifier_type_2g:BIT3:2G ext-PA, BIT4:2G ext-LNA (uint)
rtw_amplifier_type_5g:BIT6:5G ext-PA, BIT7:5G ext-LNA (uint)
rtw_RFE_type:default init value:64 (uint)
rtw_TxBBSwing_2G:default init value:0xFF (uint)
rtw_TxBBSwing_5G:default init value:0xFF (uint)
rtw_tx_pwr_lmt_enable:0:Disable, 1:Enable, 2: Depend on efuse (int)
rtw_tx_pwr_by_rate:0:Disable, 1:Enable, 2: Depend on efuse (int)
rtw_phy_file_path:The path of phy parameter (charp)
rtw_load_phy_file:PHY File Bit Map (int)
rtw_decrypt_phy_file:Enable Decrypt PHY File (int)

```

Thanks so much for your help here jeremy!

---

### Post by romeosidvicious on 2016-05-08
Would loading the driver with "[COLOR=#000000][FONT=Ubuntu Mono]rtw_power_mgnt=0 [/FONT][/COLOR][COLOR=#8B8B8B][FONT=Monaco] [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]rtw_enusbss=0" possible help?[/FONT][/COLOR]

---

### Post by jeremy31 on 2016-05-08
Not a problem, now lets see what the parameters are currently set to ```
grep [[:alnum:]] /sys/module/8812au/parameters/*
```

---

### Post by jeremy31 on 2016-05-08
> **romeosidvicious said:**
> Would loading the driver with "[COLOR=#000000][FONT=Ubuntu Mono]rtw_power_mgnt=0 [/FONT][/COLOR][COLOR=#8B8B8B][FONT=Monaco] [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]rtw_enusbss=0" possible help?[/FONT][/COLOR]

That might be the fix as that is what the pvaret github rtl8723be module uses to disable power management and usb autosuspend

---

### Post by romeosidvicious on 2016-05-08
```

/sys/module/8812au/parameters/if2name:wlan%d
/sys/module/8812au/parameters/ifname:wlan%d
/sys/module/8812au/parameters/rtw_80211d:0
/sys/module/8812au/parameters/rtw_adaptivity_en:0
/sys/module/8812au/parameters/rtw_adaptivity_mode:0
/sys/module/8812au/parameters/rtw_ampdu_amsdu:0
/sys/module/8812au/parameters/rtw_ampdu_enable:1
/sys/module/8812au/parameters/rtw_amplifier_type_2g:0
/sys/module/8812au/parameters/rtw_amplifier_type_5g:0
/sys/module/8812au/parameters/rtw_antdiv_cfg:2
/sys/module/8812au/parameters/rtw_antdiv_type:0
/sys/module/8812au/parameters/rtw_busy_thresh:40
/sys/module/8812au/parameters/rtw_bw_mode:33
/sys/module/8812au/parameters/rtw_channel:1
/sys/module/8812au/parameters/rtw_channel_plan:89
/sys/module/8812au/parameters/rtw_chip_version:0
/sys/module/8812au/parameters/rtw_decrypt_phy_file:0
/sys/module/8812au/parameters/rtw_enusbss:0
/sys/module/8812au/parameters/rtw_hiq_filter:1
/sys/module/8812au/parameters/rtw_ht_enable:1
/sys/module/8812au/parameters/rtw_hwpdn_mode:2
/sys/module/8812au/parameters/rtw_hwpwrp_detect:0
/sys/module/8812au/parameters/rtw_hw_wps_pbc:1
/sys/module/8812au/parameters/rtw_initmac:(null)
/sys/module/8812au/parameters/rtw_ips_mode:0
/sys/module/8812au/parameters/rtw_lbkmode:0
/sys/module/8812au/parameters/rtw_load_phy_file:68
/sys/module/8812au/parameters/rtw_low_power:0
/sys/module/8812au/parameters/rtw_lowrate_two_xmit:1
/sys/module/8812au/parameters/rtw_max_roaming_times:2
/sys/module/8812au/parameters/rtw_mc2u_disable:0
/sys/module/8812au/parameters/rtw_mp_mode:0
/sys/module/8812au/parameters/rtw_network_mode:0
/sys/module/8812au/parameters/rtw_nhm_en:0
/sys/module/8812au/parameters/rtw_notch_filter:0
/sys/module/8812au/parameters/rtw_power_mgnt:0
/sys/module/8812au/parameters/rtw_qos_opt_enable:0
/sys/module/8812au/parameters/rtw_rf_config:5
/sys/module/8812au/parameters/rtw_RFE_type:64
/sys/module/8812au/parameters/rtw_rfintfs:2
/sys/module/8812au/parameters/rtw_rx_stbc:1
/sys/module/8812au/parameters/rtw_smart_ps:2
/sys/module/8812au/parameters/rtw_special_rf_path:0
/sys/module/8812au/parameters/rtw_TxBBSwing_2G:255
/sys/module/8812au/parameters/rtw_TxBBSwing_5G:255
/sys/module/8812au/parameters/rtw_tx_pwr_by_rate:0
/sys/module/8812au/parameters/rtw_tx_pwr_lmt_enable:0
/sys/module/8812au/parameters/rtw_usb_rxagg_mode:2
/sys/module/8812au/parameters/rtw_vcs_type:1
/sys/module/8812au/parameters/rtw_vht_enable:1
/sys/module/8812au/parameters/rtw_vrtl_carrier_sense:2
/sys/module/8812au/parameters/rtw_wifi_spec:0
/sys/module/8812au/parameters/rtw_wmm_enable:1

```

It appears that's already set, at least for the module, according to the last command you sent.

---

### Post by jeremy31 on 2016-05-08
Can you access router logs?

---

### Post by romeosidvicious on 2016-05-08
I should be able to , let me see what I can drum up

```

May  7 12:44:53 miniupnpd[1893]: upnp_event_process_notify: connect(192.168.1.45:2869): Connection timed out
May  7 12:44:53 miniupnpd[1893]: upnp_event_process_notify: connect(192.168.1.45:2869): Connection timed out
May  7 12:44:53 miniupnpd[1893]: upnp_event_process_notify: connect(192.168.1.45:2869): Connection timed out
May  7 16:48:55 rc_service: httpd 1274:notify_rc restart_net_and_phy
May  7 16:48:57 FTP Server: daemon is stoped
May  7 16:48:57 Samba Server: smb daemon is stoped
May  7 16:48:57 miniupnpd[1893]: shutting down MiniUPnPd
May  7 16:48:58 kernel: Attempt to kill tasklet from interrupt
May  7 16:49:04 wanduck exit: apply the nat_rules(/tmp/nat_rules_eth0_eth0)!
May  7 21:49:04 watchdog: restart httpd
May  7 21:49:04 rc_service: watchdog 261:notify_rc start_httpd
May  7 21:49:04 rc_service: waitting "restart_net_and_phy" via  ...
May  7 16:49:07 kernel: wl_module_init: passivemode set to 0x0
May  7 16:49:07 kernel: eth1: Broadcom BCM4331 802.11 Wireless Controller 6.30.163.2002 (r382208)
May  7 16:49:07 kernel: eth2: Broadcom BCM4360 802.11 Wireless Controller 6.30.163.2002 (r382208)
May  7 16:49:08 kernel: wlc_phy_cal_init_acphy: NOT Implemented
May  7 16:49:08 stop_nat_rules: apply the redirect_rules!
May  7 16:49:08 dnsmasq[2286]: warning: interface ppp1* does not currently exist
May  7 16:49:08 wan: mac clone: [wan0_hwaddr] == [A0:D3:C1:9C:24:B1]
May  7 16:49:08 start_nat_rules: apply the nat_rules(/tmp/nat_rules_eth0_eth0)!
May  7 16:49:08 wan: finish adding multi routes
May  7 16:49:08 rc_service: udhcpc 2298:notify_rc stop_upnp
May  7 16:49:08 rc_service: waitting "restart_net_and_phy" via  ...
May  7 16:49:12 RT-AC66U: start httpd
May  7 16:49:12 miniupnpd[2335]: version 1.9 started
May  7 16:49:12 miniupnpd[2335]: HTTP listening on port 48060
May  7 16:49:12 miniupnpd[2335]: Listening for NAT-PMP/PCP traffic on port 5351
May  7 16:49:12 Samba Server: daemon is started
May  7 16:49:13 RT-AC66U: start httpd
May  7 16:49:13 rc_service: udhcpc 2298:notify_rc start_upnp
May  7 16:49:13 rc_service: waitting "stop_upnp" via udhcpc ...
May  7 16:49:13 miniupnpd[2335]: shutting down MiniUPnPd
May  7 16:49:14 dhcp client: bound 73.32.63.20 via 73.32.56.1 during 267775 seconds.
May  7 16:49:15 miniupnpd[2379]: version 1.9 started
May  7 16:49:15 miniupnpd[2379]: HTTP listening on port 54560
May  7 16:49:15 miniupnpd[2379]: Listening for NAT-PMP/PCP traffic on port 5351
May  7 16:49:23 WAN Connection: WAN was restored.
May  7 16:49:51 nmbd[2355]: [2016/05/07 16:49:51, 0] nmbd/nmbd_become_lmb.c:become_local_master_stage2(392)
May  7 16:49:51 nmbd[2355]:   Samba name server RT-AC66U-C860 is now a local master browser for workgroup WORKGROUP on subnet 192.168.1.1
May  7 16:50:22 dnsmasq-dhcp[2286]: not using configured address 192.168.1.220 because it is leased to 00:c2:c6:53:ff:2a
May  7 16:51:43 rc_service: httpd 2334:notify_rc restart_net_and_phy
May  7 16:51:45 FTP Server: daemon is stoped
May  7 16:51:45 Samba Server: smb daemon is stoped
May  7 16:51:45 miniupnpd[2379]: shutting down MiniUPnPd
May  7 16:51:46 kernel: Attempt to kill tasklet from interrupt
May  7 16:51:49 wanduck exit: apply the nat_rules(/tmp/nat_rules_eth0_eth0)!
May  7 16:51:51 kernel: wl_module_init: passivemode set to 0x0
May  7 16:51:51 kernel: eth1: Broadcom BCM4331 802.11 Wireless Controller 6.30.163.2002 (r382208)
May  7 16:51:51 kernel: eth2: Broadcom BCM4360 802.11 Wireless Controller 6.30.163.2002 (r382208)
May  7 16:51:51 kernel: wlc_phy_cal_init_acphy: NOT Implemented
May  7 16:51:51 stop_nat_rules: apply the redirect_rules!
May  7 16:51:51 dnsmasq[2464]: warning: interface ppp1* does not currently exist
May  7 16:51:51 wan: mac clone: [wan0_hwaddr] == [A0:D3:C1:9C:24:B1]
May  7 16:51:51 start_nat_rules: apply the nat_rules(/tmp/nat_rules_eth0_eth0)!
May  7 16:51:52 wan: finish adding multi routes
May  7 16:51:52 rc_service: udhcpc 2476:notify_rc stop_upnp
May  7 16:51:52 rc_service: waitting "restart_net_and_phy" via  ...
May  7 16:51:55 RT-AC66U: start httpd
May  7 16:51:55 miniupnpd[2516]: version 1.9 started
May  7 16:51:55 miniupnpd[2516]: HTTP listening on port 48349
May  7 16:51:55 miniupnpd[2516]: Listening for NAT-PMP/PCP traffic on port 5351
May  7 16:51:56 Samba Server: daemon is started
May  7 16:51:57 rc_service: udhcpc 2476:notify_rc start_upnp
May  7 16:51:57 rc_service: waitting "stop_upnp" via udhcpc ...
May  7 16:51:57 miniupnpd[2516]: shutting down MiniUPnPd
May  7 16:51:58 dhcp client: bound 73.32.63.20 via 73.32.56.1 during 267611 seconds.
May  7 16:51:58 miniupnpd[2554]: version 1.9 started
May  7 16:51:58 miniupnpd[2554]: HTTP listening on port 60146
May  7 16:51:58 miniupnpd[2554]: Listening for NAT-PMP/PCP traffic on port 5351
May  7 16:52:01 WAN Connection: WAN was restored.
May  7 17:44:10 rc_service: httpd 2512:notify_rc restart_net_and_phy
May  7 17:44:12 FTP Server: daemon is stoped
May  7 17:44:12 Samba Server: smb daemon is stoped
May  7 17:44:12 miniupnpd[2554]: shutting down MiniUPnPd
May  7 17:44:13 kernel: Attempt to kill tasklet from interrupt
May  7 22:44:16 watchdog: restart httpd
May  7 22:44:16 rc_service: watchdog 261:notify_rc start_httpd
May  7 22:44:16 rc_service: waitting "restart_net_and_phy" via  ...
May  7 17:44:17 wanduck exit: apply the nat_rules(/tmp/nat_rules_eth0_eth0)!
May  7 17:44:18 kernel: wl_module_init: passivemode set to 0x0
May  7 17:44:18 kernel: eth1: Broadcom BCM4331 802.11 Wireless Controller 6.30.163.2002 (r382208)
May  7 17:44:18 kernel: eth2: Broadcom BCM4360 802.11 Wireless Controller 6.30.163.2002 (r382208)
May  7 17:44:18 kernel: wlc_phy_cal_init_acphy: NOT Implemented
May  7 17:44:19 stop_nat_rules: apply the redirect_rules!
May  7 17:44:19 dnsmasq[2659]: warning: interface ppp1* does not currently exist
May  7 17:44:19 wan: mac clone: [wan0_hwaddr] == [A0:D3:C1:9C:24:B1]
May  7 17:44:19 start_nat_rules: apply the nat_rules(/tmp/nat_rules_eth0_eth0)!
May  7 17:44:19 wan: finish adding multi routes
May  7 17:44:19 rc_service: udhcpc 2671:notify_rc stop_upnp
May  7 17:44:19 rc_service: waitting "restart_net_and_phy" via  ...
May  7 17:44:23 RT-AC66U: start httpd
May  7 17:44:23 miniupnpd[2708]: version 1.9 started
May  7 17:44:23 miniupnpd[2708]: HTTP listening on port 43013
May  7 17:44:23 miniupnpd[2708]: Listening for NAT-PMP/PCP traffic on port 5351
May  7 17:44:23 Samba Server: daemon is started
May  7 17:44:24 RT-AC66U: start httpd
May  7 17:44:24 rc_service: udhcpc 2671:notify_rc start_upnp
May  7 17:44:24 rc_service: waitting "stop_upnp" via udhcpc ...
May  7 17:44:24 miniupnpd[2708]: shutting down MiniUPnPd
May  7 17:44:25 dhcp client: bound 73.32.63.20 via 73.32.56.1 during 264464 seconds.
May  7 17:44:25 miniupnpd[2752]: version 1.9 started
May  7 17:44:25 miniupnpd[2752]: HTTP listening on port 32861
May  7 17:44:25 miniupnpd[2752]: Listening for NAT-PMP/PCP traffic on port 5351
May  7 17:44:39 WAN Connection: WAN was restored.
May  7 17:59:37 nmbd[2728]: [2016/05/07 17:59:37, 0] nmbd/nmbd_namequery.c:query_name_response(109)
May  7 17:59:37 nmbd[2728]:   query_name_response: Multiple (2) responses received for a query on subnet 192.168.1.1 for name WORKGROUP<1d>.
May  7 17:59:37 nmbd[2728]:   This response was from IP 192.168.1.109, reporting an IP address of 192.168.1.109.
May  7 18:35:06 nmbd[2728]: [2016/05/07 18:35:06, 0] nmbd/nmbd_become_lmb.c:become_local_master_stage2(392)
May  7 18:35:06 nmbd[2728]:   Samba name server RT-AC66U-C860 is now a local master browser for workgroup

```

Those don't appear to be much help, let me see if I can increase the level, there's literally nothing for today in the logs.

Jeremy,

I can telnet in and set the log level, it's currently set to 6, I am assuming that higher is more verbose. Is there anything else I'd want to change while I'm in there?

And apparently 6 is the highest log level available and it's not showing much at all. I'm tempted to flash dd-wrt but would really rather not until I have everything working stock.

---

### Post by romeosidvicious on 2016-05-10
It does appear to be some sort of sleep/power saving function. I am currently using "ping -i120" and haven't lost connection once since Sunday when we were talking about this. I currently have a script that restarts NetworkManager after boot and kicks off a background ping -i as a workaround. I'll be playing with USB power settings as it appears the settings for the card are all set properly and I've had issues with USB 3 power settings on other devices on another machine and that seems like a logical next step. If I manage a working solution without my silly startup script I'll be sure and post it here.

---

