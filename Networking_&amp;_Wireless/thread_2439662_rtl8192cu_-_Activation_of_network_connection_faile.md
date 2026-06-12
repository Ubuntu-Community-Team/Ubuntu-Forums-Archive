---
title: "rtl8192cu - Activation of network connection failed"
date: 2020-03-30
forum: Networking &amp; Wireless
---

### Post by cocaybica on 2020-03-30
Hi,

OS: Ubuntu 19.10

I have a TP-Link TL-WN8200ND [Realtek RTL8192CU] wireless adapter. When it is connected the green led is on. But after trying to connect to my wifi network I'm getting an "Activation of network connection failed" popup message.

I tried booting from a Live USB with the same result.

I was following this thread: [http://forums.debian.net/viewtopic.php?f=30&t=142930](http://forums.debian.net/viewtopic.php?f=30&t=142930) 

Here the resuts:

```
uname -a
Linux PC1 5.3.0-42-generic #34-Ubuntu SMP Fri Feb 28 05:49:40 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

```

```
dmesg | grep rtl
[  349.948620] rtl8192cu: Chip version 0x11
[  350.031004] rtl8192cu: Board Type 0
[  350.031245] rtl_usb: rx_max_size 15360, rx_urb_num 8, in_ep 1
[  350.031286] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[  350.047595] ieee80211 phy1: Selected rate control algorithm 'rtl_rc'
[  350.070683] usbcore: registered new interface driver rtl8192cu
[  350.119239] rtl8192cu 1-2:1.0 wlxc025e91ae320: renamed from wlan0
[  350.237622] rtl8192cu: MAC auto ON okay!
[  350.272010] rtl8192cu: Tx queue select: 0x05
[  395.989263] rtl_usb: reg 0x102, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x390172a
[  395.989272] rtl_usb: reg 0x422, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x1717171e
[  395.989280] rtl_usb: reg 0x542, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x1717171e
[  395.989306] rtl_usb: reg 0x102, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x1e1e1e27
[ 1406.875681] rtl8192cu: Chip version 0x11
[ 1406.967938] rtl8192cu: Board Type 0
[ 1406.968181] rtl_usb: rx_max_size 15360, rx_urb_num 8, in_ep 1
[ 1406.968217] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[ 1406.968463] ieee80211 phy3: Selected rate control algorithm 'rtl_rc'
[ 1407.050506] rtl8192cu 1-2:1.0 wlxc025e91ae320: renamed from wlan0
[ 1407.098561] rtl8192cu: MAC auto ON okay!
[ 1407.136699] rtl8192cu: Tx queue select: 0x05
[ 2175.655786] rtl8192cu: Chip version 0x11
[ 2175.734170] rtl8192cu: Board Type 0
[ 2175.734415] rtl_usb: rx_max_size 15360, rx_urb_num 8, in_ep 1
[ 2175.734455] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[ 2175.735574] ieee80211 phy5: Selected rate control algorithm 'rtl_rc'
[ 2175.800898] rtl8192cu 1-2:1.0 wlxc025e91ae320: renamed from wlan0
[ 2175.844792] rtl8192cu: MAC auto ON okay!
[ 2175.884298] rtl8192cu: Tx queue select: 0x05

```

```

rfkill list
3: phy3: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

```
lsmod | grep rtl
rtl8192cu              73728  0
rtl_usb                20480  1 rtl8192cu
rtl8192c_common        53248  1 rtl8192cu
rtlwifi                86016  3 rtl8192c_common,rtl_usb,rtl8192cu
mac80211              851968  6 rtl_usb,rtl8192cu,rt2x00lib,rtlwifi,rt2x00usb,rt2800lib
cfg80211              712704  3 rt2x00lib,rtlwifi,mac80211

```

```
sudo ip link set wlxc025e91ae320 up
sudo iw dev wlxc025e91ae320 scan | grep SSID
    SSID: Fibertel WiFi515 2.4GHz
    SSID: Fibertel WiFi462 2.4GHz
    SSID: CRISTIAN
    SSID: Fibertel WiFi349 2.4GHz
    SSID: tango
         * SSID List
    SSID: cgalera
    SSID: Fibertel WiFi807 2.4GHz
    SSID: Planeta Kamikaze
    SSID: Fibertel WiFi724 2.4GHz
    SSID: WiFi-casa
    SSID: Fibertel WiFi034 2.4GHz
    SSID: DigitalCore2
    SSID: DigitalCore
    SSID: DigitalCore3
    SSID: los reyes
    SSID: Taller
    SSID: HP-Print-E1-LaserJet 1102
    SSID: Spiedo2.4GHz

```

After trying to connect to my network:
```
dmesg | grep rtl
[  349.948620] rtl8192cu: Chip version 0x11
[  350.031004] rtl8192cu: Board Type 0
[  350.031245] rtl_usb: rx_max_size 15360, rx_urb_num 8, in_ep 1
[  350.031286] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[  350.047595] ieee80211 phy1: Selected rate control algorithm 'rtl_rc'
[  350.070683] usbcore: registered new interface driver rtl8192cu
[  350.119239] rtl8192cu 1-2:1.0 wlxc025e91ae320: renamed from wlan0
[  350.237622] rtl8192cu: MAC auto ON okay!
[  350.272010] rtl8192cu: Tx queue select: 0x05
[  395.989263] rtl_usb: reg 0x102, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x390172a
[  395.989272] rtl_usb: reg 0x422, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x1717171e
[  395.989280] rtl_usb: reg 0x542, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x1717171e
[  395.989306] rtl_usb: reg 0x102, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x1e1e1e27
[ 1406.875681] rtl8192cu: Chip version 0x11
[ 1406.967938] rtl8192cu: Board Type 0
[ 1406.968181] rtl_usb: rx_max_size 15360, rx_urb_num 8, in_ep 1
[ 1406.968217] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[ 1406.968463] ieee80211 phy3: Selected rate control algorithm 'rtl_rc'
[ 1407.050506] rtl8192cu 1-2:1.0 wlxc025e91ae320: renamed from wlan0
[ 1407.098561] rtl8192cu: MAC auto ON okay!
[ 1407.136699] rtl8192cu: Tx queue select: 0x05
[ 2175.655786] rtl8192cu: Chip version 0x11
[ 2175.734170] rtl8192cu: Board Type 0
[ 2175.734415] rtl_usb: rx_max_size 15360, rx_urb_num 8, in_ep 1
[ 2175.734455] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[ 2175.735574] ieee80211 phy5: Selected rate control algorithm 'rtl_rc'
[ 2175.800898] rtl8192cu 1-2:1.0 wlxc025e91ae320: renamed from wlan0
[ 2175.844792] rtl8192cu: MAC auto ON okay!
[ 2175.884298] rtl8192cu: Tx queue select: 0x05
[ 3276.731114] rtl8192cu: Chip version 0x11
[ 3276.807626] rtl8192cu: Board Type 0
[ 3276.807865] rtl_usb: rx_max_size 15360, rx_urb_num 8, in_ep 1
[ 3276.807907] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[ 3276.809160] ieee80211 phy7: Selected rate control algorithm 'rtl_rc'
[ 3276.884031] rtl8192cu 1-2:1.0 wlxc025e91ae320: renamed from wlan0
[ 3276.934622] rtl8192cu: MAC auto ON okay!
[ 3276.972870] rtl8192cu: Tx queue select: 0x05

```

I'm stuck here. Any help? 

Thanks. 
Best Regards.

---

### Post by jeremy31 on 2020-03-31
See the wireless script link in my signature and post results

---

### Post by cocaybica on 2020-03-31
Hi,

Thank you for the support. Script results attached.

(Added [https://pastebin.com/rpqNjb4T](https://pastebin.com/rpqNjb4T))

---

### Post by jeremy31 on 2020-04-01
Try ```
sudo rm /etc/modprobe.d/blacklist-rtl8xxxu.conf
echo "blacklist rtl8192cu" | sudo tee /etc/modprobe.d/rtl8192cu.conf
```
Reboot

---

### Post by cocaybica on 2020-04-01
Ok. 
Still getting the same message.

---

### Post by praseodym on 2020-04-01
Try this one instead
```

sudo dkms remove 8192cu/1.11 --all
sudo rm -r /usr/src/8192cu* 
```
rtl8192cu should be blacklisted. Reboot and show
```

iwconfig
lsmod
```

---

### Post by cocaybica on 2020-04-01
Hi,

Thanks,

I'm getting errors trying to remove those files

> **praseodym said:**
> Try this one instead
```

sudo dkms remove 8192cu/1.11 --all
sudo rm -r /usr/src/8192cu* 
```
rtl8192cu should be blacklisted. Reboot and show
```

iwconfig
lsmod
```

```
sudo dkms remove 8192cu/1.11 --all
Error! There are no instances of module: 8192cu
1.11 located in the DKMS tree.

```

```
sudo rm -r /usr/src/8192cu*
rm: no se puede borrar '/usr/src/8192cu*': No existe el archivo o el directorio

```

---

### Post by cocaybica on 2020-04-01
Here the output for the other commands.

```
iwconfig
enp3s0    no wireless extensions.


lo        no wireless extensions.


enp2s0    no wireless extensions.
```

```
lsmod
Module                  Size  Used by
cdc_acm                36864  2
ccm                    20480  0
vboxnetadp             28672  0
vboxnetflt             28672  0
vboxdrv               487424  2 vboxnetadp,vboxnetflt
binfmt_misc            24576  1
rt2800usb              32768  0
rt2x00usb              24576  1 rt2800usb
rt2800lib             131072  1 rt2800usb
rt2x00lib              61440  3 rt2800usb,rt2x00usb,rt2800lib
mac80211              851968  3 rt2x00lib,rt2x00usb,rt2800lib
cfg80211              712704  2 rt2x00lib,mac80211
libarc4                16384  1 mac80211
snd_usb_audio         245760  2
joydev                 28672  0
input_leds             16384  0
snd_usbmidi_lib        36864  1 snd_usb_audio
mc                     53248  1 snd_usb_audio
cypress_m8             32768  0
usbserial              53248  1 cypress_m8
nvidia_uvm             36864  0
snd_hda_codec_realtek   118784  1
snd_hda_codec_generic    81920  1 snd_hda_codec_realtek
ledtrig_audio          16384  2 snd_hda_codec_generic,snd_hda_codec_realtek
snd_hda_intel          49152  3
snd_intel_nhlt         20480  1 snd_hda_intel
snd_hda_codec         131072  3 snd_hda_codec_generic,snd_hda_intel,snd_hda_codec_realtek
snd_hda_core           90112  4 snd_hda_codec_generic,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
snd_hwdep              20480  2 snd_usb_audio,snd_hda_codec
snd_pcm               106496  4 snd_hda_intel,snd_usb_audio,snd_hda_codec,snd_hda_core
nvidia              10584064  64 nvidia_uvm
snd_seq_midi           20480  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            36864  2 snd_seq_midi,snd_usbmidi_lib
snd_seq                69632  2 snd_seq_midi,snd_seq_midi_event
coretemp               20480  0
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
snd_timer              36864  2 snd_seq,snd_pcm
kvm_intel             278528  0
drm                   491520  3 nvidia
snd                    90112  22 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hwdep,snd_hda_intel,snd_usb_audio,snd_usbmidi_lib,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi
kvm                   659456  1 kvm_intel
soundcore              16384  1 snd
i82975x_edac           16384  0
irqbypass              16384  1 kvm
asus_atk0110           24576  0
mac_hid                16384  0
serio_raw              20480  0
sch_fq_codel           20480  3
parport_pc             40960  0
ppdev                  24576  0
lp                     20480  0
parport                53248  3 parport_pc,lp,ppdev
ip_tables              32768  0
x_tables               40960  1 ip_tables
autofs4                45056  2
hid_generic            16384  0
usbhid                 57344  0
hid                   131072  2 usbhid,hid_generic
psmouse               155648  0
i2c_i801               32768  0
lpc_ich                24576  0
ahci                   40960  3
libahci                32768  1 ahci
pata_acpi              16384  0
sky2                   65536  0

```

---

### Post by jeremy31 on 2020-04-02
Do ```
./wireless-info
```
Post new results

---

### Post by cocaybica on 2020-04-02
Results here:
[URL="https://pastebin.com/PUrPmWSK"]
https://pastebin.com/PUrPmWSK[/URL]

And attached file.

---

### Post by praseodym on 2020-04-02
Lets see
```

sudo modprobe -rfv rt2800usb rtl8xxxu
sudo modprobe -v rtl8xxxu
dmesg | grep rtl
iwconfig
rfkill list
sudo iwlist scan
```

---

### Post by praseodym on 2020-04-02
P.S.: Did you install ndiswrapper as well?

---

### Post by jeremy31 on 2020-04-02
> **praseodym said:**
> P.S.: Did you install ndiswrapper as well?

Nice find, didn't notice that one, not sure why that ralink USB module is loaded

---

### Post by cocaybica on 2020-04-02
I have connected a working Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter TP Link 7200ND, then I bought the new adapter which gives me the mentioned problems. Neither of them are connected at the same time.

About the ndiswrapper I have installed to try the 7200ND but I'm not using that right now. Because of all that it was that I tried from a live usb to see if I had the same issue booting with the last usb adapter.

Ok. Im gonna test those command and I'm coming back soon...

---

### Post by cocaybica on 2020-04-02
Here the first results:

```
sudo modprobe -rfv rt2800usb rtl8xxxu
rmmod rt2800usb
rmmod rt2800lib
rmmod rt2x00usb
rmmod rt2x00lib
rmmod mac80211
rmmod libarc4
rmmod cfg80211
ramiro@PC1:~$ sudo modprobe -v rtl8xxxu
insmod /lib/modules/5.3.0-45-generic/kernel/lib/crypto/libarc4.ko 
insmod /lib/modules/5.3.0-45-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/5.3.0-45-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/5.3.0-45-generic/kernel/drivers/net/wireless/realtek/rtl8xxxu/rtl8xxxu.ko 
ramiro@PC1:~$ dmesg | grep rtl
[21428.743992] usb 1-2: rtl8192cu_parse_efuse: dumping efuse (0x80 bytes):
[21428.744039] usb 1-2: rtl8xxxu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[21429.381598] usbcore: registered new interface driver rtl8xxxu
[21429.540891] rtl8xxxu 1-2:1.0 wlxc025e91ae320: renamed from wlan0
ramiro@PC1:~$ iwconfig
wlxc025e91ae320  IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
enp2s0    no wireless extensions.


lo        no wireless extensions.


enp3s0    no wireless extensions.

```



```
rfkill list
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

```

sudo iwlist scan
wlxc025e91ae320  Interface doesn't support scanning : Device or resource busy


enp2s0    Interface doesn't support scanning.


lo        Interface doesn't support scanning.


enp3s0    Interface doesn't support scanning.


```


And here trying again the last command:
[https://pastebin.com/m5uWrrTG](https://pastebin.com/m5uWrrTG)

---

### Post by cocaybica on 2020-04-02
After trying those commands:

The green led is off.
When I try to connect to a network it keep asking for its password over and over again.

---

### Post by jeremy31 on 2020-04-03
Post results for ```
grep [[:alnum:]] /etc/modprobe.d/*
```

---

### Post by cocaybica on 2020-04-03
```
grep [[:alnum:]] /etc/modprobe.d/*
# autoloader aliases
/etc/modprobe.d/alsa-base.conf:install sound-slot-0 /sbin/modprobe snd-card-0
/etc/modprobe.d/alsa-base.conf:install sound-slot-1 /sbin/modprobe snd-card-1
/etc/modprobe.d/alsa-base.conf:install sound-slot-2 /sbin/modprobe snd-card-2
/etc/modprobe.d/alsa-base.conf:install sound-slot-3 /sbin/modprobe snd-card-3
/etc/modprobe.d/alsa-base.conf:install sound-slot-4 /sbin/modprobe snd-card-4
/etc/modprobe.d/alsa-base.conf:install sound-slot-5 /sbin/modprobe snd-card-5
/etc/modprobe.d/alsa-base.conf:install sound-slot-6 /sbin/modprobe snd-card-6
/etc/modprobe.d/alsa-base.conf:install sound-slot-7 /sbin/modprobe snd-card-7
/etc/modprobe.d/alsa-base.conf:# Cause optional modules to be loaded above generic modules
/etc/modprobe.d/alsa-base.conf:install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
/etc/modprobe.d/alsa-base.conf:# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
/etc/modprobe.d/alsa-base.conf:install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
/etc/modprobe.d/alsa-base.conf:install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
/etc/modprobe.d/alsa-base.conf:install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
/etc/modprobe.d/alsa-base.conf:install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
/etc/modprobe.d/alsa-base.conf:# Cause optional modules to be loaded above sound card driver modules
/etc/modprobe.d/alsa-base.conf:install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
/etc/modprobe.d/alsa-base.conf:install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }
/etc/modprobe.d/alsa-base.conf:# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
/etc/modprobe.d/alsa-base.conf:install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
/etc/modprobe.d/alsa-base.conf:# Prevent abnormal drivers from grabbing index 0
/etc/modprobe.d/alsa-base.conf:options bt87x index=-2
/etc/modprobe.d/alsa-base.conf:options cx88_alsa index=-2
/etc/modprobe.d/alsa-base.conf:options saa7134-alsa index=-2
/etc/modprobe.d/alsa-base.conf:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base.conf:options snd-intel8x0m index=-2
/etc/modprobe.d/alsa-base.conf:options snd-via82xx-modem index=-2
/etc/modprobe.d/alsa-base.conf:options snd-usb-audio index=-2
/etc/modprobe.d/alsa-base.conf:options snd-usb-caiaq index=-2
/etc/modprobe.d/alsa-base.conf:options snd-usb-ua101 index=-2
/etc/modprobe.d/alsa-base.conf:options snd-usb-us122l index=-2
/etc/modprobe.d/alsa-base.conf:options snd-usb-usx2y index=-2
/etc/modprobe.d/alsa-base.conf:# Ubuntu #62691, enable MPU for snd-cmipci
/etc/modprobe.d/alsa-base.conf:options snd-cmipci mpu_port=0x330 fm_port=0x388
/etc/modprobe.d/alsa-base.conf:# Keep snd-pcsp from being loaded as first soundcard
/etc/modprobe.d/alsa-base.conf:options snd-pcsp index=-2
/etc/modprobe.d/alsa-base.conf:# Keep snd-usb-audio from beeing loaded as first soundcard
/etc/modprobe.d/alsa-base.conf:options snd-usb-audio index=-2
/etc/modprobe.d/alsa-base.conf:#Agregado por mi
/etc/modprobe.d/alsa-base.conf:options snd-hda-intel power_save=0 power_save_controller=N
/etc/modprobe.d/amd64-microcode-blacklist.conf:# The microcode module attempts to apply a microcode update when
/etc/modprobe.d/amd64-microcode-blacklist.conf:# it autoloads.  This is not always safe, so we block it by default.
/etc/modprobe.d/amd64-microcode-blacklist.conf:blacklist microcode
/etc/modprobe.d/blacklist-ath_pci.conf:# For some Atheros 5K RF MACs, the madwifi driver loads buts fails to
/etc/modprobe.d/blacklist-ath_pci.conf:# correctly initialize the hardware, leaving it in a state from
/etc/modprobe.d/blacklist-ath_pci.conf:# which ath5k cannot recover. To prevent this condition, stop
/etc/modprobe.d/blacklist-ath_pci.conf:# madwifi from loading by default. Use Jockey to select one driver
/etc/modprobe.d/blacklist-ath_pci.conf:# or the other. (Ubuntu: #315056, #323830)
/etc/modprobe.d/blacklist-ath_pci.conf:blacklist ath_pci
/etc/modprobe.d/blacklist.conf:# This file lists those modules which we don't want to be loaded by
/etc/modprobe.d/blacklist.conf:# alias expansion, usually so some other driver will be loaded for the
/etc/modprobe.d/blacklist.conf:# device instead.
/etc/modprobe.d/blacklist.conf:# evbug is a debug tool that should be loaded explicitly
/etc/modprobe.d/blacklist.conf:blacklist evbug
/etc/modprobe.d/blacklist.conf:# these drivers are very simple, the HID drivers are usually preferred
/etc/modprobe.d/blacklist.conf:blacklist usbmouse
/etc/modprobe.d/blacklist.conf:blacklist usbkbd
/etc/modprobe.d/blacklist.conf:# replaced by e100
/etc/modprobe.d/blacklist.conf:blacklist eepro100
/etc/modprobe.d/blacklist.conf:# replaced by tulip
/etc/modprobe.d/blacklist.conf:blacklist de4x5
/etc/modprobe.d/blacklist.conf:# causes no end of confusion by creating unexpected network interfaces
/etc/modprobe.d/blacklist.conf:blacklist eth1394
/etc/modprobe.d/blacklist.conf:# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
/etc/modprobe.d/blacklist.conf:# hardware on its own (Ubuntu bug #2011, #6810)
/etc/modprobe.d/blacklist.conf:blacklist snd_intel8x0m
/etc/modprobe.d/blacklist.conf:# Conflicts with dvb driver (which is better for handling this device)
/etc/modprobe.d/blacklist.conf:blacklist snd_aw2
/etc/modprobe.d/blacklist.conf:# replaced by p54pci
/etc/modprobe.d/blacklist.conf:blacklist prism54
/etc/modprobe.d/blacklist.conf:# replaced by b43 and ssb.
/etc/modprobe.d/blacklist.conf:blacklist bcm43xx
/etc/modprobe.d/blacklist.conf:# most apps now use garmin usb driver directly (Ubuntu: #114565)
/etc/modprobe.d/blacklist.conf:blacklist garmin_gps
/etc/modprobe.d/blacklist.conf:# replaced by asus-laptop (Ubuntu: #184721)
/etc/modprobe.d/blacklist.conf:blacklist asus_acpi
/etc/modprobe.d/blacklist.conf:# low-quality, just noise when being used for sound playback, causes
/etc/modprobe.d/blacklist.conf:# hangs at desktop session start (Ubuntu: #246969)
/etc/modprobe.d/blacklist.conf:blacklist snd_pcsp
/etc/modprobe.d/blacklist.conf:# ugly and loud noise, getting on everyone's nerves; this should be done by a
/etc/modprobe.d/blacklist.conf:# nice pulseaudio bing (Ubuntu: #77010)
/etc/modprobe.d/blacklist.conf:blacklist pcspkr
/etc/modprobe.d/blacklist.conf:# EDAC driver for amd76x clashes with the agp driver preventing the aperture
/etc/modprobe.d/blacklist.conf:# from being initialised (Ubuntu: #297750). Blacklist so that the driver
/etc/modprobe.d/blacklist.conf:# continues to build and is installable for the few cases where its
/etc/modprobe.d/blacklist.conf:# really needed.
/etc/modprobe.d/blacklist.conf:blacklist amd76x_edac
/etc/modprobe.d/blacklist-firewire.conf:# Select the legacy firewire stack over the new CONFIG_FIREWIRE one.
/etc/modprobe.d/blacklist-firewire.conf:blacklist ohci1394
/etc/modprobe.d/blacklist-firewire.conf:blacklist sbp2
/etc/modprobe.d/blacklist-firewire.conf:blacklist dv1394
/etc/modprobe.d/blacklist-firewire.conf:blacklist raw1394
/etc/modprobe.d/blacklist-firewire.conf:blacklist video1394
/etc/modprobe.d/blacklist-firewire.conf:#blacklist firewire-ohci
/etc/modprobe.d/blacklist-firewire.conf:#blacklist firewire-sbp2
/etc/modprobe.d/blacklist-framebuffer.conf:# Framebuffer drivers are generally buggy and poorly-supported, and cause
/etc/modprobe.d/blacklist-framebuffer.conf:# suspend failures, kernel panics and general mayhem.  For this reason we
/etc/modprobe.d/blacklist-framebuffer.conf:# never load them automatically.
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist aty128fb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist atyfb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist radeonfb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist cirrusfb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist cyber2000fb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist cyblafb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist gx1fb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist hgafb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist i810fb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist intelfb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist kyrofb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist lxfb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist matroxfb_base
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist neofb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist nvidiafb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist pm2fb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist rivafb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist s1d13xxxfb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist savagefb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist sisfb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist sstfb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist tdfxfb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist tridentfb
/etc/modprobe.d/blacklist-framebuffer.conf:#blacklist vesafb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist vfb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist viafb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist vt8623fb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist udlfb
/etc/modprobe.d/blacklist-modem.conf:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem.conf:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem.conf:# blacklist snd-intel8x0m
/etc/modprobe.d/blacklist-modem.conf:# blacklist snd-via82xx-modem
/etc/modprobe.d/blacklist-oss.conf:blacklist ac97
/etc/modprobe.d/blacklist-oss.conf:blacklist ac97_codec
/etc/modprobe.d/blacklist-oss.conf:blacklist ac97_plugin_ad1980
/etc/modprobe.d/blacklist-oss.conf:blacklist ad1848
/etc/modprobe.d/blacklist-oss.conf:blacklist ad1889
/etc/modprobe.d/blacklist-oss.conf:blacklist adlib_card
/etc/modprobe.d/blacklist-oss.conf:blacklist aedsp16
/etc/modprobe.d/blacklist-oss.conf:blacklist ali5455
/etc/modprobe.d/blacklist-oss.conf:blacklist btaudio
/etc/modprobe.d/blacklist-oss.conf:blacklist cmpci
/etc/modprobe.d/blacklist-oss.conf:blacklist cs4232
/etc/modprobe.d/blacklist-oss.conf:blacklist cs4281
/etc/modprobe.d/blacklist-oss.conf:blacklist cs461x
/etc/modprobe.d/blacklist-oss.conf:blacklist cs46xx
/etc/modprobe.d/blacklist-oss.conf:blacklist emu10k1
/etc/modprobe.d/blacklist-oss.conf:blacklist es1370
/etc/modprobe.d/blacklist-oss.conf:blacklist es1371
/etc/modprobe.d/blacklist-oss.conf:blacklist esssolo1
/etc/modprobe.d/blacklist-oss.conf:blacklist forte
/etc/modprobe.d/blacklist-oss.conf:blacklist gus
/etc/modprobe.d/blacklist-oss.conf:blacklist i810_audio
/etc/modprobe.d/blacklist-oss.conf:blacklist kahlua
/etc/modprobe.d/blacklist-oss.conf:blacklist mad16
/etc/modprobe.d/blacklist-oss.conf:blacklist maestro
/etc/modprobe.d/blacklist-oss.conf:blacklist maestro3
/etc/modprobe.d/blacklist-oss.conf:blacklist maui
/etc/modprobe.d/blacklist-oss.conf:blacklist mpu401
/etc/modprobe.d/blacklist-oss.conf:blacklist nm256_audio
/etc/modprobe.d/blacklist-oss.conf:blacklist opl3
/etc/modprobe.d/blacklist-oss.conf:blacklist opl3sa
/etc/modprobe.d/blacklist-oss.conf:blacklist opl3sa2
/etc/modprobe.d/blacklist-oss.conf:blacklist pas2
/etc/modprobe.d/blacklist-oss.conf:blacklist pss
/etc/modprobe.d/blacklist-oss.conf:blacklist rme96xx
/etc/modprobe.d/blacklist-oss.conf:blacklist sb
/etc/modprobe.d/blacklist-oss.conf:blacklist sb_lib
/etc/modprobe.d/blacklist-oss.conf:blacklist sgalaxy
/etc/modprobe.d/blacklist-oss.conf:blacklist sonicvibes
/etc/modprobe.d/blacklist-oss.conf:blacklist sound
/etc/modprobe.d/blacklist-oss.conf:blacklist sscape
/etc/modprobe.d/blacklist-oss.conf:blacklist trident
/etc/modprobe.d/blacklist-oss.conf:blacklist trix
/etc/modprobe.d/blacklist-oss.conf:blacklist uart401
/etc/modprobe.d/blacklist-oss.conf:blacklist uart6850
/etc/modprobe.d/blacklist-oss.conf:blacklist via82cxxx_audio
/etc/modprobe.d/blacklist-oss.conf:blacklist v_midi
/etc/modprobe.d/blacklist-oss.conf:blacklist wavefront
/etc/modprobe.d/blacklist-oss.conf:blacklist ymfpci
/etc/modprobe.d/blacklist-oss.conf:blacklist ac97_plugin_wm97xx
/etc/modprobe.d/blacklist-oss.conf:blacklist ad1816
/etc/modprobe.d/blacklist-oss.conf:blacklist audio
/etc/modprobe.d/blacklist-oss.conf:blacklist awe_wave
/etc/modprobe.d/blacklist-oss.conf:blacklist dmasound_core
/etc/modprobe.d/blacklist-oss.conf:blacklist dmasound_pmac
/etc/modprobe.d/blacklist-oss.conf:blacklist harmony
/etc/modprobe.d/blacklist-oss.conf:blacklist sequencer
/etc/modprobe.d/blacklist-oss.conf:blacklist soundcard
/etc/modprobe.d/blacklist-oss.conf:blacklist usb-midi
/etc/modprobe.d/blacklist-rare-network.conf:# Many less commonly used network protocols have recently had various
/etc/modprobe.d/blacklist-rare-network.conf:# security flaws discovered. In an effort to reduce the scope of future
/etc/modprobe.d/blacklist-rare-network.conf:# vulnerability exploitations, they are being blacklisted here so that
/etc/modprobe.d/blacklist-rare-network.conf:# unprivileged users cannot use them by default. System owners can still
/etc/modprobe.d/blacklist-rare-network.conf:# either modify this file, or specifically modprobe any needed protocols.
/etc/modprobe.d/blacklist-rare-network.conf:# ax25
/etc/modprobe.d/blacklist-rare-network.conf:alias net-pf-3 off
/etc/modprobe.d/blacklist-rare-network.conf:# netrom
/etc/modprobe.d/blacklist-rare-network.conf:alias net-pf-6 off
/etc/modprobe.d/blacklist-rare-network.conf:# x25
/etc/modprobe.d/blacklist-rare-network.conf:alias net-pf-9 off
/etc/modprobe.d/blacklist-rare-network.conf:# rose
/etc/modprobe.d/blacklist-rare-network.conf:alias net-pf-11 off
/etc/modprobe.d/blacklist-rare-network.conf:# decnet
/etc/modprobe.d/blacklist-rare-network.conf:alias net-pf-12 off
/etc/modprobe.d/blacklist-rare-network.conf:# econet
/etc/modprobe.d/blacklist-rare-network.conf:alias net-pf-19 off
/etc/modprobe.d/blacklist-rare-network.conf:# rds
/etc/modprobe.d/blacklist-rare-network.conf:alias net-pf-21 off
/etc/modprobe.d/blacklist-rare-network.conf:# af_802154
/etc/modprobe.d/blacklist-rare-network.conf:alias net-pf-36 off
/etc/modprobe.d/blacklist-watchdog.conf:# Watchdog drivers should not be loaded automatically, but only if a
/etc/modprobe.d/blacklist-watchdog.conf:# watchdog daemon is installed.
/etc/modprobe.d/blacklist-watchdog.conf:blacklist acquirewdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist advantechwdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist alim1535_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist alim7101_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist booke_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist cpu5wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist eurotechwdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist i6300esb
/etc/modprobe.d/blacklist-watchdog.conf:blacklist i8xx_tco
/etc/modprobe.d/blacklist-watchdog.conf:blacklist ib700wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist ibmasr
/etc/modprobe.d/blacklist-watchdog.conf:blacklist indydog
/etc/modprobe.d/blacklist-watchdog.conf:blacklist iTCO_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist it8712f_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist it87_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist ixp2000_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist ixp4xx_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist machzwd
/etc/modprobe.d/blacklist-watchdog.conf:blacklist mixcomwd
/etc/modprobe.d/blacklist-watchdog.conf:blacklist mpc8xx_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist mpcore_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist mv64x60_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist pc87413_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist pcwd
/etc/modprobe.d/blacklist-watchdog.conf:blacklist pcwd_pci
/etc/modprobe.d/blacklist-watchdog.conf:blacklist pcwd_usb
/etc/modprobe.d/blacklist-watchdog.conf:blacklist s3c2410_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist sa1100_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist sbc60xxwdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist sbc7240_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist sb8360
/etc/modprobe.d/blacklist-watchdog.conf:blacklist sc1200wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist sc520_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist sch311_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist scx200_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist shwdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist smsc37b787_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist softdog
/etc/modprobe.d/blacklist-watchdog.conf:blacklist twl4030_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist w83627hf_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist w83697hf_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist w83697ug_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist w83877f_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist w83977f_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist wafer5823wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist wdt_pci
/etc/modprobe.d/blacklist-watchdog.conf:blacklist wm8350_wdt
/etc/modprobe.d/dkms.conf:# modprobe information used for DKMS modules
/etc/modprobe.d/dkms.conf:# This is a stub file, should be edited when needed,
/etc/modprobe.d/dkms.conf:# used by default by DKMS.
/etc/modprobe.d/intel-microcode-blacklist.conf:# The microcode module attempts to apply a microcode update when
/etc/modprobe.d/intel-microcode-blacklist.conf:# it autoloads.  This is not always safe, so we block it by default.
/etc/modprobe.d/intel-microcode-blacklist.conf:blacklist microcode
/etc/modprobe.d/iwlwifi.conf:# /etc/modprobe.d/iwlwifi.conf
/etc/modprobe.d/iwlwifi.conf:# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
/etc/modprobe.d/iwlwifi.conf:# microcode file installed on the system.  When removing iwlwifi, first
/etc/modprobe.d/iwlwifi.conf:# remove the iwl?vm module and then iwlwifi.
/etc/modprobe.d/iwlwifi.conf:remove iwlwifi \
/etc/modprobe.d/iwlwifi.conf:(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
/etc/modprobe.d/iwlwifi.conf:&& /sbin/modprobe -r mac80211
/etc/modprobe.d/ndiswrapper.conf:alias usb:v2357p0100d*dc*dsc*dp*ic*isc*ip* ndiswrapper
/etc/modprobe.d/nvidia-nomodset.conf:#Creado por mi
/etc/modprobe.d/nvidia-nomodset.conf:options nvidia-drm modset=1
/etc/modprobe.d/rt2800usb.conf:options rt2800usb nohwcrypt=y
/etc/modprobe.d/rtl8192cu.conf:blacklist rtl8192cu
/etc/modprobe.d/rtl8xxxu.conf:options rtl8192cu nohwcrypt=0
/etc/modprobe.d/vmwgfx-fbdev.conf:options vmwgfx enable_fbdev=1

```

---

### Post by praseodym on 2020-04-04
Ok, lets get rid of
```

sudo modprobe -rfv ndiswrapper
sudo apt-get remove --purge ndiswrapper* ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
```
Reboot and show
```

lsmod
route -n
cat /etc/resolv.conf
ifconfig -a
iwconfig
rfkill list
dmesg | egrep 'radio|rtl|key'
```

---

### Post by cocaybica on 2020-04-04
Here the results:

```
lsmod
Module                  Size  Used by
rtl8xxxu              131072  0
ccm                    20480  0
vboxnetadp             28672  0
vboxnetflt             28672  0
vboxdrv               487424  2 vboxnetadp,vboxnetflt
binfmt_misc            24576  1
rt2800usb              32768  0
rt2x00usb              24576  1 rt2800usb
rt2800lib             131072  1 rt2800usb
rt2x00lib              61440  3 rt2800usb,rt2x00usb,rt2800lib
mac80211              851968  4 rt2x00lib,rtl8xxxu,rt2x00usb,rt2800lib
cfg80211              712704  2 rt2x00lib,mac80211
libarc4                16384  1 mac80211
snd_usb_audio         245760  2
snd_usbmidi_lib        36864  1 snd_usb_audio
joydev                 28672  0
mc                     53248  1 snd_usb_audio
cypress_m8             32768  0
input_leds             16384  0
usbserial              53248  1 cypress_m8
nvidia_uvm             36864  0
snd_hda_codec_realtek   118784  1
snd_hda_codec_generic    81920  1 snd_hda_codec_realtek
cdc_acm                36864  0
ledtrig_audio          16384  2 snd_hda_codec_generic,snd_hda_codec_realtek
nvidia              10584064  64 nvidia_uvm
snd_hda_intel          49152  3
snd_intel_nhlt         20480  1 snd_hda_intel
snd_hda_codec         131072  3 snd_hda_codec_generic,snd_hda_intel,snd_hda_codec_realtek
snd_hda_core           90112  4 snd_hda_codec_generic,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
coretemp               20480  0
snd_hwdep              20480  2 snd_usb_audio,snd_hda_codec
snd_pcm               106496  4 snd_hda_intel,snd_usb_audio,snd_hda_codec,snd_hda_core
kvm_intel             278528  0
snd_seq_midi           20480  0
snd_seq_midi_event     16384  1 snd_seq_midi
kvm                   659456  1 kvm_intel
irqbypass              16384  1 kvm
snd_rawmidi            36864  2 snd_seq_midi,snd_usbmidi_lib
drm                   491520  3 nvidia
snd_seq                69632  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
snd_timer              36864  2 snd_seq,snd_pcm
snd                    90112  22 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hwdep,snd_hda_intel,snd_usb_audio,snd_usbmidi_lib,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi
soundcore              16384  1 snd
i82975x_edac           16384  0
mac_hid                16384  0
asus_atk0110           24576  0
serio_raw              20480  0
sch_fq_codel           20480  7
parport_pc             40960  0
ppdev                  24576  0
lp                     20480  0
parport                53248  3 parport_pc,lp,ppdev
ip_tables              32768  0
x_tables               40960  1 ip_tables
autofs4                45056  2
hid_generic            16384  0
usbhid                 57344  0
hid                   131072  2 usbhid,hid_generic
psmouse               155648  0
ahci                   40960  3
libahci                32768  1 ahci
i2c_i801               32768  0
pata_acpi              16384  0
lpc_ich                24576  0
sky2                   65536  0

```

```
route -n
Tabla de rutas IP del núcleo
Destino         Pasarela        Genmask         Indic Métric Ref    Uso Interfaz

```

```
~$ cat /etc/resolv.conf
# This file is managed by man:systemd-resolved(8). Do not edit.
#
# This is a dynamic resolv.conf file for connecting local clients directly to
# all known uplink DNS servers. This file lists all configured search domains.
#
# Third party programs must not access this file directly, but only through the
# symlink at /etc/resolv.conf. To manage man:resolv.conf(5) in a different way,
# replace this symlink by a static file or a different symlink.
#
# See man:systemd-resolved.service(8) for details about the supported modes of
# operation for /etc/resolv.conf.


nameserver 192.168.100.1
nameserver fe80::1%4

```

```

~$ ifconfig -a
enp2s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 00:18:f3:9a:86:32  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 16  


enp3s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 00:18:f3:99:36:1f  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 19  


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Bucle local)
        RX packets 137  bytes 11949 (11.9 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 137  bytes 11949 (11.9 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlxc025e91ae320: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether c0:25:e9:1a:e3:20  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

```
~$ iwconfig
enp2s0    no wireless extensions.


lo        no wireless extensions.


wlxc025e91ae320  IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
enp3s0    no wireless extensions.

```

```
~$ rfkill list
1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

```

~$ dmesg | egrep 'radio|rtl|key'
[    0.722088] Initialise system trusted keyrings
[    0.733317] Asymmetric key parser 'x509' registered
[    0.807858] Loaded X.509 cert 'Build time autogenerated kernel key: f0fac0482d6d7ff8e43224f239a3e194a55d61db'
[    0.822217] Key type big_key registered
[   15.816520] nvidia: module verification failed: signature and/or required key missing - tainting kernel
[  175.866443] usb 1-2: rtl8192cu_parse_efuse: dumping efuse (0x80 bytes):
[  175.866478] usb 1-2: rtl8xxxu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[  176.500153] usbcore: registered new interface driver rtl8xxxu
[  176.534499] rtl8xxxu 1-2:1.0 wlxc025e91ae320: renamed from wlan0
```

---

### Post by cocaybica on 2020-04-06
No solution for this??

---

### Post by praseodym on 2020-04-07
Ok, no issues visible from the driver POV. Lets go into the NWM:

```
sudo sed -i "s/wifi.powersave = 3/wifi.powersave = 2/g" /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
sudo systemctl restart network-manager.service
```

---

### Post by cocaybica on 2020-04-07
Ok, thank you!

I had no outputs from those commands and I'm getting the same [COLOR=#000000]*Activation of network connection failed* after trying to connect to my wifi network. [/COLOR]

---

### Post by cocaybica on 2020-04-20
Anyone please

---

### Post by jeremy31 on 2020-04-20
See the wireless script link in my signature and post results

---

### Post by cocaybica on 2020-04-22
Hi,

Thanks!

Here the results:
[https://pastebin.com/bD5XP4EY](https://pastebin.com/bD5XP4EY)

And attached file.

---

### Post by jeremy31 on 2020-04-24
You might need to disable IPv6 on the wifi connections in Network Manager and set your country code with
```
sudo iw reg set AR
```

Some of the AP's in range have TKIP encryption enabled and that might cause problems.  If this doesn't help you might need to file a bug report against the kernel

---

### Post by cocaybica on 2020-04-24
Ok. Thank you. I'm getting the same message after that command. I'm gonna check how to report a bug.

---

