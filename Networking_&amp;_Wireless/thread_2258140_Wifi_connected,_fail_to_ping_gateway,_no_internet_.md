---
title: "Wifi connected, fail to ping gateway, no internet access [EeePC 1015CX, Ubuntu 14.04]"
date: 2014-12-25
forum: Networking &amp; Wireless
---

### Post by ha62791 on 2014-12-25
I know there are lots of similar posts but those are either for Ubuntu 12.04 or for a different driver.
I installed Ubuntu 14.04 on ASUS EeePC 1015CX.
I can connect to my TP-Link router wirelessly,
but ping 192.168.0.1 gives "Destination Host Unreachable",
and is unable to access the internet.
Accessing internet using LAN cable is OK.
My other notebook can access the internet wirelessly.

Below are output from the commands:

Commands:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
nm-tool
netstat -rn[/QUOTE]

Output:
[QUOTE]ha62791@EeePC:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.1 LTS"
Linux EeePC 3.13.0-43-generic #72-Ubuntu SMP Mon Dec 8 19:35:44 UTC 2014 i686 i686 i686 GNU/Linux
ha62791@EeePC:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: AzureWave Device [1a3b:2047]
    Kernel driver in use: wl
03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8468]
    Kernel driver in use: atl1c
ha62791@EeePC:~$ iwconfig
wlan0     IEEE 802.11abg  ESSID:"TP-LINK_E671B8 @ REACH @ Ha"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: E8:94:F6:E6:71:B8   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

eth0      no wireless extensions.

ha62791@EeePC:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: asus-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
ha62791@EeePC:~$ lsmod
Module                  Size  Used by
rfcomm                 53664  0 
bnep                   18895  2 
bluetooth             342208  10 bnep,rfcomm
snd_hda_codec_hdmi     45440  1 
snd_hda_codec_realtek    59259  1 
eeepc_wmi              12983  0 
asus_wmi               23495  1 eeepc_wmi
sparse_keymap          13708  1 asus_wmi
uvcvideo               71309  0 
videobuf2_vmalloc      13048  1 uvcvideo
videobuf2_memops       13170  1 videobuf2_vmalloc
videobuf2_core         39258  1 uvcvideo
videodev              108503  2 uvcvideo,videobuf2_core
snd_hda_intel          42730  3 
snd_hda_codec         164067  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                85501  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
coretemp               13195  0 
joydev                 17101  0 
serio_raw              13230  0 
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25135  1 snd_seq_midi
lpc_ich                16864  0 
lib80211_crypt_tkip    17456  0 
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
wl                   3999690  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
lib80211               14040  2 wl,lib80211_crypt_tkip
snd_timer              28584  2 snd_pcm,snd_seq
gma500_gfx            168634  2 
snd                    60939  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
video                  18903  2 gma500_gfx,asus_wmi
cfg80211              409394  1 wl
drm_kms_helper         48868  1 gma500_gfx
drm                   244037  3 drm_kms_helper,gma500_gfx
wmi                    18673  1 asus_wmi
parport_pc             31981  0 
i2c_algo_bit           13197  1 gma500_gfx
soundcore              12600  1 snd
ppdev                  17391  0 
lp                     13299  0 
mac_hid                13037  0 
parport                40836  3 lp,ppdev,parport_pc
psmouse                91357  0 
ahci                   25579  1 
libahci                27214  1 ahci
atl1c                  40949  0 
ha62791@EeePC:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        10:BF:48:21:4A:C6

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         off


- Device: wlan0  [TP-LINK_E671B8 @ REACH @ Ha] ---------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        94:DB:C9:9F:29:63

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Yip and Mo Family: Infra, C4:6E:1F:5E:59:81, Freq 2422 MHz, Rate 54 Mb/s, Strength 64 WPA2
    abkit_2:         Infra, 10:6F:3F:38:63:7C, Freq 2447 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    Chan:            Infra, 94:0C:6D:BA:41:7A, Freq 2437 MHz, Rate 54 Mb/s, Strength 52 WEP
    *TP-LINK_E671B8 @ REACH @ Ha: Infra, E8:94:F6:E6:71:B8, Freq 2412 MHz, Rate 54 Mb/s, Strength 97 WPA WPA2
    Kenny and Jeff:  Infra, 10:FE:ED:3E:CA:1A, Freq 2457 MHz, Rate 54 Mb/s, Strength 27 WPA2
    TO:              Infra, F4:EC:38:B0:F5:9E, Freq 2427 MHz, Rate 54 Mb/s, Strength 35 WEP
    TOTOLINK N100RE: Infra, 78:44:76:F9:B7:98, Freq 2462 MHz, Rate 54 Mb/s, Strength 17
    Tse Family:      Infra, C8:BE:19:5F:23:20, Freq 2437 MHz, Rate 54 Mb/s, Strength 57 WPA WPA2
    davidhome:       Infra, 00:22:75:C6:35:82, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    lan:             Infra, 00:0D:0B:87:D7:E4, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2

  IPv4 Settings:
    Address:         192.168.0.102
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1


ha62791@EeePC:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0
```

---

### Post by Sef on 2014-12-25
1) Moved to Networking and Wireless.
2) What is the model number of your TP-Link?
3) What operating system does your other computer have?
4) Have you downloaded any drivers for your wireless?

---

### Post by ha62791 on 2014-12-26
2) TP-Link model: [COLOR=#000000][FONT=Arial]WR841N v8[/FONT][/COLOR] 
3) Other OS: Mac OSX, Windows 7
4) No, I didn't download any drivers. Ubuntu can already connect to wifi during installation.

---

### Post by ha62791 on 2014-12-28
I found the solution myself from
[https://sites.google.com/site/easylinuxtipsproject/internet](https://sites.google.com/site/easylinuxtipsproject/internet)

I completed
step 1: Install a firmware package
```
[COLOR=#0000FF][FONT=Arial]sudo apt-get install linux-firmware-nonfree[/FONT][/COLOR]
```

and
step 2: Broadcom: install the right driver
```
[COLOR=#0000FF][FONT=Arial]sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source && sudo apt-get install b43-fwcutter firmware-b43-installer[/FONT][/COLOR]
```


I'm able to access the internet wirelessly after reboot.:p
From ***nm-tool*** I can see that the driver changes from ***wl*** to ***brcmsmac***

---

