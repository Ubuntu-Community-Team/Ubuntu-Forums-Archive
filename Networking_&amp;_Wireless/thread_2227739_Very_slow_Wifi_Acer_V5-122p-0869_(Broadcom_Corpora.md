---
title: "Very slow Wifi: Acer V5-122p-0869 (Broadcom Corporation BCM43142)"
date: 2014-06-03
forum: Networking &amp; Wireless
---

### Post by barbara6 on 2014-06-03
I'm a new Ubuntu user :) 

Wifi is extrememly slow on this machine. Webpages take 30-45 seconds to fully load. Prior to installing Ubuntu, Windows 8.1 on this machine loaded pages immediately. It must be a driver issue?

I ran the following into terminal, per a sticky in this forum:

```
lspci -nn
```

and output: 

```
01:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
```

Is there anything I can do to make this machine faster? There is no ethernet on the laptop.

---

### Post by varunendra on 2014-06-05
Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

I could ask you to run and post back the outputs of a bunch of individual commands, but the above script contains it all, and much more. :)

---

### Post by barbara6 on 2014-06-08
Hello varunendra,

Thank you for responding :) I ran the script. Here is the output:

```


    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

vg44 3.13.0-29-generic x86_64,  Ubuntu 14.04 LTS, trusty

CPU    : AMD A4-1250 APU with Radeon(TM) HD Graphics
Memory : 3332 MB
Uptime : 22:03:27 up 1 day,  1:09,  2 users,  load average: 0.39, 0.63, 0.62


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

01:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e078]
    Kernel driver in use: wl


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 002: ID 064e:c400 Suyin Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 04f3:009d Elan Microelectronics Corp. 
Bus 004 Device 002: ID 0489:e055 Foxconn / Hon Hai 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11abg  ESSID:"HOME3"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC C-01 HOME3>   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface                 Soft blocked  Hard blocked
0: phy0: Wireless LAN               no            no
1: brcmwl-0: Wireless LAN           no            no
3: acer-wireless: Wireless LAN      no            no
8: hci0: Bluetooth                  no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

acer_wmi               32522  0 
sparse_keymap          13948  1 acer_wmi
wl                   4207846  0 
lib80211               14381  2 wl,lib80211_crypt_tkip
cfg80211              484040  1 wl
wmi                    19177  1 acer_wmi
video                  19476  1 acer_wmi


module parameters ~~~~~~~~~~~~~~~~~~

acer_wmi      (5): brightness=-1 | ec_raw_mode=N | force_series=0 | mailled=-1 | threeg=-1
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
video         (3): allow_duplicates=N | brightness_switch_enabled=Y | use_native_backlight=-1
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
=================================o=============o========o==============o=========o===========o==============o===========
 Interface & ID                  | Type        | Driver | State        | Default | Speed     | Support      | HW Addr   
=================================o=============o========o==============o=========o===========o==============o===========
 wlan0  [HOME3] | 802.11 WiFi | wl     | connected    | yes     | 6 Mb/s    | WEP/WPA/WPA2 | <MAC wlan0>

    NETGEAR08:       Infra, <MAC C-03 NETGEAR08>, Freq 2442 MHz, Rate 54 Mb/s, Strength 12 WPA2
    *HOME3: Infra, <MAC C-01 HOME3>, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA2

    Address:         192.168.1.125
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             75.75.75.75
    DNS:             75.75.76.76
    DNS:             192.168.1.1
---------------------------------+-------------+--------+--------------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~

HOME3 : ssid=HOME3 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
NETGEAR              : ssid=NETGEAR | bssid=<MAC ID removed> | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1
search hsd1.or.comcast.net


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 1.477/10.304/19.131/8.827 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.089/0.096/0.103/0.007 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     26 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 14 (2.484 GHz)
          Channel 36 (5.18 GHz)
          Channel 38 (5.19 GHz)
          Channel 40 (5.2 GHz)
          Channel 42 (5.21 GHz)
          Channel 44 (5.22 GHz)
          Channel 46 (5.23 GHz)
          Channel 48 (5.24 GHz)
          Channel 149 (5.745 GHz)
          Channel 153 (5.765 GHz)
          Channel 157 (5.785 GHz)
          Channel 161 (5.805 GHz)
          Channel 165 (5.825 GHz)

          Current Frequency:2.462 GHz (Channel 11)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 HOME3>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"HOME3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 96ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 DLYGH>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=16/70  Signal level=-94 dBm  
                    Encryption key:on
                    ESSID:"DLYGH"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 96ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 NETGEAR08>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR08"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 96ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[wl]
filename:       /lib/modules/3.13.0-29-generic/updates/dkms/wl.ko
srcversion:     FF25FE784DC6BDFF69DAFCB
depends:        cfg80211,lib80211
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[lib80211]
filename:       /lib/modules/3.13.0-29-generic/kernel/net/wireless/lib80211.ko
srcversion:     84DEF767F03D28E373F18E5
depends:        

[cfg80211]
filename:       /lib/modules/3.13.0-29-generic/kernel/net/wireless/cfg80211.ko
srcversion:     8B3D642D1F2E6406EF33F74
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x14e4:0x4365 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-29-generic root=UUID=4cae3962-97b8-4020-9265-7ca90a0c1e7a ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    3.406527] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    3.407350] audit: initializing netlink socket (disabled)
[    4.118794] wmi: Mapper loaded
[   17.222066] wl: module license 'MIXED/Proprietary' taints kernel.
[   17.520586] wl: module verification failed: signature and/or  required key missing - tainting kernel
[   17.731150] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   17.897380] wlan0: Broadcom BCM4365 802.11 Hybrid Wireless Controller 6.30.223.141 (r415941)
[   18.151587] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.207844] usb 4-2: Direct firmware load failed with error -2
[   19.280201] acer_wmi: Acer Laptop ACPI-WMI Extras
[   19.280242] acer_wmi: Function bitmap for Communication Button: 0x801
[   19.299531] acer_wmi: Brightness must be controlled by acpi video driver
[   19.514735] Bluetooth: can't load firmware, may not work correctly
[   19.598601] acer_wmi: Enabling Launch Manager failed: 0xe2 - 0x0
[  455.056319] WARNING: CPU: 0 PID: 171 at /build/buildd/linux-3.13.0/drivers/base/firmware_class.c:1089 _request_firmware+0x5d9/0xb10()
[  455.056422] Modules linked in: dm_crypt acer_wmi sparse_keymap amd_freq_sensitivity kvm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd rfcomm snd_seq_midi snd_seq_midi_event bnep snd_hda_codec_realtek btusb uvcvideo snd_hda_codec_hdmi snd_rawmidi videobuf2_vmalloc videobuf2_memops snd_hda_intel videobuf2_core bluetooth joydev lib80211_crypt_tkip snd_hda_codec hid_multitouch snd_hwdep videodev serio_raw edac_core snd_pcm wl(POF) k10temp fam15h_power edac_mce_amd snd_seq binfmt_misc lib80211 i2c_piix4 snd_page_alloc cfg80211 snd_seq_device snd_timer snd soundcore parport_pc mac_hid ppdev lp parport usbhid hid radeon psmouse sdhci_pci ahci i2c_algo_bit sdhci libahci ttm wmi drm_kms_helper drm video
[  455.056523]  [<ffffffff814a3229>] _request_firmware+0x5d9/0xb10
[  455.056529]  [<ffffffff814a3794>] request_firmware+0x34/0x50
[  455.056651] usb 4-2: firmware: fw-0489_e055.hcd will not be loaded
[  455.056660] Bluetooth: can't load firmware, may not work correctly
[ 1770.965371] WARNING: CPU: 1 PID: 171 at /build/buildd/linux-3.13.0/drivers/base/firmware_class.c:1089 _request_firmware+0x5d9/0xb10()
[ 1770.965473] Modules linked in: dm_crypt acer_wmi sparse_keymap amd_freq_sensitivity kvm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd rfcomm snd_seq_midi snd_seq_midi_event bnep snd_hda_codec_realtek btusb uvcvideo snd_hda_codec_hdmi snd_rawmidi videobuf2_vmalloc videobuf2_memops snd_hda_intel videobuf2_core bluetooth joydev lib80211_crypt_tkip snd_hda_codec hid_multitouch snd_hwdep videodev serio_raw edac_core snd_pcm wl(POF) k10temp fam15h_power edac_mce_amd snd_seq binfmt_misc lib80211 i2c_piix4 snd_page_alloc cfg80211 snd_seq_device snd_timer snd soundcore parport_pc mac_hid ppdev lp parport usbhid hid radeon psmouse sdhci_pci ahci i2c_algo_bit sdhci libahci ttm wmi drm_kms_helper drm video
[ 1770.965571]  [<ffffffff814a3229>] _request_firmware+0x5d9/0xb10
[ 1770.965577]  [<ffffffff814a3794>] request_firmware+0x34/0x50
[ 1770.965702] usb 4-2: firmware: fw-0489_e055.hcd will not be loaded
[ 1770.965710] Bluetooth: can't load firmware, may not work correctly
[17561.384774] WARNING: CPU: 0 PID: 2900 at /build/buildd/linux-3.13.0/drivers/base/firmware_class.c:1089 _request_firmware+0x5d9/0xb10()
[17561.384877] Modules linked in: dm_crypt acer_wmi sparse_keymap amd_freq_sensitivity kvm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd rfcomm snd_seq_midi snd_seq_midi_event bnep snd_hda_codec_realtek btusb uvcvideo snd_hda_codec_hdmi snd_rawmidi videobuf2_vmalloc videobuf2_memops snd_hda_intel videobuf2_core bluetooth joydev lib80211_crypt_tkip snd_hda_codec hid_multitouch snd_hwdep videodev serio_raw edac_core snd_pcm wl(POF) k10temp fam15h_power edac_mce_amd snd_seq binfmt_misc lib80211 i2c_piix4 snd_page_alloc cfg80211 snd_seq_device snd_timer snd soundcore parport_pc mac_hid ppdev lp parport usbhid hid radeon psmouse sdhci_pci ahci i2c_algo_bit sdhci libahci ttm wmi drm_kms_helper drm video
[17561.384975]  [<ffffffff814a3229>] _request_firmware+0x5d9/0xb10
[17561.384981]  [<ffffffff814a3794>] request_firmware+0x34/0x50
[17561.385146] usb 4-2: firmware: fw-0489_e055.hcd will not be loaded
[17561.385154] Bluetooth: can't load firmware, may not work correctly
[22275.471678] WARNING: CPU: 0 PID: 2900 at /build/buildd/linux-3.13.0/drivers/base/firmware_class.c:1089 _request_firmware+0x5d9/0xb10()
[22275.471783] Modules linked in: nls_iso8859_1 usb_storage dm_crypt acer_wmi sparse_keymap amd_freq_sensitivity kvm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd rfcomm snd_seq_midi snd_seq_midi_event bnep snd_hda_codec_realtek btusb uvcvideo snd_hda_codec_hdmi snd_rawmidi videobuf2_vmalloc videobuf2_memops snd_hda_intel videobuf2_core bluetooth joydev lib80211_crypt_tkip snd_hda_codec hid_multitouch snd_hwdep videodev serio_raw edac_core snd_pcm wl(POF) k10temp fam15h_power edac_mce_amd snd_seq binfmt_misc lib80211 i2c_piix4 snd_page_alloc cfg80211 snd_seq_device snd_timer snd soundcore parport_pc mac_hid ppdev lp parport usbhid hid radeon psmouse sdhci_pci ahci i2c_algo_bit sdhci libahci ttm wmi drm_kms_helper drm video
[22275.471881]  [<ffffffff814a3229>] _request_firmware+0x5d9/0xb10
[22275.471887]  [<ffffffff814a3794>] request_firmware+0x34/0x50
[22275.472021] usb 4-2: firmware: fw-0489_e055.hcd will not be loaded
[22275.472028] Bluetooth: can't load firmware, may not work correctly
[23511.506404] WARNING: CPU: 1 PID: 2900 at /build/buildd/linux-3.13.0/drivers/base/firmware_class.c:1089 _request_firmware+0x5d9/0xb10()
[23511.506509] Modules linked in: nls_iso8859_1 usb_storage dm_crypt acer_wmi sparse_keymap amd_freq_sensitivity kvm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd rfcomm snd_seq_midi snd_seq_midi_event bnep snd_hda_codec_realtek btusb uvcvideo snd_hda_codec_hdmi snd_rawmidi videobuf2_vmalloc videobuf2_memops snd_hda_intel videobuf2_core bluetooth joydev lib80211_crypt_tkip snd_hda_codec hid_multitouch snd_hwdep videodev serio_raw edac_core snd_pcm wl(POF) k10temp fam15h_power edac_mce_amd snd_seq binfmt_misc lib80211 i2c_piix4 snd_page_alloc cfg80211 snd_seq_device snd_timer snd soundcore parport_pc mac_hid ppdev lp parport usbhid hid radeon psmouse sdhci_pci ahci i2c_algo_bit sdhci libahci ttm wmi drm_kms_helper drm video
[23511.506605]  [<ffffffff814a3229>] _request_firmware+0x5d9/0xb10
[23511.506611]  [<ffffffff814a3794>] request_firmware+0x34/0x50
[23511.506730] usb 4-2: firmware: fw-0489_e055.hcd will not be loaded
[23511.506737] Bluetooth: can't load firmware, may not work correctly
[24149.852824] ERROR @wl_dev_intvar_get : error (-1)
[24149.852844] ERROR @wl_cfg80211_get_tx_power : error (-1)

    ======== Done ========

```

---

### Post by varunendra on 2014-06-11
Looks like our schedules are not allowing us to respond sooner than 3 days. :p

Anyway, I can't find anything suspicious in the script (those error messages in the dmesg don't seem relevant to me, but I'm not sure to be honest). The only thing I can suggest for now is to try setting "IPv6" in Network Manager to "Ignore". If that doesn't help, I may be unable to help further (due to lack of both ideas, and time to dig more ideas).

---

