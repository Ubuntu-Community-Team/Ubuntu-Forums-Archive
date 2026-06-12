---
title: "Network-Man asking for password again and again"
date: 2013-12-29
forum: Networking &amp; Wireless
---

### Post by snipier on 2013-12-29
Hi all, 

I'm facing an issue with my HP Pavilion dv6. 
The wifi is working, but sometimes when I switch on my laptop, it is unable to connect : the network manager is asking for the key WEP again and again, without managing to connect. 
The only way I found to circumvent this problem is to restart my computer, several times sometimes ! 

For your information, the code below has no effect : 
```
sudo service network-manager restart
```

Another thing maybe linked to my issue : when I'm connected to my wifi network, my other devices aren't able to connect ! Weird (and really annoying)...

So if anyone has any clues...

Many thanks ! 

```
cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.3 LTS"
```

```
uname -mr
3.2.0-45-generic-pae i686
```

```
lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 5986:02ac Acer, Inc 
Bus 002 Device 003: ID 125f:312a A-DATA Technology Co., Ltd. Superior S102
Bus 002 Device 004: ID 0a5c:21b4 Broadcom Corp. BCM2070 Bluetooth 2.1 + EDR
```

```
lspci
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
0d:00.0 Network controller: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter (rev 01)

```

```
iwconfig
eth1      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off       

```

```
ifconfig
eth1      Link encap:Ethernet  HWaddr cc:52:af:8f:80:bc  
          adr inet6: fe80::ce52:afff:fe8f:80bc/64 Scope:Lien
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:3
          TX packets:0 errors:22 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)
          Interruption:17 

```

```
lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55605  1 vfat
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
pci_stub               12550  1 
vboxpci                22911  0 
vboxnetadp             25616  0 
vboxnetflt             27240  0 
snd_hda_codec_hdmi     31775  1 
snd_hda_codec_idt      60251  1 
vboxdrv               252228  3 vboxpci,vboxnetadp,vboxnetflt
joydev                 17393  0 
parport_pc             32114  0 
ppdev                  12849  0 
rfcomm                 38139  12 
bnep                   17830  2 
binfmt_misc            17292  1 
wmi                    18744  1 hp_wmi
btusb                  17948  3 
bluetooth             158479  25 rfcomm,bnep,btusb
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
snd_hda_intel          32719  3 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
hp_accel               25728  0 
lis3lv02d              19268  1 hp_accel
lib80211_crypt_tkip    17275  0 
input_polldev          13648  1 lis3lv02d
mac_hid                13077  0 
fglrx                4888596  110 
wl                   2906597  0 
psmouse                86520  0 
rts_pstor             353252  0 
mei                    36570  0 
snd                     62218  16  snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13027  0 
i915                  428014  2 
drm_kms_helper         45466  1 i915
cfg80211              178877  1 wl
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
drm                   197641  3 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  19115  1 i915
lib80211               14040  2 lib80211_crypt_tkip,wl
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usb_storage            39646  1 
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci
r8169                  56368  0

```

```
dmesg |grep "eth1"
eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 6.20.155.1 (r326264)

```

```
sudo lshw -C network
  *-network
       description: Interface réseau sans fil
       produit: BCM4313 802.11bgn Wireless Network Adapter
       fabriquant: Broadcom Corporation
       identifiant matériel: 0
       information bus: pci@0000:0d:00.0
       nom logique: eth1
       version: 01
       numéro de série: cc:52:af:8f:80:bc
       bits: 64 bits
       horloge: 33MHz
       fonctionnalités: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.20.155.1 (r326264) latency=0 multicast=yes wireless=IEEE 802.11abg
       ressources: irq:17 mémoire:c4400000-c4403fff

```


```
sudo iwlist scan

eth1      Scan completed :
          Cell 01 - Address: 2C:39:96:25:B1
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"Livebox-B"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 88ms ago
                    IE: Unknown: 000C4C697665626F782D42314136
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 0706465220010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAD011BFFFF0000000000000000000000000000000406E4A70C00
                    IE: Unknown: 331AAD011BFFFF0000000000000000000000000000000406E4A70C00
                    IE: Unknown: 3D1606080000000000000000000000000000000000000000
                    IE: Unknown: 341606080000000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101810003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD9E0050F204104A0001101044000102103B000103104700103243333939364235823141360043333910210008536167656D636F6D10230016536167656D636F6D46617374333936355F4C42322E381024000C53475F4C42335F312E322E311042000F4E51313331303930343437323730321054000800060050F2040001101100094C697665626F782033100800020006103C0001011049000600372A000120
          Cell 02 - Address: E0:A1:D7:2C:DA
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"VirginBox_D"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 88ms ago
                    IE: Unknown: 000E56697267696E426F785F44414230
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050402030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 03 - Address: 40:5A:9B:38:D4
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"Livebox-D"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 88ms ago
                    IE: Unknown: 000C4C697665626F782D44343830
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 050401030000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F20201018D0003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: 0706465220010D14

```

---

### Post by papampi on 2013-12-29
it can be your wireless channel setting
I had same problem before on one of my laptops , when it was conectting my wireless channel used to switch to a range where other devices couldnt connect

so I set the wireless channel manually and it fixed the problem

---

### Post by snipier on 2013-12-29
Hi Papampi, 

thanks for the reply. What do you mean by "setting the wireless channel manually" ? 
In the network properties, or directly within my box ?

---

### Post by papampi on 2013-12-30
in your wireless router, go to wireless settings and change the channel until all your devices can connect
hopefully it will solve the prob

---

### Post by snipier on 2013-12-30
Hum... I can have a look, but as it happens on every network I'm connecting to, I guess it's not only my router... 

And for the network manager asking the password again and again, no one has a clue ?

---

### Post by praseodym on 2013-12-30
Hi,

the Broadcom-STA driver (Version 5.x) is buggy. Uninstall it and use the native driver **brcmsmac** for this device:
```

sudo apt-get install linux-firmware-nonfree
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
sudo rm /etc/modprobe.d/broadcom-sta-dkms.conf 
sudo sed -i "s/blacklist b43/#blacklist b43/g" $(egrep -lo 'blacklist b43' /etc/modprobe.d/*)
sudo sed -i "s/blacklist ssb/#blacklist ssb/g" $(egrep -lo 'blacklist ssb' /etc/modprobe.d/*)
sudo sed -i "s/blacklist bcma/#blacklist bcma/g" $(egrep -lo 'blacklist bcma' /etc/modprobe.d/*) 
```
Errors in the last 6 lines are Ok, Reboot afterwards.

---

### Post by snipier on 2013-12-30
Thanks [**[COLOR=#000000]praseodym[/COLOR]**]("http://ubuntuforums.org/member.php?u=1411497") for the advice. 

I just upgraded my version from 12.04 to 12.10. I'm trying to see if it was sufficient to solve the problem, if not, I'll try your driver. 

Coming back as soon as I've something new.

---

### Post by praseodym on 2013-12-30
12.10 is only supported until April 2014! 13.04 only until January 2014, 13.10 until July 2014! So I strongly recommend updating to 13.04 and to 13.10. In April 14.04 LTS comes out...

---

### Post by snipier on 2013-12-30
Hum, it wasn't really strategic then... 
But I wanted to avoid a fresh install and the consumption of time it implies. 

I just replaced the driver, and it seems that my squeezebox is able to play now (?). I'm gonna wait a little bit longer to be sure.

---

### Post by snipier on 2013-12-30
Seems I'm good for an upgrade to the next LTS in april.

---

