---
title: "xubuntu 15.10 - modem no longer works after update from 15.04"
date: 2015-11-17
forum: Networking &amp; Wireless
---

### Post by francach on 2015-11-17
Hi,

I have a usb 4G modem which works with the kalmia driver/module. Everything worked until I upgraded xubuntu to 15.10 from 15.04

Now, the modem dialup script works as before, but the wwan0 network interface is no longer created.

In dmesg I see

kalmia 1-1.1:1.0 wwx78471d3754e1: renamed from wwan0

Additionally:
 I see with ifconfig -a that the name of the network interface is initially wwan0 (as usual), but that after a couple of seconds that interface disappears and is replaced by 
wwx78471d3754e1



I suppose a new version of the kalmia driver was included in the upgrade.




Anybody know how I would find that out and maybe try going back to the version which was functioning?

Thanks,
Martin.

---

### Post by Anders_Nilsson on 2015-11-17
same kind of problem here. since upgrade to 15.10 i cant install driver to Asus AC56 wifi network. when I do the "make" in terminal i get an error. 
cd.. location..
make
sudo make install
sudo modprobe 8812au

 it works in debian 8.2

---

### Post by praseodym on 2015-11-17
In Ubuntu 15.10 the networking interface names are renamed (new is here, normally only after new installations...). Please check
```

lsusb
usb-devices
lsmod
ifconfig -a
rfkill list
```

---

### Post by francach on 2015-11-19
Hi,

I see what you mean about renaming the networks. What is the rational in doing that?

Thanks,
Martin.



here's the output from the commands:
ifconfig

eth0      Link encap:Ethernet  HWaddr 0c:54:a5:0f:f0:49  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:875 errors:0 dropped:0 overruns:0 frame:0
          TX packets:875 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:94272 (94.2 KB)  TX bytes:94272 (94.2 KB)

wlan0     Link encap:Ethernet  HWaddr a4:db:30:9c:e4:74  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wwx78471d3754e1 Link encap:Ethernet  HWaddr 78:47:1d:37:54:e1  
          BROADCAST MULTICAST  MTU:1380  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
lsmod
Module                  Size  Used by
bnep                   20480  2
option                 40960  0
usb_wwan               20480  1 option
usbserial              40960  2 option,usb_wwan
binfmt_misc            20480  1
uvcvideo               77824  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
kalmia                 16384  0
usbnet                 40960  1 kalmia
videobuf2_core         49152  1 uvcvideo
v4l2_common            16384  1 videobuf2_core
ath3k                  16384  0
btusb                  36864  0
btrtl                  16384  1 btusb
btbcm                  16384  1 btusb
videodev              143360  3 uvcvideo,v4l2_common,videobuf2_core
btintel                16384  1 btusb
media                  24576  2 uvcvideo,videodev
bluetooth             466944  10 bnep,ath3k,btbcm,btrtl,btusb,btintel
mii                    16384  1 usbnet
arc4                   16384  2
ath9k                 139264  0
snd_hda_codec_hdmi     49152  1
ath9k_common           36864  1 ath9k
snd_hda_codec_realtek    73728  1
snd_hda_codec_generic    69632  1 snd_hda_codec_realtek
snd_hda_intel          32768  4
ath9k_hw              458752  2 ath9k_common,ath9k
snd_hda_codec         118784  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
snd_hda_core           57344  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
snd_hwdep              16384  1 snd_hda_codec
ath                    24576  3 ath9k_common,ath9k,ath9k_hw
mac80211              659456  1 ath9k
snd_pcm                90112  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
intel_rapl             20480  0
acer_wmi               20480  0
sparse_keymap          16384  1 acer_wmi
iosf_mbi               16384  1 intel_rapl
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
cfg80211              483328  4 ath,ath9k_common,ath9k,mac80211
kvm_intel             159744  0
rtsx_pci_ms            20480  0
kvm                   454656  1 kvm_intel
snd_rawmidi            28672  1 snd_seq_midi
snd_seq                57344  2 snd_seq_midi_event,snd_seq_midi
memstick               16384  1 rtsx_pci_ms
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
crc32_pclmul           16384  0
snd_timer              32768  2 snd_pcm,snd_seq
input_leds             16384  0
snd                    69632  19 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
joydev                 20480  0
serio_raw              16384  0
soundcore              16384  1 snd
mei_me                 28672  0
mei                    94208  1 mei_me
mac_hid                16384  0
shpchp                 32768  0
lpc_ich                20480  0
coretemp               16384  0
sunrpc                286720  1
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                45056  3 lp,ppdev,parport_pc
autofs4                40960  2
dm_mirror              24576  0
dm_region_hash         20480  1 dm_mirror
dm_log                 20480  2 dm_region_hash,dm_mirror
hid_generic            16384  0
usbhid                 49152  0
hid                    98304  2 hid_generic,usbhid
uas                    20480  0
usb_storage            57344  2 uas
rtsx_pci_sdmmc         24576  0
i915                 1048576  3
i2c_algo_bit           16384  1 i915
psmouse               114688  0
drm_kms_helper        114688  1 i915
ahci                   32768  2
libahci                32768  1 ahci
drm                   303104  5 i915,drm_kms_helper
atl1c                  40960  0
rtsx_pci               53248  2 rtsx_pci_ms,rtsx_pci_sdmmc
wmi                    20480  1 acer_wmi
video                  24576  2 i915,acer_wmi

lsusb
Bus 004 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 004: ID 046d:c05b Logitech, Inc. M-U0004 810-001317 [B110 Optical USB Mouse]
Bus 003 Device 003: ID 1bcf:2c18 Sunplus Innovation Technology Inc. 
Bus 003 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 13fd:1840 Initio Corporation INIC-1608 SATA bridge
Bus 001 Device 009: ID 04e8:6889 Samsung Electronics Co., Ltd GT-B3730 Composite LTE device (Commercial)
Bus 001 Device 002: ID 1a40:0101 Terminus Technology Inc. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

rfkill list
0: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: acer-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes

usb-devices
T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 4
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=04.02
S:  Manufacturer=Linux 4.2.0-18-generic xhci-hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 4
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1a40 ProdID=0101 Rev=01.11
S:  Product=USB 2.0 Hub
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=02 Prnt=02 Port=00 Cnt=01 Dev#=  9 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=04e8 ProdID=6889 Rev=00.01
C:  #Ifs= 2 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=00 Prot=00 Driver=kalmia
I:  If#= 1 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=option

T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=02 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=13fd ProdID=1840 Rev=01.08
S:  Manufacturer=PI-239  
S:  Product=USB 2.0 Drive   
S:  SerialNumber=533252584A39434337313031
C:  #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=2mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 4
D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1
P:  Vendor=1d6b ProdID=0003 Rev=04.02
S:  Manufacturer=Linux 4.2.0-18-generic xhci-hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=04.02
S:  Manufacturer=Linux 4.2.0-18-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1a.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0024 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=02 Prnt=02 Port=00 Cnt=01 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1bcf ProdID=2c18 Rev=00.09
S:  Manufacturer=NC.21411.00X33709F42LM0009
S:  Product=HD WebCam
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo

T:  Bus=03 Lev=02 Prnt=02 Port=01 Cnt=02 Dev#=  4 Spd=1.5 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=046d ProdID=c05b Rev=54.00
S:  Manufacturer=Logitech
S:  Product=USB Optical MouseT:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 4
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=04.02
S:  Manufacturer=Linux 4.2.0-18-generic xhci-hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 4
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1a40 ProdID=0101 Rev=01.11
S:  Product=USB 2.0 Hub
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=02 Prnt=02 Port=00 Cnt=01 Dev#=  9 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=04e8 ProdID=6889 Rev=00.01
C:  #Ifs= 2 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=00 Prot=00 Driver=kalmia
I:  If#= 1 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=option

T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=02 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=13fd ProdID=1840 Rev=01.08
S:  Manufacturer=PI-239  
S:  Product=USB 2.0 Drive   
S:  SerialNumber=533252584A39434337313031
C:  #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=2mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 4
D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1
P:  Vendor=1d6b ProdID=0003 Rev=04.02
S:  Manufacturer=Linux 4.2.0-18-generic xhci-hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=04.02
S:  Manufacturer=Linux 4.2.0-18-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1a.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0024 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=02 Prnt=02 Port=00 Cnt=01 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1bcf ProdID=2c18 Rev=00.09
S:  Manufacturer=NC.21411.00X33709F42LM0009
S:  Product=HD WebCam
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo

T:  Bus=03 Lev=02 Prnt=02 Port=01 Cnt=02 Dev#=  4 Spd=1.5 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=046d ProdID=c05b Rev=54.00
S:  Manufacturer=Logitech
S:  Product=USB Optical Mouse
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=98mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=04.02
S:  Manufacturer=Linux 4.2.0-18-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=04 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0024 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=98mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=04.02
S:  Manufacturer=Linux 4.2.0-18-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=04 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0024 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

---

