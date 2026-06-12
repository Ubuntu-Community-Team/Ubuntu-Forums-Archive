---
title: "wlan connects, but no access to internet"
date: 2015-04-06
forum: Networking &amp; Wireless
---

### Post by markus24 on 2015-04-06
Hi,

I installed ubuntu, but i don't get access to the internet. It connects to the wlan without error. It also get's an ip from my wlan-router. but ping 8.8.8.8 and so on fails, all packets lost. I can connect to the internet from the same pc with the same wlan-router with windows os.

some hopeful useful information:


```
root@markus-X58A-UD3R:~# cat/etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.10
DISTRIB_CODENAME=utopic
DISTRIB_DESCRIPTION="Ubuntu 14.10"
Linux markus-X58A-UD3R3.16.0-23-generic #31-Ubuntu SMP Tue Oct 21 17:56:17 UTC 2014 x86_64x86_64 x86_64 GNU/Linux
```


```
root@markus-X58A-UD3R:~# lspci -nnk |grep -iA2 net
04:00.0 Network controller [0280]:Realtek Semiconductor Co., Ltd. RTL8192CE PCIe Wireless NetworkAdapter [10ec:8178] (rev 01)
    Subsystem: ASUSTeK Computer Inc.Device [1043:84b6]
    Kernel driver in use: rtl8192ce

```

```
root@markus-X58A-UD3R:~# iwconfig
wlan0     IEEE 802.11bgn  ESSID:"mm44" 
          Mode:Managed  Frequency:2.427GHz  Access Point: BC:05:43:17:89:1F   
          Bit Rate=1 Mb/s   Tx-Power=20dBm   
          Retry short limit:7   RTSthr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=70/70  Signallevel=-40 dBm  
          Rx invalid nwid:0  Rx invalidcrypt:0  Rx invalid frag:0
          Tx excessive retries:0 Invalid misc:0   Missed beacon:0


lo        no wireless extensions.

``` 

```
root@markus-X58A-UD3R:~# rfkill listall
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```

```
root@markus-X58A-UD3R:~# lsmod
Module                  Size  Used by
ctr                    13049  1 
ccm                    17731  1 
btusb                  32448  0 
bnep                   19543  2 
rfcomm                 69509  8 
ath3k                  13331  0 
bluetooth             446190  23bnep,ath3k,btusb,rfcomm
6lowpan_iphc           18702  1bluetooth
snd_hda_codec_hdmi     47547  4 
uvcvideo               81065  0 
videobuf2_vmalloc      13216  1uvcvideo
videobuf2_memops       13362  1videobuf2_vmalloc
snd_usb_audio         165361  1 
videobuf2_core         59104  1uvcvideo
v4l2_common            15682  1videobuf2_core
snd_usbmidi_lib        29779  1snd_usb_audio
videodev              149725  3uvcvideo,v4l2_common,videobuf2_core
media                  21963  2uvcvideo,videodev
arc4                   12608  2 
snd_hda_codec_realtek    76887  1 
snd_hda_codec_generic    68914  1snd_hda_codec_realtek
snd_hda_intel          30379  5 
snd_hda_controller     35152  1snd_hda_intel
snd_hda_codec         139675  5snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
gpio_ich               13579  0 
coretemp               13441  0 
kvm_intel             143514  0 
kvm                   455570  1kvm_intel
serio_raw              13434  0 
lpc_ich                21093  0 
rtl8192ce              53509  0 
rtl_pci                26674  1rtl8192ce
rtlwifi                64237  2rtl_pci,rtl8192ce
snd_hwdep              17698  2snd_usb_audio,snd_hda_codec
rtl8192c_common        53170  1rtl8192ce
snd_pcm               104102  5snd_usb_audio,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
mac80211              660592  3rtl_pci,rtlwifi,rtl8192ce
snd_seq_midi           13564  0 
snd_seq_midi_event     14899  1snd_seq_midi
snd_rawmidi            30876  2snd_usbmidi_lib,snd_seq_midi
snd_seq                67224  2snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29513  2snd_pcm,snd_seq
cfg80211              510218  2mac80211,rtlwifi
snd                    87611  25snd_hda_codec_realtek,snd_usb_audio,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device
i7core_edac            24139  0 
soundcore              15052  2snd,snd_hda_codec
edac_core              56549  2i7core_edac
shpchp                 37040  0 
mac_hid                13227  0 
parport_pc             32741  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42299  3lp,ppdev,parport_pc
hid_generic            12559  0 
usbhid                 52574  0 
hid                   110426  2hid_generic,usbhid
uas                    23264  0 
usb_storage            66398  1 uas
nouveau              1234845  3 
mxm_wmi                13021  1 nouveau
video                  20128  1 nouveau
psmouse               106548  0 
i2c_algo_bit           13406  1 nouveau
ttm                    89406  1 nouveau
firewire_ohci          44323  0 
pata_acpi              13053  0 
firewire_core          68671  1firewire_ohci
drm_kms_helper         61627  1 nouveau
crc_itu_t              12707  1firewire_core
drm                   310919  6ttm,drm_kms_helper,nouveau
pata_jmicron           12775  0 
ahci                   34062  2 
libahci                32424  1 ahci
wmi                    19193  2mxm_wmi,nouveau

``` 

have you any advice? 

Thank you!

---

### Post by slickymaster on 2015-04-06
*Moved to the ***Networking & Wireless*** sub-forum*

---

### Post by Dragonbite on 2015-04-06
So the key elements here are  [LIST=1]
[*]Connecting your computer to the router
[LIST][*]wirelessly
[*]wired [/LIST]
[*]Connecting the router to the Internet
[/LIST]

I don't see an IP address in your quoted results.  No IP means you are not connected to the router. Once you have an IP address from the router then you are connected.[LIST]
[*]Try to verify you are connected to the router. You should be able to ping the router's IP address (it's listed on the router) ```
#example
ping 192.168.1.254
```.  If this comes back with nothing, then your computer does not see your router yet
[*]If you cannot connect wirelessly, try connect by wire (network cable) and run *ifconfig* to verify you have an IP address, then ping the router.  [LIST]
[*]If this works but wireless does not then your wireless is not connecting to the router.  This will at least provide for the possibility of downloading the drivers for wireless if necessary.
[*]If you can ping the router either way, then the problem lies between the router an the Internet
[/LIST]
[/LIST]

Then make sure the router can see the Internet
[LIST=1]
[*]Try to ping something like Google ```
ping google.com
```
[*]If this doesn't work, try using IPv6 just to make sure it isn't an IPv4 vs. IPv6 issue ```
ping6 google.com
```If it works with *ping6* and not with *ping* then the issue is the IPv4 [6] protocol.
[*]If *ping* works, then try to open up a web browser and see if you can navigate anywhere.
[/LIST]

I'm sure there is more, but basically you want to be able to confirm that you are connected to the router, either wireless or wired in, with *ifconfig* and *ping*.  Then it is a case of making sure your router is connected to the Internet.

---

### Post by markus24 on 2015-04-06
hi

thank you  for your answer.

ubuntu "talks" with my wlan router, it get's also an ip adress:

```
root@markus-X58A-UD3R:~# ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1 Mask:255.0.0.0
          inet6 addr: ::1/128Scope:Host
          UP LOOPBACK RUNNING MTU:65536  Metric:1
          RX packets:173 errors:0dropped:0 overruns:0 frame:0
          TX packets:173 errors:0dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12076 (12.0 KB)  TXbytes:12076 (12.0 KB)


wlan0     Link encap:Ethernet  HWaddrf4:6d:04:a2:85:0d  
          inet addr:192.168.178.25 Bcast:192.168.178.255  Mask:255.255.255.0
          inet6 addr:fe80::f66d:4ff:fea2:850d/64 Scope:Link
          UP BROADCAST RUNNINGMULTICAST  MTU:1500  Metric:1
          RX packets:9 errors:0dropped:0 overruns:0 frame:0
          TX packets:72 errors:0dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1537 (1.5 KB)  TXbytes:11582 (11.5 KB)



```


routing:

```
root@markus-X58A-UD3R:~# route -v -n
Kernel IP routing table
Destination     Gateway         Genmask        Flags Metric Ref    Use Iface
0.0.0.0         192.168.178.1   0.0.0.0        UG    0      0        0 wlan0
192.168.178.0   0.0.0.0        255.255.255.0   U     9      0        0 wlan0

```


But I'm not able to ping my wlan router:

```
root@markus-X58A-UD3R:~# ping192.168.178.1
PING 192.168.178.1 (192.168.178.1)56(84) bytes of data.
^C
--- 192.168.178.1 ping statistics ---
13 packets transmitted, 0 received,100% packet loss, time 12097ms

```

using windows os on the same machine, I get the same ip-adress and I'm able to ping my wlan router:
```

C:\Users\mborm>ping 192.168.178.1


Ping wird ausgeführt für 192.168.178.1 mit 32 Bytes Daten:
Antwort von 192.168.178.1: Bytes=32 Zeit=2ms TTL=64
Antwort von 192.168.178.1: Bytes=32 Zeit=2ms TTL=64
Antwort von 192.168.178.1: Bytes=32 Zeit=2ms TTL=64
Antwort von 192.168.178.1: Bytes=32 Zeit=2ms TTL=64


Ping-Statistik für 192.168.178.1:
    Pakete: Gesendet = 4, Empfangen = 4, Verloren = 0
    (0% Verlust),
Ca. Zeitangaben in Millisek.:
    Minimum = 2ms, Maximum = 2ms, Mittelwert = 2ms

```

---

### Post by markus24 on 2015-04-06
I see this in my syslog, an error with DNS
```

Apr  6 21:19:28 markus-X58A-UD3RNetworkManager[1085]: <info> NetworkManager state is nowCONNECTED_GLOBAL
Apr  6 21:19:28 markus-X58A-UD3RNetworkManager[1085]: <info> Policy set 'mm44' (wlan0) asdefault for IPv4 routing and DNS.
Apr  6 21:19:28 markus-X58A-UD3RNetworkManager[1085]: <info> DNS: starting dnsmasq...
Apr  6 21:19:28 markus-X58A-UD3RNetworkManager[1085]: <warn> dnsmasq not available on the bus,can't update servers.
Apr  6 21:19:28 markus-X58A-UD3RNetworkManager[1085]: <error> [1428347968.697827][nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus:Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq':no such name
Apr  6 21:19:28 markus-X58A-UD3RNetworkManager[1085]: <warn> DNS: plugin dnsmasq update failed

```

more from syslog
```

Apr  6 21:19:26 markus-X58A-UD3Rbluetoothd[961]: hci0: Load Long Term Keys (0x0013) failed: NotSupported (0x0c)
Apr  6 21:19:26 markus-X58A-UD3Rbluetoothd[961]: Adapter /org/bluez/961/hci0 has been enabled
Apr  6 21:19:26 markus-X58A-UD3Rdbus[913]: [system] Activating servicename='org.freedesktop.Accounts' (using servicehelper)
Apr  6 21:19:26 markus-X58A-UD3RNetworkManager[1085]: <info> Auto-activating connection 'mm44'.
Apr  6 21:19:26 markus-X58A-UD3RNetworkManager[1085]: <info> Activation (wlan0) startingconnection 'mm44'
Apr  6 21:19:26 markus-X58A-UD3RNetworkManager[1085]: <info> (wlan0): device state change:disconnected -> prepare (reason 'none') [30 40 0]
Apr  6 21:19:26 markus-X58A-UD3RNetworkManager[1085]: <info> NetworkManager state is nowCONNECTING
Apr  6 21:19:26 markus-X58A-UD3RNetworkManager[1085]: <info> Activation (wlan0) Stage 1 of 5(Device Prepare) scheduled...
Apr  6 21:19:26 markus-X58A-UD3RNetworkManager[1085]: <info> Activation (wlan0) Stage 1 of 5(Device Prepare) started...
Apr  6 21:19:26 markus-X58A-UD3RNetworkManager[1085]: <info> Activation (wlan0) Stage 2 of 5(Device Configure) scheduled...
Apr  6 21:19:26 markus-X58A-UD3RNetworkManager[1085]: <info> Activation (wlan0) Stage 1 of 5(Device Prepare) complete.
Apr  6 21:19:26 markus-X58A-UD3RNetworkManager[1085]: <info> Activation (wlan0) Stage 2 of 5(Device Configure) starting...
Apr  6 21:19:26 markus-X58A-UD3RNetworkManager[1085]: <info> (wlan0): device state change:prepare -> config (reason 'none') [40 50 0]
Apr  6 21:19:26 markus-X58A-UD3RNetworkManager[1085]: <info> Activation (wlan0/wireless):connection 'mm44' has security, and secrets exist.  No new secretsneeded.
Apr  6 21:19:26 markus-X58A-UD3RNetworkManager[1085]: <info> Config: added 'ssid' value 'mm44'
Apr  6 21:19:26 markus-X58A-UD3RNetworkManager[1085]: <info> Config: added 'scan_ssid' value'1'
Apr  6 21:19:26 markus-X58A-UD3RNetworkManager[1085]: <info> Config: added 'key_mgmt' value'WPA-PSK'
Apr  6 21:19:26 markus-X58A-UD3RNetworkManager[1085]: <info> Config: added 'auth_alg' value'OPEN'
Apr  6 21:19:26 markus-X58A-UD3RNetworkManager[1085]: <info> Config: added 'psk' value'<omitted>'
Apr  6 21:19:26 markus-X58A-UD3RNetworkManager[1085]: <info> Activation (wlan0) Stage 2 of 5(Device Configure) complete.
Apr  6 21:19:26 markus-X58A-UD3RNetworkManager[1085]: <info> Config: set interface ap_scan to 1
Apr  6 21:19:26 markus-X58A-UD3RNetworkManager[1085]: <info> (wlan0): supplicant interfacestate: disconnected -> inactive
Apr  6 21:19:26 markus-X58A-UD3Rwpa_supplicant[1516]: wlan0: SME: Trying to authenticate withbc:05:43:17:89:1f (SSID='mm44' freq=2427 MHz)
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   14.865322] wlan0: authenticate with bc:05:43:17:89:1f
Apr  6 21:19:26 markus-X58A-UD3RNetworkManager[1085]: <info> (wlan0): supplicant interfacestate: inactive -> authenticating
Apr  6 21:19:26 markus-X58A-UD3Rwpa_supplicant[1516]: wlan0: Trying to associate withbc:05:43:17:89:1f (SSID='mm44' freq=2427 MHz)
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   14.877157] wlan0: send auth to bc:05:43:17:89:1f (try1/3)
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   14.879031] wlan0: authenticated
Apr  6 21:19:26 markus-X58A-UD3RNetworkManager[1085]: <info> (wlan0): supplicant interfacestate: authenticating -> associating
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   14.881004] wlan0: associate with bc:05:43:17:89:1f (try1/3)
Apr  6 21:19:26 markus-X58A-UD3Rwpa_supplicant[1516]: wlan0: Associated with bc:05:43:17:89:1f
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   14.885812] wlan0: RX AssocResp from bc:05:43:17:89:1f(capab=0x411 status=0 aid=3)
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   14.885903] wlan0: associated
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   14.885914] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: linkbecomes ready
Apr  6 21:19:26 markus-X58A-UD3RNetworkManager[1085]: <info> (wlan0): supplicant interfacestate: associating -> 4-way handshake
Apr  6 21:19:26 markus-X58A-UD3Rwpa_supplicant[1516]: wlan0: WPA: Key negotiation completed withbc:05:43:17:89:1f [PTK=CCMP GTK=TKIP]
Apr  6 21:19:26 markus-X58A-UD3Rwpa_supplicant[1516]: wlan0: CTRL-EVENT-CONNECTED - Connection tobc:05:43:17:89:1f completed [id=0 id_str=]
Apr  6 21:19:26 markus-X58A-UD3RNetworkManager[1085]: <info> (wlan0): supplicant interfacestate: 4-way handshake -> completed
Apr  6 21:19:26 markus-X58A-UD3RNetworkManager[1085]: <info> Activation (wlan0/wireless) Stage2 of 5 (Device Configure) successful.  Connected to wireless network'mm44'.
Apr  6 21:19:26 markus-X58A-UD3RNetworkManager[1085]: <info> Activation (wlan0) Stage 3 of 5(IP Configure Start) scheduled.
Apr  6 21:19:26 markus-X58A-UD3RNetworkManager[1085]: <info> Activation (wlan0) Stage 3 of 5(IP Configure Start) started...
Apr  6 21:19:26 markus-X58A-UD3RNetworkManager[1085]: <info> (wlan0): device state change:config -> ip-config (reason 'none') [50 70 0]
Apr  6 21:19:26 markus-X58A-UD3RNetworkManager[1085]: <info> Activation (wlan0) BeginningDHCPv4 transaction (timeout in 45 seconds)
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.048948] ------------[ cut here ]------------
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049009] WARNING: CPU: 1 PID: 0 at/build/buildd/linux-3.16.0/net/mac80211/rate.c:512ieee80211_get_tx_rates+0x253/0x790 [mac80211]()
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049012] Modules linked in: ctr ccm btusb rfcomm bnepath3k bluetooth 6lowpan_iphc snd_hda_codec_hdmi uvcvideovideobuf2_vmalloc videobuf2_memops videobuf2_core v4l2_commonsnd_usb_audio videodev snd_usbmidi_lib media arc4 gpio_ichsnd_hda_codec_realtek snd_hda_codec_generic snd_hda_intelsnd_hda_controller snd_hda_codec coretemp kvm_intel kvm snd_seq_midisnd_seq_midi_event serio_raw rtl8192ce rtl_pci rtlwifirtl8192c_common snd_hwdep snd_rawmidi mac80211 snd_pcm lpc_ichsnd_seq snd_seq_device cfg80211 snd_timer snd i7core_edac soundcoreedac_core shpchp mac_hid parport_pc ppdev lp parport hid_genericusbhid hid uas usb_storage nouveau mxm_wmi video i2c_algo_bit ttmfirewire_ohci drm_kms_helper pata_acpi psmouse firewire_core drmcrc_itu_t pata_jmicron ahci wmi libahci
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049064] CPU: 1 PID: 0 Comm: swapper/1 Not tainted3.16.0-23-generic #31-Ubuntu
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049066] Hardware name: Gigabyte Technology Co., Ltd.X58A-UD3R/X58A-UD3R, BIOS FH 01/06/2012
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049068]  0000000000000009 ffff88019fc238e8ffffffff8177fcbc 0000000000000000
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049071]  ffff88019fc23920 ffffffff8106fd8dffff8800d8d8f830 ffff8800d8d8f800
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049074]  ffff8800d8d8f83c 0000000000000000ffff8801957a1da8 ffff88019fc23930
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049078] Call Trace:
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049080]  <IRQ>  [<ffffffff8177fcbc>]dump_stack+0x45/0x56
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049094]  [<ffffffff8106fd8d>]warn_slowpath_common+0x7d/0xa0
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049096]  [<ffffffff8106fe6a>]warn_slowpath_null+0x1a/0x20
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049104]  [<ffffffffc04747e3>]ieee80211_get_tx_rates+0x253/0x790 [mac80211]
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049108]  [<ffffffffc051b0c4>] ?rtl_get_rate+0x174/0x1f0 [rtlwifi]
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049116]  [<ffffffffc0474ef3>]rate_control_get_rate+0xd3/0xe0 [mac80211]
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049125]  [<ffffffffc0484a92>]invoke_tx_handlers+0x8d2/0x14d0 [mac80211]
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049133]  [<ffffffffc04857c9>]ieee80211_tx+0x79/0x110 [mac80211]
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049142]  [<ffffffffc0485a4a>]ieee80211_xmit+0x9a/0xf0 [mac80211]
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049150]  [<ffffffffc0486205>]ieee80211_subif_start_xmit+0x505/0xd70 [mac80211]
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049153]  [<ffffffff81680845>]dev_hard_start_xmit+0x335/0x5d0
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049156]  [<ffffffff816a2546>]sch_direct_xmit+0xa6/0x210
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049157]  [<ffffffff81680cda>]__dev_queue_xmit+0x1fa/0x4f0
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049159]  [<ffffffff81680fe0>]dev_queue_xmit+0x10/0x20
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049161]  [<ffffffff81722325>]ip6_finish_output2+0x2a5/0x470
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049163]  [<ffffffff817254bc>]ip6_finish_output+0x8c/0xd0
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049165]  [<ffffffff8172553c>]ip6_output+0x3c/0xc0
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049167]  [<ffffffff817465e3>]mld_sendpack+0x173/0x2c0
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049168]  [<ffffffff8174728d>]mld_ifc_timer_expire+0x19d/0x2f0
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049170]  [<ffffffff817470f0>] ?mld_clear_delrec+0xf0/0xf0
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049173]  [<ffffffff8107c9e6>]call_timer_fn+0x36/0x110
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049174]  [<ffffffff817470f0>] ?mld_clear_delrec+0xf0/0xf0
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049176]  [<ffffffff8107e5e0>]run_timer_softirq+0x260/0x370
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049178]  [<ffffffff810755f4>]__do_softirq+0x124/0x2e0
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049179]  [<ffffffff810759ad>]irq_exit+0xfd/0x110
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049182]  [<ffffffff8178abd4>]smp_apic_timer_interrupt+0x44/0x50
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049184]  [<ffffffff81788cdd>]apic_timer_interrupt+0x6d/0x80
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049185]  <EOI>  [<ffffffff81619159>] ?cpuidle_enter_state+0x49/0xc0
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049190]  [<ffffffff816192b7>]cpuidle_enter+0x17/0x20
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049194]  [<ffffffff810b9b77>]cpu_startup_entry+0x347/0x480
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049196]  [<ffffffff81045ac0>]start_secondary+0x230/0x2c0
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049197] ---[ end trace 218316fb9541d43b ]---
Apr  6 21:19:26 markus-X58A-UD3Raccounts-daemon[1552]: started daemon version 0.6.37
Apr  6 21:19:26 markus-X58A-UD3Rdbus[913]: [system] Successfully activated service'org.freedesktop.Accounts'
Apr  6 21:19:26 markus-X58A-UD3RNetworkManager[1085]: <info> dhclient started with pid 1578
Apr  6 21:19:26 markus-X58A-UD3RNetworkManager[1085]: <info> Activation (wlan0) Beginning IP6addrconf.
Apr  6 21:19:26 markus-X58A-UD3RNetworkManager[1085]: <info> Activation (wlan0) Stage 3 of 5(IP Configure Start) complete.
Apr  6 21:19:27 markus-X58A-UD3Rdhclient: Internet Systems Consortium DHCP Client 4.2.4
Apr  6 21:19:27 markus-X58A-UD3Rdhclient: Copyright 2004-2012 Internet Systems Consortium.
Apr  6 21:19:27 markus-X58A-UD3Rdhclient: All rights reserved.
Apr  6 21:19:27 markus-X58A-UD3Rdhclient: For info, please visit https://www.isc.org/software/dhcp/
Apr  6 21:19:27 markus-X58A-UD3Rdhclient: 
Apr  6 21:19:27 markus-X58A-UD3RNetworkManager[1085]: <info> (wlan0): DHCPv4 state changed nbi-> preinit
Apr  6 21:19:27 markus-X58A-UD3Rdhclient: Listening on LPF/wlan0/f4:6d:04:a2:85:0d
Apr  6 21:19:27 markus-X58A-UD3Rdhclient: Sending on   LPF/wlan0/f4:6d:04:a2:85:0d
Apr  6 21:19:27 markus-X58A-UD3Rdhclient: Sending on   Socket/fallback
Apr  6 21:19:27 markus-X58A-UD3Rdhclient: DHCPREQUEST of 192.168.178.25 on wlan0 to 255.255.255.255port 67 (xid=0x557e0d9a)
Apr  6 21:19:27 markus-X58A-UD3Rdhclient: DHCPACK of 192.168.178.25 from 192.168.178.1
Apr  6 21:19:27 markus-X58A-UD3Rdhclient: bound to 192.168.178.25 -- renewal in 355238 seconds.
Apr  6 21:19:27 markus-X58A-UD3RNetworkManager[1085]: <info> (wlan0): DHCPv4 state changedpreinit -> reboot
Apr  6 21:19:27 markus-X58A-UD3RNetworkManager[1085]: <info>   address 192.168.178.25
Apr  6 21:19:27 markus-X58A-UD3RNetworkManager[1085]: <info>   prefix 24 (255.255.255.0)
Apr  6 21:19:27 markus-X58A-UD3RNetworkManager[1085]: <info>   gateway 192.168.178.1
Apr  6 21:19:27 markus-X58A-UD3RNetworkManager[1085]: <info>   nameserver '192.168.178.1'
Apr  6 21:19:27 markus-X58A-UD3RNetworkManager[1085]: <info> Activation (wlan0) Stage 5 of 5(IPv4 Configure Commit) scheduled...
Apr  6 21:19:27 markus-X58A-UD3RNetworkManager[1085]: <info> Activation (wlan0) Stage 5 of 5(IPv4 Commit) started...
Apr  6 21:19:27 markus-X58A-UD3Ravahi-daemon[940]: Joining mDNS multicast group on interfacewlan0.IPv4 with address 192.168.178.25.
Apr  6 21:19:27 markus-X58A-UD3Ravahi-daemon[940]: New relevant interface wlan0.IPv4 for mDNS.
Apr  6 21:19:27 markus-X58A-UD3Ravahi-daemon[940]: Registering new address record for 192.168.178.25on wlan0.IPv4.
Apr  6 21:19:27 markus-X58A-UD3RModemManager[925]: <warn>  Couldn't find support for device at'/sys/devices/pci0000:00/0000:00:09.0/0000:04:00.0': not supported byany plugin
Apr  6 21:19:28 markus-X58A-UD3Ravahi-daemon[940]: Joining mDNS multicast group on interfacewlan0.IPv6 with address fe80::f66d:4ff:fea2:850d.
Apr  6 21:19:28 markus-X58A-UD3Ravahi-daemon[940]: New relevant interface wlan0.IPv6 for mDNS.
Apr  6 21:19:28 markus-X58A-UD3Ravahi-daemon[940]: Registering new address record forfe80::f66d:4ff:fea2:850d on wlan0.*.
Apr  6 21:19:28 markus-X58A-UD3RNetworkManager[1085]: <info> (wlan0): device state change:ip-config -> secondaries (reason 'none') [70 90 0]
Apr  6 21:19:28 markus-X58A-UD3RNetworkManager[1085]: <info> Activation (wlan0) Stage 5 of 5(IPv4 Commit) complete.
Apr  6 21:19:28 markus-X58A-UD3RNetworkManager[1085]: <info> (wlan0): device state change:secondaries -> activated (reason 'none') [90 100 0]
Apr  6 21:19:28 markus-X58A-UD3RNetworkManager[1085]: <info> NetworkManager state is nowCONNECTED_GLOBAL
Apr  6 21:19:28 markus-X58A-UD3RNetworkManager[1085]: <info> Policy set 'mm44' (wlan0) asdefault for IPv4 routing and DNS.
Apr  6 21:19:28 markus-X58A-UD3RNetworkManager[1085]: <info> DNS: starting dnsmasq...
Apr  6 21:19:28 markus-X58A-UD3RNetworkManager[1085]: <warn> dnsmasq not available on the bus,can't update servers.
Apr  6 21:19:28 markus-X58A-UD3RNetworkManager[1085]: <error> [1428347968.697827][nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus:Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq':no such name
Apr 6 21:19:28 markus-X58A-UD3R NetworkManager[1085]: <warn> DNS:plugin dnsmasq update failed
Apr  6 21:19:28 markus-X58A-UD3RNetworkManager[1085]: <info> Writing DNS information to/sbin/resolvconf
Apr  6 21:19:28 markus-X58A-UD3Rdnsmasq[1626]: started, version 2.71 cache disabled
Apr  6 21:19:28 markus-X58A-UD3Rdnsmasq[1626]: compile time options: IPv6 GNU-getopt DBus i18n IDNDHCP DHCPv6 no-Lua TFTP conntrack ipset auth DNSSEC
Apr  6 21:19:28 markus-X58A-UD3Rdnsmasq[1626]: DBus support enabled: connected to system bus
Apr  6 21:19:28 markus-X58A-UD3Rdnsmasq[1626]: warning: no upstream servers configured
Apr  6 21:19:30 markus-X58A-UD3Rdbus[913]: [system] Activating servicename='org.freedesktop.RealtimeKit1' (using servicehelper)
Apr  6 21:19:30 markus-X58A-UD3Rdbus[913]: [system] Successfully activated service'org.freedesktop.RealtimeKit1'

```

---

### Post by Dragonbite on 2015-04-06
Could look at this part: ```
Apr  6 21:19:28 markus-X58A-UD3RNetworkManager[1085]: <info> DNS: starting dnsmasq...
Apr  6 21:19:28 markus-X58A-UD3RNetworkManager[1085]: <warn> dnsmasq not available on the bus,can't update servers.
Apr  6 21:19:28 markus-X58A-UD3RNetworkManager[1085]: <error> [1428347968.697827][nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus:Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq':no such name
Apr 6 21:19:28 markus-X58A-UD3R NetworkManager[1085]: <warn> DNS:plugin dnsmasq update failed
Apr  6 21:19:28 markus-X58A-UD3RNetworkManager[1085]: <info> Writing DNS information to/sbin/resolvconf
```

Seems to be looking for *dnsmasq*, which I have never heard of before but that doesn't mean anything.

---

### Post by markus24 on 2015-04-07
and now? What I'm doing? Has anybody a hint?

---

### Post by Dragonbite on 2015-04-07
Try to install dnsmasq? ```
sudo apt-get install dnsmasq
```

---

### Post by markus24 on 2015-04-12
dnsmasq-base is installed (newest version)

---

### Post by markus24 on 2015-04-12
Does anybody know, what this kernel message means?

Apr  6 21:19:26 markus-X58A-UD3RNetworkManager[1085]: <info> Activation (wlan0) BeginningDHCPv4 transaction (timeout in 45 seconds)
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.048948] ------------[ cut here ]------------
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049009] WARNING: CPU: 1 PID: 0 at/build/buildd/linux-3.16.0/net/mac80211/rate.c:512ieee80211_get_tx_rates+0x253/0x790 [mac80211]()
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049012] Modules linked in: ctr ccm btusb rfcomm bnepath3k bluetooth 6lowpan_iphc snd_hda_codec_hdmi uvcvideovideobuf2_vmalloc videobuf2_memops videobuf2_core v4l2_commonsnd_usb_audio videodev snd_usbmidi_lib media arc4 gpio_ichsnd_hda_codec_realtek snd_hda_codec_generic snd_hda_intelsnd_hda_controller snd_hda_codec coretemp kvm_intel kvm snd_seq_midisnd_seq_midi_event serio_raw rtl8192ce rtl_pci rtlwifirtl8192c_common snd_hwdep snd_rawmidi mac80211 snd_pcm lpc_ichsnd_seq snd_seq_device cfg80211 snd_timer snd i7core_edac soundcoreedac_core shpchp mac_hid parport_pc ppdev lp parport hid_genericusbhid hid uas usb_storage nouveau mxm_wmi video i2c_algo_bit ttmfirewire_ohci drm_kms_helper pata_acpi psmouse firewire_core drmcrc_itu_t pata_jmicron ahci wmi libahci
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049064] CPU: 1 PID: 0 Comm: swapper/1 Not tainted3.16.0-23-generic #31-Ubuntu
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049066] Hardware name: Gigabyte Technology Co., Ltd.X58A-UD3R/X58A-UD3R, BIOS FH 01/06/2012
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049068]  0000000000000009 ffff88019fc238e8ffffffff8177fcbc 0000000000000000
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049071]  ffff88019fc23920 ffffffff8106fd8dffff8800d8d8f830 ffff8800d8d8f800
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049074]  ffff8800d8d8f83c 0000000000000000ffff8801957a1da8 ffff88019fc23930
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049078] Call Trace:
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049080]  <IRQ>  [<ffffffff8177fcbc>]dump_stack+0x45/0x56
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049094]  [<ffffffff8106fd8d>]warn_slowpath_common+0x7d/0xa0
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049096]  [<ffffffff8106fe6a>]warn_slowpath_null+0x1a/0x20
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049104]  [<ffffffffc04747e3>]ieee80211_get_tx_rates+0x253/0x790 [mac80211]
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049108]  [<ffffffffc051b0c4>] ?rtl_get_rate+0x174/0x1f0 [rtlwifi]
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049116]  [<ffffffffc0474ef3>]rate_control_get_rate+0xd3/0xe0 [mac80211]
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049125]  [<ffffffffc0484a92>]invoke_tx_handlers+0x8d2/0x14d0 [mac80211]
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049133]  [<ffffffffc04857c9>]ieee80211_tx+0x79/0x110 [mac80211]
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049142]  [<ffffffffc0485a4a>]ieee80211_xmit+0x9a/0xf0 [mac80211]
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049150]  [<ffffffffc0486205>]ieee80211_subif_start_xmit+0x505/0xd70 [mac80211]
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049153]  [<ffffffff81680845>]dev_hard_start_xmit+0x335/0x5d0
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049156]  [<ffffffff816a2546>]sch_direct_xmit+0xa6/0x210
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049157]  [<ffffffff81680cda>]__dev_queue_xmit+0x1fa/0x4f0
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049159]  [<ffffffff81680fe0>]dev_queue_xmit+0x10/0x20
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049161]  [<ffffffff81722325>]ip6_finish_output2+0x2a5/0x470
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049163]  [<ffffffff817254bc>]ip6_finish_output+0x8c/0xd0
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049165]  [<ffffffff8172553c>]ip6_output+0x3c/0xc0
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049167]  [<ffffffff817465e3>]mld_sendpack+0x173/0x2c0
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049168]  [<ffffffff8174728d>]mld_ifc_timer_expire+0x19d/0x2f0
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049170]  [<ffffffff817470f0>] ?mld_clear_delrec+0xf0/0xf0
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049173]  [<ffffffff8107c9e6>]call_timer_fn+0x36/0x110
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049174]  [<ffffffff817470f0>] ?mld_clear_delrec+0xf0/0xf0
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049176]  [<ffffffff8107e5e0>]run_timer_softirq+0x260/0x370
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049178]  [<ffffffff810755f4>]__do_softirq+0x124/0x2e0
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049179]  [<ffffffff810759ad>]irq_exit+0xfd/0x110
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049182]  [<ffffffff8178abd4>]smp_apic_timer_interrupt+0x44/0x50
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049184]  [<ffffffff81788cdd>]apic_timer_interrupt+0x6d/0x80
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049185]  <EOI>  [<ffffffff81619159>] ?cpuidle_enter_state+0x49/0xc0
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049190]  [<ffffffff816192b7>]cpuidle_enter+0x17/0x20
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049194]  [<ffffffff810b9b77>]cpu_startup_entry+0x347/0x480
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049196]  [<ffffffff81045ac0>]start_secondary+0x230/0x2c0
Apr  6 21:19:26 markus-X58A-UD3Rkernel: [   15.049197] ---[ end trace 218316fb9541d43b ]---
Apr  6 21:19:26 markus-X58A-UD3Raccounts-daemon[1552]: started daemon version 0.6.37
Apr  6 21:19:26 markus-X58A-UD3Rdbus[913]: [system] Successfully activated service'org.freedesktop.Accounts'
Apr  6 21:19:26 markus-X58A-UD3RNetworkManager[1085]: <info> dhclient started with pid 1578

---

