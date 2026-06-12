---
title: "wireless connects to one AP but not other"
date: 2018-06-11
forum: Networking &amp; Wireless
---

### Post by ezekiel.incorrigible on 2018-06-11
[solved] I just enabled the proprietary broadcom drivers and everything is now fine...

Lubuntu 18.04 on an HP Pavilion dm1

Out of the box, the system happily connects to my phone's wifi AP and maintains a steady connection but not our home router, if I try to connect, it tries for a good long while and then fails without reporting anything. Furthermore, the home AP often simply doesn't appear on the list of available APs (although when it does appear, its signal strength is strong - I'm physically close to it). I haven't worked out a reliable way to make it reappear - it just comes back after a while.

Multiple other devices happily connect to the home AP and maintain a stable connection, I am certain that I have entered the PSK correctly. How can I go about diagnosing/fixing this issue?

lspci
```

...
03:00.0 Network controller: Broadcom Limited BCM4313 802.11bgn Wireless Network Adapter (rev 01)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)

```

dmesg after I attempt to connect wirelessly to the AP
```

[ 2350.910430] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2350.910472] brcmsmac bcma0:1: brcms_ops_config: change power-save mode: false (implement)
[ 2350.911329] IPv6: ADDRCONF(NETDEV_UP): wlp3s0b1: link is not ready
[ 2350.979244] IPv6: ADDRCONF(NETDEV_UP): wlp3s0b1: link is not ready
[ 2390.902626] wlp3s0b1: authenticate with 1c:67:58:59:db:88
[ 2390.910038] wlp3s0b1: send auth to 1c:67:58:59:db:88 (try 1/3)
[ 2390.994412] wlp3s0b1: send auth to 1c:67:58:59:db:88 (try 2/3)
[ 2391.133914] wlp3s0b1: send auth to 1c:67:58:59:db:88 (try 3/3)
[ 2391.266956] wlp3s0b1: authentication with 1c:67:58:59:db:88 timed out
[ 2415.707451] IPv6: ADDRCONF(NETDEV_UP): wlp3s0b1: link is not ready

```


dmesg after I plug in the ethernet cable to the home router (connection fails, although I haven't been able to verify that the ethernet cable connection works with any other machines so it is possible this is a different issue):

```

...
[ 2004.918901] r8169 0000:07:00.0 eno1: link down
[ 2007.147406] r8169 0000:07:00.0 eno1: link up
[ 2008.065120] r8169 0000:07:00.0 eno1: link down
......[abridged for clarity]
[ 2103.855037] r8169 0000:07:00.0 eno1: link up
[ 2104.773090] r8169 0000:07:00.0 eno1: link down
[ 2108.877469] r8169 0000:07:00.0 eno1: link up
[ 2109.794929] r8169 0000:07:00.0 eno1: link down
[ 2129.361009] r8169 0000:07:00.0 eno1: link down


```

dmesg after I successfully connect to my phone's wireless AP
```

[ 2696.815334] brcmsmac bcma0:1: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2696.815354] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2696.815401] wlp3s0b1: associated
[ 2696.835744] brcmsmac bcma0:1: wl0: brcms_c_d11hdrs_mac80211:  txop exceeded phylen 159/256 dur 1778/1504
[ 2696.841212] brcmsmac bcma0:1: wl0: brcms_c_d11hdrs_mac80211:  txop exceeded phylen 137/256 dur 1602/1504
[ 2696.844037] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0b1: link becomes ready
[ 2697.000340] brcmsmac bcma0:1: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)

```

iwconfig
```

wlp3s0b1  IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eno1      no wireless extensions.

lo        no wireless extensions.

```

lsmod
```

Module                  Size  Used by
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  2 hid_generic,usbhid
pci_stub               16384  1
vboxpci                24576  0
vboxnetadp             28672  0
vboxnetflt             28672  0
vboxdrv               471040  3 vboxnetadp,vboxnetflt,vboxpci
ccm                    20480  6
msr                    16384  0
cmac                   16384  1
bnep                   20480  2
arc4                   16384  2
kvm                   593920  0
brcmsmac              565248  0
cordic                 16384  1 brcmsmac
brcmutil               16384  1 brcmsmac
b43                   413696  0
mac80211              778240  2 brcmsmac,b43
irqbypass              16384  1 kvm
btusb                  45056  0
btrtl                  16384  1 btusb
btbcm                  16384  1 btusb
btintel                16384  1 btusb
bluetooth             548864  28 btrtl,btintel,bnep,btbcm,btusb
cfg80211              622592  3 brcmsmac,b43,mac80211
ecdh_generic           24576  2 bluetooth
ssb                    57344  1 b43
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
joydev                 24576  0
input_leds             16384  0
wmi_bmof               16384  0
serio_raw              16384  0
k10temp                16384  0
hp_accel               28672  0
lis3lv02d              20480  1 hp_accel
input_polldev          16384  1 lis3lv02d
snd_hda_codec_idt      57344  1
snd_hda_codec_generic    73728  1 snd_hda_codec_idt
snd_hda_codec_hdmi     49152  1
snd_hda_intel          40960  4
snd_hda_codec         126976  4 snd_hda_intel,snd_hda_codec_idt,snd_hda_codec_hdmi,snd_hda_codec_generic
snd_hda_core           81920  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_idt,snd_hda_codec_hdmi,snd_hda_codec_generic
snd_hwdep              20480  1 snd_hda_codec
shpchp                 36864  0
snd_pcm                98304  4 snd_hda_intel,snd_hda_codec,snd_hda_core,snd_hda_codec_hdmi
snd_timer              32768  1 snd_pcm
snd                    81920  16 snd_hda_intel,snd_hwdep,snd_hda_codec,snd_hda_codec_idt,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_pcm
soundcore              16384  1 snd
mac_hid                16384  0
sch_fq_codel           20480  6
parport_pc             36864  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
ip_tables              28672  0
x_tables               40960  1 ip_tables
autofs4                40960  2
ums_realtek            20480  0
uas                    24576  0
usb_storage            69632  2 uas,ums_realtek
radeon               1470464  6
i2c_algo_bit           16384  1 radeon
ttm                   106496  1 radeon
psmouse               147456  0
drm_kms_helper        167936  1 radeon
syscopyarea            16384  1 drm_kms_helper
r8169                  86016  0
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
mii                    16384  1 r8169
bcma                   57344  3 brcmsmac,b43
drm                   401408  9 radeon,ttm,drm_kms_helper
ahci                   36864  1
i2c_piix4              24576  0
libahci                32768  1 ahci
wmi                    24576  2 wmi_bmof,hp_wmi
video                  40960  0


```

---

