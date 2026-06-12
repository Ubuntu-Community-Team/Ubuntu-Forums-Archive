---
title: "Intel Ultimate N WiFi Link 5300 wireless / Toshiba Satellite L550"
date: 2013-09-20
forum: Networking &amp; Wireless
---

### Post by beardo265 on 2013-09-20
to all the great ubuntu gods, geeks, gurus, experts, and all around good folks that are found around here.   having a horrible wireless disconnect issue, and after months of dealing with it, days of research, configuring, etc, it STILL goes on.

ANY help, suggestions, questions, comments, further reading, etc etc would be GREATLY appreciated. 

beyond real solutions, any workarounds, etc, would also be useful.  specifically, ways to reset the hardware without having to reboot would be useful

here are the details.

currently on a fresh install of ubuntu 12.04 LTS 64 bit  (had same problem with older install of 32 bit version of same)

running a toshiba satellite L550.   
using an intel Ultimate N WiFi Link 5300 wireless card,  driver=iwlwifi driverversion=3.8.0-30-generic
previously had in this system RTL8291SE card, replaced with above after similar disconnect problems, assuming the Intel chipset would have less compatibility issues.

what I get, is what seems to be random disconnects, and generally can't get connected again until after a reboot.   wireless will work well for anywhere from a few minutes to a few days, and work well under heavy load.  I'm not sure how to trigger it to disconnect.     sometimes, after a disconnect I can connect again by removing & adding the driver using modprobe, but rarely does that work, a reboot is most often required.

doesn't seem to be related to any power management or that type of thing... looks like it happens when system is idle, or active, on a/c power or on battery.

below is a syslog showing one of these disconnects.   it looks to me, like the card itself is shutting down, then can't be started up again?     I'm no expert on this stuff, obviously, so I could be wrong.

I've been assuming all along this is a driver/compatibility type issue.    Can anyone confirm this, or suggest otherwise?   hardware problem (bad port/motherboard? wireless card?)?  network? router? other?

could ubuntu 13.04 maybe help?

will post anything else that might be relevant or might help, please request. 

THANKS FOR READING!

```


Sep 19 23:59:26 tosh kernel: [  211.824248] iwlwifi 0000:06:00.0: fail to flush all tx fifo queuesSep 19 23:59:28 tosh kernel: [  213.823426] iwlwifi 0000:06:00.0: Error sending REPLY_ADD_STA: time out after 2000ms.
Sep 19 23:59:28 tosh kernel: [  213.823437] iwlwifi 0000:06:00.0: Current CMD queue read_ptr 182 write_ptr 188
Sep 19 23:59:28 tosh kernel: [  213.823446] wlan0: HW problem - can not stop rx aggregation for tid 0
Sep 19 23:59:30 tosh kernel: [  215.826600] iwlwifi 0000:06:00.0: Error sending REPLY_ADD_STA: time out after 2000ms.
Sep 19 23:59:30 tosh kernel: [  215.826609] iwlwifi 0000:06:00.0: Current CMD queue read_ptr 182 write_ptr 191
Sep 19 23:59:30 tosh kernel: [  215.826616] wlan0: failed to remove key (0, 00:22:2d:6b:e4:29) from hardware (-110)
Sep 19 23:59:32 tosh kernel: [  217.829691] iwlwifi 0000:06:00.0: Error sending REPLY_QOS_PARAM: time out after 2000ms.
Sep 19 23:59:32 tosh kernel: [  217.829699] iwlwifi 0000:06:00.0: Current CMD queue read_ptr 182 write_ptr 194
Sep 19 23:59:32 tosh kernel: [  217.829703] iwlwifi 0000:06:00.0: Failed to update QoS
Sep 19 23:59:34 tosh kernel: [  219.828810] iwlwifi 0000:06:00.0: Error sending REPLY_RXON: time out after 2000ms.
Sep 19 23:59:34 tosh kernel: [  219.828821] iwlwifi 0000:06:00.0: Current CMD queue read_ptr 182 write_ptr 197
Sep 19 23:59:34 tosh kernel: [  219.828829] iwlwifi 0000:06:00.0: Error clearing ASSOC_MSK on BSS (-110)
Sep 19 23:59:36 tosh kernel: [  221.828039] iwlwifi 0000:06:00.0: Error sending REPLY_RXON: time out after 2000ms.
Sep 19 23:59:36 tosh kernel: [  221.828048] iwlwifi 0000:06:00.0: Current CMD queue read_ptr 182 write_ptr 200
Sep 19 23:59:36 tosh kernel: [  221.828053] iwlwifi 0000:06:00.0: Error clearing ASSOC_MSK on BSS (-110)
Sep 19 23:59:38 tosh kernel: [  223.827213] iwlwifi 0000:06:00.0: Error sending REPLY_RXON: time out after 2000ms.
Sep 19 23:59:38 tosh kernel: [  223.827221] iwlwifi 0000:06:00.0: Current CMD queue read_ptr 182 write_ptr 203
Sep 19 23:59:38 tosh kernel: [  223.827226] iwlwifi 0000:06:00.0: Error clearing ASSOC_MSK on BSS (-110)
Sep 19 23:59:40 tosh kernel: [  225.826338] iwlwifi 0000:06:00.0: Error sending REPLY_ADD_STA: time out after 2000ms.
Sep 19 23:59:40 tosh kernel: [  225.826349] iwlwifi 0000:06:00.0: Current CMD queue read_ptr 182 write_ptr 205
Sep 19 23:59:40 tosh kernel: [  225.826368] wlan0: failed to remove key (2, ff:ff:ff:ff:ff:ff) from hardware (-110)
Sep 19 23:59:42 tosh kernel: [  227.833434] iwlwifi 0000:06:00.0: fail to flush all tx fifo queues
Sep 19 23:59:44 tosh kernel: [  229.832567] iwlwifi 0000:06:00.0: Error sending REPLY_RXON: time out after 2000ms.
Sep 19 23:59:44 tosh kernel: [  229.832581] iwlwifi 0000:06:00.0: Current CMD queue read_ptr 182 write_ptr 206
Sep 19 23:59:44 tosh kernel: [  229.832591] iwlwifi 0000:06:00.0: Error clearing ASSOC_MSK on BSS (-110)
Sep 19 23:59:46 tosh NetworkManager[1007]: <info> (wlan0): roamed from BSSID 00:22:2D:6B:E4:29 (NETWORK) to (none) ((none))
Sep 19 23:59:46 tosh wpa_supplicant[1258]: CTRL-EVENT-DISCONNECTED bssid=00:22:2d:6b:e4:29 reason=4
Sep 19 23:59:46 tosh kernel: [  231.831720] iwlwifi 0000:06:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
Sep 19 23:59:46 tosh kernel: [  231.831728] iwlwifi 0000:06:00.0: Current CMD queue read_ptr 182 write_ptr 207
Sep 19 23:59:46 tosh kernel: [  231.831761] cfg80211: Calling CRDA for country: US
Sep 19 23:59:46 tosh NetworkManager[1007]: <info> (wlan0): supplicant interface state: completed -> disconnected
Sep 19 23:59:48 tosh wpa_supplicant[1258]: Failed to initiate AP scan.
Sep 19 23:59:48 tosh kernel: [  233.930828] iwlwifi 0000:06:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
Sep 19 23:59:48 tosh kernel: [  233.930838] iwlwifi 0000:06:00.0: Current CMD queue read_ptr 182 write_ptr 208
Sep 19 23:59:51 tosh wpa_supplicant[1258]: Failed to initiate AP scan.
Sep 19 23:59:51 tosh kernel: [  236.929580] iwlwifi 0000:06:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
Sep 19 23:59:51 tosh kernel: [  236.929594] iwlwifi 0000:06:00.0: Current CMD queue read_ptr 182 write_ptr 209
Sep 19 23:59:54 tosh wpa_supplicant[1258]: Failed to initiate AP scan.
Sep 19 23:59:54 tosh kernel: [  239.928333] iwlwifi 0000:06:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
Sep 19 23:59:54 tosh kernel: [  239.928345] iwlwifi 0000:06:00.0: Current CMD queue read_ptr 182 write_ptr 210
Sep 19 23:59:57 tosh wpa_supplicant[1258]: Failed to initiate AP scan.
Sep 19 23:59:57 tosh kernel: [  242.927087] iwlwifi 0000:06:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
Sep 19 23:59:57 tosh kernel: [  242.927098] iwlwifi 0000:06:00.0: Current CMD queue read_ptr 182 write_ptr 211
Sep 20 00:00:00 tosh wpa_supplicant[1258]: Failed to initiate AP scan.
Sep 20 00:00:00 tosh kernel: [  245.925774] iwlwifi 0000:06:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
Sep 20 00:00:00 tosh kernel: [  245.925785] iwlwifi 0000:06:00.0: Current CMD queue read_ptr 182 write_ptr 212
Sep 20 00:00:01 tosh wpa_supplicant[1258]: Failed to initiate AP scan.
Sep 20 00:00:01 tosh kernel: [  246.926939] iwlwifi 0000:06:00.0: No space in command queue
Sep 20 00:00:01 tosh kernel: [  246.926955] iwlwifi 0000:06:00.0: Restarting adapter queue is full
Sep 20 00:00:01 tosh kernel: [  246.926975] iwlwifi 0000:06:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
Sep 20 00:00:02 tosh NetworkManager[1007]: <warn> (wlan0): link timed out.
Sep 20 00:00:02 tosh NetworkManager[1007]: <info> (wlan0): device state change: activated -> disconnected (reason 'supplicant-timeout') [100 30 11]
Sep 20 00:00:02 tosh NetworkManager[1007]: <info> (wlan0): deactivating device (reason 'supplicant-timeout') [11]
ep 20 00:00:02 tosh kernel: [  246.946318] ------------[ cut here ]------------
Sep 20 00:00:02 tosh kernel: [  246.946355] WARNING: at /build/buildd/linux-lts-raring-3.8.0/drivers/net/wireless/iwlwifi/iwl-io.c:150 iwl_grab_nic_access.part.1+0x6f/0x8e [iwl$
Sep 20 00:00:02 tosh kernel: [  246.946359] Hardware name: Satellite L550
Sep 20 00:00:02 tosh kernel: [  246.946362] Timeout waiting for hardware access (CSR_GP_CNTRL 0xffffffff)
Sep 20 00:00:02 tosh kernel: [  246.946365] Modules linked in: bnep(F) rfcomm(F) bluetooth(F) parport_pc(F) ppdev(F) ses(F) enclosure(F) snd_hda_codec_hdmi(F) snd_hda_codec_rea$
Sep 20 00:00:02 tosh kernel: [  246.946433] Pid: 205, comm: kworker/u:2 Tainted: GF            3.8.0-30-generic #44~precise1-Ubuntu
Sep 20 00:00:02 tosh kernel: [  246.946436] Call Trace:
Sep 20 00:00:02 tosh kernel: [  246.946452]  [<ffffffff81059b0f>] warn_slowpath_common+0x7f/0xc0
Sep 20 00:00:02 tosh kernel: [  246.946459]  [<ffffffff81059c06>] warn_slowpath_fmt+0x46/0x50
Sep 20 00:00:02 tosh kernel: [  246.946477]  [<ffffffffa0155697>] iwl_grab_nic_access.part.1+0x6f/0x8e [iwlwifi]
Sep 20 00:00:02 tosh kernel: [  246.946490]  [<ffffffffa013f78e>] iwl_grab_nic_access+0x2e/0x30 [iwlwifi]
Sep 20 00:00:02 tosh kernel: [  246.946502]  [<ffffffffa013fd56>] iwl_write_prph+0x46/0xf0 [iwlwifi]
Sep 20 00:00:02 tosh kernel: [  246.946517]  [<ffffffffa014998a>] iwl_pcie_tx_stop+0x4a/0x140 [iwlwifi]
Sep 20 00:00:02 tosh kernel: [  246.946533]  [<ffffffffa014caea>] iwl_trans_pcie_stop_device+0xda/0x4f0 [iwlwifi]
Sep 20 00:00:02 tosh kernel: [  246.946548]  [<ffffffffa02ccbda>] iwl_down+0x21a/0x320 [iwldvm]
Sep 20 00:00:02 tosh kernel: [  246.946559]  [<ffffffffa02ccd2f>] iwlagn_prepare_restart+0x4f/0xd0 [iwldvm]
Sep 20 00:00:02 tosh kernel: [  246.946567]  [<ffffffff8109c400>] ? idle_balance+0xd0/0x2f0
Sep 20 00:00:02 tosh kernel: [  246.946579]  [<ffffffffa02cd5b2>] iwl_bg_restart+0x52/0xe0 [iwldvm]
Sep 20 00:00:02 tosh kernel: [  246.946585]  [<ffffffff81078ce1>] process_one_work+0x141/0x490
Sep 20 00:00:02 tosh kernel: [  246.946592]  [<ffffffff81079ca8>] worker_thread+0x168/0x400
Sep 20 00:00:02 tosh kernel: [  246.946597]  [<ffffffff81079b40>] ? manage_workers+0x120/0x120
Sep 20 00:00:02 tosh kernel: [  246.946605]  [<ffffffff8107f1b0>] kthread+0xc0/0xd0
Sep 20 00:00:02 tosh kernel: [  246.946611]  [<ffffffff8107f0f0>] ? flush_kthread_worker+0xb0/0xb0
Sep 20 00:00:02 tosh kernel: [  246.946619]  [<ffffffff816fcaec>] ret_from_fork+0x7c/0xb0
Sep 20 00:00:02 tosh kernel: [  246.946625]  [<ffffffff8107f0f0>] ? flush_kthread_worker+0xb0/0xb0
Sep 20 00:00:02 tosh kernel: [  246.946629] ---[ end trace 1e16b8f3b796db5d ]---
Sep 20 00:00:02 tosh kernel: [  247.303609] ieee80211 phy0: Hardware restart was requested
Sep 20 00:00:02 tosh kernel: [  247.303672] iwlwifi 0000:06:00.0: L1 Disabled; Enabling L0S
Sep 20 00:00:02 tosh kernel: [  247.360071] iwlwifi 0000:06:00.0: Radio type=0x0-0x2-0x0
Sep 20 00:00:03 tosh NetworkManager[1007]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 1598
Sep 20 00:00:08 tosh kernel: [  253.034799] iwlwifi 0000:06:00.0: Failed to load firmware chunk!
Sep 20 00:00:08 tosh kernel: [  253.034807] iwlwifi 0000:06:00.0: Could not load the [0] uCode section
Sep 20 00:00:08 tosh kernel: [  253.034813] iwlwifi 0000:06:00.0: Failed to start RT ucode: -110
Sep 20 00:00:08 tosh avahi-daemon[934]: Withdrawing address record for fe80::221:6aff:fea0:e6fe on wlan0.
Sep 20 00:00:08 tosh avahi-daemon[934]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::221:6aff:fea0:e6fe.
Sep 20 00:00:08 tosh avahi-daemon[934]: Interface wlan0.IPv6 no longer relevant for mDNS.
Sep 20 00:00:08 tosh wpa_supplicant[1258]: Failed to initiate AP scan.
Sep 20 00:00:08 tosh avahi-daemon[934]: Withdrawing address record for 192.168.0.10 on wlan0.
Sep 20 00:00:08 tosh avahi-daemon[934]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.10.
Sep 20 00:00:08 tosh avahi-daemon[934]: Interface wlan0.IPv4 no longer relevant for mDNS.
Sep 20 00:00:08 tosh NetworkManager[1007]: <warn> DNS: plugin dnsmasq update failed
Sep 20 00:00:08 tosh NetworkManager[1007]: <info> (wlan0): removing resolv.conf from /sbin/resolvconf
Sep 20 00:00:08 tosh kernel: [  253.408074] iwlwifi 0000:06:00.0: Unable to initialize device.
Sep 20 00:00:08 tosh kernel: [  253.408180] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Sep 20 00:00:08 tosh kernel: [  253.408599] iwlwifi 0000:06:00.0: Request scan called when driver not ready.
Sep 20 00:00:08 tosh dnsmasq[1618]: setting upstream servers from DBus
Sep 20 00:00:08 tosh dbus[910]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Sep 20 00:00:08 tosh NetworkManager[1007]: <info> Auto-activating connection 'NETWORK'.
Sep 20 00:00:08 tosh NetworkManager[1007]: <info> Activation (wlan0) starting connection 'NETWORK'
Sep 20 00:00:08 tosh NetworkManager[1007]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Sep 20 00:00:08 tosh NetworkManager[1007]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Sep 20 00:00:08 tosh NetworkManager[1007]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Sep 20 00:00:08 tosh NetworkManager[1007]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Sep 20 00:00:08 tosh NetworkManager[1007]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Sep 20 00:00:08 tosh NetworkManager[1007]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Sep 20 00:00:08 tosh NetworkManager[1007]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Sep 20 00:00:08 tosh NetworkManager[1007]: <info> Activation (wlan0/wireless): access point 'NETWORK' has security, but secrets are required.
Sep 20 00:00:08 tosh NetworkManager[1007]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Sep 20 00:00:08 tosh NetworkManager[1007]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Sep 20 00:00:08 tosh NetworkManager[1007]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Sep 20 00:00:08 tosh NetworkManager[1007]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Sep 20 00:00:08 tosh NetworkManager[1007]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Sep 20 00:00:08 tosh dbus[910]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Sep 20 00:00:08 tosh NetworkManager[1007]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Sep 20 00:00:08 tosh NetworkManager[1007]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Sep 20 00:00:08 tosh NetworkManager[1007]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Sep 20 00:00:08 tosh NetworkManager[1007]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Sep 20 00:00:08 tosh NetworkManager[1007]: <info> Activation (wlan0/wireless): connection 'NETWORK' has security, and secrets exist.  No new secrets needed.
Sep 20 00:00:08 tosh NetworkManager[1007]: <info> Config: added 'ssid' value 'NETWORK'
Sep 20 00:00:08 tosh NetworkManager[1007]: <info> Config: added 'scan_ssid' value '1'
Sep 20 00:00:08 tosh NetworkManager[1007]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Sep 20 00:00:08 tosh NetworkManager[1007]: <info> Config: added 'auth_alg' value 'OPEN'
Sep 20 00:00:08 tosh NetworkManager[1007]: <info> Config: added 'psk' value '<omitted>'
Sep 20 00:00:08 tosh NetworkManager[1007]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Sep 20 00:00:08 tosh NetworkManager[1007]: <info> Config: set interface ap_scan to 1
Sep 20 00:00:09 tosh wpa_supplicant[1258]: Failed to initiate AP scan.
Sep 20 00:00:09 tosh kernel: [  254.409502] iwlwifi 0000:06:00.0: Request scan called when driver not ready.
Sep 20 00:00:10 tosh wpa_supplicant[1258]: Failed to initiate AP scan.
Sep 20 00:00:10 tosh kernel: [  255.410514] iwlwifi 0000:06:00.0: Request scan called when driver not ready.
Sep 20 00:00:11 tosh wpa_supplicant[1258]: Failed to initiate AP scan.
---- THIS REPEATS 20-30 times ---------
Sep 20 00:01:09 tosh NetworkManager[1007]: <warn> Activation (wlan0/wireless): association took too long.
Sep 20 00:01:09 tosh NetworkManager[1007]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Sep 20 00:01:09 tosh NetworkManager[1007]: <warn> Activation (wlan0/wireless): asking for new secrets
Sep 20 00:01:09 tosh NetworkManager[1007]: <info> (wlan0): supplicant interface state: disconnected -> inactive
Sep 20 00:01:13 tosh NetworkManager[1007]: get_secret_flags: assertion `is_secret_prop (setting, secret_name, error)' failed
Sep 20 00:01:13 tosh NetworkManager[1007]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Sep 20 00:01:13 tosh NetworkManager[1007]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Sep 20 00:01:13 tosh NetworkManager[1007]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Sep 20 00:01:13 tosh NetworkManager[1007]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Sep 20 00:01:13 tosh NetworkManager[1007]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Sep 20 00:01:13 tosh NetworkManager[1007]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Sep 20 00:01:13 tosh NetworkManager[1007]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Sep 20 00:01:13 tosh NetworkManager[1007]: <info> Activation (wlan0/wireless): connection 'NETWORK' has security, and secrets exist.  No new secrets needed.
Sep 20 00:01:13 tosh NetworkManager[1007]: <info> Config: added 'ssid' value 'NETWORK'
Sep 20 00:01:13 tosh NetworkManager[1007]: <info> Config: added 'scan_ssid' value '1'
Sep 20 00:01:13 tosh NetworkManager[1007]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Sep 20 00:01:13 tosh NetworkManager[1007]: <info> Config: added 'auth_alg' value 'OPEN'
Sep 20 00:01:13 tosh NetworkManager[1007]: <info> Config: added 'psk' value '<omitted>'
Sep 20 00:01:13 tosh NetworkManager[1007]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Sep 20 00:01:13 tosh NetworkManager[1007]: <info> Config: set interface ap_scan to 1
Sep 20 00:01:13 tosh wpa_supplicant[1258]: Failed to initiate AP scan.
Sep 20 00:01:13 tosh kernel: [  318.475797] iwlwifi 0000:06:00.0: Request scan called when driver not ready.
Sep 20 00:01:14 tosh wpa_supplicant[1258]: Failed to initiate AP scan.
Sep 20 00:01:16 tosh wpa_supplicant[1258]: Failed to initiate AP scan.
Sep 20 00:01:16 tosh kernel: [  321.478776] iwlwifi 0000:06:00.0: Request scan called when driver not ready.
Sep 20 00:01:17 tosh wpa_supplicant[1258]: Failed to initiate AP scan.
Sep 20 00:01:17 tosh kernel: [  322.479718] iwlwifi 0000:06:00.0: Request scan called when driver not ready.
Sep 20 00:01:18 tosh wpa_supplicant[1258]: Failed to initiate AP scan.
Sep 20 00:01:18 tosh kernel: [  323.479751] iwlwifi 0000:06:00.0: Request scan called when driver not ready.
Sep 20 00:01:19 tosh wpa_supplicant[1258]: Failed to initiate AP scan.
Sep 20 00:01:19 tosh kernel: [  324.480766] iwlwifi 0000:06:00.0: Request scan called when driver not ready.
Sep 20 00:01:20 tosh wpa_supplicant[1258]: Failed to initiate AP scan.
Sep 20 00:01:20 tosh kernel: [  325.481782] iwlwifi 0000:06:00.0: Request scan called when driver not ready.



```

---

### Post by tgalati4 on 2013-09-20
Only mere mortals read these forums, so you will have to accept less than divine advice.

Errors like *failed to load firmware* would point to a hardware problem.

The fact that you have tried 32-bit and 64-bit distros and 2 different wireless cards with similar results.  I presume that the wireless card is on a minipci slot under the RAM or harddisk?  Perhaps there is dirt, or a bent pin on the slot?  Pull the wireless card, blow out any dust, and inspect with a bright light and magnifying glass.  I suspect a bad connector that is causing an intermittent wireless connection.

If all of that checks out, then I suspect a poor solder connection of the connector slot to the motherboard, or a flexed/cracked motherboard that affects that circuit.

Does the laptop work OK using a wired connection?  Any hard freezes?  Do you get several months of uptime while running linux?

---

### Post by Hadaka on 2013-09-20
Hi, give this a try..
```
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi 11n_disable=1
```
DONT boot, see if it remains stable,no disconnects
report back and we can write one file to make it permanent.
thanks.

---

### Post by beardo265 on 2013-09-20
> **tgalati4 said:**
> Only mere mortals read these forums, so you will have to accept less than divine advice.

Errors like *failed to load firmware* would point to a hardware problem.

The fact that you have tried 32-bit and 64-bit distros and 2 different wireless cards with similar results.  I presume that the wireless card is on a minipci slot under the RAM or harddisk?  Perhaps there is dirt, or a bent pin on the slot?  Pull the wireless card, blow out any dust, and inspect with a bright light and magnifying glass.  I suspect a bad connector that is causing an intermittent wireless connection.

If all of that checks out, then I suspect a poor solder connection of the connector slot to the motherboard, or a flexed/cracked motherboard that affects that circuit.

Does the laptop work OK using a wired connection?  Any hard freezes?  Do you get several months of uptime while running linux?

Mortal or divine, I'll take any help/suggestions that come my way.

but yes.. mini pci slot, (actually half size mini pci e), but located under the keyboard up, not with the ram or harddisk.   ... have inspected it just now, and previously, and see nothing out of the ordinary.  nothing that looks bent or damaged, no dirt/dust.      blew it out with duster anyway, re-installed.

one note, have only tested this one card on 64 bit thus far.  the first one, I replaced due to many reports/threads of disconnect & driver issues, so I've not yet brought it back into the testing.   will put it on the list though.

no other issues with the system to speak of, no freezes, and while on wired connection, no issues (however 99% of the time I'm having to use wireless, so not tested much).    uptime not measured in months, only because I'm frequently rebooting to get my wireless back.  generally several reboots/day.    will try to run long enough test on just a wired connection, but will be difficult 

one thing that I find odd, when you mention the "*failed to load firmware" *part, to me, it looks like for some reason it's decided to re-start or disable/enable the hardware at that point, but it just didn't come back up.   or would you think it's failing or not responding before that?

waiting now until it fails again, to move on to next test.

---

### Post by mörgæs on 2013-09-20
Changed the title to a more informative one.

---

### Post by tgalati4 on 2013-09-20
The Linux Kernel was written by Gods, and as a result it expects perfect hardware.  When hardware is not perfect, you get a variety of weird, somewhat reverent, somewhat relevant (to see if you were paying attention), errors that may or may not be related to the hardware fault.  So, you have to take the error messages with a grain of salt.

Because of the variety of error messages, it appears to be a hardware error.  Which is why you want to test for uptime on a wired cable for a few months.  That's right, a few months.  If your machine doesn't stay up for a few months at a time, then you might have a motherboard issue that is affecting your wireless connectivity.

Wireless chips get hot under use.  Perhaps you can put your finger on it while the keyboard is removed.  Use a USB keyboard instead and see if the chip gets hot during use.  If it does, then you might have a wireless card problem.  Although it would be unusual to have two cards go bad.

I have had pcmcia wireless cards go bad, the chip gets hot and acts strange.  Only a reboot, or pulling the card (which allows it to cool down) will revive it.  Not a useful way to work.

If the keyboard presses against the card, it's possible that flexing of the keyboard has weakened the socket.  Try putting a little pressure on it with your finger and see if behaves differently. 17" laptops tend to flex more than 15" and smaller and tend to develop strange problems as a result.

But first do as Hadaka suggests, turn off N mode and see it changes the wireless behavior.

---

