---
title: "ASUS PCE-N15 Adapter"
date: 2015-12-26
forum: Networking &amp; Wireless
---

### Post by michael341 on 2015-12-26
Hi everyone!
I'm really new to linux and I'm really loving it. I used openSUSE for about a week and am 3 days into giving ubuntu a whirl. Here's my question. I have a desktop with an ASUS PCE-N15 wireless adapter card. It has been natively recognized by ubuntu and I'm able to connect to my home network (I assume with just the generic drivers that come with ubuntu). The problem is that it seems to drop signal more than it used to with Windows. All of a sudden I just no longer have access to the internet at all. I re-boot my computer and it works just fine again. ASUS has some linux drivers available on their website but I'm not sure if it would be helpful at all to install them. I was going to give it a shot but the readme got weird and started asking me to compile things in a directory that didn't exist. I guess the root (hehe) of my question is whether or not I should bother installing the ASUS linux drivers since it does work, somewhat, without them. Or maybe if you all have other tips on how to just re-set my network connection real quick without a full re-boot.
Thanks and merry christmas!!

---

### Post by praseodym on 2015-12-26
Please show the terminal outputs of these commands:
```

lsusb
lsmod
iwconfig
```

---

### Post by michael341 on 2015-12-26
root@michael-System-Product-Name:~# lsusb
Bus 006 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6broot@michael-System-Product-Name:~# lsusb
Bus 006 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 1532:0015 Razer USA, Ltd 
Bus 001 Device 003: ID 1532:010d Razer USA, Ltd 
Bus 001 Device 002: ID 046d:0a15 Logitech, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
:0003 Linux Foundation 3.0 root hub

root@michael-System-Product-Name:~# lsmod
Module                  Size  Used by
ctr                    16384  1 
ccm                    20480  1 
rfcomm                 69632  0 
bnep                   20480  2 
bluetooth             491520  10 bnep,rfcomm
binfmt_misc            20480  1 
nls_iso8859_1          16384  1 
nvidia               8646656  70 
snd_hda_codec_hdmi     53248  4 
snd_usb_audio         180224  2 
joydev                 20480  0 
snd_usbmidi_lib        32768  1 snd_usb_audio
eeepc_wmi              16384  0 
asus_wmi               24576  1 eeepc_wmi
sparse_keymap          16384  1 asus_wmi
mxm_wmi                16384  0 
intel_rapl             20480  0 
iosf_mbi               16384  1 intel_rapl
x86_pkg_temp_thermal    16384  0 
intel_powerclamp       20480  0 
coretemp               16384  0 
kvm                   479232  0 
snd_hda_codec_realtek    81920  1 
snd_hda_codec_generic    69632  1 snd_hda_codec_realtek
crct10dif_pclmul       16384  0 
crc32_pclmul           16384  0 
arc4                   16384  2 
snd_hda_intel          36864  6 snd_hda_codec_hdmi
snd_hda_controller     32768  1 snd_hda_intel
aesni_intel           172032  2 
snd_hda_codec         143360  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
rtl8192ce              57344  0 
snd_hwdep              20480  2 snd_usb_audio,snd_hda_codec
aes_x86_64             20480  1 aesni_intel
rtl_pci                28672  1 rtl8192ce
snd_seq_midi           16384  0 
lrw                    16384  1 aesni_intel
snd_seq_midi_event     16384  1 snd_seq_midi
rtl8192c_common        53248  1 rtl8192ce
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
rtlwifi                73728  3 rtl_pci,rtl8192c_common,rtl8192ce
ablk_helper            16384  1 aesni_intel
cryptd                 20480  2 aesni_intel,ablk_helper
mac80211              708608  3 rtl_pci,rtlwifi,rtl8192ce
serio_raw              16384  0 
lpc_ich                24576  0 
snd_rawmidi            32768  2 snd_usbmidi_lib,snd_seq_midi
snd_pcm               106496  5 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
cfg80211              524288  2 mac80211,rtlwifi
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
snd                    86016  27 snd_hda_codec_realtek,snd_usb_audio,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device
mei_me                 20480  0 
drm                   344064  3 nvidia
mei                    90112  1 mei_me
soundcore              16384  2 snd,snd_hda_codec
shpchp                 40960  0 
video                  20480  1 asus_wmi
wmi                    20480  2 mxm_wmi,asus_wmi
mac_hid                16384  0 
parport_pc             32768  0 
ppdev                  20480  0 
lp                     20480  0 
parport                45056  3 lp,ppdev,parport_pc
hid_generic            16384  0 
usbhid                 53248  0 
hid                   110592  2 hid_generic,usbhid
e1000e                237568  0 
psmouse               114688  0 
ahci                   36864  3 
ptp                    20480  1 e1000e
libahci                32768  1 ahci
pps_core               20480  1 ptp
root@michael-System-Product-Name:~# iwconfig
eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"HOME-AC07"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: CC:35:40:C9:AC:07   
          Bit Rate=144.4 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=62/70  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:46717   Missed beacon:0

lo        no wireless extensions.



Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 1532:0015 Razer USA, Ltd 
Bus 001 Device 003: ID 1532:010d Razer USA, Ltd 
Bus 001 Device 002: ID 046d:0a15 Logitech, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by praseodym on 2015-12-26
Check these module parameters:
```

echo "options rtl8192ce swlps=0 ips=0" | sudo tee /etc/modprobe.d/rtl8192ce.conf
sudo modprobe -rfv rtl8192ce
sudo modprobe -v rtl8192ce
```

---

### Post by michael341 on 2015-12-26
michael@michael-System-Product-Name:~$ echo "options rtl8192ce swlps=0 ips=0" | sudo tee /etc/modprobe.d/rtl8192ce.conf
[sudo] password for michael:
options rtl8192ce swlps=0 ips=0

michael@michael-System-Product-Name:~$ sudo modprobe -rfv rtl8192ce
rmmod rtl8192ce
rmmod rtl8192c_common
rmmod rtl_pci
rmmod rtlwifi
rmmod mac80211
rmmod cfg80211

michael@michael-System-Product-Name:~$ sudo modprobe -v rtl8192ce
insmod /lib/modules/3.19.0-42-generic/kernel/net/wireless/cfg80211.ko
insmod /lib/modules/3.19.0-42-generic/kernel/net/mac80211/mac80211.ko
insmod /lib/modules/3.19.0-42-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
insmod /lib/modules/3.19.0-42-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
insmod /lib/modules/3.19.0-42-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
insmod /lib/modules/3.19.0-42-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko swlps=0 ips=0

Just something of note, it seems when I ran these commands it kicked me off of the wifi and wouldn't let me reconnect without a reboot. Not sure what that means.

---

### Post by praseodym on 2015-12-26
Please show now
```

lspci -nnk | grep -iA2 net
iwlist chan
sudo iwlist scan
dmesg | egrep 'country|rtl|wlan|reason'
```

---

### Post by michael341 on 2015-12-27
michael@michael-System-Product-Name:~$ lspci -nnk | grep -iA2 net
00:19.0 Ethernet controller [0200]: Intel Corporation 82579V Gigabit Network Connection [8086:1503] (rev 04)
    Subsystem: ASUSTeK Computer Inc. P8P67 Deluxe Motherboard [1043:849c]
    Kernel driver in use: e1000e
--
04:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192CE PCIe Wireless Network Adapter [10ec:8178] (rev 01)
    Subsystem: ASUSTeK Computer Inc. Device [1043:85e3]
    Kernel driver in use: rtl8192ce
michael@michael-System-Product-Name:~$ iwlist chan
eth0      no frequency information.

wlan0     13 channels in total; available frequencies :
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
          Current Frequency:2.412 GHz (Channel 1)

lo        no frequency information.

michael@michael-System-Product-Name:~$ sudo iwlist scan
[sudo] password for michael: 
eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: CC:35:40:C9:AC:07
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"HOME-AC07"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000797d2f4747
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 0009484F4D452D41433037
                    IE: Unknown: 010882848B9624B0486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32048C129860
                    IE: Unknown: 2D1ABD181BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080400000000000000000000000000000000000000
                    IE: Unknown: DD8C0050F204104A0001101044000102103B00010310470010B9F3D7AAFC1559FFB6A635DBF63A2BC61021000B546563686E69636F6C6F721023000B546563686E69636F6C6F721024000631323334353610420007303030303030311054000800060050F20400011011000D546563686E69636F6C6F724150100800022008103C0001011049000600372A000120
                    IE: Unknown: DD090010180204001C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
          Cell 02 - Address: CE:35:40:C9:AC:08
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000797d676a9c
                    Extra: Last beacon: 136ms ago
                    IE: Unknown: 000C000000000000000000000000
                    IE: Unknown: 010882848B9624B0486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32048C129860
                    IE: Unknown: 2D1ABD181BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080400000000000000000000000000000000000000
                    IE: Unknown: DD090010180200001C0000
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
          Cell 03 - Address: CE:35:40:C9:AC:09
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000797d2f9326
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 000B7866696E69747977696669
                    IE: Unknown: 010882848B9624B0486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32048C129860
                    IE: Unknown: 2D1ABD181BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080400000000000000000000000000000000000000
                    IE: Unknown: DD090010180200001C0000
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
          Cell 04 - Address: 54:BE:F7:D2:A8:78
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"strand1-2.4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000796ded023a
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 000B737472616E64312D322E34
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 3204B048606C
                    IE: Unknown: 2D1AAD011BFFFFFF0000000000000000000100000000000000000000
                    IE: Unknown: 3D1606000500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080100000000000040
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD8D0050F204104A0001101044000102103B0001031047001069FFB5D14B5E5DA898BE8EF17404816510210013436973636F2053797374656D732C20496E632E10230007445043333933391024000744504333393339104200093030303030303030311054000800060050F2040001101100074450433339333910080002210C103C0001011049000600372A000120
          Cell 05 - Address: 54:BE:F7:D2:A8:7A
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000796deddab3
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 000B7866696E69747977696669
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 3204B048606C
                    IE: Unknown: 2D1AAD011BFFFFFF0000000000000000000100000000000000000000
                    IE: Unknown: 3D1606000500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080100000000000040
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 06 - Address: 54:BE:F7:D2:A8:79
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000796dee7180
                    Extra: Last beacon: 2428ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 3204B048606C
                    IE: Unknown: 2D1AAD011BFFFFFF0000000000000000000100000000000000000000
                    IE: Unknown: 3D1606000500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080100000000000040
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

lo        Interface doesn't support scanning.

michael@michael-System-Product-Name:~$ dmesg | egrep 'country|rtl|wlan|reason'
[   10.755318] rtl8192ce 0000:04:00.0: enabling device (0100 -> 0103)
[   10.766111] rtl8192ce: rtl8192ce: Power Save off (module option)
[   10.766200] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[   10.768961] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   10.769137] rtlwifi: rtlwifi: wireless switch is on
[   14.778769] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.541719] wlan0: authenticate with cc:35:40:c9:ac:07
[   16.561707] wlan0: send auth to cc:35:40:c9:ac:07 (try 1/3)
[   16.563359] wlan0: authenticated
[   16.565491] wlan0: associate with cc:35:40:c9:ac:07 (try 1/3)
[   16.568776] wlan0: RX AssocResp from cc:35:40:c9:ac:07 (capab=0x411 status=0 aid=4)
[   16.568923] wlan0: associated
[   16.568930] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   16.607598] wlan0: deauthenticating from cc:35:40:c9:ac:07 by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
[   16.617802] wlan0: authenticate with cc:35:40:c9:ac:07
[   16.627864] wlan0: send auth to cc:35:40:c9:ac:07 (try 1/3)
[   16.629603] wlan0: authenticated
[   16.633399] wlan0: associate with cc:35:40:c9:ac:07 (try 1/3)
[   16.636688] wlan0: RX AssocResp from cc:35:40:c9:ac:07 (capab=0x411 status=0 aid=4)
[   16.636848] wlan0: associated
[  696.670794] wlan0: deauthenticating from cc:35:40:c9:ac:07 by local choice (Reason: 3=DEAUTH_LEAVING)
[  699.176813] rtlwifi: rtlwifi: wireless switch is on
[  706.696653] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  708.397295] wlan0: authenticate with cc:35:40:c9:ac:07
[  708.416791] wlan0: send auth to cc:35:40:c9:ac:07 (try 1/3)
[  708.420371] wlan0: authenticated
[  708.424514] wlan0: associate with cc:35:40:c9:ac:07 (try 1/3)
[  708.431616] wlan0: RX AssocResp from cc:35:40:c9:ac:07 (capab=0x411 status=0 aid=5)
[  708.431784] wlan0: associated
[  708.431795] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  708.474866] wlan0: deauthenticating from cc:35:40:c9:ac:07 by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
[  708.485152] wlan0: authenticate with cc:35:40:c9:ac:07
[  708.495257] wlan0: send auth to cc:35:40:c9:ac:07 (try 1/3)
[  708.496985] wlan0: authenticated
[  708.500463] wlan0: associate with cc:35:40:c9:ac:07 (try 1/3)
[  708.503760] wlan0: RX AssocResp from cc:35:40:c9:ac:07 (capab=0x411 status=0 aid=5)
[  708.503936] wlan0: associated
[ 1638.243589] wlan0: deauthenticated from cc:35:40:c9:ac:07 (Reason: 7=CLASS3_FRAME_FROM_NONASSOC_STA)
[ 1639.197433] wlan0: authenticate with cc:35:40:c9:ac:07
[ 1639.217147] wlan0: send auth to cc:35:40:c9:ac:07 (try 1/3)
[ 1639.218818] wlan0: authenticated
[ 1639.220869] wlan0: associate with cc:35:40:c9:ac:07 (try 1/3)
[ 1639.224281] wlan0: RX AssocResp from cc:35:40:c9:ac:07 (capab=0x411 status=0 aid=5)
[ 1639.224472] wlan0: associated
[ 2597.099854] wlan0: deauthenticated from cc:35:40:c9:ac:07 (Reason: 7=CLASS3_FRAME_FROM_NONASSOC_STA)
[ 2597.135468] wlan0: authenticate with cc:35:40:c9:ac:07
[ 2597.145582] wlan0: send auth to cc:35:40:c9:ac:07 (try 1/3)
[ 2597.148113] wlan0: authenticated
[ 2597.151068] wlan0: associate with cc:35:40:c9:ac:07 (try 1/3)
[ 2597.154364] wlan0: RX AssocResp from cc:35:40:c9:ac:07 (capab=0x411 status=0 aid=5)
[ 2597.154553] wlan0: associated
[ 2851.774114] wlan0: deauthenticated from cc:35:40:c9:ac:07 (Reason: 7=CLASS3_FRAME_FROM_NONASSOC_STA)
[ 2851.809460] wlan0: authenticate with cc:35:40:c9:ac:07
[ 2851.819561] wlan0: send auth to cc:35:40:c9:ac:07 (try 1/3)
[ 2851.823496] wlan0: authenticated
[ 2851.825031] wlan0: associate with cc:35:40:c9:ac:07 (try 1/3)
[ 2851.828521] wlan0: RX AssocResp from cc:35:40:c9:ac:07 (capab=0x411 status=0 aid=5)
[ 2851.828722] wlan0: associated
[ 3570.891913] wlan0: deauthenticated from cc:35:40:c9:ac:07 (Reason: 7=CLASS3_FRAME_FROM_NONASSOC_STA)
[ 3570.925373] wlan0: authenticate with cc:35:40:c9:ac:07
[ 3570.935478] wlan0: send auth to cc:35:40:c9:ac:07 (try 1/3)
[ 3570.938739] wlan0: authenticated
[ 3570.940883] wlan0: associate with cc:35:40:c9:ac:07 (try 1/3)
[ 3570.944129] wlan0: RX AssocResp from cc:35:40:c9:ac:07 (capab=0x411 status=0 aid=5)
[ 3570.944324] wlan0: associated
[ 4529.844625] wlan0: deauthenticated from cc:35:40:c9:ac:07 (Reason: 7=CLASS3_FRAME_FROM_NONASSOC_STA)
[ 4529.873021] wlan0: authenticate with cc:35:40:c9:ac:07
[ 4529.883147] wlan0: send auth to cc:35:40:c9:ac:07 (try 1/3)
[ 4529.886125] wlan0: authenticated
[ 4529.888532] wlan0: associate with cc:35:40:c9:ac:07 (try 1/3)
[ 4529.891816] wlan0: RX AssocResp from cc:35:40:c9:ac:07 (capab=0x411 status=0 aid=5)
[ 4529.892014] wlan0: associated
[ 5234.030641] wlan0: deauthenticated from cc:35:40:c9:ac:07 (Reason: 7=CLASS3_FRAME_FROM_NONASSOC_STA)
[ 5234.062770] wlan0: authenticate with cc:35:40:c9:ac:07
[ 5234.072886] wlan0: send auth to cc:35:40:c9:ac:07 (try 1/3)
[ 5234.075070] wlan0: authenticated
[ 5234.078321] wlan0: associate with cc:35:40:c9:ac:07 (try 1/3)
[ 5234.081632] wlan0: RX AssocResp from cc:35:40:c9:ac:07 (capab=0x411 status=0 aid=5)
[ 5234.081804] wlan0: associated
[ 6687.297153] wlan0: deauthenticated from cc:35:40:c9:ac:07 (Reason: 7=CLASS3_FRAME_FROM_NONASSOC_STA)
[ 6687.328400] wlan0: authenticate with cc:35:40:c9:ac:07
[ 6687.338497] wlan0: send auth to cc:35:40:c9:ac:07 (try 1/3)
[ 6687.340536] wlan0: authenticated
[ 6687.343950] wlan0: associate with cc:35:40:c9:ac:07 (try 1/3)
[ 6687.347234] wlan0: RX AssocResp from cc:35:40:c9:ac:07 (capab=0x411 status=0 aid=5)
[ 6687.347407] wlan0: associated
[ 8604.990995] wlan0: deauthenticated from cc:35:40:c9:ac:07 (Reason: 7=CLASS3_FRAME_FROM_NONASSOC_STA)
[ 8605.023928] wlan0: authenticate with cc:35:40:c9:ac:07
[ 8605.034029] wlan0: send auth to cc:35:40:c9:ac:07 (try 1/3)
[ 8605.036407] wlan0: authenticated
[ 8605.039498] wlan0: associate with cc:35:40:c9:ac:07 (try 1/3)
[ 8605.042778] wlan0: RX AssocResp from cc:35:40:c9:ac:07 (capab=0x411 status=0 aid=2)
[ 8605.042971] wlan0: associated
[ 8714.862042] wlan0: deauthenticated from cc:35:40:c9:ac:07 (Reason: 7=CLASS3_FRAME_FROM_NONASSOC_STA)
[ 8714.903933] wlan0: authenticate with cc:35:40:c9:ac:07
[ 8714.914028] wlan0: send auth to cc:35:40:c9:ac:07 (try 1/3)
[ 8714.916473] wlan0: authenticated
[ 8714.919457] wlan0: associate with cc:35:40:c9:ac:07 (try 1/3)
[ 8714.922959] wlan0: RX AssocResp from cc:35:40:c9:ac:07 (capab=0x411 status=0 aid=2)
[ 8714.923147] wlan0: associated
[ 8834.729647] wlan0: deauthenticated from cc:35:40:c9:ac:07 (Reason: 7=CLASS3_FRAME_FROM_NONASSOC_STA)
[ 8834.759847] wlan0: authenticate with cc:35:40:c9:ac:07
[ 8834.769946] wlan0: send auth to cc:35:40:c9:ac:07 (try 1/3)
[ 8834.772685] wlan0: authenticated
[ 8834.775427] wlan0: associate with cc:35:40:c9:ac:07 (try 1/3)
[ 8834.778692] wlan0: RX AssocResp from cc:35:40:c9:ac:07 (capab=0x411 status=0 aid=2)
[ 8834.778871] wlan0: associated
[ 9548.889124] wlan0: deauthenticated from cc:35:40:c9:ac:07 (Reason: 7=CLASS3_FRAME_FROM_NONASSOC_STA)
[ 9548.917687] wlan0: authenticate with cc:35:40:c9:ac:07
[ 9548.927791] wlan0: send auth to cc:35:40:c9:ac:07 (try 1/3)
[ 9548.933140] wlan0: authenticated
[ 9548.937230] wlan0: associate with cc:35:40:c9:ac:07 (try 1/3)
[ 9548.940814] wlan0: RX AssocResp from cc:35:40:c9:ac:07 (capab=0x411 status=0 aid=2)
[ 9548.940999] wlan0: associated
[ 9798.595342] wlan0: deauthenticated from cc:35:40:c9:ac:07 (Reason: 7=CLASS3_FRAME_FROM_NONASSOC_STA)
[ 9798.625573] wlan0: authenticate with cc:35:40:c9:ac:07
[ 9798.635680] wlan0: send auth to cc:35:40:c9:ac:07 (try 1/3)
[ 9798.637962] wlan0: authenticated
[ 9798.641168] wlan0: associate with cc:35:40:c9:ac:07 (try 1/3)
[ 9798.646395] wlan0: RX AssocResp from cc:35:40:c9:ac:07 (capab=0x411 status=0 aid=2)
[ 9798.646568] wlan0: associated
[10514.796672] wlan0: deauthenticated from cc:35:40:c9:ac:07 (Reason: 7=CLASS3_FRAME_FROM_NONASSOC_STA)
[10514.836932] wlan0: authenticate with cc:35:40:c9:ac:07
[10514.847047] wlan0: send auth to cc:35:40:c9:ac:07 (try 1/3)
[10514.849253] wlan0: authenticated
[10514.852503] wlan0: associate with cc:35:40:c9:ac:07 (try 1/3)
[10514.855756] wlan0: RX AssocResp from cc:35:40:c9:ac:07 (capab=0x411 status=0 aid=2)
[10514.855928] wlan0: associated
[13639.098458] wlan0: deauthenticated from cc:35:40:c9:ac:07 (Reason: 7=CLASS3_FRAME_FROM_NONASSOC_STA)
[13639.134538] wlan0: authenticate with cc:35:40:c9:ac:07
[13639.144640] wlan0: send auth to cc:35:40:c9:ac:07 (try 1/3)
[13639.147655] wlan0: authenticated
[13639.150098] wlan0: associate with cc:35:40:c9:ac:07 (try 1/3)
[13639.153349] wlan0: RX AssocResp from cc:35:40:c9:ac:07 (capab=0x411 status=0 aid=2)
[13639.153519] wlan0: associated
[16505.743814] wlan0: deauthenticated from cc:35:40:c9:ac:07 (Reason: 7=CLASS3_FRAME_FROM_NONASSOC_STA)
[16505.777728] wlan0: authenticate with cc:35:40:c9:ac:07
[16505.787827] wlan0: send auth to cc:35:40:c9:ac:07 (try 1/3)
[16505.790642] wlan0: authenticated
[16505.793304] wlan0: associate with cc:35:40:c9:ac:07 (try 1/3)
[16505.797952] wlan0: RX AssocResp from cc:35:40:c9:ac:07 (capab=0x411 status=0 aid=2)
[16505.798137] wlan0: associated
[16620.609191] wlan0: deauthenticated from cc:35:40:c9:ac:07 (Reason: 7=CLASS3_FRAME_FROM_NONASSOC_STA)
[16620.639701] wlan0: authenticate with cc:35:40:c9:ac:07
[16620.649798] wlan0: send auth to cc:35:40:c9:ac:07 (try 1/3)
[16620.652525] wlan0: authenticated
[16620.655278] wlan0: associate with cc:35:40:c9:ac:07 (try 1/3)
[16620.658681] wlan0: RX AssocResp from cc:35:40:c9:ac:07 (capab=0x411 status=0 aid=2)
[16620.658860] wlan0: associated
[17699.092683] wlan0: deauthenticated from cc:35:40:c9:ac:07 (Reason: 7=CLASS3_FRAME_FROM_NONASSOC_STA)
[17699.123725] wlan0: authenticate with cc:35:40:c9:ac:07
[17699.133825] wlan0: send auth to cc:35:40:c9:ac:07 (try 1/3)
[17699.135910] wlan0: authenticated
[17699.139282] wlan0: associate with cc:35:40:c9:ac:07 (try 1/3)
[17699.142565] wlan0: RX AssocResp from cc:35:40:c9:ac:07 (capab=0x411 status=0 aid=2)
[17699.142770] wlan0: associated
[19627.092783] wlan0: deauthenticated from cc:35:40:c9:ac:07 (Reason: 7=CLASS3_FRAME_FROM_NONASSOC_STA)
[19627.126916] wlan0: authenticate with cc:35:40:c9:ac:07
[19627.137022] wlan0: send auth to cc:35:40:c9:ac:07 (try 1/3)
[19627.139115] wlan0: authenticated
[19627.142436] wlan0: associate with cc:35:40:c9:ac:07 (try 1/3)
[19627.145736] wlan0: RX AssocResp from cc:35:40:c9:ac:07 (capab=0x411 status=0 aid=2)
[19627.145909] wlan0: associated
[19736.962751] wlan0: deauthenticated from cc:35:40:c9:ac:07 (Reason: 7=CLASS3_FRAME_FROM_NONASSOC_STA)
[19737.002879] wlan0: authenticate with cc:35:40:c9:ac:07
[19737.012990] wlan0: send auth to cc:35:40:c9:ac:07 (try 1/3)
[19737.015115] wlan0: authenticated
[19737.018400] wlan0: associate with cc:35:40:c9:ac:07 (try 1/3)
[19737.021699] wlan0: RX AssocResp from cc:35:40:c9:ac:07 (capab=0x411 status=0 aid=2)
[19737.021875] wlan0: associated
[22733.503586] wlan0: deauthenticated from cc:35:40:c9:ac:07 (Reason: 7=CLASS3_FRAME_FROM_NONASSOC_STA)
[22733.533986] wlan0: authenticate with cc:35:40:c9:ac:07
[22733.544082] wlan0: send auth to cc:35:40:c9:ac:07 (try 1/3)
[22733.546218] wlan0: authenticated
[22733.549524] wlan0: associate with cc:35:40:c9:ac:07 (try 1/3)
[22733.552844] wlan0: RX AssocResp from cc:35:40:c9:ac:07 (capab=0x411 status=0 aid=2)
[22733.553024] wlan0: associated

---

### Post by praseodym on 2015-12-28
The "Scan" shows both TKIP and CCMP for your network. Try changing to pure CCMP mode in your router settings.

If its not enough then try Wicd instead of the network-manager:

```
wget http://www.elektronenblitz63.de/download/wicd-1.6.x_addon01441.tar.gz
sudo apt-get install --reinstall wicd
tar xvf wicd-1.6.x_addon01441.tar.gz
cd wicd-1.6.x_addon01441
sudo ./install_wicd_addon
sudo service network-manager stop
sudo killall wpa_supplicant
sudo service wicd restart
```
Deactivate NM from the starting programmes or uninstall it.

---

