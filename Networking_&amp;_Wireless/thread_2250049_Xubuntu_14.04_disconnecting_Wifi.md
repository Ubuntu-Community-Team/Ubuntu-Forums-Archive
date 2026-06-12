---
title: "Xubuntu 14.04 disconnecting Wifi"
date: 2014-10-26
forum: Networking &amp; Wireless
---

### Post by 2xenobii on 2014-10-26
Hi I have a problem with disengaging the Wifi on my Xubuntu 14.04.Wi-Fi  after switching on computer is working but after about 5 minutes  disconnects.The network card is a TP-LINK TL-WN321G on Windows  everything running on the RT2870 driver
lshw -C network
```
sudo lshw -C network
[sudo] password for kaczka2: 
  *-network               
       description: Wireless interface
       physical id: 1
       bus info: usb@1:4.2
       logical name: wlan0
       serial: d8:5d:4c:99:ff:a7
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb  driverversion=3.13.0-37-generic firmware=0.29 ip=192.168.0.2 link=yes  multicast=yes wireless=IEEE 802.11bg
```
dmesg | egrep -i 'rt2'
```
dmesg | egrep -i 'rt2'
[   16.467404] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[   16.495530] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 0006 detected
[   16.505132] usbcore: registered new interface driver rt2800usb
[   18.943054] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[   18.980365] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[   22.163222] rt2800usb 1-4.2:1.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[   22.872175] rt2800usb 1-4.2:1.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 1166.321111] rt2800usb 1-4.2:1.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 1529.159335] rt2800usb 1-4.2:1.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 1570.303506] rt2800usb 1-4.2:1.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 1601.088119] rt2800usb 1-4.2:1.0 wlan0: disabling HT/VHT due to WEP/TKIP use
```
dmesg | egrep -i 'firmware'
```
dmesg | egrep -i 'firmware'
[    0.102316] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-1f] only partially covers this bridge
[   18.943054] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[   18.980365] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29

```

---

### Post by praseodym on 2014-10-26
What kind of computer is it? Please show
```

lsusb
lsmod
iwconfig
rfkill list
iwlist chan
sudo iwlist scan
```

---

### Post by 2xenobii on 2014-10-26
lsusb
```
lsusb
Bus 001 Device 004: ID 148f:2070 Ralink Technology, Corp. RT2070 Wireless Adapter
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
lsmod
```
kaczka2@kaczka2:~$ lsmod
Module                  Size  Used by
bnep                   18895  2 
rfcomm                 53664  0 
bluetooth             342208  10 bnep,rfcomm
snd_hda_codec_hdmi     45440  1 
binfmt_misc            13140  1 
arc4                   12536  2 
snd_hda_codec_realtek    55163  1 
rt2800usb              26581  0 
rt2x00usb              20041  1 rt2800usb
rt2800lib              83150  1 rt2800usb
rt2x00lib              48886  3 rt2x00usb,rt2800lib,rt2800usb
mac80211              546051  3 rt2x00lib,rt2x00usb,rt2800lib
cfg80211              409394  2 mac80211,rt2x00lib
crc_ccitt              12627  1 rt2800lib
snd_hda_intel          42730  8 
snd_hda_codec         164067  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                85501  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25135  1 snd_seq_midi
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
fglrx                7531632  89 
serio_raw              13230  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28584  2 snd_pcm,snd_seq
snd                    60939  27 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
asus_atk0110           18201  0 
soundcore              12600  1 snd
i2c_nforce2            13037  0 
parport_pc             31981  1 
ppdev                  17391  0 
mac_hid                13037  0 
hwmon_vid              12687  0 
coretemp               13195  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
uvesafb                27862  0 
hid_generic            12492  0 
usbhid                 47070  0 
hid                    87604  2 hid_generic,usbhid
pata_acpi              12886  0 
ahci                   25579  0 
libahci                27214  1 ahci
pata_amd               13761  2 

```
iwconfig
```
kaczka2@kaczka2:~$ iwconfig
wlan0     IEEE 802.11bg  ESSID:"02AEE0"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: 34:BA:9A:02:AE:E0   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=53/70  Signal level=-57 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:15   Missed beacon:0

lo        no wireless extensions.

```
rfkill list
```
kaczka2@kaczka2:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```
iwlist chan
```
kaczka2@kaczka2:~$ iwlist chan
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
          Current Frequency=2.417 GHz (Channel 2)

lo        no frequency information.

```
sudo iwlist scan
```
kaczka2@kaczka2:~$ sudo iwlist scan
[sudo] password for kaczka2: 
wlan0     Scan completed :
          Cell 01 - Address: 34:BA:9A:02:AE:E0
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:on
                    ESSID:"02AEE0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003932b1bc23
                    Extra: Last beacon: 28ms ago
                    IE: Unknown: 0006303241454530
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030102
                    IE: Unknown: 2A0100
                    IE: Unknown: 32048C98B060
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05020003127A
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706465220010D10
          Cell 02 - Address: 34:BA:9A:05:07:30
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"221 B Baker Street"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000124b86bb35
                    Extra: Last beacon: 28ms ago
                    IE: Unknown: 001232323120422042616B657220537472656574
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601050000000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000005127A
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706465220010D10

lo        Interface doesn't support scanning.

```

---

### Post by praseodym on 2014-10-26
Deactivate the power management:
```

sudo iwconfig wlan0 power off
```
I recommend changing the encryption mode to WPA2-AES (CCMP) instead of WPA (TKIP) in your router, check the manual

---

### Post by 2xenobii on 2014-10-26
When re-started the computer power management is enabled again what to do so that it will automatically turn off?.I read that WPA2 reduces the quality and potency of the signal

---

### Post by praseodym on 2014-10-26
WPA is based on WEP, so its unsecure, WPA2 is more secure.

Add the line
```

iwconfig wlan0 power off
```
before "exit 0" in the file /etc/rc.local.

---

