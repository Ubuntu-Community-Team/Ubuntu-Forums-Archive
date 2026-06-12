---
title: "Wireless disabled by hardware switch in samsung np270e5e"
date: 2015-04-09
forum: Networking &amp; Wireless
---

### Post by fernando44 on 2015-04-09
I installed Ubuntu 14.04 in my Samsung Ativ book 2 and the wireless worked fine.. However after  install and reboot my wifi is being disabled by a hardware switch.  Is a uefi machine and Windows8 is not working anymore. 


  I try with "rfkill unblock all" and all the key combinations, but nothig...

Can anybody help?


  For more information, i ran the Wireless_script

```



    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

cata 3.16.0-30-generic x86_64,  Ubuntu 14.04.2 LTS, trusty

CPU    : Intel(R) Celeron(R) CPU 847 @ 1.10GHz
Memory : 3654 MB
Uptime : 14:57:53 up 23 min,  2 users,  load average: 0,03, 0,31, 0,29


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

01:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: Samsung Electronics Co Ltd Device [144d:4105]
    Kernel driver in use: ath9k
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Samsung Electronics Co Ltd Device [144d:c708]
    Kernel driver in use: r8169


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 2232:1041  
Bus 001 Device 005: ID 0cf3:3004 Atheros Communications, Inc. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            yes
1: hci0: Bluetooth         no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

ath9k                 137283  0 
ath9k_common           25638  1 ath9k
ath9k_hw              446521  2 ath9k_common,ath9k
ath                    29006  3 ath9k_common,ath9k,ath9k_hw
mac80211              652718  1 ath9k
cfg80211              494330  4 ath,ath9k_common,ath9k,mac80211
wmi                    19193  0 


module parameters ~~~~~~~~~~~~~~~~~~

ath9k         (6): blink=0 | bt_ant_diversity=0 | btcoex_enable=0 | nohwcrypt=0 | ps_enable=0 | use_chanctx=0
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: disconnected
================o=============o========o=============o=========o===========o==============o===========
 Interface & ID | Type        | Driver | State       | Default | Speed     | Support      | HW Addr   
================o=============o========o=============o=========o===========o==============o===========
 eth0           | Wired       | r8169  | unavailable | no      |           |              | <MAC eth0>
----------------+-------------+--------+-------------+---------+-----------+--------------+-----------
 wlan0          | 802.11 WiFi | ath9k  | unavailable | no      |           | WEP/WPA/WPA2 | <MAC wlan0>
----------------+-------------+--------+-------------+---------+-----------+--------------+-----------


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

emagic               : ssid=emagic | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~



Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Tabla de rutas IP del núcleo
Destino         Pasarela        Genmask         Indic Métric Ref    Uso Interfaz


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "es_AR.UTF-8")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~



blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[ath9k]
filename:       /lib/modules/3.16.0-30-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
srcversion:     F1B005F210401E25BEA4125
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)

[ath9k_common]
filename:       /lib/modules/3.16.0-30-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
srcversion:     50297023DA06CB0C907A2CA
depends:        cfg80211,ath9k_hw,ath

[ath9k_hw]
filename:       /lib/modules/3.16.0-30-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
srcversion:     459A58E79BD2B283DCE8151
depends:        ath

[ath]
filename:       /lib/modules/3.16.0-30-generic/kernel/drivers/net/wireless/ath/ath.ko
srcversion:     165C1DF76AF8C8B6A45DA4F
depends:        cfg80211

[mac80211]
filename:       /lib/modules/3.16.0-30-generic/kernel/net/mac80211/mac80211.ko
srcversion:     D421794D4F30DF3A540FD24
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.16.0-30-generic/kernel/net/wireless/cfg80211.ko
srcversion:     DEE8EAA48495E392CD51C2D
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[wmi]
filename:       /lib/modules/3.16.0-30-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     347CF30B94B5549A75865A8
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:0x0032 (ath9k)
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
modesetting.conf  : options cirrus modeset=1
                    options mgag200 modeset=1


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.16.0-30-generic root=UUID=79c02e7c-c99c-4f90-979a-f145d9b01ac4 ro quiet splash acpi_backlight=vendor acpi_osi=Linux vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.047099] Initializing cgroup subsys net_cls
[    0.047117] Initializing cgroup subsys net_prio
[    1.263212] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.264042] audit: initializing netlink subsys (disabled)
[    1.432621] wmi: Mapper loaded
[    1.470562] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   15.903027] ath: phy0: Set BT/WLAN RX diversity capability
[   15.911435] ath: EEPROM regdomain: 0x65
[   15.911441] ath: EEPROM indicates we should expect a direct regpair map
[   15.911445] ath: Country alpha2 being used: 00
[   15.911447] ath: Regpair used: 0x65
[   22.042113] Bluetooth: BNEP (Ethernet Emulation) ver 1.3

    ======== Done ========



```

---

### Post by kerry_s on 2015-04-09
check your bios, see if you can enable from there.

---

### Post by fernando44 on 2015-04-10
I checked... there is not a option for that :(

---

### Post by kerry_s on 2015-04-10
> **fernando44 said:**
> I checked... there is not a option for that :(

bummer, i have it in my toshiba bios, so i thought it was worth a check.

---

### Post by praseodym on 2015-04-10
Please show the output of

```
lsmod
```

completely

---

### Post by fernando44 on 2015-04-10
lsmod:

```

Module                  Size  Used by
uas                    23159  0 
cdc_acm                32941  0 
usb_storage            66545  2 uas
rfcomm                 69509  12 
bnep                   19624  2 
nls_iso8859_1          12713  2 
uvcvideo               81073  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         59104  1 uvcvideo
v4l2_common            15681  1 videobuf2_core
videodev              153793  3 uvcvideo,v4l2_common,videobuf2_core
media                  21903  2 uvcvideo,videodev
intel_rapl             18783  0 
arc4                   12608  2 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       18823  0 
ath9k                 137283  0 
snd_hda_codec_hdmi     47548  1 
ath9k_common           25638  1 ath9k
snd_hda_codec_realtek    72791  1 
coretemp               13441  0 
snd_hda_codec_generic    68937  1 snd_hda_codec_realtek
ath9k_hw              446521  2 ath9k_common,ath9k
snd_hda_intel          30469  6 
kvm_intel             143590  0 
snd_hda_controller     31056  1 snd_hda_intel
snd_hda_codec         139682  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
kvm                   452043  1 kvm_intel
ath                    29006  3 ath9k_common,ath9k,ath9k_hw
mac80211              652718  1 ath9k
snd_hwdep              17698  1 snd_hda_codec
snd_pcm               104112  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
ath3k                  13331  0 
snd_seq_midi           13564  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30876  1 snd_seq_midi
btusb                  32497  0 
snd_seq                63074  2 snd_seq_midi_event,snd_seq_midi
cfg80211              494330  4 ath,ath9k_common,ath9k,mac80211
bluetooth             446409  23 bnep,ath3k,btusb,rfcomm
joydev                 17393  0 
crct10dif_pclmul       14307  0 
crc32_pclmul           13133  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
6lowpan_iphc           18702  1 bluetooth
serio_raw              13483  0 
ghash_clmulni_intel    13230  0 
cryptd                 20359  1 ghash_clmulni_intel
snd_timer              29562  2 snd_pcm,snd_seq
snd                    79468  23 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              15047  2 snd,snd_hda_codec
mei_me                 19696  0 
shpchp                 37047  0 
dell_smo8800           13154  0 
mei                    87875  1 mei_me
parport_pc             32741  0 
ppdev                  17671  0 
lpc_ich                21093  0 
mac_hid                13227  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_logitech_dj        18469  0 
usbhid                 52616  0 
hid                   110426  3 usbhid,hid_logitech_dj
i915                  905798  3 
i2c_algo_bit           13413  1 i915
drm_kms_helper         61574  1 i915
ahci                   34062  4 
psmouse               106561  0 
libahci                32424  1 ahci
drm                   311018  5 i915,drm_kms_helper
r8169                  71694  0 
mii                    13934  1 r8169
wmi                    19193  0 
video                  20128  1 i915


```

---

### Post by praseodym on 2015-04-10
The driver is loaded. Lets try
```

sudo modprobe -rfv ath9k
sudo rfkill unblock all
sudo modprobe -v ath9k
rfkill list
iwconfig
```

---

### Post by fernando44 on 2015-04-12
It didn't work

more info:

sudo modprobe -rfv ath9k

```

rmmod ath9k
rmmod mac80211
rmmod ath9k_common
rmmod ath9k_hw
rmmod ath
rmmod cfg80211

```

sudo rfkill unblock all

rfkill list

```

1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```


sudo modprobe -v ath9k

```

insmod /lib/modules/3.16.0-30-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.16.0-30-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.16.0-30-generic/kernel/drivers/net/wireless/ath/ath.ko 
insmod /lib/modules/3.16.0-30-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko 
insmod /lib/modules/3.16.0-30-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko 
insmod /lib/modules/3.16.0-30-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko 

```

rfkill list

```

1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```

iwconfig
```

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

```

---

