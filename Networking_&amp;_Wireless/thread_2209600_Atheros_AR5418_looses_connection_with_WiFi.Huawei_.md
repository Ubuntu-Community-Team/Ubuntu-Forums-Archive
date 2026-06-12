---
title: "Atheros AR5418 looses connection with WiFi.Huawei E353 with Aero2 (GSM) won't connect"
date: 2014-03-06
forum: Networking &amp; Wireless
---

### Post by filu2 on 2014-03-06
Welcome. Like in topic, I have problem with WiFi in Toshiba Satellite A215-6820. I'm new user of Ubuntu (12.04 LTS Polish Version), who has just switched from the Windows. Therefore, it would be nice to explain to me how to solve this simple rule of thumb inconvenience. After installation time in common for a shorter or longer time to the network, but even after some time it was disconnecting and showed the authentication window, after which the execution did not give much effect. I was looking for already in various forums, blogs,However, this problem concerns the different equipment in different situations. I'm asking for help... Step by step. 

This is data from other, polish forum, where they didn't helped:

```
lspci -k | egrep -iA2 'net|wire|eth'
0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
    Subsystem: Toshiba America Info Systems Device ff00
    Kernel driver in use: r8169
--
14:00.0 Network controller: Qualcomm Atheros AR5418 Wireless Network Adapter [AR5008E 802.11(a)bgn] (PCI-Express) (rev 01)
    Subsystem: Askey Computer Corp. Device 7125
    Kernel driver in use: ath9k
--
1a:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
    Subsystem: Toshiba America Info Systems Device ff00
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci
1a:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
    Subsystem: Toshiba America Info Systems Device ff00

```
```
sudo lshw -C network
[sudo] password for filu: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:ec:00:98:c6
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.14 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:44 ioport:a000(size=256) memory:f8100000-f8100fff memory:c4400000-c441ffff
  *-network
       description: Wireless interface
       product: AR5418 Wireless Network Adapter [AR5008E 802.11(a)bgn] (PCI-Express)
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:14:00.0
       logical name: wlan0
       version: 01
       serial: 00:1b:9e:a2:0d:48
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.11.0-17-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:19 memory:f8200000-f820ffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: wwan0
       serial: 92:95:44:77:3a:87
       capabilities: ethernet physical
       configuration: broadcast=yes driver=qmi_wwan driverversion=22-Aug-2005 firmware=WWAN/QMI device link=no multicast=yes
```
```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:ec:00:98:c6  
          inet addr:192.168.0.14  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:ecff:fe00:98c6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1394 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1301 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1360687 (1.3 MB)  TX bytes:184852 (184.8 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:105 errors:0 dropped:0 overruns:0 frame:0
          TX packets:105 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10808 (10.8 KB)  TX bytes:10808 (10.8 KB)


wlan0     Link encap:Ethernet  HWaddr 00:1b:9e:a2:0d:48  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
```
iwconfig
wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=17 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
wwan0     no wireless extensions.


lo        no wireless extensions.


eth0      no wireless extensions.

```
```
iwlist scan
wlan0     No scan results


wwan0     Interface doesn't support scanning.


lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.



```
```
nm-tool


NetworkManager Tool


State: connected (global)


- Device: ttyUSB0 --------------------------------------------------------------
  Type:              Mobile Broadband (GSM)
  Driver:            option1
  State:             disconnected
  Default:           no


  Capabilities:




- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             disconnected
  Default:           no
  HW Address:        00:1B:9E:A2:0D:48


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 




- Device: eth0  [Po&#322;&#261;czenie przewodowe 1] ------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        00:1E:EC:00:98:C6


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.0.14
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             62.179.1.62
    DNS:             62.179.1.63

```
```
rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```
```
lsmod
Module                  Size  Used by
bnep                   19210  2 
rfcomm                 59026  0 
bluetooth             341971  10 bnep,rfcomm
qmi_wwan               17407  0 
option                 33960  0 
usbnet                 37649  1 qmi_wwan
usb_wwan               19721  1 option
usbserial              38859  2 option,usb_wwan
cdc_wdm                18399  1 qmi_wwan
parport_pc             32114  0 
ppdev                  17423  0 
snd_hda_codec_hdmi     40852  1 
binfmt_misc            17268  1 
snd_hda_codec_realtek    50877  1 
radeon               1349654  3 
snd_hda_intel          43326  5 
snd_hda_codec         169608  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
arc4                   12509  2 
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                94597  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
uvcvideo               72275  0 
ath9k                 141905  0 
snd_seq_midi           13132  0 
snd_rawmidi            25157  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
mac80211              534922  1 ath9k
videobuf2_core         39385  1 uvcvideo
ttm                    76692  1 radeon
snd_seq                55716  2 snd_seq_midi,snd_seq_midi_event
videodev              107944  2 uvcvideo,videobuf2_core
snd_timer              28930  2 snd_pcm,snd_seq
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
videobuf2_vmalloc      13048  1 uvcvideo
drm_kms_helper         47306  1 radeon
ath9k_common           13619  1 ath9k
ath9k_hw              437399  2 ath9k,ath9k_common
usb_storage            48631  0 
videobuf2_memops       13170  1 videobuf2_vmalloc
ath                    19435  3 ath9k,ath9k_common,ath9k_hw
drm                   247722  5 radeon,ttm,drm_kms_helper
pcmcia                 55837  0 
snd                    61270  21 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
joydev                 17329  0 
sp5100_tco             13754  0 
soundcore              12600  1 snd
i2c_algo_bit           13316  1 radeon
i2c_piix4              17843  0 
snd_page_alloc         18398  2 snd_hda_intel,snd_pcm
tifm_7xx1              13202  0 
yenta_socket           44614  0 
pcmcia_rsrc            18495  1 yenta_socket
cfg80211              416271  3 ath9k,mac80211,ath
tifm_core              15040  1 tifm_7xx1
psmouse                92648  0 
pcmcia_core            22396  3 pcmcia,yenta_socket,pcmcia_rsrc
toshiba_acpi           18382  0 
ati_agp                13242  0 
serio_raw              13189  0 
video                  19046  0 
k8temp                 12912  0 
sparse_keymap          13658  1 toshiba_acpi
wmi                    18744  1 toshiba_acpi
mac_hid                13077  0 
lp                     13359  0 
parport                40930  3 parport_pc,ppdev,lp
hid_generic            12492  0 
usbhid                 47620  0 
hid                    87771  2 hid_generic,usbhid
pata_acpi              12886  0 
firewire_ohci          36064  0 
sdhci_pci              18588  0 
sdhci                  37958  1 sdhci_pci
firewire_core          62303  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
pata_atiixp            13058  0 
r8169                  62856  0 
ahci                   25703  2 
mii                    13693  2 usbnet,r8169
libahci                30834  1 ahci
```
```
uname -a
Linux filu-Satellite-A215 3.11.0-17-generic #31~precise1-Ubuntu SMP Tue Feb 4 21:29:23 UTC 2014 i686 athlon i386 GNU/Linux
```


I've updated Ubuntu, and updated Kernel from[COLOR=#2E8B57][FONT=Monaco] 3.2.0-59-generic[/FONT][/COLOR] to 3.11 only. Didn't work...

---

### Post by varunendra on 2014-03-06
Welcome to the forums filu2!

Please try this -
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rv ath9k
sudo modprobe -v ath9k
```
Does it help making the connection more stable? If not, please post back the outputs of -
```
dmesg | grep ath9k
lsb_release -cd
rfkill list
sudo iwlist scan
```

---

### Post by filu2 on 2014-03-07
Didn't work.

```
 dmesg | grep ath9k
[  250.888508] ath9k: ath9k: Driver unloaded

```
```
lsb_release -cd
Description:    Ubuntu 12.04.4 LTS
Codename:    precise

```
```
rfkill list
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```
```
sudo iwlist scan
[sudo] password for filu: 
wlan0     No scan results


lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.

```

---

### Post by varunendra on 2014-03-07
Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

And can you scan the networks (sudo iwlist scan) if you boot from the Live DVD of 12.04? Not being able to even scan the networks doesn't look right, possible indication of something wrong with your installed version.

Also, can you confirm if the BIOS of the laptop has some option called "IOMMU" or not?

---

### Post by filu2 on 2014-03-07
Wireless Script

```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
--2014-03-07 15:51:32--  http://dl.dropbox.com/u/57264241/wireless_script
Translacja dl.dropbox.com (dl.dropbox.com)... 23.21.215.124
&#321;&#261;czenie si&#281; z dl.dropbox.com (dl.dropbox.com)|23.21.215.124|:80... po&#322;&#261;czono.
&#379;&#261;danie HTTP wys&#322;ano, oczekiwanie na odpowied&#378;... 302 FOUND
Lokalizacja: http://dl.dropboxusercontent.com/u/57264241/wireless_script [pod&#261;&#380;anie]
--2014-03-07 15:51:33--  http://dl.dropboxusercontent.com/u/57264241/wireless_script
Translacja dl.dropboxusercontent.com (dl.dropboxusercontent.com)... 54.225.159.160
&#321;&#261;czenie si&#281; z dl.dropboxusercontent.com (dl.dropboxusercontent.com)|54.225.159.160|:80... po&#322;&#261;czono.
&#379;&#261;danie HTTP wys&#322;ano, oczekiwanie na odpowied&#378;... 200 OK
D&#322;ugo&#347;&#263;: 4210 (4,1K) [text/plain]
Brak nag&#322;ówka Last-modified -- znaczniki czasu wy&#322;&#261;czone.
--2014-03-07 15:51:33--  http://dl.dropboxusercontent.com/u/57264241/wireless_script
Ponowne u&#380;ycie po&#322;&#261;czenia do dl.dropboxusercontent.com:80.
&#379;&#261;danie HTTP wys&#322;ano, oczekiwanie na odpowied&#378;... 200 OK
D&#322;ugo&#347;&#263;: 4210 (4,1K) [text/plain]
Zapis do: `wireless_script'

100%[======================================>] 4.210       --.-K/s   w 0,002s   

2014-03-07 15:51:34 (2,49 MB/s) - zapisano `wireless_script' [4210/4210]

[sudo] password for filu: 

Results archived in "wireless-info.tar.gz", as they exceed the 19.5 kB size limit for .txt files on the Ubuntu Forums.

```
Sudo iwlist scan of boot from DVD with Ubuntu.
```
sudo iwlist scan
lo        Interface doesn't support scanning.

wlan0     No scan results

eth0      Interface doesn't support scanning.

```
And i didn't see any IOMMU option in BIOS. I have PhoenixBIOS.

---

### Post by varunendra on 2014-03-07
> **filu2 said:**
> ```
Results archived in "**[COLOR="#0000CD"]wireless-info.tar.gz[/COLOR]**", as they exceed the 19.5 kB size limit for .txt files on the Ubuntu Forums.

```

I need the above highlighted file that the wireless_script created. It should be in your Home directory. Either attach it in your next post, or extract it > upload its contents to [http://pastebin.ubuntu.com/](http://pastebin.ubuntu.com/) and post back the link to your upload their.

And you didn't say if you have the ISO of the 12.04 or not. Can you try booting from Live DVD/USB and test the connection there?

---

### Post by filu2 on 2014-03-09
I have ISO on DVD, and I've tried connect but didn't work. 

```


*************** info trace ***************

***** uname -a *****

Linux filu-Satellite-A215 3.11.0-17-generic #31~precise1-Ubuntu SMP Tue Feb 4 21:29:23 UTC 2014 i686 athlon i386 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

***** lspci *****

0e:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)
    Subsystem: Toshiba America Info Systems Device [1179:ff00]
    Kernel driver in use: r8169
--
14:00.0 Network controller [0280]: Qualcomm Atheros AR5418 Wireless Network Adapter [AR5008E 802.11(a)bgn] (PCI-Express) [168c:0024] (rev 01)
    Subsystem: Askey Computer Corp. Device [144f:7125]
    Kernel driver in use: ath9k

***** lsusb *****

Bus 001 Device 004: ID 04f2:b008 Chicony Electronics Co., Ltd USB 2.0 Camera
Bus 004 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 005 Device 002: ID 09da:054f A4 Tech Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

***** PCMCIA Card Info *****

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

***** iwconfig *****

wlan0     IEEE 802.11abgn  ESSID:"UPC0052309"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC address removed>   
          Bit Rate=78 Mb/s   Tx-Power=17 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=50/70  Signal level=-60 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:55   Missed beacon:0


***** rfkill *****

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** iw reg get *****

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

***** route -n *****

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0

***** lsmod *****

ath9k                 141905  0 
mac80211              534922  1 ath9k
ath9k_common           13619  1 ath9k
ath9k_hw              437399  2 ath9k,ath9k_common
ath                    19435  3 ath9k,ath9k_common,ath9k_hw
cfg80211              416271  3 ath9k,mac80211,ath

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: wlan0  [UPC0052309] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           78 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    UPC0041449:      Infra, <MAC address removed>, Freq 2442 MHz, Rate 54 Mb/s, Strength 67 WPA WPA2
    DOM:             Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA
    UPC0810665:      Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    sssijGoMala:     Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA
    *UPC0052309:     Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 59 WPA WPA2
    link15:          Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    Kora:            Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WPA
    Gosia:           Infra, <MAC address removed>, Freq 2422 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    mac202:          Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    Julia WiFi:      Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2

  IPv4 Settings:
    Address:         192.168.0.12
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             62.179.1.62
    DNS:             62.179.1.63


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
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

auto lo
iface lo inet loopback


***** iwlist *****

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"UPC0052309"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001072e6de270
                    Extra: Last beacon: 36ms ago
                    IE: Unknown: 000A55504330303532333039
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081500000000000000000000000000000000000000
                    IE: Unknown: DD090010180205F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"DOM"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000005b607f6af
                    Extra: Last beacon: 36ms ago
                    IE: Unknown: 0003444F4D
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0900037F01010008FF7F
                    IE: Unknown: DD0C00037F020101020002A30000
                    IE: Unknown: DD1A00037F030100000000146CDC1F9A02146CDC1F9A64002C010808
          Cell 03 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"UPC0810665"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000cf628ccd0f
                    Extra: Last beacon: 36ms ago
                    IE: Unknown: 000A55504330383130363635
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1ABC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081500000000000000000000000000000000000000
                    IE: Unknown: DD090010180201000C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 04 - Address: <MAC address removed>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"Gosia"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000c8e06bd80
                    Extra: Last beacon: 8800ms ago
                    IE: Unknown: 0005476F736961
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030103
                    IE: Unknown: 050400010000
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
                    IE: Unknown: DD180050F2020101860003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34030D0800000000000000000000000000000000000000
                    IE: Unknown: 3D16030D0800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010006004000
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 05 - Address: <MAC address removed>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"UPC0041449"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000140dffe823
                    Extra: Last beacon: 36ms ago
                    IE: Unknown: 000A55504330303431343439
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030107
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1607001300000000000000000000000000000000000000
                    IE: Unknown: DD090010180201F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 06 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"mac202"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000107374d0183
                    Extra: Last beacon: 8432ms ago
                    IE: Unknown: 00066D6163323032
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 050400030002
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
          Cell 07 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"sssijGoMala"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000036b9907199
                    Extra: Last beacon: 176ms ago
                    IE: Unknown: 000B737373696A476F4D616C61
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD090010180201F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00


***** resolv.conf *****

nameserver 127.0.0.1

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

filename:       /lib/modules/3.11.0-17-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     9960BB0B644BE14E4A2F42B
alias:          platform:qca955x_wmac
alias:          platform:ar934x_wmac
alias:          platform:ar933x_wmac
alias:          platform:ath9k
alias:          pci:v0000168Cd00000036sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000037sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv000010CFsd00001783bc*sc*i*
alias:          pci:v0000168Cd00000034sv000014CDsd00000064bc*sc*i*
alias:          pci:v0000168Cd00000034sv000014CDsd00000063bc*sc*i*
alias:          pci:v0000168Cd00000034sv0000103Csd00001864bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006641bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006631bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001043sd0000850Ebc*sc*i*
alias:          pci:v0000168Cd00000034sv00001A3Bsd00002110bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001969sd00000091bc*sc*i*
alias:          pci:v0000168Cd00000034sv000017AAsd00003214bc*sc*i*
alias:          pci:v0000168Cd00000034sv0000168Csd00003117bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006661bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001A3Bsd00002116bc*sc*i*
alias:          pci:v0000168Cd00000033sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000105Bsd0000E075bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002152bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002126bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001237bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002086bc*sc*i*
alias:          pci:v0000168Cd00000030sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Esv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
depends:        ath9k_hw,ath9k_common,mac80211,ath,cfg80211
intree:         Y
vermagic:       3.11.0-17-generic SMP mod_unload modversions 686 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           enable_diversity:Enable Antenna diversity for AR9565 (int)

filename:       /lib/modules/3.11.0-17-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     2DB88A2876852DC1D8C5A1D
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.11.0-17-generic SMP mod_unload modversions 686 

filename:       /lib/modules/3.11.0-17-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     6F97CF09431D08603B6A91A
depends:        ath
intree:         Y
vermagic:       3.11.0-17-generic SMP mod_unload modversions 686 

filename:       /lib/modules/3.11.0-17-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     A890CDBC88E6EF28CD751DD
depends:        cfg80211
intree:         Y
vermagic:       3.11.0-17-generic SMP mod_unload modversions 686 


***** udev rules *****

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:06.0/0000:0e:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:07.0/0000:14:00.0 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[   12.646383] ath: EEPROM regdomain: 0x69
[   12.646388] ath: EEPROM indicates we should expect a direct regpair map
[   12.646392] ath: Country alpha2 being used: 00
[   12.646394] ath: Regpair used: 0x69
[   24.118862] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.119196] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   31.804682] wlan0: authenticate with <MAC address removed>
[   31.809934] wlan0: send auth to <MAC address removed> (try 1/3)
[   31.811924] wlan0: authenticated
[   31.816054] wlan0: associate with <MAC address removed> (try 1/3)
[   31.819445] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[   31.819499] wlan0: associated
[   31.819531] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

****************** done ******************

```

---

### Post by varunendra on 2014-03-10
As per the report, it seems you are connected -
> **filu2 said:**
> 
```

NetworkManager Tool

State: **[COLOR="#008000"]connected[/COLOR]** (global)

- Device: wlan0  [UPC0052309] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             **[COLOR="#008000"]connected[/COLOR]**
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    **Speed:           [COLOR="#008000"]78 Mb/s[/COLOR]**

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    ....
    ***UPC0052309:     Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 59 [COLOR="#FF0000"]WPA WPA2[/COLOR]**
    ....

  IPv4 Settings:
    Address:         192.168.0.12
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             **[COLOR="#800000"]62.179.1.62[/COLOR]**
    DNS:            [COLOR="#800000"]** 62.179.1.63**[/COLOR]
....
<snip>
....
wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:**[COLOR="#800000"]11[/COLOR]**
                    ....
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : **[COLOR="#FF0000"]TKIP[/COLOR]**
                    ....
                    IE: **[COLOR="#FF0000"]WPA[/COLOR]** Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP **[COLOR="#FF0000"]TKIP[/COLOR]**

```

There are a few settings that we don't usually like, but for now you do seem to be connected. Can you still not browse the net at all?

Please try this -
```
ping -c4 8.8.8.8
```
If you get a ping reply, try changing your DNS in Network Manager. Choose the 'Method' under "IPv4 Settings" tab to be "Automatic (DHCP) address only", then in the "DNS servers" field, save these addresses (google's DNS servers) -
**8.8.8.8, 8.8.4.4**

Then disconnect --> reconnect and try to browse.

However, if you don't get any ping replies, try these suggestions -

[INDENT]**1)** Change the encryption type in the router to pure WPA2-AES (CCMP). Currently it is set to WPA/WPA2 mixed mode with TKIP, avoid these at all costs. After saving the change, reboot the router/access-point. (you should apply this suggestion anyway, to get better connectivity and performance).

**2)** Try changing the Channel to **1**. The current channel (11) is being used by almost all the neighbourhood access-points, which may cause interference. Channel 1 seems to be least used as per scan results, so should offer better signal quality.

**3)** If the above two don't seem to help, try this in Ubuntu -
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rv ath9k
sudo modprobe -v ath9k
```

**4)** If none of the above seem to help, try disabling N-channel in the router (set it to b/g only or g-only mode, currently it seems to be in b/g/n mode).

After any change you save in the router, do not forget to reboot it. It is sometimes necessary for the changes to take effect properly.[/INDENT]

If you still can't browse the net or get a ping reply ("ping 8.8.8.8"), post back with a fresh report of wireless_script, generated AFTER applying the above changes.

Along with the fresh report, please also post back the output of -
```
grep [[:alnum:]] /sys/module/ath*/parameters/*
```
And which country you are in? We may also have to force your country code on the regdomain settings. It is currently defaulted to "00".

---

### Post by filu2 on 2014-03-12
This was just after i've turned computer on. That's why it was connected. After few minutes it was disconnected again. I've installed new Ubuntu not from Ubuntu.pl, just from [http://www.ubuntu.com/desktop](http://www.ubuntu.com/desktop) , Ubuntu LTS 12.04.4 and there is the same problem. Eh... I had hope Ubuntu will be just hard for the new user... Not attacking user by many errors and problems. So i'm think to stay with Windows. Maybe i'll try other time with new, not 6 years old computer.

---

### Post by varunendra on 2014-03-12
New hardware has no guaranty to work better with Linux. On the contrary, if a hardware or its firmware (the embedded program to control it) is a "Just arrived in the market" type, it has less chance to work properly with linux, because Linux drivers are developed mostly by volunteers, and takes some time to cover new devices.

If wireless is the only problem, it should get solved automatically with updates or later kernels. Whatever we do here with various tweaks and alternative drivers is just to make it work right now.

Recently some critical changes were introduced in the kernel to make it better. Unfortunately, like in ANY software development, critical changes are also prone to bugs and regressions. A lot of drivers faced some regression due to those changes. The one you are using has become better, but not fully recovered.

Based on user feedback here, a couple of newer versions of this driver seem to have become better again and usually solve the kind of problem you are having. If you wish, we can try them. But we always need to make sure the problem factors are not hidden somewhere else, hence the tweaking and experimenting.

But of course if you are having "many errors and problems", not just wireless, then its upto you whether you have time to fix them or get back to Windows. There is nothing wrong in switching back anyway if windows is overall working better for you.

Linux almost always gets better and easier with time and experience (in my personal experience, it is opposite in windows), but yes, it may sometimes be daunting for new users who may not have enough time to find and fix the problems.

Let me know if you wish to try further, I'll be glad to help as much as I can. But I'm also just a simple user and can't guaranty that my help will certainly solve the problem(s). The only thing I can guaranty is that nobody will hate you if you decide to go back to windows and give up on Linux/Ubuntu. :)

---

