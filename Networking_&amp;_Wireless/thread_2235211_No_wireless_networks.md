---
title: "No wireless networks"
date: 2014-07-19
forum: Networking &amp; Wireless
---

### Post by deviant085 on 2014-07-19
I can no longer see any wireless networks. One day it was working, the next nothing. 

Below is some info. 
```

$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: AR9485 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 01
       serial: 6c:71:d9:3b:68:07
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.13.0-32-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:f7c00000-f7c7ffff memory:f7c80000-f7c8ffff
  *-network
       description: Ethernet interface
       physical id: 1
       bus info: usb@4:1.4
       logical name: eth0
       serial: 74:d0:2b:0d:e3:84
       size: 1Gbit/s
       capacity: 1Gbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ax88179_178a duplex=full ip=10.13.38.12 link=yes multicast=yes port=MII speed=1Gbit/s

$ lspci -nn | grep 0280
01:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)

$ lsmod
Module                  Size  Used by
snd_hda_codec_hdmi     46254  1 
snd_hda_codec_realtek    61438  1 
hid_sensor_accel_3d    13221  0 
hid_sensor_gyro_3d     13209  0 
hid_sensor_magn_3d     13209  0 
hid_sensor_trigger     12916  3 hid_sensor_gyro_3d,hid_sensor_accel_3d,hid_sensor_magn_3d
industrialio_triggered_buffer    12882  3 hid_sensor_gyro_3d,hid_sensor_accel_3d,hid_sensor_magn_3d
kfifo_buf              13379  1 industrialio_triggered_buffer
industrialio           54069  6 hid_sensor_trigger,hid_sensor_gyro_3d,industrialio_triggered_buffer,hid_sensor_accel_3d,kfifo_buf,hid_sensor_magn_3d
hid_sensor_iio_common    13755  3 hid_sensor_gyro_3d,hid_sensor_accel_3d,hid_sensor_magn_3d
hid_generic            12548  0 
hid_multitouch         17407  0 
hid_sensor_hub         19536  5 hid_sensor_trigger,hid_sensor_gyro_3d,hid_sensor_accel_3d,hid_sensor_magn_3d,hid_sensor_iio_common
asus_nb_wmi            16990  0 
asus_wmi               24191  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
bnep                   19624  2 
rfcomm                 69160  8 
arc4                   12608  2 
ath9k                 164164  0 
intel_rapl             18773  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm_intel             143060  0 
kvm                   451511  1 kvm_intel
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_hda_intel          52355  3 
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
mac80211              630653  1 ath9k
joydev                 17381  0 
serio_raw              13462  0 
ath3k                  13318  0 
btusb                  32412  0 
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
bluetooth             391196  23 bnep,ath3k,btusb,rfcomm
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
ax88179_178a           22455  0 
usbnet                 43913  1 ax88179_178a
usb_storage            62209  1 
mii                    13934  2 usbnet,ax88179_178a
lpc_ich                21080  0 
cfg80211              484040  3 ath,ath9k,mac80211
usbhid                 52570  0 
hid                   106148  4 hid_multitouch,hid_generic,hid_sensor_hub,usbhid
nls_iso8859_1          12713  1 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
wmi                    19177  1 asus_wmi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
parport_pc             32701  0 
snd                    69238  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
i915                  783805  3 
ppdev                  17671  0 
video                  19476  2 i915,asus_wmi
drm_kms_helper         53081  1 i915
mei_me                 18627  0 
drm                   303102  4 i915,drm_kms_helper
mac_hid                13205  0 
soundcore              12680  1 snd
mei                    82276  1 mei_me
i2c_algo_bit           13413  1 i915
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
psmouse               106678  0 
ahci                   25819  3 
libahci                32560  1 ahci

$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


```

---

### Post by wildmanne39 on 2014-07-19
*Thread moved to **Networking & Wireless**.*

---

### Post by varunendra on 2014-07-20
Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

