---
title: "Wireless constantly disconnects (Access point changed)"
date: 2013-10-18
forum: Networking &amp; Wireless
---

### Post by card06 on 2013-10-18
Hello everyone
I'm having a problem with the wireless in my laptop. It hardly works, it may work for some minutes but after that it disconnects and then after a minute or so it reconnects but that disconnect/reconnect process is not shown as a notification i.e. my internet simply stops working. I know that the problem is only in my computer because I'm currently using my tethering from my smartphone and the internet works perfect. After some testing I discovered that the access point of my wireless connection changes when my internet connection breaks, here is what I did

------ (With working internet)
camo@Studio-1458:~$ iwconfig
lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"LSK"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 9C:C7:A6:4C:CE:BE   
          Bit Rate=6.5 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality=32/70  Signal level=-78 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2   Missed beacon:0


eth0      no wireless extensions.

------- (With broken internet)
lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"LSK"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 80:1F:02:C0:CA:3C   
          Bit Rate=72.2 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality=70/70  Signal level=-35 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:14   Missed beacon:0


eth0      no wireless extensions.



Thanks in advance for the help :)

---

### Post by varunendra on 2013-10-18
Welcome to the forums card06 !

Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates. It will give us a comprehensive information of your overall wireless setup.

While posting the outputs, please use the '**Code**' box. It preserves its formatting and makes your post cleaner, compact and more readable. Follow the "Using Code Tags" link in my signature to see how.

---

### Post by card06 on 2013-10-21
Hello Varun
As you requested I ran the script in the link that you gave me and here is the display. I think I should also add something else that I noticed: I moved recently and in my new flat they use some kind of "repeaters" devices for the internet. I noticed that if I turn off the closest one to my position, and move my computer to another position, then the problem with the internet diminish but it doesn't disappear. I hope this information would be helpful. 

```




*************** info trace ***************


***** uname -a *****


Linux Studio-1458 3.2.0-54-generic #82-Ubuntu SMP Tue Sep 10 20:08:42 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


***** lsb_release *****


Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.3 LTS
Release:	12.04
Codename:	precise


***** lspci *****


02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe [14e4:1692] (rev 01)
	Subsystem: Dell Device [1028:0414]
	Kernel driver in use: tg3
--
05:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
	Subsystem: Dell Inspiron M5010 / XPS 8300 [1028:0010]
	Kernel driver in use: brcmsmac


***** lsusb *****


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 004: ID 0c45:6407 Microdia 
Bus 001 Device 005: ID 413c:8161 Dell Computer Corp. Integrated Keyboard
Bus 001 Device 006: ID 413c:8162 Dell Computer Corp. Integrated Touchpad [Synaptics]


***** PCMCIA Card Info *****




***** iwconfig *****


wlan0     IEEE 802.11bgn  ESSID:"LSK"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC address removed>   
          Bit Rate=26 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=39/70  Signal level=-71 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:26  Invalid misc:746   Missed beacon:0




***** rfkill *****


0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


***** lsmod *****


bcma                   26696  0 
brcmsmac              570930  0 
mac80211              506862  1 brcmsmac
brcmutil               15139  1 brcmsmac
cfg80211              205774  2 brcmsmac,mac80211
crc8                   12893  1 brcmsmac
cordic                 12574  1 brcmsmac


***** nm-tool *****


NetworkManager Tool


State: connected (global)


- Device: wlan0  [LSK] ---------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           26 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    *LSK:            Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2
    FRITZ!Box 7312:  Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    LSK:             Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WPA2


  IPv4 Settings:
    Address:         192.168.178.31
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.178.1


    DNS:             192.168.178.1




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off






***** NetworkManager.state *****


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


***** NetworkManager.conf *****




[main]
plugins=ifupdown,keyfile
dns=dnsmasq


no-auto-default=<MAC address removed>,


[ifupdown]
managed=false


***** interfaces *****


auto lo
iface lo inet loopback




***** iwlist *****


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"LSK"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000162c51cb180
                    Extra: Last beacon: 1008ms ago
                    IE: Unknown: 00034C534B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 0706444520010D14
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 331AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D16010D0600000000000000000000000000000000000000
                    IE: Unknown: 3416010D0600000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD650050F204104A0001101044000102103B000103104700109338D735A7AE47747E9F9CC7A64CCE101021000341564D1023000446426F78102400043030303010420004303030301054000800060050F20400011011000446426F78100800020188103C000103
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"LSK"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000016292677238
                    Extra: Last beacon: 1108ms ago
                    IE: Unknown: 00034C534B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050400030000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6E181EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601050000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336E181EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401050000000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C0201E0
                    IE: Unknown: DD0E0050F204104A0001101044000102




***** resolv.conf *****


nameserver 127.0.0.1
search fritz.box


***** blacklist *****


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


[/etc/modprobe.d/blacklist-local.conf]
blacklist wl


***** modinfo *****


filename:       /lib/modules/3.2.0-54-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     722AA6B08A43CF879452476
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004331sv*sd*bc*sc*i*
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.2.0-54-generic SMP mod_unload modversions 


filename:       /lib/modules/3.2.0-54-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     99DF92A40D4267D7A7248E2
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
depends:        mac80211,brcmutil,cfg80211,cordic,crc8
intree:         Y
vermagic:       3.2.0-54-generic SMP mod_unload modversions 


filename:       /lib/modules/3.2.0-54-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     DB27B1DE461446E6FBADCFE
depends:        
intree:         Y
vermagic:       3.2.0-54-generic SMP mod_unload modversions 




***** udev rules *****


# PCI device 0x14e4:0x1692 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x14e4:0x4727 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.2/0000:05:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


***** dmesg *****


[   20.029771] brcmsmac 0000:05:00.0: bus 5 slot 0 func 0 irq 10
[   20.029819] brcmsmac 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   20.029828] brcmsmac 0000:05:00.0: setting latency timer to 64
[   20.865102] ieee80211 phy0: brcms_ops_config: change monitor mode: false (implement)
[   20.865106] ieee80211 phy0: brcms_ops_config: change power-save mode: false (implement)
[   20.865845] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   20.866173] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.866367] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  122.075114] wlan0: authenticate with <MAC address removed> (try 1)
[  122.076868] wlan0: authenticated
[  122.077034] wlan0: associate with <MAC address removed> (try 1)
[  122.081021] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[  122.081024] wlan0: associated
[  122.081028] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[  122.081701] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[  122.081709] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: associated
[  122.081716] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[  122.082163] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  122.770352] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[  132.291175] wlan0: no IPv6 routers present
[ 1161.257129] WARNING: at /build/buildd/linux-3.2.0/drivers/net/wireless/brcm80211/brcmsmac/main.c:8241 brcms_c_wait_for_tx_completion+0x99/0xb0 [brcmsmac]()
[ 1161.257138] Modules linked in: pci_stub vboxpci(O) vboxnetadp(O) vboxnetflt(O) vboxdrv(O) joydev parport_pc ppdev rfcomm bnep bluetooth binfmt_misc bcma arc4 snd_hda_codec_hdmi snd_hda_codec_realtek brcmsmac mac80211 uvcvideo videodev v4l2_compat_ioctl32 dell_wmi sparse_keymap brcmutil dell_laptop dcdbas cfg80211 crc8 cordic snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event mei(C) snd_seq i915 drm_kms_helper drm psmouse serio_raw i2c_algo_bit snd_timer snd_seq_device intel_ips snd wmi soundcore snd_page_alloc video mac_hid coretemp lp parport tg3 usbhid hid
[ 1161.257249]  [<ffffffffa0378bc9>] brcms_c_wait_for_tx_completion+0x99/0xb0 [brcmsmac]
[ 1161.257259]  [<ffffffffa03671bb>] brcms_ops_flush+0x3b/0x60 [brcmsmac]
[ 6073.002248] ieee80211 phy0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 7
[ 6073.002279] ieee80211 phy0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 7
[ 6073.002354] ieee80211 phy0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 7
[ 6073.496099] ieee80211 phy0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 8
[ 6074.360013] ieee80211 phy0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 10
[ 6074.360034] ieee80211 phy0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 10
[ 7151.610198] ieee80211 phy0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 8
[ 8349.299499] ieee80211 phy0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 9
[14219.139048] wlan0: direct probe to <MAC address removed> (try 1/3)
[14219.335293] wlan0: direct probe to <MAC address removed> (try 2/3)
[14219.534835] wlan0: direct probe to <MAC address removed> (try 3/3)
[14219.734523] wlan0: direct probe to <MAC address removed> timed out
[14225.854221] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[14225.854230] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[14225.854235] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 1 (implement)
[14225.854240] wlan0: deauthenticating from <MAC address removed> by local choice (reason=2)
[14225.889558] wlan0: authenticate with <MAC address removed> (try 1)
[14225.891340] wlan0: authenticated
[14225.894961] wlan0: associate with <MAC address removed> (try 1)
[14225.898608] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[14225.898614] wlan0: associated
[14225.898619] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[14225.899261] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[14225.899272] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: associated
[14225.899284] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)


****************** done ******************



```

Thanks for the help

---

### Post by varunendra on 2013-10-22
Your setup doesn't look normal and definitely not at defaults. I am mostly bothered by the error/warning messages in dmesg part, but lets first get some usual suspects out of the way -
> **card06 said:**
> 
```

  Wireless Access Points (* = current AP)
   ** *LSK:            Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 49 [COLOR="#FF0000"]WPA WPA2[/COLOR]**
    FRITZ!Box 7312:  Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    LSK:             Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WPA2
....
....
[/etc/modprobe.d/blacklist-local.conf]
**[COLOR="#FF0000"]blacklist wl[/COLOR]**
....
....
***** udev rules *****

# PCI device 0x14e4:0x1692 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x14e4:0x4727 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


[B]# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.2/0000:05:00.0 [COLOR="#FF0000"](wl)[/COLOR]
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="[COLOR="#FF0000"]eth1[/COLOR]"[/B]


***** dmesg *****

....
[ 1161.257129] WARNING: at /build/buildd/linux-3.2.0/drivers/net/wireless/brcm80211/brcmsmac/main.c:8241 brcms_c_wait_for_tx_completion+0x99/0xb0 [brcmsmac]()
....
[ 1161.257249]  [<ffffffffa0378bc9>] brcms_c_wait_for_tx_completion+0x99/0xb0 [brcmsmac]
[ 1161.257259]  [<ffffffffa03671bb>] brcms_ops_flush+0x3b/0x60 [brcmsmac]
[B][ 6073.002248] ieee80211 phy0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 7
[ 6073.002279] ieee80211 phy0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 7
[ 6073.002354] ieee80211 phy0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 7
[ 6073.496099] ieee80211 phy0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 8
[ 6074.360013] ieee80211 phy0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 10
[ 6074.360034] ieee80211 phy0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 10
[ 7151.610198] ieee80211 phy0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 8
[ 8349.299499] ieee80211 phy0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 9[/B]
[14219.139048] wlan0: direct probe to <MAC address removed> (try 1/3)
[14219.335293] wlan0: direct probe to <MAC address removed> (try 2/3)
[14219.534835] wlan0: direct probe to <MAC address removed> (try 3/3)
[14219.734523] wlan0: direct probe to <MAC address removed> timed out
[14225.854221] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[14225.854230] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[14225.854235] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 1 (implement)
[14225.854240] wlan0: deauthenticating from <MAC address removed> by local choice (reason=2)
[14225.889558] wlan0: authenticate with <MAC address removed> (try 1)
[14225.891340] wlan0: authenticated
[14225.894961] wlan0: associate with <MAC address removed> (try 1)
[14225.898608] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[14225.898614] wlan0: associated
[14225.898619] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[14225.899261] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[14225.899272] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: associated
[14225.899284] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)

****************** done ******************

```

1) Do you have admin access to the router/access-points? If yes, please change the encryption to pure WPA2-PSK (AES/CCMP). No WPA/WPA2 mixed mode, no TKIP.

2) Secondly, why did you need to blacklist the "wl" driver? Is it currently installed? Check with -
```
dpkg -l | grep bcmwl
modinfo wl
```
Does any of these return any output? If yes, purge that driver -
```
sudo apt-get purge bcmwl-kernel-source
```
..and remove that blacklist file, we don't need it if everything else is as it should be -
```
sudo rm /etc/modprobe.d/blacklist-local.conf
```

3) Thirdly, the udev rules file contains the entry which may be confusing the system, even if momentarily. So remove it, it'll be auto-generated immediately or at next boot, with only desired entries -
```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```

4) And lastly, try telling the Network Manager to only associate with a fixed, desired access-point by saving the access-point's MAC address in its "BSSID" field.
*(Network Manager > Edit Connection > "Wireless" tab > edit your connection > "Wireless" tab > save AP's MAC address in "BSSID" field)*
This is not really a 'fix' (binding NM to a specific AP), but let's just see if it helps.

About the dmesg part quoted above, did you try any version of brcmsmac (or brcm80211) driver from another source? The path /build... doesn't exist in a default setup.

Please answer above and try what is suggested. Let me know it helps or not and accordingly we may take further steps.

---

### Post by card06 on 2013-10-22
Hello Varun
I would like to answer your request. 
 1) I don't have admin access to the router/access points

 2) I didn't blacklisted the "wl" driver, actually this is the first time I touch the wireless configuration through the command line. Regarding the driver, when I started with Ubuntu, I installed version 10.04 and in that version my wireless didn't work, so I installed proprietary software using the "additional drivers" software provided by Ubuntu for the Broadcom drivers, after that my drivers worked, nevertheless when I moved here my wireless stopped working so I decided to uninstall it and then it started to "work" but with this connection problem. Regarding the third point, in 2) I removed that blacklist file as you requested.

 3) I removed the udev rules as you requested.

4) I edited my wireless configuration to bind it only with a specific access point.

My internet is working perfectly so far, nevertheless as you said binding my NM to a specific access point is not really what I would like to do as a solution. Do you have any additional advice for me?

This is the result of re-running the script that you gave me the link to.

```

*************** info trace ***************


***** uname -a *****


Linux Studio-1458 3.2.0-54-generic #82-Ubuntu SMP Tue Sep 10 20:08:42 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


***** lsb_release *****


Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.3 LTS
Release:	12.04
Codename:	precise


***** lspci *****


02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe [14e4:1692] (rev 01)
	Subsystem: Dell Device [1028:0414]
	Kernel driver in use: tg3
--
05:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
	Subsystem: Dell Inspiron M5010 / XPS 8300 [1028:0010]
	Kernel driver in use: brcmsmac


***** lsusb *****


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 004: ID 0c45:6407 Microdia 
Bus 001 Device 005: ID 413c:8161 Dell Computer Corp. Integrated Keyboard
Bus 001 Device 006: ID 413c:8162 Dell Computer Corp. Integrated Touchpad [Synaptics]


***** PCMCIA Card Info *****




***** iwconfig *****


wlan0     IEEE 802.11bgn  ESSID:"LSK"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC address removed>   
          Bit Rate=72.2 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=66/70  Signal level=-44 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:24   Missed beacon:0




***** rfkill *****


0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


***** lsmod *****


bcma                   26696  0 
brcmsmac              570930  0 
mac80211              506862  1 brcmsmac
brcmutil               15139  1 brcmsmac
cfg80211              205774  2 brcmsmac,mac80211
crc8                   12893  1 brcmsmac
cordic                 12574  1 brcmsmac


***** nm-tool *****


NetworkManager Tool


State: connected (global)


- Device: wlan0  [LSK] ---------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           72 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    LSK:             Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA2
    FRITZ!Box 7312:  Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    LSK:             Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    *LSK:            Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 76 WPA2


  IPv4 Settings:
    Address:         192.168.178.31
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.178.1


    DNS:             192.168.178.1




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off






***** NetworkManager.state *****


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


***** NetworkManager.conf *****




[main]
plugins=ifupdown,keyfile
dns=dnsmasq


no-auto-default=<MAC address removed>,


[ifupdown]
managed=false


***** interfaces *****


auto lo
iface lo inet loopback




***** iwlist *****


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"LSK"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000bb062177
                    Extra: Last beacon: 180ms ago
                    IE: Unknown: 00034C534B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6E181EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601050000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD800050F204104A0001101044000102103B0001031047001063041253101920061228801F02C0CA3C102100064D6564696F6E102300064D6564696F6E1024000D45562D323030392D30322D30361042000F3132333435363738393031323334371054000800060050F20400011011000B576972656C657373204150100800020086
                    IE: Unknown: DD1E00904C336E181EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401050000000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C0201E0
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"LSK"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001737deaa180
                    Extra: Last beacon: 288ms ago
                    IE: Unknown: 00034C534B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 0706444520010D14
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AEE111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 331AEE111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D16010D0600000000000000000000000000000000000000
                    IE: Unknown: 3416010D0600000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD650050F204104A0001101044000102103B000103104700109338D735A7AE47747E9F9CC7A64CCE101021000341564D1023000446426F78102400043030303010420004303030301054000800060050F20400011011000446426F78100800020188103C000103
          Cell 03 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"LSK"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001734b2a7176
                    Extra: Last beacon: 820ms ago
                    IE: Unknown: 00034C534B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050401030000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6E181EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601050000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336E181EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401050000000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C0201E0
                    IE: Unknown: DD0E0050F204104A0001101044000102




***** resolv.conf *****


nameserver 127.0.0.1
search fritz.box


***** blacklist *****


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


***** modinfo *****


filename:       /lib/modules/3.2.0-54-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     722AA6B08A43CF879452476
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004331sv*sd*bc*sc*i*
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.2.0-54-generic SMP mod_unload modversions 


filename:       /lib/modules/3.2.0-54-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     99DF92A40D4267D7A7248E2
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
depends:        mac80211,brcmutil,cfg80211,cordic,crc8
intree:         Y
vermagic:       3.2.0-54-generic SMP mod_unload modversions 


filename:       /lib/modules/3.2.0-54-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     DB27B1DE461446E6FBADCFE
depends:        
intree:         Y
vermagic:       3.2.0-54-generic SMP mod_unload modversions 




***** udev rules *****


# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.2/0000:05:00.0 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


***** dmesg *****


[   20.087998] brcmsmac 0000:05:00.0: bus 5 slot 0 func 0 irq 10
[   20.088050] brcmsmac 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   20.088060] brcmsmac 0000:05:00.0: setting latency timer to 64
[   21.262036] ieee80211 phy0: brcms_ops_config: change monitor mode: false (implement)
[   21.262041] ieee80211 phy0: brcms_ops_config: change power-save mode: false (implement)
[   21.262711] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   21.263062] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.263337] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   38.969125] wlan0: authenticate with <MAC address removed> (try 1)
[   38.970882] wlan0: authenticated
[   38.971065] wlan0: associate with <MAC address removed> (try 1)
[   38.974918] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[   38.974922] wlan0: associated
[   38.974925] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[   38.975804] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[   38.975812] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: associated
[   38.975818] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[   38.976344] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   39.601286] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[   49.788671] wlan0: no IPv6 routers present
[  142.610001] WARNING: at /build/buildd/linux-3.2.0/drivers/net/wireless/brcm80211/brcmsmac/main.c:8241 brcms_c_wait_for_tx_completion+0x99/0xb0 [brcmsmac]()
[  142.610008] Modules linked in: pci_stub vboxpci(O) vboxnetadp(O) vboxnetflt(O) vboxdrv(O) joydev snd_hda_codec_hdmi snd_hda_codec_realtek bnep parport_pc rfcomm ppdev bluetooth binfmt_misc bcma arc4 uvcvideo videodev v4l2_compat_ioctl32 snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi dell_wmi sparse_keymap snd_seq_midi_event dell_laptop dcdbas snd_seq snd_timer snd_seq_device intel_ips snd i915 brcmsmac drm_kms_helper drm mac80211 psmouse serio_raw soundcore brcmutil cfg80211 crc8 cordic snd_page_alloc i2c_algo_bit wmi mei(C) video mac_hid coretemp lp parport tg3 usbhid hid
[  142.610149]  [<ffffffffa0291bc9>] brcms_c_wait_for_tx_completion+0x99/0xb0 [brcmsmac]
[  142.610162]  [<ffffffffa02801bb>] brcms_ops_flush+0x3b/0x60 [brcmsmac]
[  444.113464] wlan0: direct probe to <MAC address removed> (try 1/3)
[  444.119167] wlan0: direct probe responded
[  444.173058] wlan0: authenticate with <MAC address removed> (try 1)
[  444.174704] wlan0: authenticated
[  444.176930] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  444.176974] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[  444.176984] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 1 (implement)
[  444.237286] wlan0: associate with <MAC address removed> (try 1)
[  444.241085] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  444.241091] wlan0: associated
[  444.243372] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[  444.243385] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: associated
[  444.243399] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[  563.722964] wlan0: direct probe to <MAC address removed> (try 1/3)
[  563.734926] wlan0: direct probe responded
[  563.742877] wlan0: authenticate with <MAC address removed> (try 1)
[  563.744717] wlan0: authenticated
[  563.746340] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  563.746356] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[  563.746365] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 1 (implement)
[  563.842749] wlan0: associate with <MAC address removed> (try 1)
[  563.847946] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[  563.847953] wlan0: associated
[  563.847959] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[  563.848594] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[  563.848606] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: associated
[  563.848619] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[ 2601.860564] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2601.884016] wlan0: direct probe responded
[ 2601.884131] wlan0: authenticate with <MAC address removed> (try 1)
[ 2602.083086] wlan0: authenticate with <MAC address removed> (try 2)
[ 2602.088101] wlan0: authenticated
[ 2602.090865] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2602.090879] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2602.090887] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 1 (implement)
[ 2602.183148] wlan0: associate with <MAC address removed> (try 1)
[ 2602.186874] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[ 2602.186882] wlan0: associated
[ 2602.187551] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2602.187564] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2602.187577] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[ 2721.494257] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2721.504946] wlan0: direct probe responded
[ 2721.557095] wlan0: authenticate with <MAC address removed> (try 1)
[ 2721.558904] wlan0: authenticated
[ 2721.561507] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2721.561521] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2721.561529] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 1 (implement)
[ 2721.597105] wlan0: associate with <MAC address removed> (try 1)
[ 2721.601169] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 2721.601178] wlan0: associated
[ 2721.601184] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[ 2721.601963] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2721.601973] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2721.601983] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[ 2791.077856] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2791.077872] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2791.077882] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 1 (implement)
[ 2791.077890] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2791.921623] wlan0: authenticate with <MAC address removed> (try 1)
[ 2791.924020] wlan0: authenticated
[ 2791.924859] wlan0: associate with <MAC address removed> (try 1)
[ 2791.930755] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[ 2791.930761] wlan0: associated
[ 2791.931446] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2791.931458] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2791.931470] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[ 2796.439044] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[ 2802.054275] wlan0: no IPv6 routers present


****************** done ******************

```

Thanks for your help

---

### Post by varunendra on 2013-10-22
> **card06 said:**
> My internet is working perfectly so far, nevertheless as you said binding my NM to a specific access point is not really what I would like to do as a solution. Do you have any additional advice for me?

As long as it works for you, I have none. The only downside of this workaround is that you will need to manually change the BSSID everytime you change your location and need to connect to a different access-point with the same name (SSID).

But if the current access-point covers all the area (with reasonably strong signal) that you may be using this laptop within, then this is a non-issue and you don't need to worry about anything.

As a side note, those awkward messages are still present in dmesg. But if your connection is fine, they may just be harmless debugging messages, although they are making me uncomfortable.

If (and ONLY IF) the problem returns, there are three things I may suggest -

1) Try installing a backported driver. This involves downloading and **compiling** a package to be able to use it.
2) Upgrade to the raring kernel to get the latest driver which seems to work better when the older one doesn't.
3) Last resort, install the proprietary "wl" driver - a version that suits your kernel and is itself not buggy.

Let me know if you wish to try any of these, although if it is working fine I'd recommend to leave it as it is. You will automatically get the best drivers when you upgrade to newer versions.

If you wish to upgrade to the latest versions *(of the driver, or whole kernel, although nothing is guaranteed to work better)*, I'd be happy to assist. If the current one is already satisfactory enough for you, please consider marking the thread as [SOLVED]. :)

---

