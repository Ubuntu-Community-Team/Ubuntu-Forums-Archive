---
title: "Computer connects to wifi but internet does not work"
date: 2014-04-19
forum: Networking &amp; Wireless
---

### Post by steve109 on 2014-04-19
Hey guys, I'm new to Ubuntu and recently installed ubuntu 14.04 along side windows on my computer for a better coding environment. Everything went smoothly except when I try to use anything that involves the internet it does not work. I can't figure out why because it recognizes my wifi connects and says connected. Please help, thanks

---

### Post by varunendra on 2014-04-20
Welcome to the forums steve109! :)

Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by steve109 on 2014-04-20
Frist thanks for the welcome! I can't wait to get more into this community and learn everything I can. Here is the generated report.

```

  	 	 	 	   ########## wireless info START ########## 

##### release ##### 

Distributor ID:	Ubuntu Description:	Ubuntu 14.04 LTS Release:	14.04 Codename:	trusty 

##### kernel ##### 

Linux steve-desktop 3.13.0-24-generic #46-Ubuntu
SMP Thu Apr 10 19:11:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux 

##### lspci ##### 

05:00.0 Ethernet controller [0200]: Realtek
Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit
Ethernet Controller [10ec:8168] (rev 06) 	Subsystem: ASRock Incorporation Motherboard
(one of many) [1849:8168] 	Kernel driver in use: r8169 06:00.0 Network controller [0280]: Realtek
Semiconductor Co., Ltd. RTL8192CE PCIe Wireless Network Adapter
[10ec:8178] (rev 01) 	Subsystem: Device [7392:7622] 	Kernel driver in use: rtl8192ce 

##### lsusb ##### 

Bus 002 Device 003: ID 046d:c016 Logitech, Inc.
Optical Wheel Mouse Bus 002 Device 002: ID 8087:0024 Intel Corp.
Integrated Rate Matching Hub Bus 002 Device 001: ID 1d6b:0002 Linux
Foundation 2.0 root hub Bus 001 Device 002: ID 8087:0024 Intel Corp.
Integrated Rate Matching Hub Bus 001 Device 001: ID 1d6b:0002 Linux
Foundation 2.0 root hub Bus 004 Device 001: ID 1d6b:0003 Linux
Foundation 3.0 root hub Bus 003 Device 003: ID 046d:c52f Logitech, Inc.
Unifying Receiver Bus 003 Device 002: ID 413c:2005 Dell Computer
Corp. RT7D50 Keyboard Bus 003 Device 001: ID 1d6b:0002 Linux
Foundation 2.0 root hub 

##### PCMCIA Card Info ##### 

##### rfkill ##### 

0: phy0: Wireless LAN 	Soft blocked: no 	Hard blocked: no 

##### iw reg get ##### 

country US: 	(2402 - 2472 @ 40), (3, 27) 	(5170 - 5250 @ 40), (3, 17) 	(5250 - 5330 @ 40), (3, 20), DFS 	(5490 - 5600 @ 40), (3, 20), DFS 	(5650 - 5710 @ 40), (3, 20), DFS 	(5735 - 5835 @ 40), (3, 30) 	(57240 - 63720 @ 2160), (N/A, 40) 

##### interfaces ##### 

# interfaces(5) file used by ifup(8) and
ifdown(8) auto lo iface lo inet loopback 

##### iwconfig ##### 

wlan0     IEEE 802.11bgn  ESSID:"O9314"
 
          Mode:Managed  Frequency:2.462 GHz 
Access Point: <MAC address removed>   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B  
Fragment thr:off           Power Management:off           Link Quality=70/70  Signal level=-30
dBm  
          Rx invalid nwid:0  Rx invalid crypt:0 
Rx invalid frag:0           Tx excessive retries:0  Invalid misc:6
  Missed beacon:0 

##### route ##### 

Kernel IP routing table Destination     Gateway         Genmask        
Flags Metric Ref    Use Iface 0.0.0.0         192.168.1.1     0.0.0.0        
UG    0      0        0 eth0 192.168.1.0     0.0.0.0         255.255.255.0  
U     1      0        0 eth0 192.168.1.0     0.0.0.0         255.255.255.0  
U     9      0        0 wlan0 

##### resolv.conf ##### 

nameserver 127.0.1.1 search home 

##### nm-tool ##### 

NetworkManager Tool 

State: connected (global) 

- Device: wlan0  [O9314]
-------------------------------------------------------   Type:              802.11 WiFi   Driver:            rtl8192ce   State:             connected   Default:           no   HW Address:        <MAC address removed> 

  Capabilities:     Speed:           1 Mb/s 

  Wireless Properties     WEP Encryption:  yes     WPA Encryption:  yes     WPA2 Encryption: yes 

  Wireless Access Points (* = current AP)     Palmer:          Infra, <MAC address
removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2     P5RCQ:           Infra, <MAC address
removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WPA2     linksys:         Infra, <MAC address
removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2     *O9314:          Infra, <MAC address
removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 90 WEP 

  IPv4 Settings:     Address:         192.168.1.12     Prefix:          24 (255.255.255.0)     Gateway:         192.168.1.1 

    DNS:             192.168.1.1     DNS:             71.242.0.12 

- Device: eth0  [Wired connection 1]
-------------------------------------------   Type:              Wired   Driver:            r8169   State:             connected   Default:           yes   HW Address:        <MAC address removed> 

  Capabilities:     Carrier Detect:  yes     Speed:           100 Mb/s 

  Wired Properties     Carrier:         on 

  IPv4 Settings:     Address:         192.168.1.11     Prefix:          24 (255.255.255.0)     Gateway:         192.168.1.1 

    DNS:             192.168.1.1     DNS:             71.242.0.12 

##### NetworkManager.state ##### 

[main] NetworkingEnabled=true WirelessEnabled=true WWANEnabled=true WimaxEnabled=true 

##### NetworkManager.conf ##### 

[main] plugins=ifupdown,keyfile,ofono dns=dnsmasq 

[ifupdown] managed=false 

##### iwlist ##### 

wlan0     Scan completed :           Cell 01 - Address: <MAC address
removed>                     Channel:11                     Frequency:2.462 GHz (Channel
11)                     Quality=70/70  Signal
level=-30 dBm  
                    Encryption key:on                     ESSID:"O9314"                     Bit Rates:1 Mb/s; 2 Mb/s;
5.5 Mb/s; 6 Mb/s; 9 Mb/s                               11 Mb/s; 12 Mb/s;
18 Mb/s                     Bit Rates:24 Mb/s; 36 Mb/s;
48 Mb/s; 54 Mb/s                     Mode:Master                     Extra:tsf=00000010405d8a79                     Extra: Last beacon: 4ms ago                     IE: Unknown: 00054F39333134                     IE: Unknown:
010882848B0C12961824                     IE: Unknown: 03010B                     IE: Unknown:
0706555320010B1B                     IE: Unknown: 200100                     IE: Unknown: 2A0102                     IE: Unknown: 32043048606C                     IE: Unknown:
DD180050F2020101830003A4000027A4000042435E0062322F00           Cell 02 - Address: <MAC address
removed>                     Channel:4                     Frequency:2.427 GHz (Channel
4)                     Quality=70/70  Signal
level=-30 dBm  
                    Encryption key:on                     ESSID:"Palmer"                     Bit Rates:1 Mb/s; 2 Mb/s;
5.5 Mb/s; 11 Mb/s; 6 Mb/s                               9 Mb/s; 12 Mb/s;
18 Mb/s                     Bit Rates:24 Mb/s; 36 Mb/s;
48 Mb/s; 54 Mb/s                     Mode:Master                     Extra:tsf=0000000e3d6c3906                     Extra: Last beacon: 4ms ago                     IE: Unknown:
000650616C6D6572                     IE: Unknown:
010882848B968C129824                     IE: Unknown: 030104                     IE: Unknown:
0706555320010B1B                     IE: IEEE 802.11i/WPA2
Version 1                         Group Cipher : TKIP                         Pairwise Ciphers (2) :
CCMP TKIP                         Authentication Suites
(1) : PSK                     IE: WPA Version 1                         Group Cipher : TKIP                         Pairwise Ciphers (2) :
CCMP TKIP                         Authentication Suites
(1) : PSK                     IE: Unknown: 2A0100                     IE: Unknown: 3204B048606C                     IE: Unknown:
DD180050F2020101820003A4000027A4000042435E0062322F00                     IE: Unknown:
DD1E00904C334E111BFF00000000000000000000000000000000000000000000                     IE: Unknown:
2D1A4E111BFF00000000000000000000000000000000000000000000                     IE: Unknown:
DD1A00904C34040D0800000000000000000000000000000000000000                     IE: Unknown:
3D16040D0800000000000000000000000000000000000000                     IE: Unknown:
DD0900037F01010000FF7F                     IE: Unknown:
DD0A00037F04010002004000                     IE: Unknown:
DD8E0050F204104A0001101044000102103B0001031047001000000000000010000000C43DC78658DF1021000D4E6574676561722C20496E632E10230009574E523130303076321024000456324831104200046E6F6E651054000800060050F20400011011001E574E523130303076322D564328576972656C6573732041502D322E344729100800020086103C000103           Cell 03 - Address: <MAC address
removed>                     Channel:6                     Frequency:2.437 GHz (Channel
6)                     Quality=70/70  Signal
level=-30 dBm  
                    Encryption key:on                     ESSID:"P5RCQ"                     Bit Rates:1 Mb/s; 2 Mb/s;
5.5 Mb/s; 11 Mb/s; 6 Mb/s                               9 Mb/s; 12 Mb/s;
18 Mb/s                     Bit Rates:24 Mb/s; 36 Mb/s;
48 Mb/s; 54 Mb/s                     Mode:Master                     Extra:tsf=0000000403894b8c                     Extra: Last beacon: 4ms ago                     IE: Unknown: 00055035524351                     IE: Unknown:
010882848B960C121824                     IE: Unknown: 030106                     IE: Unknown: 200100                     IE: IEEE 802.11i/WPA2
Version 1                         Group Cipher : CCMP                         Pairwise Ciphers (1) :
CCMP                         Authentication Suites
(1) : PSK                     IE: Unknown: 2A0100                     IE: Unknown: 32043048606C                     IE: Unknown:
DD180050F2020101040003A4000027A4000042435E0062322F00                     IE: Unknown:
2D1A8C131BFFFF000000000000000000000000000000000000000000                     IE: Unknown:
3D1606080800000000000000000000000000000000000000                     IE: Unknown:
DD0900037F01010000FF7F                     IE: Unknown:
DD0A00037F04010000000000                     IE: Unknown:
0706555320010B1B 

##### iwlist channel ##### 

wlan0     11 channels in total; available
frequencies :           Channel 01 : 2.412 GHz           Channel 02 : 2.417 GHz           Channel 03 : 2.422 GHz           Channel 04 : 2.427 GHz           Channel 05 : 2.432 GHz           Channel 06 : 2.437 GHz           Channel 07 : 2.442 GHz           Channel 08 : 2.447 GHz           Channel 09 : 2.452 GHz           Channel 10 : 2.457 GHz           Channel 11 : 2.462 GHz           Current Frequency:2.462 GHz (Channel
11) 

##### lsmod ##### 

rtl8192ce              53550  0 
rtl_pci                26690  1 rtl8192ce rtlwifi                63475  2
rtl_pci,rtl8192ce rtl8192c_common        53172  1 rtl8192ce mac80211              626489  3
rtl_pci,rtlwifi,rtl8192ce cfg80211              484040  2 mac80211,rtlwifi 

##### modinfo ##### 

filename:      
/lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko firmware:       rtlwifi/rtl8192cfwU_B.bin firmware:       rtlwifi/rtl8192cfwU.bin firmware:       rtlwifi/rtl8192cfw.bin description:    Realtek 8192C/8188C 802.11n PCI
wireless license:        GPL author:         Larry
Finger	<Larry.Finger@lwfinger.net> author:         Realtek
WlanFAE	<wlanfae@realtek.com> author:        
lizhaoming	<chaoming_li@realsil.com.cn> srcversion:     BF8278DF19B67D7D6C6B8C5 alias:         
pci:v000010ECd00008176sv*sd*bc*sc*i* alias:         
pci:v000010ECd00008177sv*sd*bc*sc*i* alias:         
pci:v000010ECd00008178sv*sd*bc*sc*i* alias:         
pci:v000010ECd00008191sv*sd*bc*sc*i* depends:       
rtlwifi,rtl_pci,rtl8192c-common,mac80211 intree:         Y vermagic:       3.13.0-24-generic SMP mod_unload
modversions 
signer:         Magrathea: Glacier signing key sig_key:        <MAC address
removed>:47:4B:C5:C4:31:20:88:0C:1B:94:A5:39:F4:31 sig_hashalgo:   sha512 parm:           swenc:Set to 1 for software
crypto (default 0)  (bool) parm:           ips:Set to 0 to not use link
power save (default 1)  (bool) parm:           swlps:Set to 1 to use SW control
power save (default 0)  (bool) parm:           fwlps:Set to 1 to use FW control
power save (default 1)  (bool) parm:           debug:Set debug level (0-5)
(default 0) (int) 

filename:      
/lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko description:    PCI basic driver for rtlwifi license:        GPL author:         Larry
Finger	<Larry.FInger@lwfinger.net> author:         Realtek
WlanFAE	<wlanfae@realtek.com> author:        
lizhaoming	<chaoming_li@realsil.com.cn> srcversion:     B6B8AA929B5F982954A6DE1 depends:        mac80211,rtlwifi intree:         Y vermagic:       3.13.0-24-generic SMP mod_unload
modversions 
signer:         Magrathea: Glacier signing key sig_key:        <MAC address
removed>:47:4B:C5:C4:31:20:88:0C:1B:94:A5:39:F4:31 sig_hashalgo:   sha512 

filename:      
/lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko description:    Realtek 802.11n PCI wireless
core license:        GPL author:         Larry
Finger	<Larry.FInger@lwfinger.net> author:         Realtek
WlanFAE	<wlanfae@realtek.com> author:        
lizhaoming	<chaoming_li@realsil.com.cn> srcversion:     C21FC2F90947540319DE390 depends:        mac80211,cfg80211 intree:         Y vermagic:       3.13.0-24-generic SMP mod_unload
modversions 
signer:         Magrathea: Glacier signing key sig_key:        <MAC address
removed>:47:4B:C5:C4:31:20:88:0C:1B:94:A5:39:F4:31 sig_hashalgo:   sha512 

filename:      
/lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko description:    Realtek 8192C/8188C 802.11n PCI
wireless license:        GPL author:         Larry
Finger	<Larry.Finger@lwfinger.net> author:         Ziv
Huang	<ziv_huang@realtek.com> author:         Georgia		<georgia@realtek.com> author:         Realtek
WlanFAE	<wlanfae@realtek.com> author:        
lizhaoming	<chaoming_li@realsil.com.cn> srcversion:     32F826C623BC49F764F7974 depends:        
intree:         Y vermagic:       3.13.0-24-generic SMP mod_unload
modversions 
signer:         Magrathea: Glacier signing key sig_key:        <MAC address
removed>:47:4B:C5:C4:31:20:88:0C:1B:94:A5:39:F4:31 sig_hashalgo:   sha512 

##### modules ##### 

lp rtc 

##### blacklist ##### 

[/etc/modprobe.d/blacklist-ath_pci.conf] blacklist ath_pci 

[/etc/modprobe.d/blacklist.conf] blacklist evbug blacklist usbmouse blacklist usbkbd blacklist eepro100 blacklist de4x5 blacklist eth1394 blacklist snd_intel8x0m blacklist snd_aw2 blacklist i2c_i801 blacklist prism54 blacklist bcm43xx blacklist garmin_gps blacklist asus_acpi blacklist snd_pcsp blacklist pcspkr blacklist amd76x_edac 

[/etc/modprobe.d/fbdev-blacklist.conf] blacklist arkfb blacklist aty128fb blacklist atyfb blacklist radeonfb blacklist cirrusfb blacklist cyber2000fb blacklist gx1fb blacklist gxfb blacklist kyrofb blacklist matroxfb_base blacklist mb862xxfb blacklist neofb blacklist nvidiafb blacklist pm2fb blacklist pm3fb blacklist s3fb blacklist savagefb blacklist sisfb blacklist tdfxfb blacklist tridentfb blacklist viafb blacklist vt8623fb 

##### udev rules ##### 

# PCI device 0x10ec:0x8168 (r8169) SUBSYSTEM=="net", ACTION=="add",
DRIVERS=="?*", ATTR{address}=="<MAC address
removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1",
KERNEL=="eth*", NAME="eth0" 

# PCI device 0x10ec:0x8178 (rtl8192ce) SUBSYSTEM=="net", ACTION=="add",
DRIVERS=="?*", ATTR{address}=="<MAC address
removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1",
KERNEL=="wlan*", NAME="wlan0" 

##### dmesg ##### 

[    9.418692] rtl8192ce: Using firmware
rtlwifi/rtl8192cfw.bin [    9.901097] ieee80211 phy0: Selected rate
control algorithm 'rtl_rc' [    9.901228] rtlwifi: wireless switch is on [   18.932836] IPv6: ADDRCONF(NETDEV_UP): wlan0:
link is not ready [   18.933088] IPv6: ADDRCONF(NETDEV_UP): wlan0:
link is not ready [   19.829667] wlan0: authenticate with <MAC
address removed> [   19.846724] wlan0: send auth to <MAC
address removed> (try 1/3) [   19.848802] wlan0: authenticated [   19.848933] rtl8192ce 0000:06:00.0 wlan0:
disabling HT/VHT due to WEP/TKIP use [   19.850177] wlan0: associate with <MAC
address removed> (try 1/3) [   19.852551] wlan0: RX AssocResp from <MAC
address removed> (capab=0x431 status=0 aid=7) [   19.852711] wlan0: associated [   19.852718] IPv6: ADDRCONF(NETDEV_CHANGE):
wlan0: link becomes ready [   19.858203] Modules linked in: rfcomm bnep
bluetooth joydev arc4 snd_hda_codec_hdmi snd_hda_codec_realtek
snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_page_alloc
snd_seq_midi snd_seq_midi_event snd_rawmidi intel_rapl
x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm snd_seq
crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel
aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd snd_seq_device
rtl8192ce snd_timer rtl_pci rtlwifi psmouse rtl8192c_common serio_raw
mac80211 snd lpc_ich cfg80211 nouveau i915 soundcore mxm_wmi wmi ttm
drm_kms_helper drm mei_me mei i2c_algo_bit video mac_hid
intel_smartconnect parport_pc ppdev lp parport hid_generic usbhid hid
r8169 mii ahci libahci [   19.858263]  [<ffffffffa04c83ad>] ?
rtl_is_special_data+0x2d/0x110 [rtlwifi] [   19.861730] wlan0: Limiting TX power to 27
(27 - 0) dBm as advertised by <MAC address removed> 

########## wireless info END ############  

```

---

### Post by varunendra on 2014-04-21
It seems you opened the report file in Windows and copy-pasted its contents from there. If you have to do so, open the file in Ubuntu first, click "Save As" in the file menu, set "Line Ending" to be "Windows" compatible in the "Save As" dialogue box, and save it with a different name or different place. This will ensure that the line-breaks and related formatting is maintained while opening the file in Windows. As you can notice yourself, the formatting of the output results is pretty messed up in its current form. :)

Alternatively, you can simply attach the original report file itself in your post.

From whatever I could grasp in a quick observation, I would recommend you change the encryption type in the router to WPA2-PSK with AES (CCMP) instead of WEP which it is currently using. WEP security is almost no security (can be cracked within 10 minutes), plus it is not as efficient as AES. Remember - pure WPA2, not WPA/WPA2 mixed mode (and no TKIP!).

If that doesn't help, help me understanding the outputs better by re-posting the report in its original, cleaner format as asked above. :)

---

### Post by steve109 on 2014-04-22
ok this is the file opened in gedit. I hope thats what you wanted if not i believe i attached the file to this post, thanks again. [ATTACH]252374[/ATTACH]


```
- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.11
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1
    DNS:             71.242.0.12

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
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-22 dBm  
                    Encryption key:on
                    ESSID:"O9314"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001901b0842
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 00054F39333134
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-22 dBm  
                    Encryption key:on
                    ESSID:"linksys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000133b9b313ac
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 00076C696E6B737973
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD7E0050F204104A0001101044000102103B00010310470010138140001DD211B29FFFC67E816B4BFB102100074C696E6B73797310230006526F7574657210240007575254353447321042000C43535630314A3745323330351054000800060050F204000110110011576972656C6573732D4720526F75746572100800020084
                    IE: Unknown: DD090010180200F4000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### iwlist channel #####

wlan0     11 channels in total; available frequencies :
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
          Current Frequency:2.462 GHz (Channel 11)

##### lsmod #####

rtl8192ce              53550  0 
rtl_pci                26690  1 rtl8192ce
rtlwifi                63475  2 rtl_pci,rtl8192ce
rtl8192c_common        53172  1 rtl8192ce
mac80211              626489  3 rtl_pci,rtlwifi,rtl8192ce
cfg80211              484040  2 mac80211,rtlwifi

##### modinfo #####

filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfwU_B.bin
firmware:       rtlwifi/rtl8192cfwU.bin
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     BF8278DF19B67D7D6C6B8C5
alias:          pci:v000010ECd00008176sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008177sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008178sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008191sv*sd*bc*sc*i*
depends:        rtlwifi,rtl_pci,rtl8192c-common,mac80211
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:47:4B:C5:C4:31:20:88:0C:1B:94:A5:39:F4:31
sig_hashalgo:   sha512
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     B6B8AA929B5F982954A6DE1
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:47:4B:C5:C4:31:20:88:0C:1B:94:A5:39:F4:31
sig_hashalgo:   sha512

filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     C21FC2F90947540319DE390
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:47:4B:C5:C4:31:20:88:0C:1B:94:A5:39:F4:31
sig_hashalgo:   sha512

filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     32F826C623BC49F764F7974
depends:        
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:47:4B:C5:C4:31:20:88:0C:1B:94:A5:39:F4:31
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

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:0x8178 (rtl8192ce)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[   13.840536] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[   14.510129] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   14.510263] rtlwifi: wireless switch is on
[   22.910294] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.910589] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.859080] wlan0: authenticate with <MAC address removed>
[   23.876636] wlan0: send auth to <MAC address removed> (try 1/3)
[   23.879250] wlan0: authenticated
[   23.879444] rtl8192ce 0000:06:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[   23.880333] wlan0: associate with <MAC address removed> (try 1/3)
[   23.883360] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=4)
[   23.883521] wlan0: associated
[   23.883527] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   23.888257] Modules linked in: bnep rfcomm bluetooth joydev arc4 snd_hda_codec_hdmi snd_hda_codec_realtek intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel snd_seq_midi kvm snd_seq_midi_event crct10dif_pclmul crc32_pclmul ghash_clmulni_intel snd_rawmidi snd_seq aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd snd_hda_intel snd_hda_codec snd_seq_device snd_hwdep rtl8192ce rtl_pci rtlwifi rtl8192c_common mac80211 cfg80211 psmouse serio_raw snd_pcm lpc_ich nouveau i915 snd_page_alloc snd_timer mxm_wmi wmi mei_me mei ttm drm_kms_helper drm snd i2c_algo_bit soundcore video mac_hid intel_smartconnect parport_pc ppdev lp parport hid_generic usbhid hid ahci r8169 libahci mii
[   23.888345]  [<ffffffffa044c3ad>] ? rtl_is_special_data+0x2d/0x110 [rtlwifi]
[   23.981030] wlan0: Limiting TX power to 27 (27 - 0) dBm as advertised by <MAC address removed>

########## wireless info END ############
```

---

### Post by steve109 on 2014-04-22
Also I will definitely work on changing it from WEP. thanks for the advice

---

### Post by varunendra on 2014-04-22
Apart from changing the encryption type in the router, please also try some driver parameters (if required) in Ubuntu as suggested in this post : [http://ubuntuforums.org/showpost.php?p=12815912](http://ubuntuforums.org/showpost.php?p=12815912)

---

