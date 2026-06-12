---
title: "Netgear WMA1000m on Ubuntu 13.10"
date: 2013-10-27
forum: Networking &amp; Wireless
---

### Post by c0mputerguy on 2013-10-27
I'm trying to get a Netgear WMA1000m usb adapter to work on 13.10. Ndiswrapper was working until I updated, but now it doesn't work at all. I can't get any other drivers to work properly with it. The rtl8192cu driver will detect it and allow me (after repeated attempts) to connect to my network, but it drops the connection every few seconds and makes it unusable. Here is the output of dmesg while it is "connected" to my network:

```
[403485.912037] usb 1-8: new high-speed USB device number 7 using ehci-pci
[403486.045845] usb 1-8: New USB device found, idVendor=0846, idProduct=9041
[403486.045856] usb 1-8: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[403486.045862] usb 1-8: Product: 802.11n WLAN Adapter
[403486.045868] usb 1-8: Manufacturer: Realtek
[403486.045875] usb 1-8: SerialNumber: 00e04c000001
[403486.047345] rtl8192cu: Chip version 0x10
[403486.129829] rtl8192cu: MAC address: c4:3d:c7:7f:1f:09
[403486.129840] rtl8192cu: Board Type 0
[403486.130068] rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
[403486.130132] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw.bin
[403486.130515] ieee80211 phy3: Selected rate control algorithm 'rtl_rc'
[403486.131712] rtlwifi: wireless switch is on
[403486.207612] rtl8192cu: MAC auto ON okay!
[403486.272337] rtl8192cu: Tx queue select: 0x05
[403486.629890] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[403488.264866] wlan0: authenticate with 58:6d:8f:05:0a:6a
[403488.288927] wlan0: send auth to 58:6d:8f:05:0a:6a (try 1/3)
[403488.338016] wlan0: authenticated
[403488.345078] wlan0: associate with 58:6d:8f:05:0a:6a (try 1/3)
[403488.359174] wlan0: RX AssocResp from 58:6d:8f:05:0a:6a (capab=0x411 status=0 aid=2)
[403488.359300] wlan0: associated
[403488.360158] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[403488.620043] ------------[ cut here ]------------
[403488.620061] WARNING: CPU: 0 PID: 9659 at /build/buildd/linux-3.11.0/kernel/workqueue.c:1378 __queue_work+0x255/0x2b0()
[403488.620065] Modules linked in: rtl8192cu(OF) rtl8192c_common(OF) rtlwifi(OF) mac80211(OF) cfg80211(OF) compat(OF) arc4(F) pci_stub vboxpci(OF) vboxnetadp(OF) vboxnetflt(OF) vboxdrv(OF) bnep rfcomm bluetooth binfmt_misc(F) gpio_ich ppdev(F) ext2(F) microcode(F) i915 snd_intel8x0 snd_ac97_codec psmouse(F) serio_raw(F) ac97_bus snd_pcm(F) snd_page_alloc(F) snd_seq_midi(F) snd_seq_midi_event(F) snd_rawmidi(F) snd_seq(F) snd_seq_device(F) snd_timer(F) snd(F) lpc_ich video(F) drm_kms_helper soundcore(F) wmi drm i2c_algo_bit parport_pc(F) mac_hid smsc47b397 lp(F) parport(F) tg3 ptp(F) pps_core(F) floppy(F) [last unloaded: rtl8192c_common]
[403488.620144] CPU: 0 PID: 9659 Comm: kworker/0:0 Tainted: GF       W  O 3.11.0-12-generic #19-Ubuntu
[403488.620147] Hardware name: Hewlett-Packard HP Compaq dc7100 CMT(PJ360UA)/0968h, BIOS 786C1 v01.05 06/16/2004
[403488.620158] Workqueue: rtl92c_usb rtl_watchdog_wq_callback [rtlwifi]
[403488.620162]  00000000 00000000 ef7c7e18 c162566b 00000000 ef7c7e48 c105273e c17f5fb8
[403488.620172]  00000000 000025bb c17f6c24 00000562 c10687b5 c10687b5 f541f900 f6ff2500
[403488.620181]  00000001 ef7c7e58 c1052802 00000009 00000000 ef7c7e8c c10687b5 f0006700
[403488.620190] Call Trace:
[403488.620201]  [<c162566b>] dump_stack+0x41/0x52
[403488.620207]  [<c105273e>] warn_slowpath_common+0x7e/0xa0
[403488.620212]  [<c10687b5>] ? __queue_work+0x255/0x2b0
[403488.620217]  [<c10687b5>] ? __queue_work+0x255/0x2b0
[403488.620222]  [<c1052802>] warn_slowpath_null+0x22/0x30
[403488.620226]  [<c10687b5>] __queue_work+0x255/0x2b0
[403488.620231]  [<c10689bf>] queue_work_on+0x4f/0x60
[403488.620238]  [<f892535a>] rtl_watchdog_wq_callback+0x26a/0x3e0 [rtlwifi]
[403488.620243]  [<c162984e>] ? __schedule+0x35e/0x790
[403488.620249]  [<c1069f88>] process_one_work+0x118/0x380
[403488.620254]  [<c106ad61>] worker_thread+0x101/0x340
[403488.620259]  [<c106ac60>] ? manage_workers.isra.26+0x250/0x250
[403488.620264]  [<c1070164>] kthread+0x94/0xa0
[403488.620268]  [<c1070000>] ? __kthread_parkme+0x60/0x70
[403488.620274]  [<c1632c37>] ret_from_kernel_thread+0x1b/0x28
[403488.620278]  [<c10700d0>] ? kthread_create_on_node+0xc0/0xc0
[403488.620282] ---[ end trace d8b09e7df87a5d3a ]---
[403496.641081] rtlwifi:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[403496.641101] wlan0: Connection to AP 58:6d:8f:05:0a:6a lost
[403496.661049] cfg80211: Calling CRDA to update world regulatory domain
[403496.667650] cfg80211: World regulatory domain updated:
[403496.667659] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[403496.667663] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[403496.667666] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[403496.667669] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[403496.667672] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[403496.667675] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[403497.472860] wlan0: authenticate with 58:6d:8f:05:0a:6a
[403497.485308] wlan0: send auth to 58:6d:8f:05:0a:6a (try 1/3)
[403497.588033] wlan0: send auth to 58:6d:8f:05:0a:6a (try 2/3)
[403497.692026] wlan0: send auth to 58:6d:8f:05:0a:6a (try 3/3)
[403497.796025] wlan0: authentication with 58:6d:8f:05:0a:6a timed out
[403504.380940] wlan0: authenticate with 58:6d:8f:05:0a:6a
[403504.402059] wlan0: send auth to 58:6d:8f:05:0a:6a (try 1/3)
[403504.406749] wlan0: authenticated
[403504.408049] wlan0: associate with 58:6d:8f:05:0a:6a (try 1/3)
[403504.432222] wlan0: RX AssocResp from 58:6d:8f:05:0a:6a (capab=0x411 status=0 aid=2)
[403504.432283] wlan0: associated
[403510.665718] rtlwifi:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[403510.665746] wlan0: Connection to AP 58:6d:8f:05:0a:6a lost
[403510.696175] cfg80211: Calling CRDA to update world regulatory domain
[403510.703440] cfg80211: World regulatory domain updated:
[403510.703448] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[403510.703452] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[403510.703455] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[403510.703458] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[403510.703461] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[403510.703464] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[403511.504829] wlan0: authenticate with 58:6d:8f:05:0a:6a
[403511.518308] wlan0: send auth to 58:6d:8f:05:0a:6a (try 1/3)
[403511.620038] wlan0: send auth to 58:6d:8f:05:0a:6a (try 2/3)
[403511.724059] wlan0: send auth to 58:6d:8f:05:0a:6a (try 3/3)
[403511.828024] wlan0: authentication with 58:6d:8f:05:0a:6a timed out
[403518.385609] wlan0: authenticate with 58:6d:8f:05:0a:6a
[403518.414878] wlan0: send auth to 58:6d:8f:05:0a:6a (try 1/3)
[403518.496307] wlan0: authenticated
[403518.500096] wlan0: associate with 58:6d:8f:05:0a:6a (try 1/3)
[403518.530603] wlan0: RX AssocResp from 58:6d:8f:05:0a:6a (capab=0x411 status=0 aid=2)
[403518.530671] wlan0: associated
[403524.697260] rtlwifi:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[403524.697287] wlan0: Connection to AP 58:6d:8f:05:0a:6a lost
[403524.741193] cfg80211: Calling CRDA to update world regulatory domain
[403524.749833] cfg80211: World regulatory domain updated:
[403524.749848] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[403524.749853] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[403524.749858] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[403524.749862] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[403524.749867] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[403524.749871] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[403525.544795] wlan0: authenticate with 58:6d:8f:05:0a:6a
[403525.570705] wlan0: send auth to 58:6d:8f:05:0a:6a (try 1/3)
[403525.672067] wlan0: send auth to 58:6d:8f:05:0a:6a (try 2/3)
[403525.776021] wlan0: send auth to 58:6d:8f:05:0a:6a (try 3/3)
[403525.880019] wlan0: authentication with 58:6d:8f:05:0a:6a timed out
[403532.444922] wlan0: authenticate with 58:6d:8f:05:0a:6a
[403532.457683] wlan0: send auth to 58:6d:8f:05:0a:6a (try 1/3)
[403532.482348] wlan0: authenticated
[403532.484058] wlan0: associate with 58:6d:8f:05:0a:6a (try 1/3)
[403532.490386] wlan0: RX AssocResp from 58:6d:8f:05:0a:6a (capab=0x411 status=0 aid=2)
[403532.490461] wlan0: associated
[403534.206350] wlan0: deauthenticating from 58:6d:8f:05:0a:6a by local choice (reason=3)
[403534.229511] cfg80211: Calling CRDA to update world regulatory domain
[403534.237324] cfg80211: World regulatory domain updated:
[403534.237331] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[403534.237336] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[403534.237341] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[403534.237345] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[403534.237349] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[403534.237353] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[403537.808906] wlan0: authenticate with 58:6d:8f:05:0a:6a
[403537.821694] wlan0: send auth to 58:6d:8f:05:0a:6a (try 1/3)
[403537.823400] wlan0: authenticated
[403537.824067] wlan0: associate with 58:6d:8f:05:0a:6a (try 1/3)
[403537.849385] wlan0: RX AssocResp from 58:6d:8f:05:0a:6a (capab=0x411 status=0 aid=2)
[403537.849446] wlan0: associated
[403544.737859] rtlwifi:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[403544.737899] wlan0: Connection to AP 58:6d:8f:05:0a:6a lost
[403544.817278] cfg80211: Calling CRDA to update world regulatory domain
[403544.824672] cfg80211: World regulatory domain updated:
[403544.824681] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[403544.824685] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[403544.824688] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[403544.824691] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[403544.824694] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[403544.824697] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[403545.576941] wlan0: authenticate with 58:6d:8f:05:0a:6a
[403545.589688] wlan0: send auth to 58:6d:8f:05:0a:6a (try 1/3)
[403545.692066] wlan0: send auth to 58:6d:8f:05:0a:6a (try 2/3)
[403545.796033] wlan0: send auth to 58:6d:8f:05:0a:6a (try 3/3)
[403545.900019] wlan0: authentication with 58:6d:8f:05:0a:6a timed out
[403546.752933] wlan0: authenticate with 58:6d:8f:05:0a:6a
[403546.765975] wlan0: send auth to 58:6d:8f:05:0a:6a (try 1/3)
[403546.787760] wlan0: authenticated
[403546.792042] wlan0: associate with 58:6d:8f:05:0a:6a (try 1/3)
[403546.821607] wlan0: RX AssocResp from 58:6d:8f:05:0a:6a (capab=0x411 status=0 aid=2)
[403546.821666] wlan0: associated
[403554.753486] rtlwifi:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[403554.753513] wlan0: Connection to AP 58:6d:8f:05:0a:6a lost
[403554.785142] cfg80211: Calling CRDA to update world regulatory domain
[403554.795693] cfg80211: World regulatory domain updated:
[403554.795701] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[403554.795705] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[403554.795708] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[403554.795711] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[403554.795714] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[403554.795717] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[403555.584824] wlan0: authenticate with 58:6d:8f:05:0a:6a
[403555.597242] wlan0: send auth to 58:6d:8f:05:0a:6a (try 1/3)
[403555.704065] wlan0: send auth to 58:6d:8f:05:0a:6a (try 2/3)
[403555.808052] wlan0: send auth to 58:6d:8f:05:0a:6a (try 3/3)
[403555.912021] wlan0: authentication with 58:6d:8f:05:0a:6a timed out
[403562.456818] wlan0: authenticate with 58:6d:8f:05:0a:6a
[403562.469317] wlan0: send auth to 58:6d:8f:05:0a:6a (try 1/3)
[403562.522492] wlan0: authenticated
[403562.524051] wlan0: associate with 58:6d:8f:05:0a:6a (try 1/3)
[403562.532528] wlan0: RX AssocResp from 58:6d:8f:05:0a:6a (capab=0x411 status=0 aid=2)
[403562.532592] wlan0: associated

```

---

### Post by praseodym on 2013-10-27
For 13.04 and 13.10 there is a respective patched driver available:

[http://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#post-5638107](http://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#post-5638107)

Uninstall ndiswrapper for that!

---

### Post by c0mputerguy on 2013-10-28
The card now connects to wifi on the first try with no errors in dmesg. However, I am getting very high packet loss. Any ideas?

---

### Post by praseodym on 2013-10-29
Add the mtu value of your ISP instead of "Automatic" in the network manager

---

### Post by c0mputerguy on 2013-10-29
It's behind a router and I'm pinging the router with high packet loss, not an outside site. Other computers on the same network don't have any packet loss.

---

### Post by praseodym on 2013-10-30
Add these nameservers for a better resolution of the DNS:
```

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
sudo service network-manager restart
```

---

### Post by c0mputerguy on 2013-11-02
After rebooting, the card is doing the same thing as before, except that it claims it has "Successfully connected to (none)". Same dmesg loop too.

---

### Post by praseodym on 2013-11-02
Check:
```

ifconfig -a
iwconfig
route -n
sudo iwlist scan
cat /etc/resolv.conf
```

---

### Post by bagator.davis on 2013-11-02
I have tryed everything on this page and nothing is working will not reconice card anyone got any ideas

---

### Post by praseodym on 2013-11-02
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2742](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2742)

There is a new driver on the Realtek HP

---

### Post by kurt18947 on 2013-11-02
> **praseodym said:**
> [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2742](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2742)

There is a new driver on the Realtek HP

Halleluiah!  I wonder if that works on the 3.11 kernel of 13.10 as well?  I'm quite satisifed with Tim Patterson & Balinaries2 work and will continue with them.  It's nice that Realtek got on the ball.  I was beginning to wonder if they only updated drivers when LTS versions were released.

---

### Post by c0mputerguy on 2013-11-02
That driver won't compile for me. Here is the output of the install.sh script:

```
##################################################
Realtek Wi-Fi driver Auto installation script
Novembor, 21 2011 v1.1.0
##################################################
Decompress the driver source tar ball:
    rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911.tar.gz
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/runwpa
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_xmit.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_ioctl_query.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/efuse/
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/efuse/rtw_efuse.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_recv.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_br_ext.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_eeprom.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_debug.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_tdls.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_p2p.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_ieee80211.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_security.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_cmd.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_mlme.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_mp.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_sreset.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_sta_mgt.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_rf.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_pwrctrl.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_wlan_util.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_mlme_ext.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_io.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_ap.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_ioctl_rtl.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_mp_ioctl.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_ioctl_set.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_iol.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/wlan0dhcp
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/osdep_service.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/ioctl_linux.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/recv_linux.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/pci_ops_linux.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/usb_intf.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/mlme_linux.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/pci_intf.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/rtw_android.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/xmit_linux.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/usb_ops_linux.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/ioctl_cfg80211.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/hal_com.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/wlan_bssdef.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/cmd_osdep.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_recv.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_mlme_ext.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/wifi.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtl8192c_led.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtl8192d_recv.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/HalPwrSeqCmd.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/Hal8192CPhyReg.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/Hal8192DPhyCfg.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtl8192d_hal.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtl8192c_dm.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtl8192c_rf.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_android.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtl8192c_recv.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/nic_spec.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/usb_osintf.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtl8192d_dm.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_xmit.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtl8192c_event.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_qos.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_pwrctrl.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtl8192c_xmit.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtl8192d_spec.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/osdep_ce_service.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/ieee80211.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/recv_osdep.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/drv_types_linux.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_efuse.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/Hal8192CUHWImg.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/usb_ops.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_ht.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/ioctl_cfg80211.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/ethernet.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/mp_custom_oid.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_ioctl_rtl.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/Hal8192DUHWImg.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtl8192c_spec.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_mlme.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/drv_types.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/Hal8192DEHWImg.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_sreset.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/ieee80211_ext.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/drv_types_ce.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/Hal8192CPhyCfg.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtl8192d_led.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/byteorder/
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/byteorder/swab.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/byteorder/swabb.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/byteorder/big_endian.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/byteorder/little_endian.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/byteorder/generic.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_mp_ioctl.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/usb_ops_linux.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/Hal8192CUHWImg_wowlan.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/Hal8192CEHWImg.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_p2p.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/pci_hal.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/drv_conf.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/usb_vendor_req.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/linux/
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/linux/wireless.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/osdep_service.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/Hal8192DUHWImg_wowlan.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_ioctl_query.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_eeprom.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/drv_types_xp.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_byteorder.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtl8192d_xmit.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_version.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtl8192d_cmd.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_ioctl_set.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/h2clbk.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/pci_osintf.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_cmd.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtl8192d_rf.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/pci_ops.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_tdls.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtl8192c_cmd.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_event.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/mlme_osdep.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_debug.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_ap.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/osdep_intf.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/hal_intf.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/sta_info.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_iol.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_mp_phy_regdef.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_rf.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/usb_hal.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/autoconf.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_security.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_io.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/Hal8192DPhyReg.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_br_ext.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/circ_buf.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/basic_types.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtl8192c_hal.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/ip.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_led.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/if_ether.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/xmit_osdep.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtl8192c_sreset.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_mp.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/rtw_ioctl.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/include/drv_types_sdio.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/ifcfg-wlan0
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/Makefile
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/Kconfig
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/dm.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/hal_intf.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_cmd.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_phycfg.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_xmit.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_dm.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_mp.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_rxdesc.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_rf6052.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/usb/
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/usb/rtl8192cu_led.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/usb/usb_halinit.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/usb/rtl8192cu_recv.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/usb/Hal8192CUHWImg_wowlan.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/usb/usb_ops_ce.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/usb/Hal8192CUHWImg.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/usb/usb_ops_linux.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/usb/rtl8192cu_xmit.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/usb/usb_ops_xp.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_sreset.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_hal_init.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/hal_com.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/dm.h
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/HalPwrSeqCmd.c
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/clean
rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911
Authentication requested [root] for make clean:
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm .tmp_versions -fr ; rm Module.symvers -fr
rm -fr Module.markers ; rm -fr modules.order
cd core/efuse ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd core ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd hal/rtl8192c/usb ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd hal/rtl8192c ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd hal ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd os_dep/linux ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd os_dep ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
Authentication requested [root] for make driver:
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/3.11.0-12-generic/build M=/home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911  modules
make[1]: Entering directory `/usr/src/linux-headers-3.11.0-12-generic'
  CC [M]  /home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_cmd.o
  CC [M]  /home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_security.o
  CC [M]  /home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_debug.o
  CC [M]  /home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_io.o
  CC [M]  /home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_ioctl_query.o
  CC [M]  /home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_ioctl_set.o
  CC [M]  /home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_ieee80211.o
  CC [M]  /home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_mlme.o
  CC [M]  /home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_mlme_ext.o
  CC [M]  /home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_wlan_util.o
  CC [M]  /home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_pwrctrl.o
  CC [M]  /home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_rf.o
  CC [M]  /home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_recv.o
  CC [M]  /home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_sta_mgt.o
  CC [M]  /home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_ap.o
  CC [M]  /home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_xmit.o
  CC [M]  /home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_p2p.o
  CC [M]  /home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_tdls.o
  CC [M]  /home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_br_ext.o
  CC [M]  /home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_iol.o
  CC [M]  /home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/rtw_sreset.o
  CC [M]  /home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/core/efuse/rtw_efuse.o
  CC [M]  /home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/hal_intf.o
  CC [M]  /home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/hal_com.o
  CC [M]  /home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/dm.o
  CC [M]  /home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_hal_init.o
  CC [M]  /home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_phycfg.o
  CC [M]  /home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_rf6052.o
  CC [M]  /home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_dm.o
  CC [M]  /home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_rxdesc.o
  CC [M]  /home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_cmd.o
  CC [M]  /home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/usb/usb_halinit.o
  CC [M]  /home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/usb/rtl8192cu_led.o
  CC [M]  /home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/usb/rtl8192cu_xmit.o
  CC [M]  /home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/usb/rtl8192cu_recv.o
  CC [M]  /home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/usb/usb_ops_linux.o
  CC [M]  /home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_sreset.o
  CC [M]  /home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/rtl8192c_xmit.o
  CC [M]  /home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/hal/rtl8192c/usb/Hal8192CUHWImg.o
  CC [M]  /home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/osdep_service.o
  CC [M]  /home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.o
/home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c: In function ‘rtw_proc_init_one’:
/home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:313:3: error: implicit declaration of function ‘create_proc_entry’ [-Werror=implicit-function-declaration]
   rtw_proc=create_proc_entry(rtw_proc_name, S_IFDIR, init_net.proc_net);
   ^
/home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:313:11: warning: assignment makes pointer from integer without a cast [enabled by default]
   rtw_proc=create_proc_entry(rtw_proc_name, S_IFDIR, init_net.proc_net);
           ^
/home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:320:3: error: implicit declaration of function ‘create_proc_read_entry’ [-Werror=implicit-function-declaration]
   entry = create_proc_read_entry("ver_info", S_IFREG | S_IRUGO, rtw_proc, proc_get_drv_version, dev);
   ^
/home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:320:9: warning: assignment makes pointer from integer without a cast [enabled by default]
   entry = create_proc_read_entry("ver_info", S_IFREG | S_IRUGO, rtw_proc, proc_get_drv_version, dev);
         ^
/home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:326:9: warning: assignment makes pointer from integer without a cast [enabled by default]
   entry = create_proc_read_entry("log_level", S_IFREG | S_IRUGO,
         ^
/home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:332:8: error: dereferencing pointer to incomplete type
   entry->write_proc = proc_set_log_level;
        ^
/home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:348:21: warning: assignment makes pointer from integer without a cast [enabled by default]
   padapter->dir_dev = create_proc_entry(dev->name,
                     ^
/home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:379:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("write_reg", S_IFREG | S_IRUGO,
        ^
/home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:385:7: error: dereferencing pointer to incomplete type
  entry->write_proc = proc_set_write_reg;
       ^
/home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:387:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("read_reg", S_IFREG | S_IRUGO,
        ^
/home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:393:7: error: dereferencing pointer to incomplete type
  entry->write_proc = proc_set_read_reg;
       ^
/home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:396:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("fwstate", S_IFREG | S_IRUGO,
        ^
/home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:404:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("sec_info", S_IFREG | S_IRUGO,
        ^
/home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:412:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("mlmext_state", S_IFREG | S_IRUGO,
        ^
/home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:420:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("qos_option", S_IFREG | S_IRUGO,
        ^
/home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:427:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("ht_option", S_IFREG | S_IRUGO,
        ^
/home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:434:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("rf_info", S_IFREG | S_IRUGO,
        ^
/home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:441:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("ap_info", S_IFREG | S_IRUGO,
        ^
/home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:448:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("adapter_state", S_IFREG | S_IRUGO,
        ^
/home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:455:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("trx_info", S_IFREG | S_IRUGO,
        ^
/home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:462:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("mac_reg_dump1", S_IFREG | S_IRUGO,
        ^
/home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:469:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("mac_reg_dump2", S_IFREG | S_IRUGO,
        ^
/home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:476:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("mac_reg_dump3", S_IFREG | S_IRUGO,
        ^
/home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:483:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("bb_reg_dump1", S_IFREG | S_IRUGO,
        ^
/home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:490:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("bb_reg_dump2", S_IFREG | S_IRUGO,
        ^
/home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:497:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("bb_reg_dump3", S_IFREG | S_IRUGO,
        ^
/home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:504:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("rf_reg_dump1", S_IFREG | S_IRUGO,
        ^
/home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:511:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("rf_reg_dump2", S_IFREG | S_IRUGO,
        ^
/home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:520:9: warning: assignment makes pointer from integer without a cast [enabled by default]
   entry = create_proc_read_entry("rf_reg_dump3", S_IFREG | S_IRUGO,
         ^
/home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:527:9: warning: assignment makes pointer from integer without a cast [enabled by default]
   entry = create_proc_read_entry("rf_reg_dump4", S_IFREG | S_IRUGO,
         ^
/home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:537:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("all_sta_info", S_IFREG | S_IRUGO,
        ^
/home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:555:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("best_channel", S_IFREG | S_IRUGO,
        ^
/home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:561:7: error: dereferencing pointer to incomplete type
  entry->write_proc = proc_set_best_channel;
       ^
/home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:564:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("rx_signal", S_IFREG | S_IRUGO,
        ^
/home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:570:7: error: dereferencing pointer to incomplete type
  entry->write_proc = proc_set_rx_signal;
       ^
/home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:572:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("ht_enable", S_IFREG | S_IRUGO,
        ^
/home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:578:7: error: dereferencing pointer to incomplete type
  entry->write_proc = proc_set_ht_enable;
       ^
/home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:580:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("cbw40_enable", S_IFREG | S_IRUGO,
        ^
/home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:586:7: error: dereferencing pointer to incomplete type
  entry->write_proc = proc_set_cbw40_enable;
       ^
/home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:588:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("ampdu_enable", S_IFREG | S_IRUGO,
        ^
/home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:594:7: error: dereferencing pointer to incomplete type
  entry->write_proc = proc_set_ampdu_enable;
       ^
/home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:596:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("rx_stbc", S_IFREG | S_IRUGO,
        ^
/home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:602:7: error: dereferencing pointer to incomplete type
  entry->write_proc = proc_set_rx_stbc;
       ^
/home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:605:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("path_rssi", S_IFREG | S_IRUGO,
        ^
/home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:608:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("vid", S_IFREG | S_IRUGO,
        ^
/home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:615:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("pid", S_IFREG | S_IRUGO,
        ^
/home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:622:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("rssi_disp", S_IFREG | S_IRUGO,
        ^
/home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:628:7: error: dereferencing pointer to incomplete type
  entry->write_proc = proc_set_rssi_disp;
       ^
/home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:631:8: warning: assignment makes pointer from integer without a cast [enabled by default]
  entry = create_proc_read_entry("sreset", S_IFREG | S_IRUGO,
        ^
/home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.c:637:7: error: dereferencing pointer to incomplete type
  entry->write_proc = proc_set_sreset;
       ^
cc1: some warnings being treated as errors
make[2]: *** [/home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.o] Error 1
make[1]: *** [_module_/home/david/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.11.0-12-generic'
make: *** [modules] Error 2
##################################################
Compile make driver error: 2
Please check error Mesg
##################################################

```



Here is the output of the commands you posted earlier:

ifconfig -a:

```
eth0      Link encap:Ethernet  HWaddr 00:12:79:ae:15:78  
          inet6 addr: fe80::212:79ff:feae:1578/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:10640 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7152 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13633396 (13.6 MB)  TX bytes:999983 (999.9 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1315 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1315 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:118347 (118.3 KB)  TX bytes:118347 (118.3 KB)

wlan0     Link encap:Ethernet  HWaddr c4:3d:c7:7f:1f:09  
          inet addr:192.168.200.239  Bcast:192.168.200.255  Mask:255.255.255.0
          inet6 addr: fe80::c63d:c7ff:fe7f:1f09/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:187 errors:0 dropped:0 overruns:0 frame:0
          TX packets:309 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23801 (23.8 KB)  TX bytes:58518 (58.5 KB)

```

iwconfig:

```
wlan0     IEEE 802.11bgn  ESSID:"dodge"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 58:6D:8F:05:0A:6A   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=10 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.

```

route -n:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.200.1   0.0.0.0         UG    0      0        0 wlan0
192.168.200.0   0.0.0.0         255.255.255.0   U     9      0        0 wlan0

```

sudo iwlist scan:

```
wlan0     Scan completed :
          Cell 01 - Address: 00:60:0F:DE:ED:72
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000008164371f005
                    Extra: Last beacon: 80ms ago
                    IE: Unknown: 00200000000000000000000000000000000000000000000000000000000000000000
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050402030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: 00:1D:7E:D7:B2:E5
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=10 dBm  
                    Encryption key:off
                    ESSID:"linksys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000125847054e
                    Extra: Last beacon: 12848ms ago
                    IE: Unknown: 00076C696E6B737973
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD09001018020014000000
          Cell 03 - Address: 58:6D:8F:05:0A:6A
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption key:on
                    ESSID:"dodge"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000e86fc5fc563
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 0005646F646765
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD6E0050F204104A00011010440001021041000100103B000103104700102892C0591E8BBCFA7428A8954433B29410210005436973636F102300054531323030102400063132333435361042000234321054000800060050F2040001101100054531323030100800020084103C000101
                    IE: Unknown: DD090010180208F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.


```

cat /etc/resolv.conf:

---

### Post by praseodym on 2013-11-02
Add the nameservers again. You may want to remove the package "resolvconf", too.

---

### Post by c0mputerguy on 2013-11-02
Oops, I forgot to add resolv.conf:

```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search localdomain

```

Should I still add the nameservers?

---

### Post by praseodym on 2013-11-03
Try the NS first, then uninstalling resolvconf

---

### Post by c0mputerguy on 2013-11-05
Neither the nameservers nor removing resolvconf made a difference, it still says "Connected (none)"

---

### Post by praseodym on 2013-11-06
Try it as "root":
```

sudo su
sh ./install.sh
exit
```

---

### Post by c0mputerguy on 2013-11-06
Still fails with the same error.

---

### Post by praseodym on 2013-11-06
So, now I am running out of ideas, except: Use 12.04 or 13.04 with the dkms installation. I know it works. The new Realtek driver obviously only works until kernel 3.9...

---

### Post by kurt18947 on 2013-11-07
> **praseodym said:**
> So, now I am running out of ideas, except: Use 12.04 or 13.04 with the dkms installation. I know it works. The new Realtek driver obviously only works until kernel 3.9...

That's disappointing.

---

