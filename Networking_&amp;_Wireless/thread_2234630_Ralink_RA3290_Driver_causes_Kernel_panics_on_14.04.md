---
title: "Ralink RA3290 Driver causes Kernel panics on 14.04"
date: 2014-07-15
forum: Networking &amp; Wireless
---

### Post by shane-u on 2014-07-15
Dear All,
I am after some assistance with the Wifi Drivers on my HP Split x2 with the Ralink RT3290 card.  With the driver that Ubuntu 14.04 supplies (rt2800pci & rt2x00pci) I get very poor performance on our N band router (3.87mbps upload & 2.17mbps download as compared to 67.32mbps up & 38.24mbps down wired on the same network)  at work (it is OK on the G band at home).  I am not able to turn off the N band and besides I want it to be able to work on the newer technology.
I have installed the RT3290 driver as shown [here]("http://linuxforums.org.uk/index.php?topic=10422.0") and unfortunately this causes the kernel to crash as soon as I try to access the internet (I have tried other browsers but it is still the same so it is not a Firefox thing).  When the kernel crashes I get this message (sorry had to take a picture with my camera).

[http://i136.photobucket.com/albums/q163/rangi01/Mobile%20Uploads/2014-07/65006054-9E91-448C-B88E-972E5179BFA4_zpsfaonipdp.jpg](http://i136.photobucket.com/albums/q163/rangi01/Mobile%20Uploads/2014-07/65006054-9E91-448C-B88E-972E5179BFA4_zpsfaonipdp.jpg)

Any help is most appreciated.  Any information that you need please just ask.

Kind regards

Shane

---

### Post by shane-u on 2014-07-15
Sorry I forgot to mention that I am using the latest 3.16.0-031600rc4 kernel.

---

### Post by shane-u on 2014-07-15
And here is the output for 
 wget -N -t 5 -T 10 [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script) && chmod +x wireless_script && ./wireless_script


```
########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux shane-HP 3.16.0-031600rc4-generic #201407061635 SMP Sun Jul 6 20:36:26 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

##### lspci #####

01:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]
    Subsystem: Hewlett-Packard Company Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Adapter [103c:18ec]
    Kernel driver in use: rt2800pci

##### lsusb #####

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04f3:0117 Elan Microelectronics Corp. 
Bus 001 Device 003: ID 06cb:5710 Synaptics, Inc. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 064e:c350 Suyin Corp. 
Bus 003 Device 002: ID 0483:91d1 STMicroelectronics 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA Card Info #####

##### rfkill #####

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #####

rt2800pci              13674  0 
rt2800mmio             21082  1 rt2800pci
rt2800lib              95492  2 rt2800pci,rt2800mmio
rt2x00pci              13287  1 rt2800pci
rt2x00mmio             13661  2 rt2800pci,rt2800mmio
rt2x00lib              56170  5 rt2x00pci,rt2800lib,rt2800pci,rt2800mmio,rt2x00mmio
mac80211              687067  3 rt2x00lib,rt2x00pci,rt2800lib
cfg80211              521225  2 mac80211,rt2x00lib
eeprom_93cx6           13344  1 rt2800pci
crc_ccitt              12707  1 rt2800lib

##### iw reg get #####

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### interfaces #####

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

##### iwconfig #####

wlan0     IEEE 802.11bgn  ESSID:"Kiwilink"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: <MAC address removed>   
          Bit Rate=15 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=65/70  Signal level=-45 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:44  Invalid misc:32   Missed beacon:0

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.88.1    0.0.0.0         UG    0      0        0 wlan0
192.168.88.0    0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #####

nameserver 127.0.1.1

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: wlan0  [Kiwilink 1] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           15 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    ThodeUtting:     Infra, <MAC address removed>, Freq 2467 MHz, Rate 54 Mb/s, Strength 27 WPA
    Telecom-3282:    Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    *Kiwilink:       Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 77 WPA WPA2
    TNZ-3992:        Infra, <MAC address removed>, Freq 2472 MHz, Rate 54 Mb/s, Strength 10 WPA
    Kilian & Associates: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2

  IPv4 Settings:
    Address:         192.168.88.234
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.88.1

    DNS:             192.168.88.1

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### iwlist #####

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:"Kiwilink"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001a833b46a62
                    Extra: Last beacon: 36ms ago
                    IE: Unknown: 00084B6977696C696E6B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030102
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A4E1003FFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 3D1602050000000000000000000000000000000000000000
                    IE: Unknown: DD2A000C42000000011E0010000000660A060000443443413644413433324437000000000000000005027109
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E1003FFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3402050000000000000000000000000000000000000000
          Cell 02 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"Telecom-3282"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=8002ca644836e4d0
                    Extra: Last beacon: 36ms ago
                    IE: Unknown: 000C54656C65636F6D2D33323832
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 07064E5A20010D14
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A6E001EFFFF0000010000000000000000000000C8000000000000
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: 3D1606000500000000000000000000000000000000000000
                    IE: Unknown: 480100
                    IE: Unknown: 7F0101
                    IE: Unknown: DD1E00904C336E001EFFFF0000010000000000000000000000C8000000000000
                    IE: Unknown: DD1A00904C3406000500000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD050009860100
          Cell 03 - Address: <MAC address removed>
                    Channel:12
                    Frequency:2.467 GHz (Channel 12)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"ThodeUtting"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002bc4828c289
                    Extra: Last beacon: 36ms ago
                    IE: Unknown: 000B54686F6465557474696E67
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010C
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A8E1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D160C070700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DDA20050F204104A0001101044000102103B00010310470010BC329E001DD811B286016AC61F3BE0F41021001D48756177656920546563686E6F6C6F6769657320436F2E2C204C74642E1023001C48756177656920576972656C6573732041636365737320506F696E74102400065254323836301042000831323334353637381054000800060050F204000110110009487561776569415053100800020084103C000100
                    IE: Unknown: 0B05020015127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706455320010D10
                    IE: Unknown: DD1E00904C338E1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C340C070700000000000000000000000000000000000000

##### iwlist channel #####

wlan0     14 channels in total; available frequencies :
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
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Current Frequency:2.417 GHz (Channel 2)

##### modinfo #####

filename:       /lib/modules/3.16.0-031600rc4-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     F8D3E83728CFFB1CC77557E
alias:          pci:v00001814d0000539Fsv*sd*bc*sc*i*
alias:          pci:v00001814d0000539Bsv*sd*bc*sc*i*
alias:          pci:v00001814d0000539Asv*sd*bc*sc*i*
alias:          pci:v00001814d00005392sv*sd*bc*sc*i*
alias:          pci:v00001814d00005390sv*sd*bc*sc*i*
alias:          pci:v00001814d00005362sv*sd*bc*sc*i*
alias:          pci:v00001814d00005360sv*sd*bc*sc*i*
alias:          pci:v00001814d0000359Fsv*sd*bc*sc*i*
alias:          pci:v00001814d00003593sv*sd*bc*sc*i*
alias:          pci:v00001814d00003592sv*sd*bc*sc*i*
alias:          pci:v00001814d00003562sv*sd*bc*sc*i*
alias:          pci:v00001814d00003062sv*sd*bc*sc*i*
alias:          pci:v00001814d00003060sv*sd*bc*sc*i*
alias:          pci:v00001432d00007722sv*sd*bc*sc*i*
alias:          pci:v00001432d00007711sv*sd*bc*sc*i*
alias:          pci:v00001814d00003390sv*sd*bc*sc*i*
alias:          pci:v00001814d00003290sv*sd*bc*sc*i*
alias:          pci:v00001A3Bd00001059sv*sd*bc*sc*i*
alias:          pci:v00001462d0000891Asv*sd*bc*sc*i*
alias:          pci:v00001432d00007768sv*sd*bc*sc*i*
alias:          pci:v00001432d00007758sv*sd*bc*sc*i*
alias:          pci:v00001432d00007748sv*sd*bc*sc*i*
alias:          pci:v00001432d00007738sv*sd*bc*sc*i*
alias:          pci:v00001432d00007728sv*sd*bc*sc*i*
alias:          pci:v00001432d00007727sv*sd*bc*sc*i*
alias:          pci:v00001432d00007708sv*sd*bc*sc*i*
alias:          pci:v00001814d00003092sv*sd*bc*sc*i*
alias:          pci:v00001814d00003091sv*sd*bc*sc*i*
alias:          pci:v00001814d00003090sv*sd*bc*sc*i*
alias:          pci:v00001814d00000781sv*sd*bc*sc*i*
alias:          pci:v00001814d00000701sv*sd*bc*sc*i*
alias:          pci:v00001814d00000681sv*sd*bc*sc*i*
alias:          pci:v00001814d00000601sv*sd*bc*sc*i*
depends:        rt2x00lib,rt2800lib,rt2800mmio,rt2x00mmio,rt2x00pci,eeprom_93cx6
intree:         Y
vermagic:       3.16.0-031600rc4-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:48:53:B0:07:EF:17:03:13:9B:18:CF:98:AF:49
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)

filename:       /lib/modules/3.16.0-031600rc4-generic/kernel/drivers/net/wireless/rt2x00/rt2800mmio.ko
license:        GPL
description:    rt2800 MMIO library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     63729A11A0371D38A62802F
depends:        rt2800lib,rt2x00lib,rt2x00mmio
intree:         Y
vermagic:       3.16.0-031600rc4-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:48:53:B0:07:EF:17:03:13:9B:18:CF:98:AF:49
sig_hashalgo:   sha512

filename:       /lib/modules/3.16.0-031600rc4-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com), Bartlomiej Zolnierkiewicz
srcversion:     8D9F59A658EAF90D8F1EF97
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       3.16.0-031600rc4-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:48:53:B0:07:EF:17:03:13:9B:18:CF:98:AF:49
sig_hashalgo:   sha512

filename:       /lib/modules/3.16.0-031600rc4-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     7856EF56F97508465F566A2
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.16.0-031600rc4-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:48:53:B0:07:EF:17:03:13:9B:18:CF:98:AF:49
sig_hashalgo:   sha512

filename:       /lib/modules/3.16.0-031600rc4-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     37A76810C0FE9E4E11476DA
depends:        rt2x00lib
intree:         Y
vermagic:       3.16.0-031600rc4-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:48:53:B0:07:EF:17:03:13:9B:18:CF:98:AF:49
sig_hashalgo:   sha512

filename:       /lib/modules/3.16.0-031600rc4-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     02B2F4D2982AACC016889FC
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.16.0-031600rc4-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:48:53:B0:07:EF:17:03:13:9B:18:CF:98:AF:49
sig_hashalgo:   sha512

##### modules #####

lp
rtc

##### blacklist #####

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
blacklist rt2x00pci
blacklist rt3290sta

[/etc/modprobe.d/fbdev-blacklist.conf]
blacklist arkfb
blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist gx1fb
blacklist gxfb
blacklist kyrofb
blacklist matroxfb_base
blacklist mb862xxfb
blacklist neofb
blacklist nvidiafb
blacklist pm2fb
blacklist pm3fb
blacklist s3fb
blacklist savagefb
blacklist sisfb
blacklist tdfxfb
blacklist tridentfb
blacklist viafb
blacklist vt8623fb

##### udev rules #####

# PCI device 0x1814:0x3290 (rt2800pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #####

[    3.714417] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3290, rev 0015 detected
[    3.776301] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 3290 detected
[    5.106432] Modules linked in: hid_sensor_als hid_sensor_rotation hid_sensor_incl_3d hid_sensor_accel_3d hid_sensor_magn_3d hid_sensor_gyro_3d hid_sensor_trigger industrialio_triggered_buffer kfifo_buf industrialio hid_sensor_iio_common joydev hid_multitouch hid_rmi hid_sensor_hub hp_wmi snd_hda_intel(+) snd_hda_controller sparse_keymap snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_seq_midi_event snd_rawmidi intel_rapl x86_pkg_temp_thermal intel_powerclamp bnep coretemp rfcomm arc4 kvm bluetooth crct10dif_pclmul crc32_pclmul ghash_clmulni_intel 6lowpan_iphc cryptd snd_seq rt2800pci rt2800mmio rt2800lib rt2x00pci rt2x00mmio rt2x00lib snd_seq_device usbhid snd_timer mac80211 serio_raw hid mmc_block rtsx_pci_ms memstick cfg80211 lpc_ich(+) snd eeprom_93cx6 crc_ccitt soundcore mei_me mei i915(+) wmi hp_wireless uvcvideo video videobuf2_vmalloc drm_kms_helper videobuf2_memops videobuf2_core v4l2_common drm mac_hid videodev i2c_algo_bit parport_pc nls_iso8859_1 ppdev lp parport rtsx_pci_sdmmc ahci rtsx_pci libahci
[    5.107246] Modules linked in: hid_sensor_als hid_sensor_rotation hid_sensor_incl_3d hid_sensor_accel_3d hid_sensor_magn_3d hid_sensor_gyro_3d hid_sensor_trigger industrialio_triggered_buffer kfifo_buf industrialio hid_sensor_iio_common joydev hid_multitouch hid_rmi hid_sensor_hub hp_wmi snd_hda_intel(+) snd_hda_controller sparse_keymap snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_seq_midi_event snd_rawmidi intel_rapl x86_pkg_temp_thermal intel_powerclamp bnep coretemp rfcomm arc4 kvm bluetooth crct10dif_pclmul crc32_pclmul ghash_clmulni_intel 6lowpan_iphc cryptd snd_seq rt2800pci rt2800mmio rt2800lib rt2x00pci rt2x00mmio rt2x00lib snd_seq_device usbhid snd_timer mac80211 serio_raw hid mmc_block rtsx_pci_ms memstick cfg80211 lpc_ich(+) snd eeprom_93cx6 crc_ccitt soundcore mei_me mei i915(+) wmi hp_wireless uvcvideo video videobuf2_vmalloc drm_kms_helper videobuf2_memops videobuf2_core v4l2_common drm mac_hid videodev i2c_algo_bit parport_pc nls_iso8859_1 ppdev lp parport rtsx_pci_sdmmc ahci rtsx_pci libahci
[    5.150669] snd_hda_intel 0000:00:1b.0: Applying patch firmware 'hda-jack-retask.fw'
[    6.005725] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt3290.bin'
[    6.007096] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.37
[    6.135249] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    8.211782] wlan0: authenticate with <MAC address removed>
[    8.226905] wlan0: send auth to <MAC address removed> (try 1/3)
[    8.229202] wlan0: authenticated
[    8.230730] wlan0: associate with <MAC address removed> (try 1/3)
[    8.255467] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=4)
[    8.255594] wlan0: associated
[    8.255669] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[    8.788676] wlan0: deauthenticating from <MAC address removed> by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
[    8.810823] wlan0: authenticate with <MAC address removed>
[    8.818843] wlan0: send auth to <MAC address removed> (try 1/3)
[    8.821933] wlan0: authenticated
[    8.826649] wlan0: associate with <MAC address removed> (try 1/3)
[    8.855754] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=4)
[    8.855878] wlan0: associated
[   83.031121] wlan0: authenticate with <MAC address removed>
[   83.046443] wlan0: send auth to <MAC address removed> (try 1/3)
[   83.070431] wlan0: authenticated
[   83.074254] wlan0: associate with <MAC address removed> (try 1/3)
[   83.125004] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=4)
[   83.125122] wlan0: associated
[  135.981931] wlan0: authenticate with <MAC address removed>
[  135.997481] wlan0: send auth to <MAC address removed> (try 1/3)
[  136.034261] wlan0: authenticated
[  136.037269] wlan0: associate with <MAC address removed> (try 1/3)
[  136.145195] wlan0: associate with <MAC address removed> (try 2/3)
[  136.157448] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=4)
[  136.157585] wlan0: associated
[  196.936530] wlan0: authenticate with <MAC address removed>
[  196.951515] wlan0: send auth to <MAC address removed> (try 1/3)
[  196.981484] wlan0: authenticated
[  196.983264] wlan0: associate with <MAC address removed> (try 1/3)
[  197.167141] wlan0: associate with <MAC address removed> (try 2/3)
[  197.173668] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=4)
[  197.173827] wlan0: associated
[ 4715.343042] wlan0: authenticate with <MAC address removed>
[ 4715.358527] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4715.559048] wlan0: authenticated
[ 4715.562388] wlan0: associate with <MAC address removed> (try 1/3)
[ 4715.686370] wlan0: associate with <MAC address removed> (try 2/3)
[ 4715.698769] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=4)
[ 4715.698919] wlan0: associated
[ 4758.337883] wlan0: authenticate with <MAC address removed>
[ 4758.353269] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4758.407944] wlan0: authenticated
[ 4758.409092] wlan0: associate with <MAC address removed> (try 1/3)
[ 4758.441975] wlan0: associate with <MAC address removed> (try 2/3)
[ 4758.565101] wlan0: associate with <MAC address removed> (try 3/3)
[ 4758.574178] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=4)
[ 4758.574316] wlan0: associated
[ 4906.331706] wlan0: authenticate with <MAC address removed>
[ 4906.347172] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 4906.550909] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 4906.754885] wlan0: send auth to <MAC address removed> (try 3/3)
[ 4906.851992] wlan0: authenticated
[ 4906.854863] wlan0: associate with <MAC address removed> (try 1/3)
[ 4907.050845] wlan0: associate with <MAC address removed> (try 2/3)
[ 4907.064726] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=4)
[ 4907.064865] wlan0: associated

########## wireless info END ############
```

---

### Post by shane-u on 2014-07-19
I decided on a fresh install (as it has a seperate 500gb harddrive in the base I didn't lose any of my data) and try this [version]("http://askubuntu.com/questions/455030/ralink-rt3290-wifi-driver-is-not-working-in-ubuntu-14-04").
    After downloading the driver I moved it to the home folder then followed his instructions (with a couple of add-ons) Install dkms from the software centre
    Extract rt3290sta-2.6.0.0 directory into /usr/src using sudo tar -xf rt3290sta-2.6.0.0.tar -C /usr/src

    Run sudo dkms install -m rt3290sta -v 2.6.0.0 --force
    Reboot and you should be good :)

    After reboot I have good signal strength, speed and no drop-outs and no kernel panics (so far anyway)



    All is good and I hope that this helps someone.

---

### Post by wildmanne39 on 2014-07-19
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Please use thumbnails or URL"S when posting images because large images make it impossible for people with slow connections to load.

Glad you got it working!!

---

