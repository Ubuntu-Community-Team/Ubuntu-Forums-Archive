---
title: "Need help installing Awus036nhr"
date: 2013-09-05
forum: Networking &amp; Wireless
---

### Post by key-x on 2013-09-05
I bought this Wifi Stick and ubuntu is detecting it.
I can connect to a wireless network, but there are connections issues.. sometimes no outgoing packets.. no ping :(

Here some Informations about my Systemconfig with this stick

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.3 LTS"
Linux Hamburg 3.5.0-39-generic #60~precise1-Ubuntu SMP Wed Aug 14 15:28:09 UTC 2013 i686 i686 i386 GNU/Linux
```

```

lsusb
Bus 002 Device 011: ID 0bda:817f Realtek Semiconductor Corp. 

```

```

wlan2     IEEE 802.11bgn  ESSID:xxxxx
          Mode:Managed  Frequency:2.462 GHz  Access Point: xx-xx-xx-xx-xx-xx
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr ff
          Encryption key ff
          Power Management:off
          Link Quality=62/70  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:15   Missed beacon:0
```

```

lsmod
Module                  Size  Used by
nls_iso8859_1          12618  0 
rtl8180                35919  0 
eeprom_93cx6           13169  1 rtl8180
nls_utf8               12494  0 
isofs                  39595  0 
zl10353                17660  1 
tm6000_dvb             13131  0 
dvb_core               99332  1 tm6000_dvb
tm6000_alsa            13326  1 
rc_nec_terratec_cinergy_xs    12503  0 
rfcomm                 38104  0 
bnep                   17791  2 
parport_pc             32115  0 
ppdev                  12850  0 
bluetooth             189625  10 rfcomm,bnep
joydev                 17394  0 
snd_hda_codec_hdmi     31778  1 
snd_hda_codec_conexant    52560  1 
tuner_xc2028           26636  2 
tuner                  26874  1 
arc4                   12474  4 
coretemp               13362  0 
hp_wmi                 13653  0 
sparse_keymap          13659  1 hp_wmi
rtl8192cu              67480  0 
microcode              18396  0 
rtl8192c_common        47696  1 rtl8192cu
snd_hda_intel          32983  3 
snd_hda_codec         116477  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13277  1 snd_hda_codec
snd_pcm                81124  4 tm6000_alsa,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
rtlwifi                65304  1 rtl8192cu
snd_seq_midi           13133  0 
snd_rawmidi            25426  1 snd_seq_midi
snd_seq_midi_event     14476  1 snd_seq_midi
tm6000                 57579  2 tm6000_dvb,tm6000_alsa
videobuf_vmalloc       13337  1 tm6000
videobuf_core          25410  2 tm6000,videobuf_vmalloc
rc_core                21295  3 rc_nec_terratec_cinergy_xs,tm6000
v4l2_common            15794  2 tuner,tm6000
wmi                    18745  1 hp_wmi
snd_seq                51594  2 snd_seq_midi,snd_seq_midi_event
psmouse                91408  0 
serio_raw              13032  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
mac_hid                13078  0 
i915                  479235  2 
drm_kms_helper         47459  1 i915
snd                    62675  19 tm6000_alsa,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   240443  3 i915,drm_kms_helper
ath5k                 137284  0 
soundcore              14636  1 snd
ath                    19436  1 ath5k
snd_page_alloc         14109  2 snd_hda_intel,snd_pcm
uvcvideo               72249  0 
videobuf2_core         32212  1 uvcvideo
videodev              100265  5 tuner,tm6000,v4l2_common,uvcvideo,videobuf2_core
videobuf2_vmalloc      12757  1 uvcvideo
videobuf2_memops       13213  1 videobuf2_vmalloc
mac80211              475546  5 rtl8180,rtl8192cu,rtl8192c_common,rtlwifi,ath5k
lpc_ich                16993  0 
i2c_algo_bit           13317  1 i915
video                  19117  1 i915
cfg80211              181041  5 rtl8180,rtlwifi,ath5k,ath,mac80211
lp                     17456  0 
parport                40931  3 parport_pc,ppdev,lp
hid_generic            12485  0 
usbhid                 46054  0 
ums_realtek            17929  0 
hid                    82511  2 hid_generic,usbhid
usb_storage            39720  1 ums_realtek
ahci                   25621  2 
libahci                26166  1 ahci
r8169                  56828  0 

```

---

### Post by chili555 on 2013-09-05
You also have the driver for your internal device loaded. Is it not working as expected? I suspect you'd have better luck with the internal blacklisted. You also seem to have several other wireless drivers loaded which undoubtedly conflict.> mac80211 475546 5 [COLOR="#FF0000"]rtl8180[/COLOR],rtl8192cu,rtl8192c_common,[COLOR="#FF0000"]rtlwifi[/COLOR],[COLOR="#FF0000"]ath5k[/COLOR]May I also see:```
ls /etc/modprobe.d
sudo lshw -C network -numeric
```

---

### Post by key-x on 2013-09-05
Hi chili.. thx for your Help..

I dont know weather my internal card is working as expected.. i dont use/need it at the time but i think that ist work (eth0)

I tried to blacklistrtl8180,rtlwifi and ath5k without an effect -.-

Then i tried to remove the module by "rmmod rtlwifi" with the result -> "ERROR: Module rtlwifi is in use by rtl8192cu

"
Here are your further informations:
```

ls -l /etc/modprobe.d
insgesamt 44
-rw-r--r-- 1 root root 2507 Feb 16  2012 alsa-base.conf
-rw-r--r-- 1 root root  325 Mär 18  2011 blacklist-ath_pci.conf
-rw-r--r-- 1 root root 1678 Sep  5 16:57 blacklist.conf
-rw-r--r-- 1 root root  210 Mär 18  2011 blacklist-firewire.conf
-rw-r--r-- 1 root root  661 Nov 20  2011 blacklist-framebuffer.conf
-rw-r--r-- 1 root root  156 Feb 16  2012 blacklist-modem.conf
lrwxrwxrwx 1 root root   41 Sep  1 07:34 blacklist-oss.conf -> /lib/linux-sound-base/noOSS.modprobe.conf
-rw-r--r-- 1 root root  583 Mär 18  2011 blacklist-rare-network.conf
-rw-r--r-- 1 root root 1077 Mär 18  2011 blacklist-watchdog.conf
-rw-r--r-- 1 root root  110 Sep  1 08:48 ndiswrapper.conf
-rw-r--r-- 1 root root  356 Sep  1 22:06 oss-compat.conf
-rw-r--r-- 1 root root   30 Jan 20  2013 vmwgfx-fbdev.conf

```

```
sudo lshw -C network -numeric
*-network               
       Beschreibung: Ethernet interface
       Produkt: RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10EC:8136]
       Hersteller: Realtek Semiconductor Co., Ltd. [10EC]
       Physische ID: 0
       Bus-Informationen: pci@0000:01:00.0
       Logischer Name: eth0
       Version: 02
       Seriennummer: 00:1f:16:67:41:a1
       Größe: 10Mbit/s
       Kapazität: 100Mbit/s
       Breite: 64 bits
       Takt: 33MHz
       Fähigkeiten: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       Konfiguration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       Ressourcen: irq:42 ioport:3000(Größe=256) memory:d0410000-d0410fff memory:d0400000-d040ffff memory:d0420000-d043ffff
  *-network
       Beschreibung: Kabellose Verbindung
       Produkt: AR242x / AR542x Wireless Network Adapter (PCI-Express) [168C:1C]
       Hersteller: Qualcomm Atheros [168C]
       Physische ID: 0
       Bus-Informationen: pci@0000:02:00.0
       Logischer Name: wlan0
       Version: 01
       Seriennummer: 00:24:2b:06:57:7d
       Breite: 64 bits
       Takt: 33MHz
       Fähigkeiten: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       Konfiguration: broadcast=yes driver=ath5k driverversion=3.5.0-39-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bg
       Ressourcen: irq:17 memory:d2600000-d260ffff
  *-network
       Beschreibung: Kabellose Verbindung
       Physische ID: 2
       Bus-Informationen: usb@2:5
       Logischer Name: wlan2
       Seriennummer: 00:c0:ca:71:ba:59
       Fähigkeiten: ethernet physical wireless
       Konfiguration: broadcast=yes driver=rtl8192cu driverversion=3.5.0-39-generic firmware=N/A ip=192.168.178.52 link=yes multicast=yes wireless=IEEE 802.11bgn

```

---

### Post by key-x on 2013-09-05
here's my new

```

lsmod
Module                  Size  Used by
zl10353                17660  1 
tm6000_dvb             13131  6 
dvb_core               99332  1 tm6000_dvb
tm6000_alsa            13326  1 
rc_nec_terratec_cinergy_xs    12503  0 
joydev                 17394  0 
snd_hda_codec_hdmi     31778  1 
snd_hda_codec_conexant    52560  1 
tuner_xc2028           26636  2 
tuner                  26874  1 
rfcomm                 38104  0 
bnep                   17791  2 
parport_pc             32115  0 
ppdev                  12850  0 
bluetooth             189625  10 rfcomm,bnep
coretemp               13362  0 
arc4                   12474  4 
hp_wmi                 13653  0 
sparse_keymap          13659  1 hp_wmi
microcode              18396  0 
snd_hda_intel          32983  5 
snd_hda_codec         116477  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13277  1 snd_hda_codec
uvcvideo               72249  0 
videobuf2_core         32212  1 uvcvideo
snd_pcm                81124  5 tm6000_alsa,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
psmouse                91408  0 
serio_raw              13032  0 
snd_seq_midi           13133  0 
snd_rawmidi            25426  1 snd_seq_midi
rtl8192cu              67480  0 
rtl8192c_common        47696  1 rtl8192cu
rtlwifi                65304  1 rtl8192cu
snd_seq_midi_event     14476  1 snd_seq_midi
tm6000                 57579  2 tm6000_dvb,tm6000_alsa
videobuf_vmalloc       13337  1 tm6000
videobuf_core          25410  2 tm6000,videobuf_vmalloc
rc_core                21295  3 rc_nec_terratec_cinergy_xs,tm6000
v4l2_common            15794  2 tuner,tm6000
videobuf2_vmalloc      12757  1 uvcvideo
videobuf2_memops       13213  1 videobuf2_vmalloc
snd_seq                51594  2 snd_seq_midi,snd_seq_midi_event
videodev              100265  5 tuner,uvcvideo,videobuf2_core,tm6000,v4l2_common
ath5k                 137284  0 
ath                    19436  1 ath5k
mac80211              475546  4 rtl8192cu,rtl8192c_common,rtlwifi,ath5k
cfg80211              181041  4 rtlwifi,ath5k,ath,mac80211
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
wmi                    18745  1 hp_wmi
mac_hid                13078  0 
snd                    62675  22  tm6000_alsa,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  479235  2 
drm_kms_helper         47459  1 i915
lpc_ich                16993  0 
drm                   240443  3 i915,drm_kms_helper
i2c_algo_bit           13317  1 i915
video                  19117  1 i915
soundcore              14636  1 snd
snd_page_alloc         14109  2 snd_hda_intel,snd_pcm
lp                     17456  0 
parport                40931  3 parport_pc,ppdev,lp
hid_generic            12485  0 
ums_realtek            17929  0 
usbhid                 46054  0 
hid                    82511  2 hid_generic,usbhid
usb_storage            39720  1 ums_realtek
ahci                   25621  2 
libahci                26166  1 ahci
r8169                  56828  0
```

---

### Post by chili555 on 2013-09-05
Wait! I'm confused.>  i dont use/need it at the time but i think that ist workIf you don't need/use the internal wireless card, why do you need/use a USB device??

This is your internal device:> *-network
Beschreibung: Kabellose Verbindung
Produkt: AR242x / AR542x Wireless Network Adapter (PCI-Express) [168C:1C]
Hersteller: Qualcomm Atheros [168C]
Physische ID: 0
Bus-Informationen: pci@0000:02:00.0
Logischer Name: [COLOR="#FF0000"]wlan0[/COLOR]
Version: 01
Seriennummer: 00:24:2b:06:57:7d
Breite: 64 bits
Takt: 33MHz
Fähigkeiten: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
Konfiguration: broadcast=yes [COLOR="#FF0000"]driver=ath5k[/COLOR] driverversion=3.5.0-39-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bg
Ressourcen: irq:17 memory:d2600000-d260ffffIf you remove the USB, does the internal device see networks?```
sudo iwlist wlan0 scan
```Is the switch on or off?```
rfkill list all
```If we can get the internal to work properly, isn't that preferable to a USB stick? 

By the way, eth0 is your wired ethernet device.

---

### Post by key-x on 2013-09-05
Sorry, my fold.. i wouldnt confuse you :)

I thought you mean the internal (eth0 LAN) because it uses a rtl module too.. The Internal Wifi (Wlan0) is working properly
There are only Problems with the Wlan2.. i have to reconnect to the AP so that i have for a few Minutes an online connection -.-

rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


I need the Stick because the Signalo of my internal wifi is to weak

---

### Post by chili555 on 2013-09-05
I see. Then let's blacklist the driver for the internal device:```
sudo -i
echo "blacklist ath5k" >> /etc/modprobe.d/blacklist.conf
echo "blacklist ath" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot and tell us if your connectivity has improved.

---

### Post by key-x on 2013-09-05
This has no effect.. i received 3-4mb and the connection stucks.. no ping.. no traffic :(

---

### Post by chili555 on 2013-09-05
Let's try a temporary driver parameter:```
sudo modprobe -r rtl8192cu
sudo modprobe rtl8192cu swenc=1
```If it helps, we'll write one new file to make it persistent.

---

### Post by varunendra on 2013-09-06
Hi key-x !!

It will make your posts look a lot more cleaner, compact and better-looking if you use 'Code' tags instead of 'Quote' tags to post the outputs. It will also prevent the code from turning into those funny smileys, making it more readable.

A quick post with screenshots on How to use code tags : [http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

You can (and 'should') also edit your existing posts above to do that now. :)

---

### Post by key-x on 2013-09-06
@Varunendra.. thank you for your reference

@Chili, the parameter didnt change anything.. the same problems like before

---

### Post by chili555 on 2013-09-06
You might try disabling N speeds at the router. If that doesn't help, I suggest you compile a newer driver. Please see post #4 here: [http://ubuntuforums.org/showthread.php?t=2167956](http://ubuntuforums.org/showthread.php?t=2167956) You may get one or two harmless warnings in 12.04, but I am confident it will work.

---

### Post by key-x on 2013-09-08
i think i found the solution :)

There are 2 different modules for this stick.. rtl8192cu and 8192cu
Monitor mode is only working with rtl8192cu.. internet and N speed only works properly with 8192cu

anyway..  thanks to you all

---

