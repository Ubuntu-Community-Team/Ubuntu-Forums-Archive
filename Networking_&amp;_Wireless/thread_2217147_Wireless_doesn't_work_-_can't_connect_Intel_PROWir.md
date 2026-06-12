---
title: "Wireless doesn't work - can't connect Intel PRO/Wireless 2200BG"
date: 2014-04-15
forum: Networking &amp; Wireless
---

### Post by N_L on 2014-04-15
I just installed lubuntu on my old laptop that I hadn't used in a while and was working slow on win xp. I installed 13.10 lubuntu and everything appears to be working but wireless. I'm currently connected via ethernet and that works fine. I tried without, restarting and few other things and nothing worked for me. It sees connections, can scan but when I try to connect I get: ```
Failed to add/activate connection (4) Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
``` and not just on my home network but I tried turning on tethering on my phone and same thing happened.  I ran some commands with info that might be useful to troubleshooting this.  ```
rfkill list all 1: hci0: Bluetooth     Soft blocked: no     Hard blocked: no 2: phy0: Wireless LAN     Soft blocked: no     Hard blocked: no  
```  ```
dmesg | grep ipw [   15.418576] libipw: 802.11 data/management/control stack, git-1.1.13 [   15.418582] libipw: Copyright (C) 2004-2005 Intel Corporation  [   15.452694] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq [   15.452700] ipw2200: Copyright(c) 2003-2006 Intel Corporation [   15.452926] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection [   15.713972] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels) [ 1472.594285] libipw: 802.11 data/management/control stack, git-1.1.13 [ 1472.594296] libipw: Copyright (C) 2004-2005 Intel Corporation  [ 1472.650096] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq [ 1472.650104] ipw2200: Copyright(c) 2003-2006 Intel Corporation [ 1472.650347] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection [ 1472.812518] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)  
```  Scanned and here's my network: ```
 Cell 03 - Address: 38:22:9D:1A:A0:64                     ESSID:"NL"                     Protocol:IEEE 802.11bg                     Mode:Master                     Frequency:2.437 GHz (Channel 6)                     Encryption key:on                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s                               9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s                               48 Mb/s; 54 Mb/s                     Quality=92/100  Signal level=-36 dBm                       IE: WPA Version 1                         Group Cipher : TKIP                         Pairwise Ciphers (2) : TKIP CCMP                         Authentication Suites (1) : PSK                     IE: IEEE 802.11i/WPA2 Version 1                         Group Cipher : TKIP                         Pairwise Ciphers (2) : TKIP CCMP                         Authentication Suites (1) : PSK                     Extra: Last beacon: 84ms ago  
``` Auth: ```
 Authentication capabilities :         WPA         WPA2         CIPHER-TKIP         CIPHER-CCMP           Current TKIP countermeasures : yes           Current Drop unencrypted : no           Current Authentication algorithm :           Current Receive unencrypted EAPOL : yes           Current Roaming control : no           Current Privacy invoked : no  
``` Also tried modprobe but it doesnt return anything

---

### Post by N_L on 2014-04-16
Edited the post and text in [code] messed itself up :x
Also would like to add I've updated everything and it's still not working. If anyone has any suggestions I'd appreciate it, really need to fix this laptop because I need it for work.

---

### Post by praseodym on 2014-04-16
Hi,

please show the outputs of:
```

lspci -nnk | grep -iA2 net
lsmod
iwconfig
dmesg | grep ipw
ifconfig -a
```

---

### Post by N_L on 2014-04-16
Here are the results:
```
lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Subsystem: ASUSTeK Computer Inc. L8400B or L3C/S notebook [1043:1045]
    Kernel driver in use: 8139too
--
03:03.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
    Subsystem: Intel Corporation WM3B2300BG Mini-PCI Card [8086:2701]
    Kernel driver in use: ipw2200

lsmod
Module                  Size  Used by
zram                   18070  1 
bnep                   18959  2 
rfcomm                 53664  12 
snd_hda_codec_realtek    50315  1 
joydev                 17097  0 
ppdev                  17391  0 
snd_hda_intel          42658  1 
snd_hda_codec         164003  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                89488  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
microcode              18894  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25094  1 snd_seq_midi
gspca_m5602            48694  0 
radeon               1312332  2 
psmouse                90642  0 
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
gspca_main             27772  1 gspca_m5602
serio_raw              13189  0 
r852                   17925  0 
lpc_ich                16864  0 
ivtv                  143152  0 
sm_common              16772  1 r852
tveeprom               16984  1 ivtv
ttm                    75982  1 radeon
nand                   58878  2 r852,sm_common
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
pcmcia                 51368  0 
cx2341x                27654  1 ivtv
snd_timer              24447  2 snd_pcm,snd_seq
nand_ecc               13136  1 nand
btusb                  23443  0 
v4l2_common            15812  2 ivtv,cx2341x
drm_kms_helper         46867  1 radeon
nand_bch               13067  1 nand
bluetooth             323656  22 bnep,btusb,rfcomm
videodev              107508  5 ivtv,cx2341x,gspca_main,v4l2_common,gspca_m5602
snd                    60790  12 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
nand_ids                8547  1 nand
drm                   242400  4 ttm,drm_kms_helper,radeon
r592                   17711  0 
memstick               16008  1 r592
yenta_socket           40193  0 
i2c_algo_bit           13197  2 ivtv,radeon
pcmcia_rsrc            18319  1 yenta_socket
bch                    17197  1 nand_bch
soundcore              12600  1 snd
pcmcia_core            22328  3 pcmcia,pcmcia_rsrc,yenta_socket
mtd                    52735  2 nand,sm_common
ir_lirc_codec          12869  0 
ir_mce_kbd_decoder     13030  0 
lirc_dev               19324  1 ir_lirc_codec
ir_sanyo_decoder       12727  0 
ir_sony_decoder        12625  0 
ir_jvc_decoder         12655  0 
ir_rc6_decoder         12754  0 
ir_rc5_decoder         12622  0 
ir_nec_decoder         12787  0 
parport_pc             31981  1 
rc_rc6_mce             12454  0 
ite_cir                24704  0 
asus_laptop            23897  0 
mac_hid                13037  0 
rc_core                26398  11 ir_lirc_codec,ir_rc5_decoder,ir_nec_decoder,ir_sony_decoder,ir_mce_kbd_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_sanyo_decoder,ite_cir,rc_rc6_mce
video                  18777  0 
sparse_keymap          13708  1 asus_laptop
input_polldev          13648  1 asus_laptop
ipw2200               140497  0 
libipw                 33144  1 ipw2200
lib80211               14040  2 libipw,ipw2200
cfg80211              401762  2 libipw,ipw2200
lp                     13299  0 
parport                40795  3 lp,ppdev,parport_pc
8139too                32530  0 
firewire_ohci          35463  0 
8139cp                 27130  0 
sdhci_pci              18456  0 
firewire_core          57656  1 firewire_ohci
sdhci                  37644  1 sdhci_pci
crc_itu_t              12627  1 firewire_core
mii                    13654  2 8139cp,8139too

iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
 
dmesg | grep ipw
[   16.000758] libipw: 802.11 data/management/control stack, git-1.1.13
[   16.000764] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   16.055719] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   16.055725] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   16.055967] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   16.440587] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)


ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:13:d4:d8:95:75  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  HWaddr 00:13:ce:69:dc:6c  
          inet6 addr: fe80::213:ceff:fe69:dc6c/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:3724 (3.7 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:400 errors:0 dropped:0 overruns:0 frame:0
          TX packets:400 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:31840 (31.8 KB)  TX bytes:31840 (31.8 KB)


```

---

### Post by praseodym on 2014-04-16
Please check in your router interface:
[LIST]
[*]
[*]Encryption to pure WPA2-AES (CCMP)
[*]fixed channel (e.g. channel "1")
[*]MAC address filter OFF
[*]Network not hidden ("broadcast ESSID)
[/LIST]

---

### Post by N_L on 2014-04-16
Checked:
security is set to WPA/WPA2 with pre shared key (password)
Channel is set to 6.
MAC filet is disabled
and it's not hidden, I can connect with all other devices, this laptop included while it was running win xp.

---

### Post by praseodym on 2014-04-17
Lets check the logs:
```

egrep -i 'net|eth|wlan|firm|reason' /var/log/syslog 
dmesg | egrep 'net|eth|sky|sis|via|3c3|3c5|e100|8139|8169|acx|air|ath|atl|ar9|carl|atme|at7|herm|iwl|ipw|rtl8|r81|rt2|rt3|rt6|rt7|tg3|ssb|wl|b43|b44|ori|pri|p5|zd|ndis|wmi|ns8|FW' 
```
Add them via c/p ;)

---

### Post by N_L on 2014-04-17
```
stefan@stefan-A7V:~$ egrep -i 'net|eth|wlan|firm|reason' /var/log/syslog 
Apr 16 00:45:17 stefan-A7V kernel: [    0.000000]   Transmeta GenuineTMx86
Apr 16 00:45:17 stefan-A7V kernel: [    0.089946] NET: Registered protocol family 16
Apr 16 00:45:17 stefan-A7V kernel: [    0.145958] NetLabel: Initializing
Apr 16 00:45:17 stefan-A7V kernel: [    0.145960] NetLabel:  domain hash size = 128
Apr 16 00:45:17 stefan-A7V kernel: [    0.145962] NetLabel:  protocols = UNLABELED CIPSOv4
Apr 16 00:45:17 stefan-A7V kernel: [    0.145977] NetLabel:  unlabeled traffic allowed by default
Apr 16 00:45:17 stefan-A7V kernel: [    0.201469] NET: Registered protocol family 2
Apr 16 00:45:17 stefan-A7V kernel: [    0.201894] NET: Registered protocol family 1
Apr 16 00:45:17 stefan-A7V kernel: [    0.665032] audit: initializing netlink socket (disabled)
Apr 16 00:45:17 stefan-A7V kernel: [    1.010448] NET: Registered protocol family 10
Apr 16 00:45:17 stefan-A7V kernel: [    1.010726] NET: Registered protocol family 17
Apr 16 00:45:17 stefan-A7V kernel: [    1.353426] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Apr 16 00:45:17 stefan-A7V kernel: [    1.428959] 8139too: 8139too Fast Ethernet driver 0.9.28
Apr 16 00:45:17 stefan-A7V kernel: [    1.430027] 8139too 0000:03:00.0 eth0: RealTek RTL8139 at 0x0001d800, 00:13:d4:d8:95:75, IRQ 20
Apr 16 00:45:17 stefan-A7V kernel: [   15.095274] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr 16 00:45:17 stefan-A7V kernel: [   15.452694] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
Apr 16 00:45:17 stefan-A7V kernel: [   15.452926] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Apr 16 00:45:17 stefan-A7V kernel: [   15.989339] type=1400 audit(1397601915.460:3): apparmor="STATUS" operation="profile_load" parent=314 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=315 comm="apparmor_parser"
Apr 16 00:45:17 stefan-A7V kernel: [   15.990267] type=1400 audit(1397601915.460:5): apparmor="STATUS" operation="profile_replace" parent=314 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=315 comm="apparmor_parser"
Apr 16 00:45:17 stefan-A7V kernel: [   16.234975] NET: Registered protocol family 31
Apr 16 00:45:18 stefan-A7V kernel: [   18.805051] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Apr 16 00:45:19 stefan-A7V kernel: [   20.252491] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
Apr 16 00:45:19 stefan-A7V NetworkManager[644]: <info> NetworkManager (version 0.9.8.0) is starting...
Apr 16 00:45:19 stefan-A7V NetworkManager[644]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Apr 16 00:45:19 stefan-A7V NetworkManager[644]: <info> WEXT support is enabled
Apr 16 00:45:20 stefan-A7V NetworkManager[644]: <info> DNS: loaded plugin dnsmasq
Apr 16 00:45:20 stefan-A7V NetworkManager[644]:    SCPlugin-Ifupdown: init!
Apr 16 00:45:20 stefan-A7V NetworkManager[644]:    SCPlugin-Ifupdown: update_system_hostname
Apr 16 00:45:20 stefan-A7V NetworkManager[644]:    SCPluginIfupdown: management mode: unmanaged
Apr 16 00:45:20 stefan-A7V NetworkManager[644]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:03:00.0/net/eth0, iface: eth0)
Apr 16 00:45:20 stefan-A7V NetworkManager[644]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:03:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Apr 16 00:45:20 stefan-A7V NetworkManager[644]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:03:03.0/net/eth1, iface: eth1)
Apr 16 00:45:20 stefan-A7V NetworkManager[644]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:03:03.0/net/eth1, iface: eth1): no ifupdown configuration found.
Apr 16 00:45:20 stefan-A7V NetworkManager[644]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Apr 16 00:45:20 stefan-A7V NetworkManager[644]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Apr 16 00:45:20 stefan-A7V NetworkManager[644]:    SCPlugin-Ifupdown: end _init.
Apr 16 00:45:20 stefan-A7V NetworkManager[644]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Apr 16 00:45:20 stefan-A7V NetworkManager[644]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Apr 16 00:45:20 stefan-A7V NetworkManager[644]:    SCPlugin-Ofono: Acquired D-Bus service com.canonical.NMOfono
Apr 16 00:45:20 stefan-A7V NetworkManager[644]:    SCPlugin-Ofono: init!
Apr 16 00:45:20 stefan-A7V NetworkManager[644]:    SCPlugin-Ofono: end _init.
Apr 16 00:45:20 stefan-A7V NetworkManager[644]: <info> Loaded plugin (null): (null)
Apr 16 00:45:20 stefan-A7V NetworkManager[644]:    Ifupdown: get unmanaged devices count: 0
Apr 16 00:45:20 stefan-A7V NetworkManager[644]:    SCPlugin-Ifupdown: (159503056) ... get_connections.
Apr 16 00:45:20 stefan-A7V NetworkManager[644]:    SCPlugin-Ifupdown: (159503056) ... get_connections (managed=false): return empty list.
Apr 16 00:45:20 stefan-A7V NetworkManager[644]:    SCPlugin-Ofono: (159493584) ... get_connections.
Apr 16 00:45:20 stefan-A7V NetworkManager[644]:    SCPlugin-Ofono: (159493584) connections count: 0
Apr 16 00:45:20 stefan-A7V NetworkManager[644]:    Ifupdown: get unmanaged devices count: 0
Apr 16 00:45:20 stefan-A7V NetworkManager[644]: <info> modem-manager is now available
Apr 16 00:45:20 stefan-A7V NetworkManager[644]: <info> monitoring kernel firmware directory '/lib/firmware'.
Apr 16 00:45:20 stefan-A7V NetworkManager[644]: <info> rfkill0: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:1e.0/0000:03:03.0/ieee80211/phy0/rfkill0) (driver ipw2200)
Apr 16 00:45:20 stefan-A7V NetworkManager[644]: <info> WiFi hardware radio set enabled
Apr 16 00:45:20 stefan-A7V NetworkManager[644]: <info> WiFi enabled by radio killswitch; enabled by state file
Apr 16 00:45:20 stefan-A7V NetworkManager[644]: <info> WWAN enabled by radio killswitch; enabled by state file
Apr 16 00:45:20 stefan-A7V NetworkManager[644]: <info> WiMAX enabled by radio killswitch; enabled by state file
Apr 16 00:45:20 stefan-A7V NetworkManager[644]: <info> Networking is enabled by state file
Apr 16 00:45:20 stefan-A7V NetworkManager[644]: <warn> failed to allocate link cache: (-10) Operation not supported
Apr 16 00:45:20 stefan-A7V NetworkManager[644]: <info> (eth0): carrier is OFF
Apr 16 00:45:20 stefan-A7V NetworkManager[644]: <info> (eth0): new Ethernet device (driver: '8139too' ifindex: 2)
Apr 16 00:45:20 stefan-A7V NetworkManager[644]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Apr 16 00:45:20 stefan-A7V NetworkManager[644]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Apr 16 00:45:20 stefan-A7V NetworkManager[644]: <info> (eth0): bringing up device.
Apr 16 00:45:20 stefan-A7V kernel: [   21.031978] 8139too 0000:03:00.0 eth0: link down
Apr 16 00:45:20 stefan-A7V NetworkManager[644]: <info> (eth0): preparing device.
Apr 16 00:45:20 stefan-A7V kernel: [   21.032371] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr 16 00:45:20 stefan-A7V NetworkManager[644]: <info> (eth0): deactivating device (reason 'managed') [2]
Apr 16 00:45:20 stefan-A7V NetworkManager[644]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:1e.0/0000:03:00.0/net/eth0
Apr 16 00:45:20 stefan-A7V kernel: [   21.036634] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr 16 00:45:20 stefan-A7V NetworkManager[644]: <info> (eth1): driver supports SSID scans (scan_capa 0x21).
Apr 16 00:45:20 stefan-A7V NetworkManager[644]: <info> (eth1): using WEXT for WiFi device control
Apr 16 00:45:20 stefan-A7V NetworkManager[644]: <info> (eth1): new 802.11 WiFi device (driver: 'ipw2200' ifindex: 3)
Apr 16 00:45:20 stefan-A7V NetworkManager[644]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/1
Apr 16 00:45:20 stefan-A7V NetworkManager[644]: <info> (eth1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Apr 16 00:45:20 stefan-A7V NetworkManager[644]: <info> (eth1): bringing up device.
Apr 16 00:45:20 stefan-A7V NetworkManager[644]: <info> (eth1): preparing device.
Apr 16 00:45:20 stefan-A7V NetworkManager[644]: <info> (eth1): deactivating device (reason 'managed') [2]
Apr 16 00:45:20 stefan-A7V NetworkManager[644]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Apr 16 00:45:20 stefan-A7V NetworkManager[644]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Apr 16 00:45:20 stefan-A7V NetworkManager[644]: <info> wpa_supplicant started
Apr 16 00:45:20 stefan-A7V NetworkManager[644]: <info> (eth1) supports 1 scan SSIDs
Apr 16 00:45:20 stefan-A7V NetworkManager[644]: <warn> Trying to remove a non-existant call id.
Apr 16 00:45:20 stefan-A7V NetworkManager[644]: <info> (eth1): supplicant interface state: starting -> ready
Apr 16 00:45:20 stefan-A7V NetworkManager[644]: <info> (eth1): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Apr 16 00:45:20 stefan-A7V NetworkManager[644]: <info> (eth1): supplicant interface state: ready -> inactive
Apr 16 00:45:20 stefan-A7V NetworkManager[644]: <info> (eth1) supports 1 scan SSIDs
Apr 16 00:45:20 stefan-A7V avahi-daemon[785]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::213:ceff:fe69:dc6c.
Apr 16 00:45:20 stefan-A7V avahi-daemon[785]: New relevant interface eth1.IPv6 for mDNS.
Apr 16 00:45:20 stefan-A7V avahi-daemon[785]: Network interface enumeration completed.
Apr 16 00:45:20 stefan-A7V avahi-daemon[785]: Registering new address record for fe80::213:ceff:fe69:dc6c on eth1.*.
Apr 16 00:45:23 stefan-A7V ntpd[781]: Listen normally on 4 eth1 fe80::213:ceff:fe69:dc6c UDP 123
Apr 16 00:47:36 stefan-A7V kernel: [  157.511484] 8139too 0000:03:00.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Apr 16 00:47:36 stefan-A7V kernel: [  157.511804] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Apr 16 00:47:36 stefan-A7V NetworkManager[644]: <info> (eth0): carrier now ON (device state 20)
Apr 16 00:47:36 stefan-A7V NetworkManager[644]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Apr 16 00:47:36 stefan-A7V NetworkManager[644]: <info> Auto-activating connection 'Wired connection 1'.
Apr 16 00:47:36 stefan-A7V NetworkManager[644]: <info> Activation (eth0) starting connection 'Wired connection 1'
Apr 16 00:47:36 stefan-A7V NetworkManager[644]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Apr 16 00:47:36 stefan-A7V NetworkManager[644]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 16 00:47:36 stefan-A7V NetworkManager[644]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Apr 16 00:47:36 stefan-A7V NetworkManager[644]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Apr 16 00:47:36 stefan-A7V NetworkManager[644]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Apr 16 00:47:36 stefan-A7V NetworkManager[644]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Apr 16 00:47:36 stefan-A7V NetworkManager[644]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Apr 16 00:47:36 stefan-A7V NetworkManager[644]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Apr 16 00:47:36 stefan-A7V NetworkManager[644]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Apr 16 00:47:36 stefan-A7V NetworkManager[644]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Apr 16 00:47:37 stefan-A7V NetworkManager[644]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Apr 16 00:47:37 stefan-A7V NetworkManager[644]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Apr 16 00:47:37 stefan-A7V NetworkManager[644]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Apr 16 00:47:37 stefan-A7V NetworkManager[644]: <info> dhclient started with pid 1264
Apr 16 00:47:37 stefan-A7V NetworkManager[644]: <info> Activation (eth0) Beginning IP6 addrconf.
Apr 16 00:47:37 stefan-A7V NetworkManager[644]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Apr 16 00:47:37 stefan-A7V dhclient: Internet Systems Consortium DHCP Client 4.2.4
Apr 16 00:47:37 stefan-A7V dhclient: Copyright 2004-2012 Internet Systems Consortium.
Apr 16 00:47:37 stefan-A7V NetworkManager[644]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Apr 16 00:47:37 stefan-A7V dhclient: Listening on LPF/eth0/00:13:d4:d8:95:75
Apr 16 00:47:37 stefan-A7V dhclient: Sending on   LPF/eth0/00:13:d4:d8:95:75
Apr 16 00:47:37 stefan-A7V dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 (xid=0x104048b9)
Apr 16 00:47:37 stefan-A7V dhclient: DHCPREQUEST of 192.168.1.72 on eth0 to 255.255.255.255 port 67 (xid=0x104048b9)
Apr 16 00:47:37 stefan-A7V NetworkManager[644]: <info> (eth0): DHCPv4 state changed preinit -> bound
Apr 16 00:47:37 stefan-A7V NetworkManager[644]: <info>   address 192.168.1.72
Apr 16 00:47:37 stefan-A7V NetworkManager[644]: <info>   prefix 24 (255.255.255.0)
Apr 16 00:47:37 stefan-A7V NetworkManager[644]: <info>   gateway 192.168.1.254
Apr 16 00:47:37 stefan-A7V NetworkManager[644]: <info>   nameserver '192.168.1.254'
Apr 16 00:47:37 stefan-A7V NetworkManager[644]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Apr 16 00:47:37 stefan-A7V NetworkManager[644]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Apr 16 00:47:37 stefan-A7V avahi-daemon[785]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.72.
Apr 16 00:47:37 stefan-A7V avahi-daemon[785]: New relevant interface eth0.IPv4 for mDNS.
Apr 16 00:47:37 stefan-A7V avahi-daemon[785]: Registering new address record for 192.168.1.72 on eth0.IPv4.
Apr 16 00:47:38 stefan-A7V NetworkManager[644]: <info> (eth0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Apr 16 00:47:38 stefan-A7V NetworkManager[644]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Apr 16 00:47:38 stefan-A7V NetworkManager[644]: <info> (eth0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Apr 16 00:47:38 stefan-A7V NetworkManager[644]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Apr 16 00:47:38 stefan-A7V NetworkManager[644]: <info> DNS: starting dnsmasq...
Apr 16 00:47:38 stefan-A7V NetworkManager[644]: <warn> dnsmasq not available on the bus, can't update servers.
Apr 16 00:47:38 stefan-A7V NetworkManager[644]: <error> [1397602058.177970] [nm-dns-dnsmasq.c:402] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Apr 16 00:47:38 stefan-A7V NetworkManager[644]: <warn> DNS: plugin dnsmasq update failed
Apr 16 00:47:38 stefan-A7V NetworkManager[644]: <info> Writing DNS information to /sbin/resolvconf
Apr 16 00:47:38 stefan-A7V avahi-daemon[785]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::213:d4ff:fed8:9575.
Apr 16 00:47:38 stefan-A7V avahi-daemon[785]: New relevant interface eth0.IPv6 for mDNS.
Apr 16 00:47:38 stefan-A7V avahi-daemon[785]: Registering new address record for fe80::213:d4ff:fed8:9575 on eth0.*.
Apr 16 00:47:40 stefan-A7V ntpd[781]: Listen normally on 5 eth0 192.168.1.72 UDP 123
Apr 16 00:47:40 stefan-A7V ntpd[781]: Listen normally on 6 eth0 fe80::213:d4ff:fed8:9575 UDP 123
Apr 16 00:47:48 stefan-A7V NetworkManager[644]: <info> Activation (eth0) successful, device activated.
Apr 16 00:47:48 stefan-A7V NetworkManager[644]: <warn> dnsmasq appeared on DBus: :1.27
Apr 16 00:47:48 stefan-A7V NetworkManager[644]: <info> Writing DNS information to /sbin/resolvconf
Apr 16 00:47:58 stefan-A7V NetworkManager[644]: <info> (eth0): IP6 addrconf timed out or failed.
Apr 16 00:47:58 stefan-A7V NetworkManager[644]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Apr 16 00:47:58 stefan-A7V NetworkManager[644]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Apr 16 00:47:58 stefan-A7V NetworkManager[644]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Apr 16 00:48:20 stefan-A7V ntpd[1551]: Listen normally on 3 eth0 192.168.1.72 UDP 123
Apr 16 00:48:20 stefan-A7V ntpd[1551]: Listen normally on 5 eth1 fe80::213:ceff:fe69:dc6c UDP 123
Apr 16 00:48:20 stefan-A7V ntpd[1551]: Listen normally on 6 eth0 fe80::213:d4ff:fed8:9575 UDP 123
Apr 16 01:09:20 stefan-A7V avahi-daemon[785]: Interface eth1.IPv6 no longer relevant for mDNS.
Apr 16 01:09:20 stefan-A7V avahi-daemon[785]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::213:ceff:fe69:dc6c.
Apr 16 01:09:20 stefan-A7V avahi-daemon[785]: Withdrawing address record for fe80::213:ceff:fe69:dc6c on eth1.
Apr 16 01:09:20 stefan-A7V avahi-daemon[785]: Withdrawing workstation service for eth1.
Apr 16 01:09:20 stefan-A7V NetworkManager[644]: <info> radio killswitch /sys/devices/pci0000:00/0000:00:1e.0/0000:03:03.0/ieee80211/phy0/rfkill0 disappeared
Apr 16 01:09:20 stefan-A7V NetworkManager[644]: <info> (eth1): device state change: disconnected -> unmanaged (reason 'removed') [30 10 36]
Apr 16 01:09:20 stefan-A7V NetworkManager[644]: <info> (eth1): cleaning up...
Apr 16 01:09:20 stefan-A7V NetworkManager[644]: <warn> (3) failed to find interface name for index
Apr 16 01:09:20 stefan-A7V NetworkManager[644]: (nm-system.c:766):nm_system_iface_get_flags: runtime check failed: (iface != NULL)
Apr 16 01:09:20 stefan-A7V NetworkManager[644]: <error> [1397603360.727423] [nm-system.c:768] nm_system_iface_get_flags(): (unknown): failed to get interface link object
Apr 16 01:09:20 stefan-A7V NetworkManager[644]: <warn> sysctl: failed to open '/proc/sys/net/ipv6/conf/eth1/accept_ra': (2) No such file or directory
Apr 16 01:09:20 stefan-A7V NetworkManager[644]: <warn> sysctl: failed to open '/proc/sys/net/ipv6/conf/eth1/use_tempaddr': (2) No such file or directory
Apr 16 01:09:20 stefan-A7V NetworkManager[644]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:03:03.0/net/eth1, iface: eth1)
Apr 16 01:09:20 stefan-A7V wpa_supplicant[753]: Could not read interface eth1 flags: No such device
Apr 16 01:09:21 stefan-A7V ntpd[1551]: Deleting interface #5 eth1, fe80::213:ceff:fe69:dc6c#123, interface stats: received=0, sent=0, dropped=0, active_time=1236 secs
Apr 16 01:09:32 stefan-A7V kernel: [ 1472.650096] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
Apr 16 01:09:32 stefan-A7V kernel: [ 1472.650347] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Apr 16 01:09:32 stefan-A7V NetworkManager[644]: <info> rfkill2: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:1e.0/0000:03:03.0/ieee80211/phy0/rfkill2) (driver ipw2200)
Apr 16 01:09:32 stefan-A7V NetworkManager[644]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:03:03.0/net/eth1, iface: eth1)
Apr 16 01:09:32 stefan-A7V NetworkManager[644]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:03:03.0/net/eth1, iface: eth1): no ifupdown configuration found.
Apr 16 01:09:32 stefan-A7V NetworkManager[644]: <info> (eth1): driver supports SSID scans (scan_capa 0x21).
Apr 16 01:09:32 stefan-A7V NetworkManager[644]: <info> (eth1): using WEXT for WiFi device control
Apr 16 01:09:32 stefan-A7V NetworkManager[644]: <info> (eth1): new 802.11 WiFi device (driver: 'ipw2200' ifindex: 4)
Apr 16 01:09:32 stefan-A7V NetworkManager[644]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/2
Apr 16 01:09:32 stefan-A7V NetworkManager[644]: <info> (eth1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Apr 16 01:09:32 stefan-A7V NetworkManager[644]: <info> (eth1): bringing up device.
Apr 16 01:09:32 stefan-A7V NetworkManager[644]: <info> (eth1): preparing device.
Apr 16 01:09:32 stefan-A7V NetworkManager[644]: <info> (eth1): deactivating device (reason 'managed') [2]
Apr 16 01:09:32 stefan-A7V NetworkManager[644]: <info> (eth1) supports 1 scan SSIDs
Apr 16 01:09:32 stefan-A7V NetworkManager[644]: <warn> Trying to remove a non-existant call id.
Apr 16 01:09:32 stefan-A7V NetworkManager[644]: <info> (eth1): supplicant interface state: starting -> ready
Apr 16 01:09:32 stefan-A7V NetworkManager[644]: <info> (eth1): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Apr 16 01:09:32 stefan-A7V NetworkManager[644]: <info> (eth1): supplicant interface state: ready -> inactive
Apr 16 01:09:32 stefan-A7V NetworkManager[644]: <info> (eth1) supports 1 scan SSIDs
Apr 16 01:09:33 stefan-A7V avahi-daemon[785]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::213:ceff:fe69:dc6c.
Apr 16 01:09:33 stefan-A7V avahi-daemon[785]: New relevant interface eth1.IPv6 for mDNS.
Apr 16 01:09:33 stefan-A7V avahi-daemon[785]: Registering new address record for fe80::213:ceff:fe69:dc6c on eth1.*.
Apr 16 01:09:35 stefan-A7V ntpd[1551]: Listen normally on 7 eth1 fe80::213:ceff:fe69:dc6c UDP 123
Apr 16 22:09:56 stefan-A7V kernel: [    0.000000]   Transmeta GenuineTMx86
Apr 16 22:09:56 stefan-A7V kernel: [    0.089950] NET: Registered protocol family 16
Apr 16 22:09:56 stefan-A7V kernel: [    0.145948] NetLabel: Initializing
Apr 16 22:09:56 stefan-A7V kernel: [    0.145951] NetLabel:  domain hash size = 128
Apr 16 22:09:56 stefan-A7V kernel: [    0.145953] NetLabel:  protocols = UNLABELED CIPSOv4
Apr 16 22:09:56 stefan-A7V kernel: [    0.145968] NetLabel:  unlabeled traffic allowed by default
Apr 16 22:09:56 stefan-A7V kernel: [    0.201473] NET: Registered protocol family 2
Apr 16 22:09:56 stefan-A7V kernel: [    0.201898] NET: Registered protocol family 1
Apr 16 22:09:56 stefan-A7V kernel: [    0.664999] audit: initializing netlink socket (disabled)
Apr 16 22:09:56 stefan-A7V kernel: [    1.012163] NET: Registered protocol family 10
Apr 16 22:09:56 stefan-A7V kernel: [    1.012444] NET: Registered protocol family 17
Apr 16 22:09:56 stefan-A7V kernel: [    1.781106] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Apr 16 22:09:56 stefan-A7V kernel: [    1.795351] 8139too: 8139too Fast Ethernet driver 0.9.28
Apr 16 22:09:56 stefan-A7V kernel: [    1.857146] 8139too 0000:03:00.0 eth0: RealTek RTL8139 at 0x0001d800, 00:13:d4:d8:95:75, IRQ 20
Apr 16 22:09:56 stefan-A7V kernel: [   15.711198] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr 16 22:09:56 stefan-A7V kernel: [   16.055719] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
Apr 16 22:09:56 stefan-A7V kernel: [   16.055967] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Apr 16 22:09:56 stefan-A7V kernel: [   16.535161] type=1400 audit(1397678993.005:3): apparmor="STATUS" operation="profile_load" parent=316 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=318 comm="apparmor_parser"
Apr 16 22:09:56 stefan-A7V kernel: [   16.540982] type=1400 audit(1397678993.013:5): apparmor="STATUS" operation="profile_replace" parent=316 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=318 comm="apparmor_parser"
Apr 16 22:09:56 stefan-A7V kernel: [   16.800926] NET: Registered protocol family 31
Apr 16 22:09:57 stefan-A7V kernel: [   20.555438] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
Apr 16 22:09:57 stefan-A7V kernel: [   21.207460] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Apr 16 22:09:58 stefan-A7V avahi-daemon[743]: Network interface enumeration completed.
Apr 16 22:09:58 stefan-A7V NetworkManager[794]: <info> NetworkManager (version 0.9.8.0) is starting...
Apr 16 22:09:58 stefan-A7V NetworkManager[794]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Apr 16 22:09:58 stefan-A7V NetworkManager[794]: <info> WEXT support is enabled
Apr 16 22:09:59 stefan-A7V NetworkManager[794]: <info> DNS: loaded plugin dnsmasq
Apr 16 22:09:59 stefan-A7V NetworkManager[794]:    SCPlugin-Ifupdown: init!
Apr 16 22:09:59 stefan-A7V NetworkManager[794]:    SCPlugin-Ifupdown: update_system_hostname
Apr 16 22:09:59 stefan-A7V NetworkManager[794]:    SCPluginIfupdown: management mode: unmanaged
Apr 16 22:09:59 stefan-A7V NetworkManager[794]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:03:00.0/net/eth0, iface: eth0)
Apr 16 22:09:59 stefan-A7V NetworkManager[794]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:03:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Apr 16 22:09:59 stefan-A7V NetworkManager[794]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:03:03.0/net/eth1, iface: eth1)
Apr 16 22:09:59 stefan-A7V NetworkManager[794]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:03:03.0/net/eth1, iface: eth1): no ifupdown configuration found.
Apr 16 22:09:59 stefan-A7V NetworkManager[794]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Apr 16 22:09:59 stefan-A7V NetworkManager[794]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Apr 16 22:09:59 stefan-A7V NetworkManager[794]:    SCPlugin-Ifupdown: end _init.
Apr 16 22:09:59 stefan-A7V NetworkManager[794]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Apr 16 22:09:59 stefan-A7V NetworkManager[794]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Apr 16 22:09:59 stefan-A7V NetworkManager[794]:    SCPlugin-Ofono: Acquired D-Bus service com.canonical.NMOfono
Apr 16 22:09:59 stefan-A7V NetworkManager[794]:    SCPlugin-Ofono: init!
Apr 16 22:09:59 stefan-A7V NetworkManager[794]:    SCPlugin-Ofono: end _init.
Apr 16 22:09:59 stefan-A7V NetworkManager[794]: <info> Loaded plugin (null): (null)
Apr 16 22:09:59 stefan-A7V NetworkManager[794]:    Ifupdown: get unmanaged devices count: 0
Apr 16 22:09:59 stefan-A7V NetworkManager[794]:    SCPlugin-Ifupdown: (138504008) ... get_connections.
Apr 16 22:09:59 stefan-A7V NetworkManager[794]:    SCPlugin-Ifupdown: (138504008) ... get_connections (managed=false): return empty list.
Apr 16 22:09:59 stefan-A7V NetworkManager[794]:    SCPlugin-Ofono: (138419664) ... get_connections.
Apr 16 22:09:59 stefan-A7V NetworkManager[794]:    SCPlugin-Ofono: (138419664) connections count: 0
Apr 16 22:09:59 stefan-A7V NetworkManager[794]:    Ifupdown: get unmanaged devices count: 0
Apr 16 22:09:59 stefan-A7V NetworkManager[794]: <info> modem-manager is now available
Apr 16 22:09:59 stefan-A7V NetworkManager[794]: <info> monitoring kernel firmware directory '/lib/firmware'.
Apr 16 22:09:59 stefan-A7V NetworkManager[794]: <info> rfkill0: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:1e.0/0000:03:03.0/ieee80211/phy0/rfkill0) (driver ipw2200)
Apr 16 22:09:59 stefan-A7V NetworkManager[794]: <info> WiFi hardware radio set enabled
Apr 16 22:09:59 stefan-A7V NetworkManager[794]: <info> WiFi enabled by radio killswitch; enabled by state file
Apr 16 22:09:59 stefan-A7V NetworkManager[794]: <info> WWAN enabled by radio killswitch; enabled by state file
Apr 16 22:09:59 stefan-A7V NetworkManager[794]: <info> WiMAX enabled by radio killswitch; enabled by state file
Apr 16 22:09:59 stefan-A7V NetworkManager[794]: <info> Networking is enabled by state file
Apr 16 22:09:59 stefan-A7V NetworkManager[794]: <warn> failed to allocate link cache: (-10) Operation not supported
Apr 16 22:09:59 stefan-A7V NetworkManager[794]: <info> (eth0): carrier is OFF
Apr 16 22:09:59 stefan-A7V NetworkManager[794]: <info> (eth0): new Ethernet device (driver: '8139too' ifindex: 2)
Apr 16 22:09:59 stefan-A7V NetworkManager[794]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Apr 16 22:09:59 stefan-A7V NetworkManager[794]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Apr 16 22:09:59 stefan-A7V NetworkManager[794]: <info> (eth0): bringing up device.
Apr 16 22:09:59 stefan-A7V NetworkManager[794]: <info> (eth0): preparing device.
Apr 16 22:09:59 stefan-A7V NetworkManager[794]: <info> (eth0): deactivating device (reason 'managed') [2]
Apr 16 22:09:59 stefan-A7V kernel: [   23.386518] 8139too 0000:03:00.0 eth0: link down
Apr 16 22:09:59 stefan-A7V kernel: [   23.386654] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr 16 22:09:59 stefan-A7V kernel: [   23.387159] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr 16 22:09:59 stefan-A7V NetworkManager[794]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:1e.0/0000:03:00.0/net/eth0
Apr 16 22:09:59 stefan-A7V NetworkManager[794]: <info> (eth1): driver supports SSID scans (scan_capa 0x21).
Apr 16 22:09:59 stefan-A7V NetworkManager[794]: <info> (eth1): using WEXT for WiFi device control
Apr 16 22:09:59 stefan-A7V NetworkManager[794]: <info> (eth1): new 802.11 WiFi device (driver: 'ipw2200' ifindex: 3)
Apr 16 22:09:59 stefan-A7V NetworkManager[794]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/1
Apr 16 22:09:59 stefan-A7V NetworkManager[794]: <info> (eth1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Apr 16 22:09:59 stefan-A7V NetworkManager[794]: <info> (eth1): bringing up device.
Apr 16 22:09:59 stefan-A7V NetworkManager[794]: <info> (eth1): preparing device.
Apr 16 22:09:59 stefan-A7V NetworkManager[794]: <info> (eth1): deactivating device (reason 'managed') [2]
Apr 16 22:09:59 stefan-A7V NetworkManager[794]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Apr 16 22:09:59 stefan-A7V NetworkManager[794]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Apr 16 22:09:59 stefan-A7V NetworkManager[794]: <info> wpa_supplicant started
Apr 16 22:09:59 stefan-A7V NetworkManager[794]: <info> (eth1) supports 1 scan SSIDs
Apr 16 22:09:59 stefan-A7V NetworkManager[794]: <warn> Trying to remove a non-existant call id.
Apr 16 22:09:59 stefan-A7V NetworkManager[794]: <info> (eth1): supplicant interface state: starting -> ready
Apr 16 22:09:59 stefan-A7V NetworkManager[794]: <info> (eth1): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Apr 16 22:09:59 stefan-A7V NetworkManager[794]: <info> (eth1): supplicant interface state: ready -> inactive
Apr 16 22:09:59 stefan-A7V NetworkManager[794]: <info> (eth1) supports 1 scan SSIDs
Apr 16 22:10:01 stefan-A7V avahi-daemon[743]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::213:ceff:fe69:dc6c.
Apr 16 22:10:01 stefan-A7V avahi-daemon[743]: New relevant interface eth1.IPv6 for mDNS.
Apr 16 22:10:01 stefan-A7V avahi-daemon[743]: Registering new address record for fe80::213:ceff:fe69:dc6c on eth1.*.
Apr 16 22:10:03 stefan-A7V ntpd[790]: Listen normally on 4 eth1 fe80::213:ceff:fe69:dc6c UDP 123
Apr 16 22:14:33 stefan-A7V kernel: [  296.697115] 8139too 0000:03:00.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Apr 16 22:14:33 stefan-A7V NetworkManager[794]: <info> (eth0): carrier now ON (device state 20)
Apr 16 22:14:33 stefan-A7V NetworkManager[794]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Apr 16 22:14:33 stefan-A7V NetworkManager[794]: <info> Auto-activating connection 'Wired connection 1'.
Apr 16 22:14:33 stefan-A7V NetworkManager[794]: <info> Activation (eth0) starting connection 'Wired connection 1'
Apr 16 22:14:33 stefan-A7V NetworkManager[794]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Apr 16 22:14:33 stefan-A7V kernel: [  296.697456] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Apr 16 22:14:33 stefan-A7V NetworkManager[794]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 16 22:14:33 stefan-A7V NetworkManager[794]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Apr 16 22:14:33 stefan-A7V NetworkManager[794]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Apr 16 22:14:33 stefan-A7V NetworkManager[794]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Apr 16 22:14:33 stefan-A7V NetworkManager[794]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Apr 16 22:14:33 stefan-A7V NetworkManager[794]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Apr 16 22:14:33 stefan-A7V NetworkManager[794]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Apr 16 22:14:33 stefan-A7V NetworkManager[794]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Apr 16 22:14:33 stefan-A7V NetworkManager[794]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Apr 16 22:14:33 stefan-A7V NetworkManager[794]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Apr 16 22:14:33 stefan-A7V NetworkManager[794]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Apr 16 22:14:33 stefan-A7V NetworkManager[794]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Apr 16 22:14:33 stefan-A7V NetworkManager[794]: <info> dhclient started with pid 1333
Apr 16 22:14:33 stefan-A7V NetworkManager[794]: <info> Activation (eth0) Beginning IP6 addrconf.
Apr 16 22:14:33 stefan-A7V NetworkManager[794]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Apr 16 22:14:33 stefan-A7V dhclient: Internet Systems Consortium DHCP Client 4.2.4
Apr 16 22:14:33 stefan-A7V dhclient: Copyright 2004-2012 Internet Systems Consortium.
Apr 16 22:14:33 stefan-A7V NetworkManager[794]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Apr 16 22:14:33 stefan-A7V dhclient: Listening on LPF/eth0/00:13:d4:d8:95:75
Apr 16 22:14:33 stefan-A7V dhclient: Sending on   LPF/eth0/00:13:d4:d8:95:75
Apr 16 22:14:33 stefan-A7V dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 (xid=0x9942f5)
Apr 16 22:14:33 stefan-A7V dhclient: DHCPREQUEST of 192.168.1.72 on eth0 to 255.255.255.255 port 67 (xid=0x9942f5)
Apr 16 22:14:33 stefan-A7V NetworkManager[794]: <info> (eth0): DHCPv4 state changed preinit -> bound
Apr 16 22:14:33 stefan-A7V NetworkManager[794]: <info>   address 192.168.1.72
Apr 16 22:14:33 stefan-A7V NetworkManager[794]: <info>   prefix 24 (255.255.255.0)
Apr 16 22:14:33 stefan-A7V NetworkManager[794]: <info>   gateway 192.168.1.254
Apr 16 22:14:33 stefan-A7V NetworkManager[794]: <info>   nameserver '192.168.1.254'
Apr 16 22:14:33 stefan-A7V NetworkManager[794]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Apr 16 22:14:33 stefan-A7V NetworkManager[794]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Apr 16 22:14:33 stefan-A7V avahi-daemon[743]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.72.
Apr 16 22:14:33 stefan-A7V avahi-daemon[743]: New relevant interface eth0.IPv4 for mDNS.
Apr 16 22:14:33 stefan-A7V avahi-daemon[743]: Registering new address record for 192.168.1.72 on eth0.IPv4.
Apr 16 22:14:34 stefan-A7V NetworkManager[794]: <info> (eth0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Apr 16 22:14:34 stefan-A7V NetworkManager[794]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Apr 16 22:14:34 stefan-A7V NetworkManager[794]: <info> (eth0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Apr 16 22:14:34 stefan-A7V NetworkManager[794]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Apr 16 22:14:34 stefan-A7V NetworkManager[794]: <info> DNS: starting dnsmasq...
Apr 16 22:14:34 stefan-A7V NetworkManager[794]: <warn> dnsmasq not available on the bus, can't update servers.
Apr 16 22:14:34 stefan-A7V NetworkManager[794]: <error> [1397679274.378662] [nm-dns-dnsmasq.c:402] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Apr 16 22:14:34 stefan-A7V NetworkManager[794]: <warn> DNS: plugin dnsmasq update failed
Apr 16 22:14:34 stefan-A7V NetworkManager[794]: <info> Writing DNS information to /sbin/resolvconf
Apr 16 22:14:34 stefan-A7V avahi-daemon[743]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::213:d4ff:fed8:9575.
Apr 16 22:14:34 stefan-A7V avahi-daemon[743]: New relevant interface eth0.IPv6 for mDNS.
Apr 16 22:14:34 stefan-A7V avahi-daemon[743]: Registering new address record for fe80::213:d4ff:fed8:9575 on eth0.*.
Apr 16 22:14:36 stefan-A7V ntpd[790]: Listen normally on 5 eth0 192.168.1.72 UDP 123
Apr 16 22:14:36 stefan-A7V ntpd[790]: Listen normally on 6 eth0 fe80::213:d4ff:fed8:9575 UDP 123
Apr 16 22:14:44 stefan-A7V NetworkManager[794]: <info> Activation (eth0) successful, device activated.
Apr 16 22:14:44 stefan-A7V NetworkManager[794]: <warn> dnsmasq appeared on DBus: :1.27
Apr 16 22:14:44 stefan-A7V NetworkManager[794]: <info> Writing DNS information to /sbin/resolvconf
Apr 16 22:14:54 stefan-A7V NetworkManager[794]: <info> (eth0): IP6 addrconf timed out or failed.
Apr 16 22:14:54 stefan-A7V NetworkManager[794]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Apr 16 22:14:55 stefan-A7V NetworkManager[794]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Apr 16 22:14:55 stefan-A7V NetworkManager[794]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Apr 16 20:15:31 stefan-A7V ntpd[1558]: Listen normally on 3 eth0 192.168.1.72 UDP 123
Apr 16 20:15:31 stefan-A7V ntpd[1558]: Listen normally on 5 eth1 fe80::213:ceff:fe69:dc6c UDP 123
Apr 16 20:15:31 stefan-A7V ntpd[1558]: Listen normally on 6 eth0 fe80::213:d4ff:fed8:9575 UDP 123
Sep 20 02:13:59 stefan-A7V kernel: [    0.000000]   Transmeta GenuineTMx86
Sep 20 02:13:59 stefan-A7V kernel: [    0.085956] NET: Registered protocol family 16
Sep 20 02:13:59 stefan-A7V kernel: [    0.142012] NetLabel: Initializing
Sep 20 02:13:59 stefan-A7V kernel: [    0.142015] NetLabel:  domain hash size = 128
Sep 20 02:13:59 stefan-A7V kernel: [    0.142017] NetLabel:  protocols = UNLABELED CIPSOv4
Sep 20 02:13:59 stefan-A7V kernel: [    0.142032] NetLabel:  unlabeled traffic allowed by default
Sep 20 02:13:59 stefan-A7V kernel: [    0.197463] NET: Registered protocol family 2
Sep 20 02:13:59 stefan-A7V kernel: [    0.197888] NET: Registered protocol family 1
Sep 20 02:13:59 stefan-A7V kernel: [    0.660800] audit: initializing netlink socket (disabled)
Sep 20 02:13:59 stefan-A7V kernel: [    0.782452] NET: Registered protocol family 10
Sep 20 02:13:59 stefan-A7V kernel: [    0.782733] NET: Registered protocol family 17
Sep 20 02:13:59 stefan-A7V kernel: [    1.323283] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Sep 20 02:13:59 stefan-A7V kernel: [    1.356730] 8139too: 8139too Fast Ethernet driver 0.9.28
Sep 20 02:13:59 stefan-A7V kernel: [    1.421162] 8139too 0000:03:00.0 eth0: RealTek RTL8139 at 0x0001d800, 00:13:d4:d8:95:75, IRQ 20
Sep 20 02:13:59 stefan-A7V kernel: [   16.465359] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Sep 20 02:13:59 stefan-A7V kernel: [   16.817637] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
Sep 20 02:13:59 stefan-A7V kernel: [   16.817895] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Sep 20 02:13:59 stefan-A7V kernel: [   17.211646] type=1400 audit(1127175235.780:3): apparmor="STATUS" operation="profile_load" parent=302 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=306 comm="apparmor_parser"
Sep 20 02:13:59 stefan-A7V kernel: [   17.212621] type=1400 audit(1127175235.784:5): apparmor="STATUS" operation="profile_replace" parent=302 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=306 comm="apparmor_parser"
Sep 20 02:13:59 stefan-A7V kernel: [   17.442423] NET: Registered protocol family 31
Sep 20 02:13:59 stefan-A7V kernel: [   21.182125] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
Sep 20 02:14:00 stefan-A7V kernel: [   21.919951] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Sep 20 02:14:01 stefan-A7V avahi-daemon[768]: Network interface enumeration completed.
Sep 20 02:14:01 stefan-A7V NetworkManager[790]: <info> NetworkManager (version 0.9.8.0) is starting...
Sep 20 02:14:01 stefan-A7V NetworkManager[790]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Sep 20 02:14:01 stefan-A7V NetworkManager[790]: <info> WEXT support is enabled
Sep 20 02:14:02 stefan-A7V NetworkManager[790]: <info> DNS: loaded plugin dnsmasq
Sep 20 02:14:02 stefan-A7V NetworkManager[790]:    SCPlugin-Ifupdown: init!
Sep 20 02:14:02 stefan-A7V NetworkManager[790]:    SCPlugin-Ifupdown: update_system_hostname
Sep 20 02:14:02 stefan-A7V NetworkManager[790]:    SCPluginIfupdown: management mode: unmanaged
Sep 20 02:14:02 stefan-A7V NetworkManager[790]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:03:00.0/net/eth0, iface: eth0)
Sep 20 02:14:02 stefan-A7V NetworkManager[790]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:03:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Sep 20 02:14:02 stefan-A7V NetworkManager[790]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:03:03.0/net/eth1, iface: eth1)
Sep 20 02:14:02 stefan-A7V NetworkManager[790]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:03:03.0/net/eth1, iface: eth1): no ifupdown configuration found.
Sep 20 02:14:02 stefan-A7V NetworkManager[790]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Sep 20 02:14:02 stefan-A7V NetworkManager[790]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Sep 20 02:14:02 stefan-A7V NetworkManager[790]:    SCPlugin-Ifupdown: end _init.
Sep 20 02:14:02 stefan-A7V NetworkManager[790]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Sep 20 02:14:02 stefan-A7V NetworkManager[790]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Sep 20 02:14:02 stefan-A7V NetworkManager[790]:    SCPlugin-Ofono: Acquired D-Bus service com.canonical.NMOfono
Sep 20 02:14:02 stefan-A7V NetworkManager[790]:    SCPlugin-Ofono: init!
Sep 20 02:14:02 stefan-A7V NetworkManager[790]:    SCPlugin-Ofono: end _init.
Sep 20 02:14:02 stefan-A7V NetworkManager[790]: <info> Loaded plugin (null): (null)
Sep 20 02:14:02 stefan-A7V NetworkManager[790]:    Ifupdown: get unmanaged devices count: 0
Sep 20 02:14:02 stefan-A7V NetworkManager[790]:    SCPlugin-Ifupdown: (151295816) ... get_connections.
Sep 20 02:14:02 stefan-A7V NetworkManager[790]:    SCPlugin-Ifupdown: (151295816) ... get_connections (managed=false): return empty list.
Sep 20 02:14:02 stefan-A7V NetworkManager[790]:    SCPlugin-Ofono: (151211472) ... get_connections.
Sep 20 02:14:02 stefan-A7V NetworkManager[790]:    SCPlugin-Ofono: (151211472) connections count: 0
Sep 20 02:14:02 stefan-A7V NetworkManager[790]:    Ifupdown: get unmanaged devices count: 0
Sep 20 02:14:02 stefan-A7V NetworkManager[790]: <info> modem-manager is now available
Sep 20 02:14:02 stefan-A7V NetworkManager[790]: <info> monitoring kernel firmware directory '/lib/firmware'.
Sep 20 02:14:02 stefan-A7V NetworkManager[790]: <info> rfkill0: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:1e.0/0000:03:03.0/ieee80211/phy0/rfkill0) (driver ipw2200)
Sep 20 02:14:02 stefan-A7V NetworkManager[790]: <info> WiFi hardware radio set enabled
Sep 20 02:14:02 stefan-A7V NetworkManager[790]: <info> WiFi enabled by radio killswitch; enabled by state file
Sep 20 02:14:02 stefan-A7V NetworkManager[790]: <info> WWAN enabled by radio killswitch; enabled by state file
Sep 20 02:14:02 stefan-A7V NetworkManager[790]: <info> WiMAX enabled by radio killswitch; enabled by state file
Sep 20 02:14:02 stefan-A7V NetworkManager[790]: <info> Networking is enabled by state file
Sep 20 02:14:02 stefan-A7V NetworkManager[790]: <warn> failed to allocate link cache: (-10) Operation not supported
Sep 20 02:14:02 stefan-A7V NetworkManager[790]: <info> (eth0): carrier is OFF
Sep 20 02:14:02 stefan-A7V NetworkManager[790]: <info> (eth0): new Ethernet device (driver: '8139too' ifindex: 2)
Sep 20 02:14:02 stefan-A7V NetworkManager[790]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Sep 20 02:14:02 stefan-A7V NetworkManager[790]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Sep 20 02:14:02 stefan-A7V NetworkManager[790]: <info> (eth0): bringing up device.
Sep 20 02:14:02 stefan-A7V NetworkManager[790]: <info> (eth0): preparing device.
Sep 20 02:14:02 stefan-A7V NetworkManager[790]: <info> (eth0): deactivating device (reason 'managed') [2]
Sep 20 02:14:02 stefan-A7V NetworkManager[790]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:1e.0/0000:03:00.0/net/eth0
Sep 20 02:14:02 stefan-A7V NetworkManager[790]: <info> (eth1): driver supports SSID scans (scan_capa 0x21).
Sep 20 02:14:02 stefan-A7V kernel: [   24.029149] 8139too 0000:03:00.0 eth0: link down
Sep 20 02:14:02 stefan-A7V kernel: [   24.029288] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Sep 20 02:14:02 stefan-A7V kernel: [   24.029794] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Sep 20 02:14:02 stefan-A7V NetworkManager[790]: <info> (eth1): using WEXT for WiFi device control
Sep 20 02:14:02 stefan-A7V NetworkManager[790]: <info> (eth1): new 802.11 WiFi device (driver: 'ipw2200' ifindex: 3)
Sep 20 02:14:02 stefan-A7V NetworkManager[790]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/1
Sep 20 02:14:02 stefan-A7V NetworkManager[790]: <info> (eth1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Sep 20 02:14:02 stefan-A7V NetworkManager[790]: <info> (eth1): bringing up device.
Sep 20 02:14:02 stefan-A7V NetworkManager[790]: <info> (eth1): preparing device.
Sep 20 02:14:02 stefan-A7V NetworkManager[790]: <info> (eth1): deactivating device (reason 'managed') [2]
Sep 20 02:14:02 stefan-A7V NetworkManager[790]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Sep 20 02:14:02 stefan-A7V NetworkManager[790]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Sep 20 02:14:02 stefan-A7V NetworkManager[790]: <info> wpa_supplicant started
Sep 20 02:14:02 stefan-A7V NetworkManager[790]: <info> (eth1) supports 1 scan SSIDs
Sep 20 02:14:02 stefan-A7V NetworkManager[790]: <warn> Trying to remove a non-existant call id.
Sep 20 02:14:02 stefan-A7V NetworkManager[790]: <info> (eth1): supplicant interface state: starting -> ready
Sep 20 02:14:02 stefan-A7V NetworkManager[790]: <info> (eth1): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Sep 20 02:14:02 stefan-A7V NetworkManager[790]: <info> (eth1): supplicant interface state: ready -> inactive
Sep 20 02:14:02 stefan-A7V NetworkManager[790]: <info> (eth1) supports 1 scan SSIDs
Sep 20 02:14:04 stefan-A7V avahi-daemon[768]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::213:ceff:fe69:dc6c.
Sep 20 02:14:04 stefan-A7V avahi-daemon[768]: New relevant interface eth1.IPv6 for mDNS.
Sep 20 02:14:04 stefan-A7V avahi-daemon[768]: Registering new address record for fe80::213:ceff:fe69:dc6c on eth1.*.
Sep 20 02:14:06 stefan-A7V ntpd[774]: Listen normally on 4 eth1 fe80::213:ceff:fe69:dc6c UDP 123
stefan@stefan-A7V:~$ 



```

and

```
stefan@stefan-A7V:~$ dmesg | egrep 'net|eth|sky|sis|via|3c3|3c5|e100|8139|8169|acx|air|ath|atl|ar9|carl|atme|at7|herm|iwl|ipw|rtl8|r81|rt2|rt3|rt6|rt7|tg3|ssb|wl|b43|b44|ori|pri|p5|zd|ndis|wmi|ns8|FW'
[    0.004666] CPU0: Thermal monitoring enabled (TM2)
[    0.119006] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.136029] pci 0000:00:01.0:   bridge window [mem 0xfe100000-0xfe1fffff]
[    0.136151] pci 0000:03:00.0: [10ec:8139] type 00 class 0x020000
[    0.197029] pci 0000:00:01.0:   bridge window [mem 0xfe100000-0xfe1fffff]
[    0.197374] pci_bus 0000:01: resource 1 [mem 0xfe100000-0xfe1fffff]
[    0.660800] audit: initializing netlink socket (disabled)
[    0.698231] thermal LNXTHERM:00: registered as thermal_zone0
[    0.698235] ACPI: Thermal Zone [THRM] (71 C)
[    0.775747] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.788724] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: dc76185d2ae5997387e7fb78078a8a42ed21701f'
[    1.323283] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    1.323313] 8139cp 0000:03:00.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    1.356730] 8139too: 8139too Fast Ethernet driver 0.9.28
[    1.421162] 8139too 0000:03:00.0 eth0: RealTek RTL8139 at 0x0001d800, 00:13:d4:d8:95:75, IRQ 20
[   16.359631] Adding 522236k swap on /dev/sda5.  Priority:-1 extents:1 across:522236k FS
[   16.465359] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.755962] lib80211_crypt: registered algorithm 'NULL'
[   16.788111] libipw: 802.11 data/management/control stack, git-1.1.13
[   16.788117] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   16.817637] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   16.817643] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   16.817895] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   17.145299] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   17.193048] intel_rng: FWH not detected
[   19.052196] fbcon: radeondrmfb (fb0) is primary device
[   21.182125] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   21.919951] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   22.639203] audit_printk_skb: 96 callbacks suppressed
[   24.029149] 8139too 0000:03:00.0 eth0: link down
[   24.029288] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   24.029794] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.110010] Adding 253652k swap on /dev/zram0.  Priority:5 extents:1 across:253652k SSFS
stefan@stefan-A7V:~$ 


```

---

### Post by praseodym on 2014-04-17
```
NetworkManager[794]: <info> (eth1): using WEXT for WiFi device control
```
Are you using Wicd? Lets check
```
ps aux | egrep '[N]etw|[W]icd|[W]pa'
sudo service network-manager stop
sudo killall wpa_supplicant
sudo service network-manager restart
ps aux | egrep '[N]etw|[W]icd|[W]pa'
```
Try deactivating IPv6 in the applet.

---

### Post by N_L on 2014-04-17
```
stefan@stefan-A7V:~$ ps aux | egrep '[N]etw|[W]icd|[W]pa'
root       720  0.0  1.0  44120  5236 ?        Ssl  16:45   0:00 NetworkManager
stefan@stefan-A7V:~$ sudo service network-manager stop
[sudo] password for stefan: 
network-manager stop/waiting
stefan@stefan-A7V:~$ sudo killall wpa_supplicant 
stefan@stefan-A7V:~$ sudo service network-manager restart
stop: Unknown instance: 
network-manager start/running, process 1428
stefan@stefan-A7V:~$ ps aux | egrep '[N]etw|[W]icd|[W]pa'
root      1428  0.2  1.0  44120  5164 ?        Ssl  16:50   0:00 NetworkManager

```


Deactivate ipv6 where? In network connections I only have ethernet available which I'm not using at the moment.

---

### Post by praseodym on 2014-04-17
```
[   17.145299] ipw2200: Detected geography ZZM ([COLOR="#FF0000"]11[/COLOR] 802.11bg channels, 0 802.11a channels)
```
Which country do you live? On which channel does the router send? Change the channel to a fixed one between 1-11 and change the settings to b/g only, not b/g/n

---

### Post by N_L on 2014-04-17
I live in Montenegro. It's set on channel 6 (fixed) and mode is 802.11g + 802.11b(Mixed)

---

### Post by praseodym on 2014-04-17
Check:
```

sudo apt-get install iw
iw reg get
sudo iw reg set ME
iw reg get
iwlist chan
```

---

### Post by N_L on 2014-04-17
Downloaded iw and here's the rest of stuff
```
stefan@stefan-A7V:~$ iw reg get
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
stefan@stefan-A7V:~$ sudo iw reg set ME
stefan@stefan-A7V:~$ iwlist chan
lo        no frequency information.

eth0      no frequency information.

eth1      11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Current Channel:0


```

---

### Post by praseodym on 2014-04-18
> ```
          Current Channel:0
```
Did you check the channel? Router firmware is up-to-date? Tried to reset the router to default settings?

---

### Post by N_L on 2014-04-18
I did, channel is set to 6. Everything about router is fine and working fine with all other devices, heck it even worked with this laptop while win xp was on it before. And not just the router, I turn on tethering on my phone and try to connect and same thing happens, same thing happens on any network in vicinity, it doesn't give me wrong password just no reply, I don't think it's even trying to connect and I have no idea why.

---

### Post by praseodym on 2014-04-18
In some routers you need to explicitly add the device MAC address. Tried that? Check
```

ifconfig eth1
```

---

### Post by N_L on 2014-04-18
I have that off, had it on a while back but I turned it off, I'll paste icfonfig soon

---

### Post by N_L on 2014-04-19
Ok did the ifconfig and it gave info about ethernet hwd, I think I'm gonna try to reinstall win xp, and if it runs poorly I'll be back at lubuntu and see if this can be fixed, maybe another install will do it, although even at install it didn't offer me connections I could just pick my wlan card


Edit: Ran lubuntu from USB with try option and wifi works there, different window pops up to connect, one that says authenticate blabla... dafuq. I'll reinstall now and see if it fixes itself.

Editx2: reinstall fixed it, wonder what was the problem...

---

