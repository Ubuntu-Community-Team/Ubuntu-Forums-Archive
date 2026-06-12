---
title: "RTL8188ce Wireless Card not working properly"
date: 2013-11-15
forum: Networking &amp; Wireless
---

### Post by smilligan93 on 2013-11-15
I recently updated to Ubuntu 13.10 64 bit on my laptop and cannot get the wireless card working properly. I installed the newest 13.10 driver that FreedomBen edited found here: [https://github.com/FreedomBen/rtl8188ce-linux-driver/tree/ubuntu-13.10](https://github.com/FreedomBen/rtl8188ce-linux-driver/tree/ubuntu-13.10). The issues I'm having is: Can connect to my schools WiFi (SUNY at Buffalo using PEAP security) but not my home WiFi (WPA2 security). Sadly I haven't been able to test other networks. I am also able to connect to my schools WiFi that has the guest option which I believe is similar to an Airports WiFi. Also when I am connected to the schools WiFi, it will just stop working at random times which clearly I don't want to be happening. I found a script that apparently gets all my internet hardware information so that's what I'm posting from.

```


*************** info trace ***************


***** uname -a *****


Linux compizzle 3.11.0-13-generic #20-Ubuntu SMP Wed Oct 23 07:38:26 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


***** lsb_release *****


Distributor ID:	Ubuntu
Description:	Ubuntu 13.10
Release:	13.10
Codename:	saucy


***** lspci *****


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
	Subsystem: Hewlett-Packard Company Device [103c:1807]
	Kernel driver in use: r8169
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:1629]
	Kernel driver in use: rtl8192ce


***** lsusb *****


Bus 002 Device 002: ID 5986:02ac Acer, Inc 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 138a:0018 Validity Sensors, Inc. Fingerprint scanner
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


***** PCMCIA Card Info *****




***** iwconfig *****


wlan0     IEEE 802.11bgn  ESSID:"UB_Secure"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC address removed>   
          Bit Rate=18 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=37/70  Signal level=-73 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:514   Missed beacon:0




***** rfkill *****


1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


***** lsmod *****


rtl8192ce             137725  0 
rtlwifi               110108  1 rtl8192ce
mac80211              596969  2 rtlwifi,rtl8192ce
cfg80211              479757  2 mac80211,rtlwifi


***** nm-tool *****


NetworkManager Tool


State: connected (global)


- Device: wlan0  [UB_Secure] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           18 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    UB_Voice:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 55 WPA WPA2 Enterprise
    UB_Voice:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 69 WPA WPA2 Enterprise
    UB_Voice:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2 Enterprise
    UB_Voice:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2 Enterprise
    UB_Voice:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 84 WPA WPA2 Enterprise
    UB_Voice:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 59 WPA WPA2 Enterprise
    UB_Secure:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WPA2 Enterprise
    UB_Voice:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2 Enterprise
    UB_Secure:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 45 WPA2 Enterprise
    UB_Voice:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2 Enterprise
    UB_Voice:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2 Enterprise
    UB_Voice:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2 Enterprise
    PolyApple:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 7 WPA WPA2
    UB_Guest:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100
    UB_Gaming:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100
    UB_Wireless:     Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 60
    UB_Guest:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100
    UB_Wireless:     Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100
    UB_Guest:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100
    UB_Gaming:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100
    UB_Gaming:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 59
    UB_Guest:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 69
    UB_Wireless:     Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 7
    UB_Wireless:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 67
    UB_Gaming:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 55
    UB_Guest:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 59
    UB_Guest:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 50
    UB_Guest:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 37
    UB_Gaming:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44
    UB_Wireless:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39
    UB_Wireless:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 54
    UB_Gaming:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 54
    UB_Wireless:     Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 74
    UB_Guest:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 45
    UB_Wireless:     Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 7
    UB_Gaming:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 55
    UB_Gaming:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44
    UB_Guest:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44
    UB_Guest:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 0
    UB_Wireless:     Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 42
    UB_Gaming:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 70
    UB_Guest:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 39
    UB_Wireless:     Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 42
    UB_Gaming:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 35
    UB_Wireless:     Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 0
    UB_Secure:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 39 WPA2 Enterprise
    UB_Voice:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2 Enterprise
    UB_Secure:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    UB_Gaming:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 62
    UB_Secure:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WPA2 Enterprise
    UB_Secure:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 WPA2 Enterprise
    UB_Guest:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 55
    UB_Secure:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    UB_Secure:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 72 WPA2 Enterprise
    UB_Voice:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2 Enterprise
    UB_Gaming:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 67
    UB_Wireless:     Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 42
    UB_Secure:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 45 WPA2 Enterprise
    UB_Secure:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WPA2 Enterprise
    UB_Secure:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 49 WPA2 Enterprise
    *UB_Secure:      Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 46 WPA2 Enterprise


  IPv4 Settings:
    Address:         128.205.60.31
    Prefix:          23 (255.255.254.0)
    Gateway:         128.205.61.254


    DNS:             128.205.106.106
    DNS:             128.205.7.1
    DNS:             128.205.1.2




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
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
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


***** interfaces *****


auto lo
iface lo inet loopback




***** iwlist *****




***** resolv.conf *****


nameserver 127.0.1.1


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


filename:       /lib/modules/3.11.0-13-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     B140057BDC2D312F995749E
alias:          pci:v000010ECd00008176sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008177sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008178sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008191sv*sd*bc*sc*i*
depends:        rtlwifi,mac80211
vermagic:       3.11.0-13-generic SMP mod_unload modversions 
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)


filename:       /lib/modules/3.11.0-13-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     019F93BDB32F49BC7749C53
depends:        mac80211,cfg80211
vermagic:       3.11.0-13-generic SMP mod_unload modversions 




***** udev rules *****


# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:04.0/0000:02:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:05.0/0000:03:00.0 (rtl8192ce)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


***** dmesg *****


[   39.616589] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   68.646017] rtlwifi-0:rtl_op_ampdu_action():<0-0> IEEE80211_AMPDU_ERR!!!!:
[   68.646060] Modules linked in: dm_crypt(F) nvram(F) cuse parport_pc(F) ppdev(F) rfcomm bnep bluetooth uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev joydev(F) binfmt_misc(F) hp_wmi sparse_keymap arc4(F) kvm_amd(F) kvm(F) microcode(F) psmouse(F) serio_raw(F) snd_hda_codec_idt snd_hda_codec_hdmi k10temp snd_hda_intel snd_hda_codec snd_hwdep(F) rtsx_pci_ms memstick snd_pcm(F) snd_page_alloc(F) i2c_piix4 rtl8192ce(OF) rtlwifi(OF) snd_seq_midi(F) snd_seq_midi_event(F) mac80211 snd_rawmidi(F) snd_seq(F) cfg80211 snd_seq_device(F) snd_timer(F) snd(F) soundcore(F) hp_accel lis3lv02d input_polldev mac_hid lp(F) parport(F) pata_acpi hid_logitech_dj usbhid hid rtsx_pci_sdmmc radeon i2c_algo_bit ttm pata_atiixp ohci_pci drm_kms_helper sdhci_pci rtsx_pci ahci(F) sdhci libahci(F) drm r8169 mii(F) wmi video(F)
[   68.656782] wlan0: authenticate with <MAC address removed>
[   68.667221] wlan0: send auth to <MAC address removed> (try 1/3)
[   68.668870] wlan0: authenticated
[   68.672420] wlan0: associate with <MAC address removed> (try 1/3)
[   68.678474] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[   68.678710] wlan0: associated
[   73.571034] wlan0: authenticate with <MAC address removed>
[   73.583830] wlan0: send auth to <MAC address removed> (try 1/3)
[   73.585981] wlan0: authenticated
[   73.587112] wlan0: associate with <MAC address removed> (try 1/3)
[   73.592893] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[   73.593087] wlan0: associated
[   84.893628] rtlwifi-0:rtl_op_ampdu_action():<0-0> IEEE80211_AMPDU_ERR!!!!:
[   84.893703] Modules linked in: dm_crypt(F) nvram(F) cuse parport_pc(F) ppdev(F) rfcomm bnep bluetooth uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev joydev(F) binfmt_misc(F) hp_wmi sparse_keymap arc4(F) kvm_amd(F) kvm(F) microcode(F) psmouse(F) serio_raw(F) snd_hda_codec_idt snd_hda_codec_hdmi k10temp snd_hda_intel snd_hda_codec snd_hwdep(F) rtsx_pci_ms memstick snd_pcm(F) snd_page_alloc(F) i2c_piix4 rtl8192ce(OF) rtlwifi(OF) snd_seq_midi(F) snd_seq_midi_event(F) mac80211 snd_rawmidi(F) snd_seq(F) cfg80211 snd_seq_device(F) snd_timer(F) snd(F) soundcore(F) hp_accel lis3lv02d input_polldev mac_hid lp(F) parport(F) pata_acpi hid_logitech_dj usbhid hid rtsx_pci_sdmmc radeon i2c_algo_bit ttm pata_atiixp ohci_pci drm_kms_helper sdhci_pci rtsx_pci ahci(F) sdhci libahci(F) drm r8169 mii(F) wmi video(F)
[   84.905178] wlan0: authenticate with <MAC address removed>
[   84.915561] wlan0: direct probe to <MAC address removed> (try 1/3)
[   85.553226] wlan0: direct probe to <MAC address removed> (try 2/3)
[   85.848679] wlan0: direct probe to <MAC address removed> (try 3/3)
[   86.134518] wlan0: authentication with <MAC address removed> timed out
[   86.158549] wlan0: authenticate with <MAC address removed>
[   86.169193] wlan0: send auth to <MAC address removed> (try 1/3)
[   86.171542] wlan0: authenticated
[   86.483007] wlan0: authenticate with <MAC address removed>
[   86.493541] wlan0: send auth to <MAC address removed> (try 1/3)
[   86.495368] wlan0: authenticated
[   86.497854] wlan0: associate with <MAC address removed> (try 1/3)
[   86.503883] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[   86.504177] wlan0: associated
[   94.997772] wlan0: authenticate with <MAC address removed>
[   95.008521] wlan0: send auth to <MAC address removed> (try 1/3)
[   95.010235] wlan0: authenticated
[   95.014825] wlan0: associate with <MAC address removed> (try 1/3)
[   95.020630] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[   95.021050] wlan0: associated
[  106.533302] wlan0: authenticate with <MAC address removed>
[  106.543486] wlan0: send auth to <MAC address removed> (try 1/3)
[  106.546597] wlan0: authenticated
[  106.550518] wlan0: associate with <MAC address removed> (try 1/3)
[  106.557076] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[  106.557191] wlan0: associated
[  117.109539] rtlwifi-0:rtl_op_ampdu_action():<0-0> IEEE80211_AMPDU_ERR!!!!:
[  117.109610] Modules linked in: dm_crypt(F) nvram(F) cuse parport_pc(F) ppdev(F) rfcomm bnep bluetooth uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev joydev(F) binfmt_misc(F) hp_wmi sparse_keymap arc4(F) kvm_amd(F) kvm(F) microcode(F) psmouse(F) serio_raw(F) snd_hda_codec_idt snd_hda_codec_hdmi k10temp snd_hda_intel snd_hda_codec snd_hwdep(F) rtsx_pci_ms memstick snd_pcm(F) snd_page_alloc(F) i2c_piix4 rtl8192ce(OF) rtlwifi(OF) snd_seq_midi(F) snd_seq_midi_event(F) mac80211 snd_rawmidi(F) snd_seq(F) cfg80211 snd_seq_device(F) snd_timer(F) snd(F) soundcore(F) hp_accel lis3lv02d input_polldev mac_hid lp(F) parport(F) pata_acpi hid_logitech_dj usbhid hid rtsx_pci_sdmmc radeon i2c_algo_bit ttm pata_atiixp ohci_pci drm_kms_helper sdhci_pci rtsx_pci ahci(F) sdhci libahci(F) drm r8169 mii(F) wmi video(F)
[  117.120843] wlan0: authenticate with <MAC address removed>
[  117.131027] wlan0: send auth to <MAC address removed> (try 1/3)
[  117.132282] wlan0: authenticated
[  117.140891] wlan0: associate with <MAC address removed> (try 1/3)
[  117.146727] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[  117.146879] wlan0: associated
[  133.627866] rtlwifi-0:rtl_op_ampdu_action():<0-0> IEEE80211_AMPDU_ERR!!!!:
[  133.627938] Modules linked in: dm_crypt(F) nvram(F) cuse parport_pc(F) ppdev(F) rfcomm bnep bluetooth uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev joydev(F) binfmt_misc(F) hp_wmi sparse_keymap arc4(F) kvm_amd(F) kvm(F) microcode(F) psmouse(F) serio_raw(F) snd_hda_codec_idt snd_hda_codec_hdmi k10temp snd_hda_intel snd_hda_codec snd_hwdep(F) rtsx_pci_ms memstick snd_pcm(F) snd_page_alloc(F) i2c_piix4 rtl8192ce(OF) rtlwifi(OF) snd_seq_midi(F) snd_seq_midi_event(F) mac80211 snd_rawmidi(F) snd_seq(F) cfg80211 snd_seq_device(F) snd_timer(F) snd(F) soundcore(F) hp_accel lis3lv02d input_polldev mac_hid lp(F) parport(F) pata_acpi hid_logitech_dj usbhid hid rtsx_pci_sdmmc radeon i2c_algo_bit ttm pata_atiixp ohci_pci drm_kms_helper sdhci_pci rtsx_pci ahci(F) sdhci libahci(F) drm r8169 mii(F) wmi video(F)
[  133.639733] wlan0: authenticate with <MAC address removed>
[  133.650112] wlan0: send auth to <MAC address removed> (try 1/3)
[  133.890731] wlan0: send auth to <MAC address removed> (try 2/3)
[  134.119107] wlan0: send auth to <MAC address removed> (try 3/3)
[  134.350580] wlan0: authentication with <MAC address removed> timed out
[  134.574209] wlan0: authenticate with <MAC address removed>
[  134.593133] wlan0: direct probe to <MAC address removed> (try 1/3)
[  134.796253] wlan0: direct probe to <MAC address removed> (try 2/3)
[  135.000262] wlan0: direct probe to <MAC address removed> (try 3/3)
[  135.204184] wlan0: authentication with <MAC address removed> timed out
[  135.462142] wlan0: authenticate with <MAC address removed>
[  135.472335] wlan0: send auth to <MAC address removed> (try 1/3)
[  135.473839] wlan0: authenticated
[  135.475983] wlan0: associate with <MAC address removed> (try 1/3)
[  135.579879] wlan0: associate with <MAC address removed> (try 2/3)
[  135.587739] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[  135.587993] wlan0: associated
[  212.522670] rtlwifi-0:rtl_op_ampdu_action():<0-0> IEEE80211_AMPDU_ERR!!!!:
[  212.522741] Modules linked in: dm_crypt(F) nvram(F) cuse parport_pc(F) ppdev(F) rfcomm bnep bluetooth uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev joydev(F) binfmt_misc(F) hp_wmi sparse_keymap arc4(F) kvm_amd(F) kvm(F) microcode(F) psmouse(F) serio_raw(F) snd_hda_codec_idt snd_hda_codec_hdmi k10temp snd_hda_intel snd_hda_codec snd_hwdep(F) rtsx_pci_ms memstick snd_pcm(F) snd_page_alloc(F) i2c_piix4 rtl8192ce(OF) rtlwifi(OF) snd_seq_midi(F) snd_seq_midi_event(F) mac80211 snd_rawmidi(F) snd_seq(F) cfg80211 snd_seq_device(F) snd_timer(F) snd(F) soundcore(F) hp_accel lis3lv02d input_polldev mac_hid lp(F) parport(F) pata_acpi hid_logitech_dj usbhid hid rtsx_pci_sdmmc radeon i2c_algo_bit ttm pata_atiixp ohci_pci drm_kms_helper sdhci_pci rtsx_pci ahci(F) sdhci libahci(F) drm r8169 mii(F) wmi video(F)
[  212.533851] wlan0: authenticate with <MAC address removed>
[  212.543998] wlan0: direct probe to <MAC address removed> (try 1/3)
[  213.054294] wlan0: direct probe to <MAC address removed> (try 2/3)
[  213.990252] wlan0: send auth to <MAC address removed> (try 3/3)
[  213.995212] wlan0: authenticated
[  214.296425] wlan0: authenticate with <MAC address removed>
[  214.306857] wlan0: send auth to <MAC address removed> (try 1/3)
[  214.308747] wlan0: authenticated
[  214.311087] wlan0: associate with <MAC address removed> (try 1/3)
[  214.316841] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[  214.317016] wlan0: associated
[  262.562073] rtlwifi-0:rtl_op_ampdu_action():<0-0> IEEE80211_AMPDU_ERR!!!!:
[  262.562116] Modules linked in: dm_crypt(F) nvram(F) cuse parport_pc(F) ppdev(F) rfcomm bnep bluetooth uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev joydev(F) binfmt_misc(F) hp_wmi sparse_keymap arc4(F) kvm_amd(F) kvm(F) microcode(F) psmouse(F) serio_raw(F) snd_hda_codec_idt snd_hda_codec_hdmi k10temp snd_hda_intel snd_hda_codec snd_hwdep(F) rtsx_pci_ms memstick snd_pcm(F) snd_page_alloc(F) i2c_piix4 rtl8192ce(OF) rtlwifi(OF) snd_seq_midi(F) snd_seq_midi_event(F) mac80211 snd_rawmidi(F) snd_seq(F) cfg80211 snd_seq_device(F) snd_timer(F) snd(F) soundcore(F) hp_accel lis3lv02d input_polldev mac_hid lp(F) parport(F) pata_acpi hid_logitech_dj usbhid hid rtsx_pci_sdmmc radeon i2c_algo_bit ttm pata_atiixp ohci_pci drm_kms_helper sdhci_pci rtsx_pci ahci(F) sdhci libahci(F) drm r8169 mii(F) wmi video(F)
[  262.562374] rtlwifi-0:rtl_op_ampdu_action():<0-0> IEEE80211_AMPDU_ERR!!!!:
[  262.562386] Modules linked in: dm_crypt(F) nvram(F) cuse parport_pc(F) ppdev(F) rfcomm bnep bluetooth uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev joydev(F) binfmt_misc(F) hp_wmi sparse_keymap arc4(F) kvm_amd(F) kvm(F) microcode(F) psmouse(F) serio_raw(F) snd_hda_codec_idt snd_hda_codec_hdmi k10temp snd_hda_intel snd_hda_codec snd_hwdep(F) rtsx_pci_ms memstick snd_pcm(F) snd_page_alloc(F) i2c_piix4 rtl8192ce(OF) rtlwifi(OF) snd_seq_midi(F) snd_seq_midi_event(F) mac80211 snd_rawmidi(F) snd_seq(F) cfg80211 snd_seq_device(F) snd_timer(F) snd(F) soundcore(F) hp_accel lis3lv02d input_polldev mac_hid lp(F) parport(F) pata_acpi hid_logitech_dj usbhid hid rtsx_pci_sdmmc radeon i2c_algo_bit ttm pata_atiixp ohci_pci drm_kms_helper sdhci_pci rtsx_pci ahci(F) sdhci libahci(F) drm r8169 mii(F) wmi video(F)
[  262.572910] wlan0: authenticate with <MAC address removed>
[  262.583276] wlan0: direct probe to <MAC address removed> (try 1/3)
[  263.209801] wlan0: direct probe to <MAC address removed> (try 2/3)
[  263.451990] wlan0: send auth to <MAC address removed> (try 3/3)
[  263.453433] wlan0: authenticated
[  263.693743] wlan0: authenticate with <MAC address removed>
[  263.704093] wlan0: send auth to <MAC address removed> (try 1/3)
[  263.706431] wlan0: authenticated
[  263.708920] wlan0: associate with <MAC address removed> (try 1/3)
[  263.717563] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[  263.717784] wlan0: associated
[  299.223580] rtlwifi-0:rtl_op_ampdu_action():<0-0> IEEE80211_AMPDU_ERR!!!!:
[  299.223652] Modules linked in: dm_crypt(F) nvram(F) cuse parport_pc(F) ppdev(F) rfcomm bnep bluetooth uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev joydev(F) binfmt_misc(F) hp_wmi sparse_keymap arc4(F) kvm_amd(F) kvm(F) microcode(F) psmouse(F) serio_raw(F) snd_hda_codec_idt snd_hda_codec_hdmi k10temp snd_hda_intel snd_hda_codec snd_hwdep(F) rtsx_pci_ms memstick snd_pcm(F) snd_page_alloc(F) i2c_piix4 rtl8192ce(OF) rtlwifi(OF) snd_seq_midi(F) snd_seq_midi_event(F) mac80211 snd_rawmidi(F) snd_seq(F) cfg80211 snd_seq_device(F) snd_timer(F) snd(F) soundcore(F) hp_accel lis3lv02d input_polldev mac_hid lp(F) parport(F) pata_acpi hid_logitech_dj usbhid hid rtsx_pci_sdmmc radeon i2c_algo_bit ttm pata_atiixp ohci_pci drm_kms_helper sdhci_pci rtsx_pci ahci(F) sdhci libahci(F) drm r8169 mii(F) wmi video(F)
[  299.235110] wlan0: authenticate with <MAC address removed>
[  299.246088] wlan0: direct probe to <MAC address removed> (try 1/3)
[  299.818314] wlan0: direct probe to <MAC address removed> (try 2/3)
[  300.050027] wlan0: direct probe to <MAC address removed> (try 3/3)
[  300.271979] wlan0: authentication with <MAC address removed> timed out
[  300.284304] wlan0: authenticate with <MAC address removed>
[  300.294677] wlan0: send auth to <MAC address removed> (try 1/3)
[  300.296256] wlan0: authenticated
[  300.480854] wlan0: authenticate with <MAC address removed>
[  300.491919] wlan0: send auth to <MAC address removed> (try 1/3)
[  300.494159] wlan0: authenticated
[  300.495535] wlan0: associate with <MAC address removed> (try 1/3)
[  300.501290] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=3)
[  300.501716] wlan0: associated
[  398.463867] rtlwifi-0:rtl_op_ampdu_action():<0-0> IEEE80211_AMPDU_ERR!!!!:
[  398.463939] Modules linked in: dm_crypt(F) nvram(F) cuse parport_pc(F) ppdev(F) rfcomm bnep bluetooth uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev joydev(F) binfmt_misc(F) hp_wmi sparse_keymap arc4(F) kvm_amd(F) kvm(F) microcode(F) psmouse(F) serio_raw(F) snd_hda_codec_idt snd_hda_codec_hdmi k10temp snd_hda_intel snd_hda_codec snd_hwdep(F) rtsx_pci_ms memstick snd_pcm(F) snd_page_alloc(F) i2c_piix4 rtl8192ce(OF) rtlwifi(OF) snd_seq_midi(F) snd_seq_midi_event(F) mac80211 snd_rawmidi(F) snd_seq(F) cfg80211 snd_seq_device(F) snd_timer(F) snd(F) soundcore(F) hp_accel lis3lv02d input_polldev mac_hid lp(F) parport(F) pata_acpi hid_logitech_dj usbhid hid rtsx_pci_sdmmc radeon i2c_algo_bit ttm pata_atiixp ohci_pci drm_kms_helper sdhci_pci rtsx_pci ahci(F) sdhci libahci(F) drm r8169 mii(F) wmi video(F)
[  398.475106] wlan0: authenticate with <MAC address removed>
[  398.485305] wlan0: direct probe to <MAC address removed> (try 1/3)
[  399.058397] wlan0: direct probe to <MAC address removed> (try 2/3)
[  399.259301] wlan0: send auth to <MAC address removed> (try 3/3)
[  399.260595] wlan0: authenticated
[  400.176454] wlan0: authenticate with <MAC address removed>
[  400.187241] wlan0: send auth to <MAC address removed> (try 1/3)
[  400.190813] wlan0: authenticated
[  400.194878] wlan0: associate with <MAC address removed> (try 1/3)
[  400.205866] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=3)
[  400.206071] wlan0: associated
[  407.022233] wlan0: authenticate with <MAC address removed>
[  407.033046] wlan0: direct probe to <MAC address removed> (try 1/3)
[  407.670746] wlan0: direct probe to <MAC address removed> (try 2/3)
[  407.966698] wlan0: direct probe to <MAC address removed> (try 3/3)
[  408.262869] wlan0: authentication with <MAC address removed> timed out
[  408.550135] wlan0: authenticate with <MAC address removed>
[  408.558575] wlan0: send auth to <MAC address removed> (try 1/3)
[  408.659884] wlan0: send auth to <MAC address removed> (try 2/3)
[  408.661951] wlan0: authenticated
[  408.663999] wlan0: associate with <MAC address removed> (try 1/3)
[  408.669737] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[  408.669941] wlan0: associated
[  413.593062] wlan0: authenticate with <MAC address removed>
[  413.603418] wlan0: send auth to <MAC address removed> (try 1/3)
[  413.606000] wlan0: authenticated
[  413.609986] wlan0: associate with <MAC address removed> (try 1/3)
[  413.615611] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[  413.615852] wlan0: associated
[  435.510256] rtlwifi-0:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[  435.510349] wlan0: Connection to AP <MAC address removed> lost
[  435.518388] rtlwifi-0:rtl_op_ampdu_action():<0-0> IEEE80211_AMPDU_ERR!!!!:
[  435.518459] Modules linked in: dm_crypt(F) nvram(F) cuse parport_pc(F) ppdev(F) rfcomm bnep bluetooth uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev joydev(F) binfmt_misc(F) hp_wmi sparse_keymap arc4(F) kvm_amd(F) kvm(F) microcode(F) psmouse(F) serio_raw(F) snd_hda_codec_idt snd_hda_codec_hdmi k10temp snd_hda_intel snd_hda_codec snd_hwdep(F) rtsx_pci_ms memstick snd_pcm(F) snd_page_alloc(F) i2c_piix4 rtl8192ce(OF) rtlwifi(OF) snd_seq_midi(F) snd_seq_midi_event(F) mac80211 snd_rawmidi(F) snd_seq(F) cfg80211 snd_seq_device(F) snd_timer(F) snd(F) soundcore(F) hp_accel lis3lv02d input_polldev mac_hid lp(F) parport(F) pata_acpi hid_logitech_dj usbhid hid rtsx_pci_sdmmc radeon i2c_algo_bit ttm pata_atiixp ohci_pci drm_kms_helper sdhci_pci rtsx_pci ahci(F) sdhci libahci(F) drm r8169 mii(F) wmi video(F)
[  436.171892] wlan0: authenticate with <MAC address removed>
[  436.190637] wlan0: send auth to <MAC address removed> (try 1/3)
[  436.191951] wlan0: authenticated
[  436.194325] wlan0: associate with <MAC address removed> (try 1/3)
[  436.200137] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[  436.200416] wlan0: associated
[  456.007799] rtlwifi-0:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[  456.007893] wlan0: Connection to AP <MAC address removed> lost
[  456.602008] wlan0: authenticate with <MAC address removed>
[  456.620783] wlan0: direct probe to <MAC address removed> (try 1/3)
[  456.823837] wlan0: send auth to <MAC address removed> (try 2/3)
[  456.825973] wlan0: authenticated
[  456.827704] wlan0: associate with <MAC address removed> (try 1/3)
[  456.833895] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[  456.834199] wlan0: associated
[  476.514406] rtlwifi-0:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[  476.514498] wlan0: Connection to AP <MAC address removed> lost
[  476.769009] wlan0: authenticate with <MAC address removed>
[  476.779636] wlan0: direct probe to <MAC address removed> (try 1/3)
[  476.982519] wlan0: direct probe to <MAC address removed> (try 2/3)
[  477.186631] wlan0: direct probe to <MAC address removed> (try 3/3)
[  477.390579] wlan0: authentication with <MAC address removed> timed out
[  478.305521] wlan0: authenticate with <MAC address removed>
[  478.315841] wlan0: direct probe to <MAC address removed> (try 1/3)
[  478.518697] wlan0: direct probe to <MAC address removed> (try 2/3)
[  478.722822] wlan0: direct probe to <MAC address removed> (try 3/3)
[  478.926795] wlan0: authentication with <MAC address removed> timed out
[  479.840677] wlan0: authenticate with <MAC address removed>
[  479.851057] wlan0: send auth to <MAC address removed> (try 1/3)
[  479.852432] wlan0: authenticated
[  479.854831] wlan0: associate with <MAC address removed> (try 1/3)
[  479.861474] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[  479.861783] wlan0: associated
[  513.898536] rtlwifi-0:rtl_op_ampdu_action():<0-0> IEEE80211_AMPDU_ERR!!!!:
[  513.898606] Modules linked in: dm_crypt(F) nvram(F) cuse parport_pc(F) ppdev(F) rfcomm bnep bluetooth uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev joydev(F) binfmt_misc(F) hp_wmi sparse_keymap arc4(F) kvm_amd(F) kvm(F) microcode(F) psmouse(F) serio_raw(F) snd_hda_codec_idt snd_hda_codec_hdmi k10temp snd_hda_intel snd_hda_codec snd_hwdep(F) rtsx_pci_ms memstick snd_pcm(F) snd_page_alloc(F) i2c_piix4 rtl8192ce(OF) rtlwifi(OF) snd_seq_midi(F) snd_seq_midi_event(F) mac80211 snd_rawmidi(F) snd_seq(F) cfg80211 snd_seq_device(F) snd_timer(F) snd(F) soundcore(F) hp_accel lis3lv02d input_polldev mac_hid lp(F) parport(F) pata_acpi hid_logitech_dj usbhid hid rtsx_pci_sdmmc radeon i2c_algo_bit ttm pata_atiixp ohci_pci drm_kms_helper sdhci_pci rtsx_pci ahci(F) sdhci libahci(F) drm r8169 mii(F) wmi video(F)
[  513.909962] wlan0: authenticate with <MAC address removed>
[  513.920764] wlan0: send auth to <MAC address removed> (try 1/3)
[  514.098134] wlan0: send auth to <MAC address removed> (try 2/3)
[  515.034024] wlan0: send auth to <MAC address removed> (try 3/3)
[  515.319907] wlan0: authentication with <MAC address removed> timed out
[  515.344243] wlan0: authenticate with <MAC address removed>
[  515.354646] wlan0: send auth to <MAC address removed> (try 1/3)
[  515.455642] wlan0: send auth to <MAC address removed> (try 2/3)
[  515.658220] wlan0: send auth to <MAC address removed> (try 3/3)
[  515.954888] wlan0: authentication with <MAC address removed> timed out
[  516.241762] wlan0: authenticate with <MAC address removed>
[  516.252462] wlan0: send auth to <MAC address removed> (try 1/3)
[  516.355766] wlan0: send auth to <MAC address removed> (try 2/3)
[  516.459613] wlan0: send auth to <MAC address removed> (try 3/3)
[  516.563766] wlan0: authentication with <MAC address removed> timed out
[  516.877617] wlan0: authenticate with <MAC address removed>
[  516.896409] wlan0: direct probe to <MAC address removed> (try 1/3)
[  517.099893] wlan0: direct probe to <MAC address removed> (try 2/3)
[  517.303969] wlan0: direct probe to <MAC address removed> (try 3/3)
[  517.507858] wlan0: authentication with <MAC address removed> timed out
[  517.773578] wlan0: authenticate with <MAC address removed>
[  517.792502] wlan0: send auth to <MAC address removed> (try 1/3)
[  517.796052] wlan0: authenticated
[  517.799768] wlan0: associate with <MAC address removed> (try 1/3)
[  517.806451] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[  517.806846] wlan0: associated
[  551.290876] rtlwifi-0:rtl_op_ampdu_action():<0-0> IEEE80211_AMPDU_ERR!!!!:
[  551.290913] Modules linked in: dm_crypt(F) nvram(F) cuse parport_pc(F) ppdev(F) rfcomm bnep bluetooth uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev joydev(F) binfmt_misc(F) hp_wmi sparse_keymap arc4(F) kvm_amd(F) kvm(F) microcode(F) psmouse(F) serio_raw(F) snd_hda_codec_idt snd_hda_codec_hdmi k10temp snd_hda_intel snd_hda_codec snd_hwdep(F) rtsx_pci_ms memstick snd_pcm(F) snd_page_alloc(F) i2c_piix4 rtl8192ce(OF) rtlwifi(OF) snd_seq_midi(F) snd_seq_midi_event(F) mac80211 snd_rawmidi(F) snd_seq(F) cfg80211 snd_seq_device(F) snd_timer(F) snd(F) soundcore(F) hp_accel lis3lv02d input_polldev mac_hid lp(F) parport(F) pata_acpi hid_logitech_dj usbhid hid rtsx_pci_sdmmc radeon i2c_algo_bit ttm pata_atiixp ohci_pci drm_kms_helper sdhci_pci rtsx_pci ahci(F) sdhci libahci(F) drm r8169 mii(F) wmi video(F)
[  551.301446] wlan0: authenticate with <MAC address removed>
[  551.311668] wlan0: send auth to <MAC address removed> (try 1/3)
[  551.317582] wlan0: authenticated
[  551.320594] wlan0: associate with <MAC address removed> (try 1/3)
[  551.326067] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[  551.326259] wlan0: associated
[  562.128757] rtlwifi-0:rtl_op_ampdu_action():<0-0> IEEE80211_AMPDU_ERR!!!!:
[  562.128829] Modules linked in: dm_crypt(F) nvram(F) cuse parport_pc(F) ppdev(F) rfcomm bnep bluetooth uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev joydev(F) binfmt_misc(F) hp_wmi sparse_keymap arc4(F) kvm_amd(F) kvm(F) microcode(F) psmouse(F) serio_raw(F) snd_hda_codec_idt snd_hda_codec_hdmi k10temp snd_hda_intel snd_hda_codec snd_hwdep(F) rtsx_pci_ms memstick snd_pcm(F) snd_page_alloc(F) i2c_piix4 rtl8192ce(OF) rtlwifi(OF) snd_seq_midi(F) snd_seq_midi_event(F) mac80211 snd_rawmidi(F) snd_seq(F) cfg80211 snd_seq_device(F) snd_timer(F) snd(F) soundcore(F) hp_accel lis3lv02d input_polldev mac_hid lp(F) parport(F) pata_acpi hid_logitech_dj usbhid hid rtsx_pci_sdmmc radeon i2c_algo_bit ttm pata_atiixp ohci_pci drm_kms_helper sdhci_pci rtsx_pci ahci(F) sdhci libahci(F) drm r8169 mii(F) wmi video(F)
[  562.140508] wlan0: authenticate with <MAC address removed>
[  562.151441] wlan0: direct probe to <MAC address removed> (try 1/3)
[  562.720701] wlan0: direct probe to <MAC address removed> (try 2/3)
[  562.942254] wlan0: send auth to <MAC address removed> (try 3/3)
[  562.944229] wlan0: authenticated
[  563.130592] wlan0: authenticate with <MAC address removed>
[  563.141139] wlan0: send auth to <MAC address removed> (try 1/3)
[  563.143394] wlan0: authenticated
[  563.145859] wlan0: associate with <MAC address removed> (try 1/3)
[  563.156319] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[  563.156508] wlan0: associated
[  611.906578] rtlwifi-0:rtl_op_ampdu_action():<0-0> IEEE80211_AMPDU_ERR!!!!:
[  611.906649] Modules linked in: dm_crypt(F) nvram(F) cuse parport_pc(F) ppdev(F) rfcomm bnep bluetooth uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev joydev(F) binfmt_misc(F) hp_wmi sparse_keymap arc4(F) kvm_amd(F) kvm(F) microcode(F) psmouse(F) serio_raw(F) snd_hda_codec_idt snd_hda_codec_hdmi k10temp snd_hda_intel snd_hda_codec snd_hwdep(F) rtsx_pci_ms memstick snd_pcm(F) snd_page_alloc(F) i2c_piix4 rtl8192ce(OF) rtlwifi(OF) snd_seq_midi(F) snd_seq_midi_event(F) mac80211 snd_rawmidi(F) snd_seq(F) cfg80211 snd_seq_device(F) snd_timer(F) snd(F) soundcore(F) hp_accel lis3lv02d input_polldev mac_hid lp(F) parport(F) pata_acpi hid_logitech_dj usbhid hid rtsx_pci_sdmmc radeon i2c_algo_bit ttm pata_atiixp ohci_pci drm_kms_helper sdhci_pci rtsx_pci ahci(F) sdhci libahci(F) drm r8169 mii(F) wmi video(F)
[  611.917826] wlan0: authenticate with <MAC address removed>
[  611.928364] wlan0: direct probe to <MAC address removed> (try 1/3)
[  612.389191] wlan0: direct probe to <MAC address removed> (try 2/3)
[  613.335048] wlan0: direct probe to <MAC address removed> (try 3/3)
[  613.631184] wlan0: authentication with <MAC address removed> timed out
[  613.918876] wlan0: authenticate with <MAC address removed>
[  613.937649] wlan0: send auth to <MAC address removed> (try 1/3)
[  613.939000] wlan0: authenticated
[  613.941473] wlan0: associate with <MAC address removed> (try 1/3)
[  613.947818] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[  613.948017] wlan0: associated
[  623.690339] rtlwifi-0:rtl_op_ampdu_action():<0-0> IEEE80211_AMPDU_ERR!!!!:
[  623.690413] Modules linked in: dm_crypt(F) nvram(F) cuse parport_pc(F) ppdev(F) rfcomm bnep bluetooth uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev joydev(F) binfmt_misc(F) hp_wmi sparse_keymap arc4(F) kvm_amd(F) kvm(F) microcode(F) psmouse(F) serio_raw(F) snd_hda_codec_idt snd_hda_codec_hdmi k10temp snd_hda_intel snd_hda_codec snd_hwdep(F) rtsx_pci_ms memstick snd_pcm(F) snd_page_alloc(F) i2c_piix4 rtl8192ce(OF) rtlwifi(OF) snd_seq_midi(F) snd_seq_midi_event(F) mac80211 snd_rawmidi(F) snd_seq(F) cfg80211 snd_seq_device(F) snd_timer(F) snd(F) soundcore(F) hp_accel lis3lv02d input_polldev mac_hid lp(F) parport(F) pata_acpi hid_logitech_dj usbhid hid rtsx_pci_sdmmc radeon i2c_algo_bit ttm pata_atiixp ohci_pci drm_kms_helper sdhci_pci rtsx_pci ahci(F) sdhci libahci(F) drm r8169 mii(F) wmi video(F)
[  623.701665] wlan0: authenticate with <MAC address removed>
[  623.711888] wlan0: direct probe to <MAC address removed> (try 1/3)
[  624.338628] wlan0: direct probe to <MAC address removed> (try 2/3)
[  624.638939] wlan0: direct probe to <MAC address removed> (try 3/3)
[  624.934603] wlan0: authentication with <MAC address removed> timed out
[  624.970773] wlan0: authenticate with <MAC address removed>
[  624.981521] wlan0: send auth to <MAC address removed> (try 1/3)
[  624.983167] wlan0: authenticated
[  625.295317] wlan0: authenticate with <MAC address removed>
[  625.305798] wlan0: send auth to <MAC address removed> (try 1/3)
[  625.307369] wlan0: authenticated
[  625.310258] wlan0: associate with <MAC address removed> (try 1/3)
[  625.316057] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[  625.316321] wlan0: associated
[  631.633411] wlan0: authenticate with <MAC address removed>
[  631.643834] wlan0: direct probe to <MAC address removed> (try 1/3)
[  632.271699] wlan0: direct probe to <MAC address removed> (try 2/3)
[  632.578069] wlan0: direct probe to <MAC address removed> (try 3/3)
[  632.799853] wlan0: authentication with <MAC address removed> timed out
[  632.824720] wlan0: authenticate with <MAC address removed>
[  632.835046] wlan0: send auth to <MAC address removed> (try 1/3)
[  632.837289] wlan0: authenticated
[  633.020448] wlan0: authenticate with <MAC address removed>
[  633.031066] wlan0: send auth to <MAC address removed> (try 1/3)
[  633.034500] wlan0: authenticated
[  633.035245] wlan0: associate with <MAC address removed> (try 1/3)
[  633.041531] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[  633.041760] wlan0: associated
[  948.865559] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  968.564448] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[  968.564973] rtlwifi: wireless switch is on
[  968.913145] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  968.913822] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  970.775295] wlan0: authenticate with <MAC address removed>
[  970.792887] wlan0: direct probe to <MAC address removed> (try 1/3)
[  970.996382] wlan0: direct probe to <MAC address removed> (try 2/3)
[  971.200384] wlan0: direct probe to <MAC address removed> (try 3/3)
[  971.404423] wlan0: authentication with <MAC address removed> timed out
[  972.403083] wlan0: authenticate with <MAC address removed>
[  972.422015] wlan0: direct probe to <MAC address removed> (try 1/3)
[  972.624620] wlan0: direct probe to <MAC address removed> (try 2/3)
[  972.828741] wlan0: direct probe to <MAC address removed> (try 3/3)
[  973.032652] wlan0: authentication with <MAC address removed> timed out
[  974.040072] wlan0: authenticate with <MAC address removed>
[  974.050455] wlan0: send auth to <MAC address removed> (try 1/3)
[  974.051601] wlan0: authenticated
[  974.052666] wlan0: associate with <MAC address removed> (try 1/3)
[  974.058157] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[  974.058343] wlan0: associated
[  974.058383] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  977.916839] wlan0: deauthenticating from <MAC address removed> by local choice (reason=2)
[  979.232890] wlan0: authenticate with <MAC address removed>
[  979.250943] wlan0: send auth to <MAC address removed> (try 1/3)
[  979.255628] wlan0: authenticated
[  979.257536] wlan0: associate with <MAC address removed> (try 1/3)
[  979.264140] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=5)
[  979.264383] wlan0: associated
[ 1013.081243] rtlwifi-0:rtl_op_ampdu_action():<0-0> IEEE80211_AMPDU_ERR!!!!:
[ 1013.081305] Modules linked in: rtl8192ce(OF) rtlwifi(OF) mac80211 cfg80211 dm_crypt(F) nvram(F) cuse parport_pc(F) ppdev(F) rfcomm bnep bluetooth uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev joydev(F) binfmt_misc(F) hp_wmi sparse_keymap arc4(F) kvm_amd(F) kvm(F) microcode(F) psmouse(F) serio_raw(F) snd_hda_codec_idt snd_hda_codec_hdmi k10temp snd_hda_intel snd_hda_codec snd_hwdep(F) rtsx_pci_ms memstick snd_pcm(F) snd_page_alloc(F) i2c_piix4 snd_seq_midi(F) snd_seq_midi_event(F) snd_rawmidi(F) snd_seq(F) snd_seq_device(F) snd_timer(F) snd(F) soundcore(F) hp_accel lis3lv02d input_polldev mac_hid lp(F) parport(F) pata_acpi hid_logitech_dj usbhid hid rtsx_pci_sdmmc radeon i2c_algo_bit ttm pata_atiixp ohci_pci drm_kms_helper sdhci_pci rtsx_pci ahci(F) sdhci libahci(F) drm r8169 mii(F) wmi video(F) [last unloaded: cfg80211]
[ 1013.095078] wlan0: authenticate with <MAC address removed>
[ 1013.106818] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1013.740231] wlan0: send auth to <MAC address removed> (try 2/3)
[ 1013.741407] wlan0: authenticated
[ 1013.752612] wlan0: authenticate with <MAC address removed>
[ 1013.762926] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1013.765367] wlan0: authenticated
[ 1013.767022] wlan0: associate with <MAC address removed> (try 1/3)
[ 1013.776598] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=5)
[ 1013.776755] wlan0: associated
[ 1067.157634] rtlwifi-0:rtl_op_ampdu_action():<0-0> IEEE80211_AMPDU_ERR!!!!:
[ 1067.157712] Modules linked in: rtl8192ce(OF) rtlwifi(OF) mac80211 cfg80211 dm_crypt(F) nvram(F) cuse parport_pc(F) ppdev(F) rfcomm bnep bluetooth uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev joydev(F) binfmt_misc(F) hp_wmi sparse_keymap arc4(F) kvm_amd(F) kvm(F) microcode(F) psmouse(F) serio_raw(F) snd_hda_codec_idt snd_hda_codec_hdmi k10temp snd_hda_intel snd_hda_codec snd_hwdep(F) rtsx_pci_ms memstick snd_pcm(F) snd_page_alloc(F) i2c_piix4 snd_seq_midi(F) snd_seq_midi_event(F) snd_rawmidi(F) snd_seq(F) snd_seq_device(F) snd_timer(F) snd(F) soundcore(F) hp_accel lis3lv02d input_polldev mac_hid lp(F) parport(F) pata_acpi hid_logitech_dj usbhid hid rtsx_pci_sdmmc radeon i2c_algo_bit ttm pata_atiixp ohci_pci drm_kms_helper sdhci_pci rtsx_pci ahci(F) sdhci libahci(F) drm r8169 mii(F) wmi video(F) [last unloaded: cfg80211]
[ 1067.169057] wlan0: authenticate with <MAC address removed>
[ 1067.179523] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1067.182317] wlan0: authenticated
[ 1067.185189] wlan0: associate with <MAC address removed> (try 1/3)
[ 1067.190807] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 1067.190968] wlan0: associated
[ 1088.751474] rtlwifi-0:rtl_op_ampdu_action():<0-0> IEEE80211_AMPDU_ERR!!!!:
[ 1088.751551] Modules linked in: rtl8192ce(OF) rtlwifi(OF) mac80211 cfg80211 dm_crypt(F) nvram(F) cuse parport_pc(F) ppdev(F) rfcomm bnep bluetooth uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev joydev(F) binfmt_misc(F) hp_wmi sparse_keymap arc4(F) kvm_amd(F) kvm(F) microcode(F) psmouse(F) serio_raw(F) snd_hda_codec_idt snd_hda_codec_hdmi k10temp snd_hda_intel snd_hda_codec snd_hwdep(F) rtsx_pci_ms memstick snd_pcm(F) snd_page_alloc(F) i2c_piix4 snd_seq_midi(F) snd_seq_midi_event(F) snd_rawmidi(F) snd_seq(F) snd_seq_device(F) snd_timer(F) snd(F) soundcore(F) hp_accel lis3lv02d input_polldev mac_hid lp(F) parport(F) pata_acpi hid_logitech_dj usbhid hid rtsx_pci_sdmmc radeon i2c_algo_bit ttm pata_atiixp ohci_pci drm_kms_helper sdhci_pci rtsx_pci ahci(F) sdhci libahci(F) drm r8169 mii(F) wmi video(F) [last unloaded: cfg80211]
[ 1088.762946] wlan0: authenticate with <MAC address removed>
[ 1088.773224] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1089.416281] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1089.709381] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1090.010677] wlan0: authentication with <MAC address removed> timed out
[ 1090.051263] wlan0: authenticate with <MAC address removed>
[ 1090.062435] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1090.357493] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1090.666786] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1090.899613] wlan0: authentication with <MAC address removed> timed out
[ 1091.060915] wlan0: authenticate with <MAC address removed>
[ 1091.079477] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1091.080832] wlan0: authenticated
[ 1091.084071] wlan0: associate with <MAC address removed> (try 1/3)
[ 1091.090013] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 1091.090243] wlan0: associated
[ 1141.350090] rtlwifi-0:rtl_op_ampdu_action():<0-0> IEEE80211_AMPDU_ERR!!!!:
[ 1141.350152] Modules linked in: rtl8192ce(OF) rtlwifi(OF) mac80211 cfg80211 dm_crypt(F) nvram(F) cuse parport_pc(F) ppdev(F) rfcomm bnep bluetooth uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev joydev(F) binfmt_misc(F) hp_wmi sparse_keymap arc4(F) kvm_amd(F) kvm(F) microcode(F) psmouse(F) serio_raw(F) snd_hda_codec_idt snd_hda_codec_hdmi k10temp snd_hda_intel snd_hda_codec snd_hwdep(F) rtsx_pci_ms memstick snd_pcm(F) snd_page_alloc(F) i2c_piix4 snd_seq_midi(F) snd_seq_midi_event(F) snd_rawmidi(F) snd_seq(F) snd_seq_device(F) snd_timer(F) snd(F) soundcore(F) hp_accel lis3lv02d input_polldev mac_hid lp(F) parport(F) pata_acpi hid_logitech_dj usbhid hid rtsx_pci_sdmmc radeon i2c_algo_bit ttm pata_atiixp ohci_pci drm_kms_helper sdhci_pci rtsx_pci ahci(F) sdhci libahci(F) drm r8169 mii(F) wmi video(F) [last unloaded: cfg80211]
[ 1141.361544] wlan0: authenticate with <MAC address removed>
[ 1141.361748] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1141.363538] wlan0: authenticated
[ 1141.367380] wlan0: associate with <MAC address removed> (try 1/3)
[ 1141.374900] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[ 1141.375249] wlan0: associated
[ 1163.382284] rtlwifi-0:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[ 1163.382352] wlan0: Connection to AP <MAC address removed> lost
[ 1163.874611] wlan0: authenticate with <MAC address removed>
[ 1163.884974] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1163.886273] wlan0: authenticated
[ 1163.890501] wlan0: associate with <MAC address removed> (try 1/3)
[ 1163.896327] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=5)
[ 1163.896556] wlan0: associated
[ 1190.629396] rtlwifi-0:rtl_op_ampdu_action():<0-0> IEEE80211_AMPDU_ERR!!!!:
[ 1190.629458] Modules linked in: rtl8192ce(OF) rtlwifi(OF) mac80211 cfg80211 dm_crypt(F) nvram(F) cuse parport_pc(F) ppdev(F) rfcomm bnep bluetooth uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev joydev(F) binfmt_misc(F) hp_wmi sparse_keymap arc4(F) kvm_amd(F) kvm(F) microcode(F) psmouse(F) serio_raw(F) snd_hda_codec_idt snd_hda_codec_hdmi k10temp snd_hda_intel snd_hda_codec snd_hwdep(F) rtsx_pci_ms memstick snd_pcm(F) snd_page_alloc(F) i2c_piix4 snd_seq_midi(F) snd_seq_midi_event(F) snd_rawmidi(F) snd_seq(F) snd_seq_device(F) snd_timer(F) snd(F) soundcore(F) hp_accel lis3lv02d input_polldev mac_hid lp(F) parport(F) pata_acpi hid_logitech_dj usbhid hid rtsx_pci_sdmmc radeon i2c_algo_bit ttm pata_atiixp ohci_pci drm_kms_helper sdhci_pci rtsx_pci ahci(F) sdhci libahci(F) drm r8169 mii(F) wmi video(F) [last unloaded: cfg80211]
[ 1190.641068] wlan0: authenticate with <MAC address removed>
[ 1190.651295] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1190.658321] wlan0: authenticated
[ 1190.661875] wlan0: associate with <MAC address removed> (try 1/3)
[ 1190.667734] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 1190.667967] wlan0: associated
[ 1257.660432] wlan0: authenticate with <MAC address removed>
[ 1257.672955] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1257.675263] wlan0: authenticated
[ 1257.678862] wlan0: associate with <MAC address removed> (try 1/3)
[ 1257.684440] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=5)
[ 1257.684725] wlan0: associated
[ 1323.614131] rtlwifi-0:rtl_op_ampdu_action():<0-0> IEEE80211_AMPDU_ERR!!!!:
[ 1323.614192] Modules linked in: rtl8192ce(OF) rtlwifi(OF) mac80211 cfg80211 dm_crypt(F) nvram(F) cuse parport_pc(F) ppdev(F) rfcomm bnep bluetooth uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev joydev(F) binfmt_misc(F) hp_wmi sparse_keymap arc4(F) kvm_amd(F) kvm(F) microcode(F) psmouse(F) serio_raw(F) snd_hda_codec_idt snd_hda_codec_hdmi k10temp snd_hda_intel snd_hda_codec snd_hwdep(F) rtsx_pci_ms memstick snd_pcm(F) snd_page_alloc(F) i2c_piix4 snd_seq_midi(F) snd_seq_midi_event(F) snd_rawmidi(F) snd_seq(F) snd_seq_device(F) snd_timer(F) snd(F) soundcore(F) hp_accel lis3lv02d input_polldev mac_hid lp(F) parport(F) pata_acpi hid_logitech_dj usbhid hid rtsx_pci_sdmmc radeon i2c_algo_bit ttm pata_atiixp ohci_pci drm_kms_helper sdhci_pci rtsx_pci ahci(F) sdhci libahci(F) drm r8169 mii(F) wmi video(F) [last unloaded: cfg80211]
[ 1323.625351] wlan0: authenticate with <MAC address removed>
[ 1323.638464] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1323.644784] wlan0: authenticated
[ 1323.647947] wlan0: associate with <MAC address removed> (try 1/3)
[ 1323.653689] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 1323.653879] wlan0: associated
[ 1361.003671] rtlwifi-0:rtl_op_ampdu_action():<0-0> IEEE80211_AMPDU_ERR!!!!:
[ 1361.003733] Modules linked in: rtl8192ce(OF) rtlwifi(OF) mac80211 cfg80211 dm_crypt(F) nvram(F) cuse parport_pc(F) ppdev(F) rfcomm bnep bluetooth uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev joydev(F) binfmt_misc(F) hp_wmi sparse_keymap arc4(F) kvm_amd(F) kvm(F) microcode(F) psmouse(F) serio_raw(F) snd_hda_codec_idt snd_hda_codec_hdmi k10temp snd_hda_intel snd_hda_codec snd_hwdep(F) rtsx_pci_ms memstick snd_pcm(F) snd_page_alloc(F) i2c_piix4 snd_seq_midi(F) snd_seq_midi_event(F) snd_rawmidi(F) snd_seq(F) snd_seq_device(F) snd_timer(F) snd(F) soundcore(F) hp_accel lis3lv02d input_polldev mac_hid lp(F) parport(F) pata_acpi hid_logitech_dj usbhid hid rtsx_pci_sdmmc radeon i2c_algo_bit ttm pata_atiixp ohci_pci drm_kms_helper sdhci_pci rtsx_pci ahci(F) sdhci libahci(F) drm r8169 mii(F) wmi video(F) [last unloaded: cfg80211]
[ 1361.015819] wlan0: authenticate with <MAC address removed>
[ 1361.026337] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1361.028741] wlan0: authenticated
[ 1361.032641] wlan0: associate with <MAC address removed> (try 1/3)
[ 1361.039944] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=5)
[ 1361.040118] wlan0: associated
[ 1380.306810] rtlwifi-0:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[ 1380.306885] wlan0: Connection to AP <MAC address removed> lost
[ 1380.343480] rtlwifi-0:rtl_op_ampdu_action():<0-0> IEEE80211_AMPDU_ERR!!!!:
[ 1380.343541] Modules linked in: rtl8192ce(OF) rtlwifi(OF) mac80211 cfg80211 dm_crypt(F) nvram(F) cuse parport_pc(F) ppdev(F) rfcomm bnep bluetooth uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev joydev(F) binfmt_misc(F) hp_wmi sparse_keymap arc4(F) kvm_amd(F) kvm(F) microcode(F) psmouse(F) serio_raw(F) snd_hda_codec_idt snd_hda_codec_hdmi k10temp snd_hda_intel snd_hda_codec snd_hwdep(F) rtsx_pci_ms memstick snd_pcm(F) snd_page_alloc(F) i2c_piix4 snd_seq_midi(F) snd_seq_midi_event(F) snd_rawmidi(F) snd_seq(F) snd_seq_device(F) snd_timer(F) snd(F) soundcore(F) hp_accel lis3lv02d input_polldev mac_hid lp(F) parport(F) pata_acpi hid_logitech_dj usbhid hid rtsx_pci_sdmmc radeon i2c_algo_bit ttm pata_atiixp ohci_pci drm_kms_helper sdhci_pci rtsx_pci ahci(F) sdhci libahci(F) drm r8169 mii(F) wmi video(F) [last unloaded: cfg80211]
[ 1380.829492] wlan0: authenticate with <MAC address removed>
[ 1380.840611] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1380.842175] wlan0: authenticated
[ 1380.843316] wlan0: associate with <MAC address removed> (try 1/3)
[ 1380.849043] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 1380.849393] wlan0: associated
[ 1440.930432] rtlwifi-0:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[ 1440.930515] wlan0: Connection to AP <MAC address removed> lost
[ 1440.947636] rtlwifi-0:rtl_op_ampdu_action():<0-0> IEEE80211_AMPDU_ERR!!!!:
[ 1440.947699] Modules linked in: rtl8192ce(OF) rtlwifi(OF) mac80211 cfg80211 dm_crypt(F) nvram(F) cuse parport_pc(F) ppdev(F) rfcomm bnep bluetooth uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev joydev(F) binfmt_misc(F) hp_wmi sparse_keymap arc4(F) kvm_amd(F) kvm(F) microcode(F) psmouse(F) serio_raw(F) snd_hda_codec_idt snd_hda_codec_hdmi k10temp snd_hda_intel snd_hda_codec snd_hwdep(F) rtsx_pci_ms memstick snd_pcm(F) snd_page_alloc(F) i2c_piix4 snd_seq_midi(F) snd_seq_midi_event(F) snd_rawmidi(F) snd_seq(F) snd_seq_device(F) snd_timer(F) snd(F) soundcore(F) hp_accel lis3lv02d input_polldev mac_hid lp(F) parport(F) pata_acpi hid_logitech_dj usbhid hid rtsx_pci_sdmmc radeon i2c_algo_bit ttm pata_atiixp ohci_pci drm_kms_helper sdhci_pci rtsx_pci ahci(F) sdhci libahci(F) drm r8169 mii(F) wmi video(F) [last unloaded: cfg80211]
[ 1442.239005] wlan0: authenticate with <MAC address removed>
[ 1442.256168] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1442.257446] wlan0: authenticated
[ 1442.259448] wlan0: associate with <MAC address removed> (try 1/3)
[ 1442.265351] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 1442.265625] wlan0: associated
[ 1506.074937] rtlwifi-0:rtl_op_ampdu_action():<0-0> IEEE80211_AMPDU_ERR!!!!:
[ 1506.074999] Modules linked in: rtl8192ce(OF) rtlwifi(OF) mac80211 cfg80211 dm_crypt(F) nvram(F) cuse parport_pc(F) ppdev(F) rfcomm bnep bluetooth uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev joydev(F) binfmt_misc(F) hp_wmi sparse_keymap arc4(F) kvm_amd(F) kvm(F) microcode(F) psmouse(F) serio_raw(F) snd_hda_codec_idt snd_hda_codec_hdmi k10temp snd_hda_intel snd_hda_codec snd_hwdep(F) rtsx_pci_ms memstick snd_pcm(F) snd_page_alloc(F) i2c_piix4 snd_seq_midi(F) snd_seq_midi_event(F) snd_rawmidi(F) snd_seq(F) snd_seq_device(F) snd_timer(F) snd(F) soundcore(F) hp_accel lis3lv02d input_polldev mac_hid lp(F) parport(F) pata_acpi hid_logitech_dj usbhid hid rtsx_pci_sdmmc radeon i2c_algo_bit ttm pata_atiixp ohci_pci drm_kms_helper sdhci_pci rtsx_pci ahci(F) sdhci libahci(F) drm r8169 mii(F) wmi video(F) [last unloaded: cfg80211]
[ 1506.086628] wlan0: authenticate with <MAC address removed>
[ 1506.097020] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1506.101398] wlan0: authenticated
[ 1506.103900] wlan0: associate with <MAC address removed> (try 1/3)
[ 1506.109483] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 1506.109683] wlan0: associated
[ 1516.196039] wlan0: authenticate with <MAC address removed>
[ 1516.206577] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1516.209098] wlan0: authenticated
[ 1516.213265] wlan0: associate with <MAC address removed> (try 1/3)
[ 1516.219922] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=6)
[ 1516.220259] wlan0: associated
[ 1530.659180] rtlwifi-0:rtl_op_ampdu_action():<0-0> IEEE80211_AMPDU_ERR!!!!:
[ 1530.659242] Modules linked in: rtl8192ce(OF) rtlwifi(OF) mac80211 cfg80211 dm_crypt(F) nvram(F) cuse parport_pc(F) ppdev(F) rfcomm bnep bluetooth uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev joydev(F) binfmt_misc(F) hp_wmi sparse_keymap arc4(F) kvm_amd(F) kvm(F) microcode(F) psmouse(F) serio_raw(F) snd_hda_codec_idt snd_hda_codec_hdmi k10temp snd_hda_intel snd_hda_codec snd_hwdep(F) rtsx_pci_ms memstick snd_pcm(F) snd_page_alloc(F) i2c_piix4 snd_seq_midi(F) snd_seq_midi_event(F) snd_rawmidi(F) snd_seq(F) snd_seq_device(F) snd_timer(F) snd(F) soundcore(F) hp_accel lis3lv02d input_polldev mac_hid lp(F) parport(F) pata_acpi hid_logitech_dj usbhid hid rtsx_pci_sdmmc radeon i2c_algo_bit ttm pata_atiixp ohci_pci drm_kms_helper sdhci_pci rtsx_pci ahci(F) sdhci libahci(F) drm r8169 mii(F) wmi video(F) [last unloaded: cfg80211]
[ 1530.670420] wlan0: authenticate with <MAC address removed>
[ 1530.670623] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1530.691314] wlan0: authenticated
[ 1530.695289] wlan0: associate with <MAC address removed> (try 1/3)
[ 1530.974247] wlan0: associate with <MAC address removed> (try 2/3)
[ 1530.981208] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=3)
[ 1530.981515] wlan0: associated
[ 1564.680390] wlan0: authenticate with <MAC address removed>
[ 1564.690800] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1565.316724] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1565.612240] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1565.918433] wlan0: authentication with <MAC address removed> timed out
[ 1566.206872] wlan0: authenticate with <MAC address removed>
[ 1566.225465] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1566.226860] wlan0: authenticated
[ 1566.227954] wlan0: associate with <MAC address removed> (try 1/3)
[ 1566.235960] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 1566.236191] wlan0: associated
[ 1629.571641] rtlwifi-0:rtl_op_ampdu_action():<0-0> IEEE80211_AMPDU_ERR!!!!:
[ 1629.571704] Modules linked in: rtl8192ce(OF) rtlwifi(OF) mac80211 cfg80211 dm_crypt(F) nvram(F) cuse parport_pc(F) ppdev(F) rfcomm bnep bluetooth uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev joydev(F) binfmt_misc(F) hp_wmi sparse_keymap arc4(F) kvm_amd(F) kvm(F) microcode(F) psmouse(F) serio_raw(F) snd_hda_codec_idt snd_hda_codec_hdmi k10temp snd_hda_intel snd_hda_codec snd_hwdep(F) rtsx_pci_ms memstick snd_pcm(F) snd_page_alloc(F) i2c_piix4 snd_seq_midi(F) snd_seq_midi_event(F) snd_rawmidi(F) snd_seq(F) snd_seq_device(F) snd_timer(F) snd(F) soundcore(F) hp_accel lis3lv02d input_polldev mac_hid lp(F) parport(F) pata_acpi hid_logitech_dj usbhid hid rtsx_pci_sdmmc radeon i2c_algo_bit ttm pata_atiixp ohci_pci drm_kms_helper sdhci_pci rtsx_pci ahci(F) sdhci libahci(F) drm r8169 mii(F) wmi video(F) [last unloaded: cfg80211]
[ 1629.583078] wlan0: authenticate with <MAC address removed>
[ 1629.593364] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1629.598773] wlan0: authenticated
[ 1629.600526] wlan0: associate with <MAC address removed> (try 1/3)
[ 1629.606536] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=3)
[ 1629.606965] wlan0: associated
[ 1693.397433] rtlwifi-0:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[ 1693.397581] wlan0: Connection to AP <MAC address removed> lost
[ 1694.067446] wlan0: authenticate with <MAC address removed>
[ 1694.086231] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1694.087560] wlan0: authenticated
[ 1694.089109] wlan0: associate with <MAC address removed> (try 1/3)
[ 1694.095360] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 1694.095595] wlan0: associated
[ 1723.929156] rtlwifi-0:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[ 1723.929253] wlan0: Connection to AP <MAC address removed> lost
[ 1723.937475] rtlwifi-0:rtl_op_ampdu_action():<0-0> IEEE80211_AMPDU_ERR!!!!:
[ 1723.937536] Modules linked in: rtl8192ce(OF) rtlwifi(OF) mac80211 cfg80211 dm_crypt(F) nvram(F) cuse parport_pc(F) ppdev(F) rfcomm bnep bluetooth uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev joydev(F) binfmt_misc(F) hp_wmi sparse_keymap arc4(F) kvm_amd(F) kvm(F) microcode(F) psmouse(F) serio_raw(F) snd_hda_codec_idt snd_hda_codec_hdmi k10temp snd_hda_intel snd_hda_codec snd_hwdep(F) rtsx_pci_ms memstick snd_pcm(F) snd_page_alloc(F) i2c_piix4 snd_seq_midi(F) snd_seq_midi_event(F) snd_rawmidi(F) snd_seq(F) snd_seq_device(F) snd_timer(F) snd(F) soundcore(F) hp_accel lis3lv02d input_polldev mac_hid lp(F) parport(F) pata_acpi hid_logitech_dj usbhid hid rtsx_pci_sdmmc radeon i2c_algo_bit ttm pata_atiixp ohci_pci drm_kms_helper sdhci_pci rtsx_pci ahci(F) sdhci libahci(F) drm r8169 mii(F) wmi video(F) [last unloaded: cfg80211]
[ 1724.591271] wlan0: authenticate with <MAC address removed>
[ 1724.610375] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1724.813299] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1725.017211] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1725.221202] wlan0: authentication with <MAC address removed> timed out
[ 1726.215957] wlan0: authenticate with <MAC address removed>
[ 1726.234124] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1726.235799] wlan0: authenticated
[ 1726.237287] wlan0: associate with <MAC address removed> (try 1/3)
[ 1726.243059] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=6)
[ 1726.243255] wlan0: associated
[ 1773.686372] rtlwifi-0:rtl_op_ampdu_action():<0-0> IEEE80211_AMPDU_ERR!!!!:
[ 1773.686433] Modules linked in: rtl8192ce(OF) rtlwifi(OF) mac80211 cfg80211 dm_crypt(F) nvram(F) cuse parport_pc(F) ppdev(F) rfcomm bnep bluetooth uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev joydev(F) binfmt_misc(F) hp_wmi sparse_keymap arc4(F) kvm_amd(F) kvm(F) microcode(F) psmouse(F) serio_raw(F) snd_hda_codec_idt snd_hda_codec_hdmi k10temp snd_hda_intel snd_hda_codec snd_hwdep(F) rtsx_pci_ms memstick snd_pcm(F) snd_page_alloc(F) i2c_piix4 snd_seq_midi(F) snd_seq_midi_event(F) snd_rawmidi(F) snd_seq(F) snd_seq_device(F) snd_timer(F) snd(F) soundcore(F) hp_accel lis3lv02d input_polldev mac_hid lp(F) parport(F) pata_acpi hid_logitech_dj usbhid hid rtsx_pci_sdmmc radeon i2c_algo_bit ttm pata_atiixp ohci_pci drm_kms_helper sdhci_pci rtsx_pci ahci(F) sdhci libahci(F) drm r8169 mii(F) wmi video(F) [last unloaded: cfg80211]
[ 1773.697829] wlan0: authenticate with <MAC address removed>
[ 1773.708167] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1774.218697] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1775.155176] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1776.091483] wlan0: authentication with <MAC address removed> timed out
[ 1776.378702] wlan0: authenticate with <MAC address removed>
[ 1776.389061] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1776.392422] wlan0: authenticated
[ 1776.396011] wlan0: associate with <MAC address removed> (try 1/3)
[ 1776.404168] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=6)
[ 1776.404496] wlan0: associated
[ 1796.186681] rtlwifi-0:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[ 1796.186732] wlan0: Connection to AP <MAC address removed> lost
[ 1796.210862] rtlwifi-0:rtl_op_ampdu_action():<0-0> IEEE80211_AMPDU_ERR!!!!:
[ 1796.210924] Modules linked in: rtl8192ce(OF) rtlwifi(OF) mac80211 cfg80211 dm_crypt(F) nvram(F) cuse parport_pc(F) ppdev(F) rfcomm bnep bluetooth uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev joydev(F) binfmt_misc(F) hp_wmi sparse_keymap arc4(F) kvm_amd(F) kvm(F) microcode(F) psmouse(F) serio_raw(F) snd_hda_codec_idt snd_hda_codec_hdmi k10temp snd_hda_intel snd_hda_codec snd_hwdep(F) rtsx_pci_ms memstick snd_pcm(F) snd_page_alloc(F) i2c_piix4 snd_seq_midi(F) snd_seq_midi_event(F) snd_rawmidi(F) snd_seq(F) snd_seq_device(F) snd_timer(F) snd(F) soundcore(F) hp_accel lis3lv02d input_polldev mac_hid lp(F) parport(F) pata_acpi hid_logitech_dj usbhid hid rtsx_pci_sdmmc radeon i2c_algo_bit ttm pata_atiixp ohci_pci drm_kms_helper sdhci_pci rtsx_pci ahci(F) sdhci libahci(F) drm r8169 mii(F) wmi video(F) [last unloaded: cfg80211]
[ 1796.533361] wlan0: authenticate with <MAC address removed>
[ 1796.552542] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1796.554695] wlan0: authenticated
[ 1796.558932] wlan0: associate with <MAC address removed> (try 1/3)
[ 1796.564645] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 1796.564920] wlan0: associated
[ 1810.280367] rtlwifi-0:rtl_op_ampdu_action():<0-0> IEEE80211_AMPDU_ERR!!!!:
[ 1810.280474] Modules linked in: rtl8192ce(OF) rtlwifi(OF) mac80211 cfg80211 dm_crypt(F) nvram(F) cuse parport_pc(F) ppdev(F) rfcomm bnep bluetooth uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev joydev(F) binfmt_misc(F) hp_wmi sparse_keymap arc4(F) kvm_amd(F) kvm(F) microcode(F) psmouse(F) serio_raw(F) snd_hda_codec_idt snd_hda_codec_hdmi k10temp snd_hda_intel snd_hda_codec snd_hwdep(F) rtsx_pci_ms memstick snd_pcm(F) snd_page_alloc(F) i2c_piix4 snd_seq_midi(F) snd_seq_midi_event(F) snd_rawmidi(F) snd_seq(F) snd_seq_device(F) snd_timer(F) snd(F) soundcore(F) hp_accel lis3lv02d input_polldev mac_hid lp(F) parport(F) pata_acpi hid_logitech_dj usbhid hid rtsx_pci_sdmmc radeon i2c_algo_bit ttm pata_atiixp ohci_pci drm_kms_helper sdhci_pci rtsx_pci ahci(F) sdhci libahci(F) drm r8169 mii(F) wmi video(F) [last unloaded: cfg80211]
[ 1810.291622] wlan0: authenticate with <MAC address removed>
[ 1810.302224] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1810.304374] wlan0: authenticated
[ 1810.308927] wlan0: associate with <MAC address removed> (try 1/3)
[ 1810.314737] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[ 1810.314937] wlan0: associated
[ 1820.060265] wlan0: authenticate with <MAC address removed>
[ 1820.071379] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1820.708904] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1821.004639] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1821.300375] wlan0: authentication with <MAC address removed> timed out
[ 1821.588291] wlan0: authenticate with <MAC address removed>
[ 1821.607272] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1821.609579] wlan0: authenticated
[ 1821.613984] wlan0: associate with <MAC address removed> (try 1/3)
[ 1821.621452] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[ 1821.621744] wlan0: associated
[ 1831.318879] rtlwifi-0:rtl_op_ampdu_action():<0-0> IEEE80211_AMPDU_ERR!!!!:
[ 1831.318941] Modules linked in: rtl8192ce(OF) rtlwifi(OF) mac80211 cfg80211 dm_crypt(F) nvram(F) cuse parport_pc(F) ppdev(F) rfcomm bnep bluetooth uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev joydev(F) binfmt_misc(F) hp_wmi sparse_keymap arc4(F) kvm_amd(F) kvm(F) microcode(F) psmouse(F) serio_raw(F) snd_hda_codec_idt snd_hda_codec_hdmi k10temp snd_hda_intel snd_hda_codec snd_hwdep(F) rtsx_pci_ms memstick snd_pcm(F) snd_page_alloc(F) i2c_piix4 snd_seq_midi(F) snd_seq_midi_event(F) snd_rawmidi(F) snd_seq(F) snd_seq_device(F) snd_timer(F) snd(F) soundcore(F) hp_accel lis3lv02d input_polldev mac_hid lp(F) parport(F) pata_acpi hid_logitech_dj usbhid hid rtsx_pci_sdmmc radeon i2c_algo_bit ttm pata_atiixp ohci_pci drm_kms_helper sdhci_pci rtsx_pci ahci(F) sdhci libahci(F) drm r8169 mii(F) wmi video(F) [last unloaded: cfg80211]
[ 1831.330463] wlan0: authenticate with <MAC address removed>
[ 1831.341287] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1831.978321] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1832.274398] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1832.570136] wlan0: authentication with <MAC address removed> timed out
[ 1832.793681] wlan0: authenticate with <MAC address removed>
[ 1832.812775] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1832.819004] wlan0: authenticated
[ 1832.819758] wlan0: associate with <MAC address removed> (try 1/3)
[ 1832.825577] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[ 1832.825835] wlan0: associated
[ 1866.310795] rtlwifi-0:rtl_op_ampdu_action():<0-0> IEEE80211_AMPDU_ERR!!!!:
[ 1866.310859] Modules linked in: rtl8192ce(OF) rtlwifi(OF) mac80211 cfg80211 dm_crypt(F) nvram(F) cuse parport_pc(F) ppdev(F) rfcomm bnep bluetooth uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev joydev(F) binfmt_misc(F) hp_wmi sparse_keymap arc4(F) kvm_amd(F) kvm(F) microcode(F) psmouse(F) serio_raw(F) snd_hda_codec_idt snd_hda_codec_hdmi k10temp snd_hda_intel snd_hda_codec snd_hwdep(F) rtsx_pci_ms memstick snd_pcm(F) snd_page_alloc(F) i2c_piix4 snd_seq_midi(F) snd_seq_midi_event(F) snd_rawmidi(F) snd_seq(F) snd_seq_device(F) snd_timer(F) snd(F) soundcore(F) hp_accel lis3lv02d input_polldev mac_hid lp(F) parport(F) pata_acpi hid_logitech_dj usbhid hid rtsx_pci_sdmmc radeon i2c_algo_bit ttm pata_atiixp ohci_pci drm_kms_helper sdhci_pci rtsx_pci ahci(F) sdhci libahci(F) drm r8169 mii(F) wmi video(F) [last unloaded: cfg80211]
[ 1866.322456] wlan0: authenticate with <MAC address removed>
[ 1866.333304] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1866.843100] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1867.782677] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1868.078826] wlan0: authentication with <MAC address removed> timed out
[ 1868.367081] wlan0: authenticate with <MAC address removed>
[ 1868.385904] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1868.387392] wlan0: authenticated
[ 1868.388261] wlan0: associate with <MAC address removed> (try 1/3)
[ 1868.394223] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=3)
[ 1868.394503] wlan0: associated
[ 1887.317837] rtlwifi-0:rtl_op_ampdu_action():<0-0> IEEE80211_AMPDU_ERR!!!!:
[ 1887.317900] Modules linked in: rtl8192ce(OF) rtlwifi(OF) mac80211 cfg80211 dm_crypt(F) nvram(F) cuse parport_pc(F) ppdev(F) rfcomm bnep bluetooth uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev joydev(F) binfmt_misc(F) hp_wmi sparse_keymap arc4(F) kvm_amd(F) kvm(F) microcode(F) psmouse(F) serio_raw(F) snd_hda_codec_idt snd_hda_codec_hdmi k10temp snd_hda_intel snd_hda_codec snd_hwdep(F) rtsx_pci_ms memstick snd_pcm(F) snd_page_alloc(F) i2c_piix4 snd_seq_midi(F) snd_seq_midi_event(F) snd_rawmidi(F) snd_seq(F) snd_seq_device(F) snd_timer(F) snd(F) soundcore(F) hp_accel lis3lv02d input_polldev mac_hid lp(F) parport(F) pata_acpi hid_logitech_dj usbhid hid rtsx_pci_sdmmc radeon i2c_algo_bit ttm pata_atiixp ohci_pci drm_kms_helper sdhci_pci rtsx_pci ahci(F) sdhci libahci(F) drm r8169 mii(F) wmi video(F) [last unloaded: cfg80211]
[ 1887.329547] wlan0: authenticate with <MAC address removed>
[ 1887.340140] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1887.343178] wlan0: authenticated
[ 1887.346819] wlan0: associate with <MAC address removed> (try 1/3)
[ 1887.353012] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=5)
[ 1887.353169] wlan0: associated
[ 1893.716409] rtlwifi-0:rtl_op_ampdu_action():<0-0> IEEE80211_AMPDU_ERR!!!!:
[ 1893.716469] Modules linked in: rtl8192ce(OF) rtlwifi(OF) mac80211 cfg80211 dm_crypt(F) nvram(F) cuse parport_pc(F) ppdev(F) rfcomm bnep bluetooth uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev joydev(F) binfmt_misc(F) hp_wmi sparse_keymap arc4(F) kvm_amd(F) kvm(F) microcode(F) psmouse(F) serio_raw(F) snd_hda_codec_idt snd_hda_codec_hdmi k10temp snd_hda_intel snd_hda_codec snd_hwdep(F) rtsx_pci_ms memstick snd_pcm(F) snd_page_alloc(F) i2c_piix4 snd_seq_midi(F) snd_seq_midi_event(F) snd_rawmidi(F) snd_seq(F) snd_seq_device(F) snd_timer(F) snd(F) soundcore(F) hp_accel lis3lv02d input_polldev mac_hid lp(F) parport(F) pata_acpi hid_logitech_dj usbhid hid rtsx_pci_sdmmc radeon i2c_algo_bit ttm pata_atiixp ohci_pci drm_kms_helper sdhci_pci rtsx_pci ahci(F) sdhci libahci(F) drm r8169 mii(F) wmi video(F) [last unloaded: cfg80211]
[ 1893.728068] wlan0: authenticate with <MAC address removed>
[ 1893.728282] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1893.732468] wlan0: authenticated
[ 1893.735744] wlan0: associate with <MAC address removed> (try 1/3)
[ 1893.744872] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 1893.745130] wlan0: associated
[ 1927.222760] wlan0: authenticate with <MAC address removed>
[ 1927.233448] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1927.235555] wlan0: authenticated
[ 1927.240211] wlan0: associate with <MAC address removed> (try 1/3)
[ 1927.249578] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=3)
[ 1927.249859] wlan0: associated
[ 1935.175339] wlan0: authenticate with <MAC address removed>
[ 1935.185707] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1935.813716] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1936.110204] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1936.418429] wlan0: authentication with <MAC address removed> timed out
[ 1936.703563] wlan0: authenticate with <MAC address removed>
[ 1936.722474] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1936.825450] wlan0: send auth to <MAC address removed> (try 2/3)
[ 1936.830692] wlan0: authenticated
[ 1936.833465] wlan0: associate with <MAC address removed> (try 1/3)
[ 1936.937440] wlan0: associate with <MAC address removed> (try 2/3)
[ 1936.953345] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 1936.953795] wlan0: associated
[ 1989.200725] wlan0: authenticate with <MAC address removed>
[ 1989.211104] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1989.851517] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1990.147896] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1990.433364] wlan0: authentication with <MAC address removed> timed out
[ 1990.445951] wlan0: authenticate with <MAC address removed>
[ 1990.456257] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1990.458489] wlan0: authenticated
[ 1990.705945] wlan0: authenticate with <MAC address removed>
[ 1990.716545] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1990.920764] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1991.124889] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1991.328851] wlan0: authentication with <MAC address removed> timed out
[ 1991.510631] wlan0: authenticate with <MAC address removed>
[ 1991.529770] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1991.532433] wlan0: authenticated
[ 1991.536784] wlan0: associate with <MAC address removed> (try 1/3)
[ 1991.545803] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 1991.546079] wlan0: associated


****************** done ******************



```

---

