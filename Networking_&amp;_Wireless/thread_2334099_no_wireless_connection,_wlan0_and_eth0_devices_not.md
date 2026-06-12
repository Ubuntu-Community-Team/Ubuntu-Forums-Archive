---
title: "no wireless connection, wlan0 and eth0 devices not found"
date: 2016-08-16
forum: Networking &amp; Wireless
---

### Post by buoncri on 2016-08-16
on my 3rd day on Ubuntu 16.04 (which I love) wifi connection suddenly disappeared: here i post some diagnostics in advance.

[B]lspci:

[/B]```
0:00.0 Host bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d5)
00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5)
00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d5)
00:1c.6 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #7 (rev d5)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM87 Express LPC Controller (rev 05)
00:1f.2 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode] (rev 05)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
01:00.0 3D controller: NVIDIA Corporation GK208M [GeForce GT 740M] (rev a1)
07:00.0 Network controller: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe
07:00.1 Bluetooth: Ralink corp. RT3290 Bluetooth
09:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5227 PCI Express Card Reader (rev 01)
0f:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)
```

[B]iwconfig

[/B]```
lo        no wireless extensions.

wlo1      IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eno1      no wireless extensions.


```

```
buoncri@buoncri-HP-ENVY:~$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device
buoncri@buoncri-HP-ENVY:~$ sudo ifconfig eth0 up
eth0: ERROR while getting interface flags: No such device


```

and at last I tried this:
```
buoncri@buoncri-HP-ENVY:~$ dmesg | grep -e wlan -e b43
[    5.259831] rt2800pci 0000:07:00.0 wlo1: renamed from wlan0


```

I sense there's something wrong here, but i'm really new and i really don't know. Thanks in advance

---

### Post by chili555 on 2016-08-16
Here is the whole answer:> rt2800pci 0000:07:00.0 [COLOR="#FF0000"]wlo1: renamed from wlan0[/COLOR]And here is the relevant interface:> [COLOR="#FF0000"]wlo1[/COLOR]      IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          This naming scheme is new for circa-16.04: [http://askubuntu.com/questions/760196/why-is-enps-in-stead-of-eth-whats-the-meaning-of-enps/760243#760243](http://askubuntu.com/questions/760196/why-is-enps-in-stead-of-eth-whats-the-meaning-of-enps/760243#760243)

So nothing is wrong so far; however, I expect you are questioning this because your wireless isn't working as expected. Let's see what the message log has to say:```
dmesg | grep -e wlo1 -e rt2
rfkill list all
```

---

### Post by buoncri on 2016-08-16
```
buoncri@buoncri-HP-ENVY:~$ dmesg | grep -e wlo1 -e rt2
[    3.120348] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3290, rev 0015 detected
[    3.123826] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 3290 detected
[    3.200458] rt2800pci 0000:07:00.0 wlo1: renamed from wlan0
[    4.275551] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[    4.275580] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt3290.bin'
[    4.278768] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.37
[    5.916374] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[    7.516364] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[    7.516369] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[    9.240351] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   10.840341] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   10.840346] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   12.456330] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   14.056335] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   14.056340] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   25.664246] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   27.264209] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   27.264214] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   28.880224] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   30.480217] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   30.480222] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   42.668077] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   44.268072] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   44.268077] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   45.884082] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   47.488051] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   47.488055] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   59.672023] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   61.275949] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   61.275954] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   62.895965] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   64.499990] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   64.499996] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   76.675907] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   78.275894] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   78.275900] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   79.903886] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   81.503826] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   81.503830] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   93.671742] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   95.275784] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   95.275790] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   96.891736] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   98.495711] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   98.495716] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
```

```
buoncri@buoncri-HP-ENVY:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


```

Yes, it shows no wi-fi, still ethernet is doing ok. Another problem is with signal strenght: when it worked, i had low signal from the router in the same room...

---

### Post by chili555 on 2016-08-16
Let's dig deeper:```
lsmod
```Old Chili doesn't like this one bit:> rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]Also, if you shut down *completely*, not reboot, and start up again, do you get the same error?```
dmesg | grep rt2
```

---

### Post by buoncri on 2016-08-16
```
buoncri@buoncri-HP-ENVY:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          16384  1
snd_hda_codec_hdmi     53248  1
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
kvm                   540672  0
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
snd_hda_codec_idt      57344  1
irqbypass              16384  1 kvm
arc4                   16384  2
crct10dif_pclmul       16384  0
snd_hda_codec_generic    77824  1 snd_hda_codec_idt
rt2800pci              16384  0
rt2800mmio             20480  1 rt2800pci
crc32_pclmul           16384  0
rt2800lib              94208  2 rt2800pci,rt2800mmio
snd_hda_intel          36864  5
aesni_intel           167936  0
rt2x00pci              16384  1 rt2800pci
snd_hda_codec         135168  4 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_codec_generic,snd_hda_intel
rt2x00mmio             16384  2 rt2800pci,rt2800mmio
rt2x00lib              57344  5 rt2x00pci,rt2800lib,rt2800pci,rt2800mmio,rt2x00mmio
snd_hda_core           73728  5 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
snd_hwdep              16384  1 snd_hda_codec
mac80211              737280  3 rt2x00lib,rt2x00pci,rt2800lib
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
cryptd                 20480  2 aesni_intel,ablk_helper
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
uvcvideo               90112  0
input_leds             16384  0
videobuf2_vmalloc      16384  1 uvcvideo
joydev                 20480  0
videobuf2_memops       16384  1 videobuf2_vmalloc
serio_raw              16384  0
videobuf2_v4l2         28672  1 uvcvideo
snd_seq_midi           16384  0
videobuf2_core         36864  2 uvcvideo,videobuf2_v4l2
snd_seq_midi_event     16384  1 snd_seq_midi
v4l2_common            16384  1 videobuf2_v4l2
videodev              176128  4 uvcvideo,v4l2_common,videobuf2_core,videobuf2_v4l2
media                  24576  2 uvcvideo,videodev
snd_rawmidi            32768  1 snd_seq_midi
rtsx_pci_ms            20480  0
cfg80211              565248  2 mac80211,rt2x00lib
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
memstick               20480  1 rtsx_pci_ms
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
eeprom_93cx6           16384  1 rt2800pci
lpc_ich                24576  0
snd                    81920  21 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
crc_ccitt              16384  1 rt2800lib
mei_me                 36864  0
mei                    98304  1 mei_me
soundcore              16384  1 snd
hp_accel               28672  0
ie31200_edac           16384  0
lis3lv02d              20480  1 hp_accel
shpchp                 36864  0
edac_core              53248  1 ie31200_edac
input_polldev          16384  1 lis3lv02d
hp_wireless            16384  0
soc_button_array       16384  0
intel_smartconnect     16384  0
mac_hid                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  2 hid_generic,usbhid
rtsx_pci_sdmmc         24576  0
nouveau              1495040  1
i915                 1208320  4
mxm_wmi                16384  1 nouveau
ttm                    94208  1 nouveau
i2c_algo_bit           16384  2 i915,nouveau
ahci                   36864  4
drm_kms_helper        147456  2 i915,nouveau
psmouse               126976  0
r8169                  81920  0
libahci                32768  1 ahci
mii                    16384  1 r8169
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   364544  8 ttm,i915,drm_kms_helper,nouveau
rtsx_pci               53248  2 rtsx_pci_ms,rtsx_pci_sdmmc
video                  40960  2 i915,nouveau
wmi                    20480  3 hp_wmi,mxm_wmi,nouveau
fjes                   28672  0


```

```
buoncri@buoncri-HP-ENVY:~$ dmesg | grep rt2
[    3.008123] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3290, rev 0015 detected
[    3.011890] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 3290 detected
[    3.166747] rt2800pci 0000:07:00.0 wlo1: renamed from wlan0
[    4.294404] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt3290.bin'
[    4.298055] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.37
[    5.932223] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[    7.532140] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[    7.532145] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[    9.240054] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   10.843972] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   10.843977] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   12.463863] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   14.063807] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   14.063813] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   25.663144] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   27.267061] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   27.267066] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   28.883057] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   30.486974] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   30.486979] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   42.658297] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   44.258225] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   44.258229] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   45.874140] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   47.474059] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   47.474064] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   59.661439] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   61.261408] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   61.261413] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   62.881325] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   64.485244] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   64.485249] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   76.664329] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   78.264211] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   78.264216] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   79.880097] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   81.483920] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   81.483924] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   93.659225] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   95.259133] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   95.259138] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   96.875013] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   98.474885] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   98.474890] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
```
seems so...

---

### Post by chili555 on 2016-08-16
I am grasping at straws in the wind here: [https://forums.opensuse.org/showthread.php/506888-OpenSUSE-13-1-wireless-problem-with-firmware-Ralink-RT3290-(kernel-4-0-0-1-1-g49e42b3-x86_64)](https://forums.opensuse.org/showthread.php/506888-OpenSUSE-13-1-wireless-problem-with-firmware-Ralink-RT3290-(kernel-4-0-0-1-1-g49e42b3-x86_64))

> While I was waiting for answers I did recall reading someone in these forums suggesting to remove 802.11n from the router . 

So I tested that today it it worked. 

That is, I set the router to broadcast only 802.11g. ( Previously 802.11n was among the protocols it broadcasted.) 

And it WORKED. wlan has been on since this morning with no glitch.Would you please try, then reboot the router and the computer.

---

### Post by buoncri on 2016-08-17
YES!! I removed 802.11n, leaving both "b" and "g" on, and it works!! 
thank you very much!!

---

### Post by chili555 on 2016-08-17
Awesome! I am confident this will help more than a few searchers. Please use thread tools at the top to mark Solved.

---

### Post by msjr65 on 2017-04-23
Hello again,

I ran across this tread researching because I also have the exact same issue (Ubuntu 16.04) 
> [COLOR=#000000]*"rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068] "*[/COLOR][COLOR=#000000][I]
**but only when I reboot.** After normal shutdown and booting up the computer everything is working fine:

[/I][/COLOR]```
sudo dmesg | grep rt2
[   10.060907] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3090, rev 3213 detected
[   10.064386] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 0005 detected
[   10.155058] rt2800pci 0000:05:00.0 wlp5s0: renamed from wlan0
[   12.279917] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2860.bin'
[   12.286489] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.34

```

Any ideas?

Thanks a lot in advance for any hint :)

---

### Post by jeremy31 on 2017-04-23
I would try
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Reboot and see if the issue persists, if it does disable wireless N on the wifi router as chili555 suggested

---

