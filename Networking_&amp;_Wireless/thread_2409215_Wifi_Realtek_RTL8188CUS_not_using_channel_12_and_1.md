---
title: "Wifi Realtek RTL8188CUS not using channel 12 and 13"
date: 2018-12-29
forum: Networking &amp; Wireless
---

### Post by Andre12345 on 2018-12-29
I have a TL-WN722N V3.0 usb dongle (rtl8192cu) and it's only using channels 1-11, but I have one access point using channel 13.
How can I convince the WiFi donge to use channel 12 and 13?

I have another WiFi dongle EW-7811Un (Realtek RTL8188CUS) capable of using channel 12 and 13, but this has a very bad or no signal from the WiFi router.

---

### Post by jeremy31 on 2018-12-29
Moved to networking
See the wireless script link in my signature and post results

---

### Post by him610 on 2018-12-29
Allowable channels in North America are 1-11 in addition 12 allowed in Canada only. Channels 13 & 14 not allowed in North America.

---

### Post by Andre12345 on 2018-12-30
Here is the script output: [https://paste.ubuntu.com/p/BVn8fDZ8MY/](https://paste.ubuntu.com/p/BVn8fDZ8MY/)
In my country channels 12 and 13 are allowed, channel 14 is not allowed.

---

### Post by praseodym on 2018-12-30
First, set the country code, second, blacklist the outdated driver, it loads two:
```
echo "blacklist rtl8192cu" | sudo tee /etc/modprobe.d/blacklist-rtl8192cu.conf
sudo sed -i "s/REGDOMAIN=/REGDOMAIN=NL/g" /etc/default/crda 
```
Reboot and show
```
lsmod
iwlist chan
dmesg | grep country
```

---

### Post by Andre12345 on 2018-12-30
lsmod:
```

Module                  Size  Used by
pci_stub               16384  1
vboxpci                24576  0
vboxnetadp             28672  0
vboxnetflt             28672  0
vboxdrv               471040  3 vboxpci,vboxnetadp,vboxnetflt
arc4                   16384  2
binfmt_misc            20480  1
ip6t_REJECT            16384  1
nf_reject_ipv6         16384  1 ip6t_REJECT
nf_log_ipv6            16384  5
snd_hda_codec_hdmi     49152  1
xt_hl                  16384  22
ip6t_rt                16384  3
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
hid_plantronics        16384  0
uvcvideo               86016  0
rtl8xxxu              122880  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
r8188eu               421888  0
videobuf2_v4l2         24576  1 uvcvideo
mac80211              778240  1 rtl8xxxu
videobuf2_core         40960  2 videobuf2_v4l2,uvcvideo
kvm_intel             212992  0
kvm                   598016  1 kvm_intel
videodev              184320  3 videobuf2_core,videobuf2_v4l2,uvcvideo
snd_hda_codec_realtek   106496  1
snd_usb_audio         196608  6
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
snd_usbmidi_lib        32768  1 snd_usb_audio
media                  40960  2 videodev,uvcvideo
joydev                 24576  0
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
snd_hda_intel          40960  10
cfg80211              622592  2 mac80211,r8188eu
snd_hda_codec         126976  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
ghash_clmulni_intel    16384  0
snd_hda_core           81920  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
snd_hwdep              20480  2 snd_usb_audio,snd_hda_codec
pcbc                   16384  0
snd_pcm                98304  5 snd_hda_codec_hdmi,snd_hda_intel,snd_usb_audio,snd_hda_codec,snd_hda_core
aesni_intel           188416  0
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
aes_x86_64             20480  1 aesni_intel
nf_conntrack_ipv6      20480  8
nf_defrag_ipv6         36864  1 nf_conntrack_ipv6
crypto_simd            16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
ipt_REJECT             16384  1
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
nf_reject_ipv4         16384  1 ipt_REJECT
snd_rawmidi            32768  2 snd_seq_midi,snd_usbmidi_lib
intel_cstate           20480  0
nf_log_ipv4            16384  5
nf_log_common          16384  2 nf_log_ipv4,nf_log_ipv6
snd_seq                65536  2 snd_seq_midi,snd_seq_midi_event
intel_rapl_perf        16384  0
xt_LOG                 16384  10
input_leds             16384  0
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
serio_raw              16384  0
snd_timer              32768  2 snd_seq,snd_pcm
xt_limit               16384  13
snd                     81920  45  snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_usb_audio,snd_usbmidi_lib,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi
xt_tcpudp              16384  18
mei_me                 40960  0
xt_addrtype            16384  4
lpc_ich                24576  0
soundcore              16384  1 snd
mei                    90112  1 mei_me
nvidia_uvm            757760  0
intel_smartconnect     16384  0
ie31200_edac           16384  0
shpchp                 36864  0
mac_hid                16384  0
nf_conntrack_ipv4      16384  8
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
xt_conntrack           16384  16
sch_fq_codel           20480  10
ip6table_filter        16384  1
ip6_tables             28672  1 ip6table_filter
nf_conntrack_netbios_ns    16384  0
nf_conntrack_broadcast    16384  1 nf_conntrack_netbios_ns
nf_nat_ftp             16384  0
nf_nat                 32768  1 nf_nat_ftp
nf_conntrack_ftp       20480  1 nf_nat_ftp
nf_conntrack           131072  8  xt_conntrack,nf_conntrack_ipv6,nf_conntrack_ipv4,nf_nat,nf_nat_ftp,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_conntrack_ftp
libcrc32c              16384  2 nf_conntrack,nf_nat
parport_pc             36864  1
ppdev                  20480  0
iptable_filter         16384  1
lp                     20480  0
parport                49152  3 parport_pc,lp,ppdev
ip_tables              28672  1 iptable_filter
x_tables                40960  13  ip6table_filter,xt_conntrack,iptable_filter,xt_LOG,xt_tcpudp,xt_addrtype,ip6t_rt,ip6_tables,ipt_REJECT,ip_tables,xt_limit,xt_hl,ip6t_REJECT
autofs4                40960  2
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  3 usbhid,hid_generic,hid_plantronics
nvidia_drm             40960  2
nvidia_modeset       1110016  11 nvidia_drm
nvidia              14360576  446 nvidia_uvm,nvidia_modeset
drm_kms_helper        172032  1 nvidia_drm
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
i2c_i801               28672  0
ahci                   36864  3
drm                   401408  5 drm_kms_helper,nvidia_drm
libahci                32768  1 ahci
r8169                  86016  0
ipmi_devintf           20480  0
mii                    16384  1 r8169
ipmi_msghandler        53248  2 ipmi_devintf,nvidia
video                  45056  0

```

iwlist chan
```

wlx<IF from MAC [IF2]>  11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Current Frequency:2.447 GHz (Channel 8)

enp4s0    no frequency information.

lo        no frequency information.

wlx<IF from MAC [IF3]>  13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz

```

dmesg | grep country
Gives nothing

---

### Post by praseodym on 2018-12-30
Ok, that was for the rtl8188cus. The other one uses r8188eu. Lets see
```

sudo apt-get install iw
iw reg get
sudo iw reg set NL
iw reg get
```

Try updating the drivers otherwise:

```
sudo apt-get install git build-essential dkms linux-headers-$(uname -r)
git clone -b extended https://github.com/lwfinger/rtlwifi_new.git
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6
sudo cp /usr/src/rtlwifi-new-0.6/firmware/rtlwifi/* /lib/firmware/rtlwifi/ 
```
Reboot

---

### Post by Andre12345 on 2018-12-31
The EW-7811Un (Realtek RTL8188CUS) is working correct, the TL-WN722N V3.0  (rtl8192cu) is only using channels 1-11. In the subject this is not correct.

I did code, the country code is all ready correct. The driver update did nothing.

lsmod:
```

Module                  Size  Used by
pci_stub               16384  1
vboxpci                24576  0
vboxnetadp             28672  0
vboxnetflt             28672  0
vboxdrv               471040  3 vboxpci,vboxnetadp,vboxnetflt
arc4                   16384  2
binfmt_misc            20480  1
ip6t_REJECT            16384  1
nf_reject_ipv6         16384  1 ip6t_REJECT
nf_log_ipv6            16384  5
xt_hl                  16384  22
ip6t_rt                16384  3
snd_hda_codec_hdmi     49152  1
intel_rapl             20480  0
nf_conntrack_ipv6      20480  8
nf_defrag_ipv6         36864  1 nf_conntrack_ipv6
ipt_REJECT             16384  1
nf_reject_ipv4         16384  1 ipt_REJECT
nf_log_ipv4            16384  5
nf_log_common          16384  2 nf_log_ipv4,nf_log_ipv6
xt_LOG                 16384  10
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
kvm_intel             212992  0
xt_limit               16384  13
kvm                   598016  1 kvm_intel
xt_tcpudp              16384  18
xt_addrtype            16384  4
irqbypass              16384  1 kvm
rtl8xxxu              122880  0
crct10dif_pclmul       16384  0
uvcvideo               86016  0
joydev                 24576  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
mac80211              778240  1 rtl8xxxu
videobuf2_v4l2         24576  1 uvcvideo
videobuf2_core         40960  2 videobuf2_v4l2,uvcvideo
pcbc                   16384  0
videodev              184320  3 videobuf2_core,videobuf2_v4l2,uvcvideo
snd_usb_audio         196608  6
snd_usbmidi_lib        32768  1 snd_usb_audio
media                  40960  2 videodev,uvcvideo
snd_hda_codec_realtek   106496  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
r8188eu               421888  0
snd_hda_intel          40960  10
cfg80211              622592  2 mac80211,r8188eu
aesni_intel           188416  0
snd_hda_codec         126976  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
snd_hda_core           81920  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
snd_hwdep              20480  2 snd_usb_audio,snd_hda_codec
aes_x86_64             20480  1 aesni_intel
crypto_simd            16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
snd_pcm                98304  5 snd_hda_codec_hdmi,snd_hda_intel,snd_usb_audio,snd_hda_codec,snd_hda_core
intel_cstate           20480  0
snd_seq_midi           16384  0
intel_rapl_perf        16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  2 snd_seq_midi,snd_usbmidi_lib
input_leds             16384  0
serio_raw              16384  0
snd_seq                65536  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
snd_timer              32768  2 snd_seq,snd_pcm
nvidia_uvm            757760  0
lpc_ich                24576  0
snd                    81920  45 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_usb_audio,snd_usbmidi_lib,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi
mei_me                 40960  0
mei                    90112  1 mei_me
soundcore              16384  1 snd
shpchp                 36864  0
ie31200_edac           16384  0
mac_hid                16384  0
intel_smartconnect     16384  0
nf_conntrack_ipv4      16384  8
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
xt_conntrack           16384  16
ip6table_filter        16384  1
ip6_tables             28672  1 ip6table_filter
sch_fq_codel           20480  10
nf_conntrack_netbios_ns    16384  0
nf_conntrack_broadcast    16384  1 nf_conntrack_netbios_ns
nf_nat_ftp             16384  0
nf_nat                 32768  1 nf_nat_ftp
nf_conntrack_ftp       20480  1 nf_nat_ftp
nf_conntrack          131072  8 xt_conntrack,nf_conntrack_ipv6,nf_conntrack_ipv4,nf_nat,nf_nat_ftp,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_conntrack_ftp
libcrc32c              16384  2 nf_conntrack,nf_nat
parport_pc             36864  1
iptable_filter         16384  1
ppdev                  20480  0
lp                     20480  0
parport                49152  3 parport_pc,lp,ppdev
ip_tables              28672  1 iptable_filter
x_tables               40960  13 ip6table_filter,xt_conntrack,iptable_filter,xt_LOG,xt_tcpudp,xt_addrtype,ip6t_rt,ip6_tables,ipt_REJECT,ip_tables,xt_limit,xt_hl,ip6t_REJECT
autofs4                40960  2
hid_plantronics        16384  0
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  3 usbhid,hid_generic,hid_plantronics
nvidia_drm             40960  2
nvidia_modeset       1110016  15 nvidia_drm
nvidia              14360576  610 nvidia_uvm,nvidia_modeset
drm_kms_helper        172032  1 nvidia_drm
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
i2c_i801               28672  0
drm                   401408  5 drm_kms_helper,nvidia_drm
ahci                   36864  3
r8169                  86016  0
ipmi_devintf           20480  0
libahci                32768  1 ahci
mii                    16384  1 r8169
ipmi_msghandler        53248  2 ipmi_devintf,nvidia
video                  45056  0

```

The others didn't change, still using only channels 1-11 :(

---

### Post by praseodym on 2018-12-31
Please show for each stick separately
```

lsusb
lsmod
iwlist chan
```

to distinguish them 8188cus and 8192cus are the same driver. The other one is r8188eu!

---

### Post by jeremy31 on 2018-12-31
I would try blacklisting the rtl8192cu driver in case it conflicts with rtl8xxxu

---

### Post by praseodym on 2018-12-31
We already did ;-)

---

### Post by jeremy31 on 2018-12-31
There must be a channel limit in kernel source or in the firmware as both modules use the same firmware

---

### Post by Andre12345 on 2019-01-01
Here is the info for the EW-7811Un (Realtek RTL8188CUS):
```

Bus 002 Device 004: ID 047f:c024 Plantronics, Inc. 
Bus 002 Device 003: ID 0471:0331 Philips (or NXP) SPC 1300NC PC Camera
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 1532:0043 Razer USA, Ltd 
Bus 001 Device 004: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 003: ID 7392:7811 Edimax Technology Co., Ltd EW-7811Un 802.11n Wireless Adapter [Realtek RTL8188CUS]
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
```

Module                  Size  Used by
snd_seq_dummy          16384  0
ccm                    20480  0
pci_stub               16384  1
vboxpci                24576  0
vboxnetadp             28672  0
vboxnetflt             28672  0
vboxdrv               471040  3 vboxpci,vboxnetadp,vboxnetflt
arc4                   16384  2
binfmt_misc            20480  1
ip6t_REJECT            16384  1
nf_reject_ipv6         16384  1 ip6t_REJECT
nf_log_ipv6            16384  5
xt_hl                  16384  22
ip6t_rt                16384  3
snd_hda_codec_hdmi     49152  1
intel_rapl             20480  0
nf_conntrack_ipv6      20480  8
nf_defrag_ipv6         36864  1 nf_conntrack_ipv6
ipt_REJECT             16384  1
nf_reject_ipv4         16384  1 ipt_REJECT
nf_log_ipv4            16384  5
nf_log_common          16384  2 nf_log_ipv4,nf_log_ipv6
xt_LOG                 16384  10
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
kvm_intel             212992  0
xt_limit               16384  13
kvm                   598016  1 kvm_intel
xt_tcpudp              16384  18
xt_addrtype            16384  4
irqbypass              16384  1 kvm
rtl8xxxu              122880  0
crct10dif_pclmul       16384  0
uvcvideo               86016  0
joydev                 24576  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
mac80211              778240  1 rtl8xxxu
videobuf2_v4l2         24576  1 uvcvideo
videobuf2_core         40960  2 videobuf2_v4l2,uvcvideo
pcbc                   16384  0
videodev              184320  3 videobuf2_core,videobuf2_v4l2,uvcvideo
snd_usb_audio         196608  6
snd_usbmidi_lib        32768  1 snd_usb_audio
media                  40960  2 videodev,uvcvideo
snd_hda_codec_realtek   106496  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
r8188eu               421888  0
snd_hda_intel          40960  10
cfg80211              622592  2 mac80211,r8188eu
aesni_intel           188416  0
snd_hda_codec         126976  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
snd_hda_core           81920  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
snd_hwdep              20480  2 snd_usb_audio,snd_hda_codec
aes_x86_64             20480  1 aesni_intel
crypto_simd            16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
snd_pcm                98304  5 snd_hda_codec_hdmi,snd_hda_intel,snd_usb_audio,snd_hda_codec,snd_hda_core
intel_cstate           20480  0
snd_seq_midi           16384  0
intel_rapl_perf        16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  2 snd_seq_midi,snd_usbmidi_lib
input_leds             16384  0
serio_raw              16384  0
snd_seq                65536  3 snd_seq_midi,snd_seq_midi_event,snd_seq_dummy
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
snd_timer              32768  2 snd_seq,snd_pcm
nvidia_uvm            757760  0
lpc_ich                24576  0
snd                     81920  45  snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_usb_audio,snd_usbmidi_lib,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi
mei_me                 40960  0
mei                    90112  1 mei_me
soundcore              16384  1 snd
shpchp                 36864  0
ie31200_edac           16384  0
mac_hid                16384  0
intel_smartconnect     16384  0
nf_conntrack_ipv4      16384  8
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
xt_conntrack           16384  16
ip6table_filter        16384  1
ip6_tables             28672  1 ip6table_filter
sch_fq_codel           20480  6
nf_conntrack_netbios_ns    16384  0
nf_conntrack_broadcast    16384  1 nf_conntrack_netbios_ns
nf_nat_ftp             16384  0
nf_nat                 32768  1 nf_nat_ftp
nf_conntrack_ftp       20480  1 nf_nat_ftp
nf_conntrack           131072  8  xt_conntrack,nf_conntrack_ipv6,nf_conntrack_ipv4,nf_nat,nf_nat_ftp,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_conntrack_ftp
libcrc32c              16384  2 nf_conntrack,nf_nat
parport_pc             36864  1
iptable_filter         16384  1
ppdev                  20480  0
lp                     20480  0
parport                49152  3 parport_pc,lp,ppdev
ip_tables              28672  1 iptable_filter
x_tables                40960  13  ip6table_filter,xt_conntrack,iptable_filter,xt_LOG,xt_tcpudp,xt_addrtype,ip6t_rt,ip6_tables,ipt_REJECT,ip_tables,xt_limit,xt_hl,ip6t_REJECT
autofs4                40960  2
hid_plantronics        16384  0
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  3 usbhid,hid_generic,hid_plantronics
nvidia_drm             40960  2
nvidia_modeset       1110016  15 nvidia_drm
nvidia              14360576  616 nvidia_uvm,nvidia_modeset
drm_kms_helper        172032  1 nvidia_drm
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
i2c_i801               28672  0
drm                   401408  5 drm_kms_helper,nvidia_drm
ahci                   36864  3
r8169                  86016  0
ipmi_devintf           20480  0
libahci                32768  1 ahci
mii                    16384  1 r8169
ipmi_msghandler        53248  2 ipmi_devintf,nvidia
video                  45056  0

```
```

wlx<IF from MAC [IF3]>  13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
lo        no frequency information.

enp4s0    no frequency information.

```

Here is the info for the TL-WN722N V3.0  (rtl8192cu)
```

Bus 002 Device 004: ID 047f:c024 Plantronics, Inc. 
Bus 002 Device 003: ID 0471:0331 Philips (or NXP) SPC 1300NC PC Camera
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 1532:0043 Razer USA, Ltd 
Bus 001 Device 004: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 2357:010c  
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
```

Module                  Size  Used by
snd_seq_dummy          16384  0
ccm                    20480  0
pci_stub               16384  1
vboxpci                24576  0
vboxnetadp             28672  0
vboxnetflt             28672  0
vboxdrv               471040  3 vboxpci,vboxnetadp,vboxnetflt
arc4                   16384  0
binfmt_misc            20480  1
ip6t_REJECT            16384  1
nf_reject_ipv6         16384  1 ip6t_REJECT
nf_log_ipv6            16384  5
xt_hl                  16384  22
ip6t_rt                16384  3
snd_hda_codec_hdmi     49152  1
intel_rapl             20480  0
nf_conntrack_ipv6      20480  8
nf_defrag_ipv6         36864  1 nf_conntrack_ipv6
ipt_REJECT             16384  1
nf_reject_ipv4         16384  1 ipt_REJECT
nf_log_ipv4            16384  5
nf_log_common          16384  2 nf_log_ipv4,nf_log_ipv6
xt_LOG                 16384  10
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
kvm_intel             212992  0
xt_limit               16384  13
kvm                   598016  1 kvm_intel
xt_tcpudp              16384  18
xt_addrtype            16384  4
irqbypass              16384  1 kvm
rtl8xxxu              122880  0
crct10dif_pclmul       16384  0
uvcvideo               86016  0
joydev                 24576  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
mac80211              778240  1 rtl8xxxu
videobuf2_v4l2         24576  1 uvcvideo
videobuf2_core         40960  2 videobuf2_v4l2,uvcvideo
pcbc                   16384  0
videodev              184320  3 videobuf2_core,videobuf2_v4l2,uvcvideo
snd_usb_audio         196608  6
snd_usbmidi_lib        32768  1 snd_usb_audio
media                  40960  2 videodev,uvcvideo
snd_hda_codec_realtek   106496  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
r8188eu               421888  0
snd_hda_intel          40960  10
cfg80211              622592  2 mac80211,r8188eu
aesni_intel           188416  0
snd_hda_codec         126976  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
snd_hda_core           81920  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
snd_hwdep              20480  2 snd_usb_audio,snd_hda_codec
aes_x86_64             20480  1 aesni_intel
crypto_simd            16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
snd_pcm                98304  5 snd_hda_codec_hdmi,snd_hda_intel,snd_usb_audio,snd_hda_codec,snd_hda_core
intel_cstate           20480  0
snd_seq_midi           16384  0
intel_rapl_perf        16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  2 snd_seq_midi,snd_usbmidi_lib
input_leds             16384  0
serio_raw              16384  0
snd_seq                65536  3 snd_seq_midi,snd_seq_midi_event,snd_seq_dummy
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
snd_timer              32768  2 snd_seq,snd_pcm
nvidia_uvm            757760  0
lpc_ich                24576  0
snd                     81920  45  snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_usb_audio,snd_usbmidi_lib,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi
mei_me                 40960  0
mei                    90112  1 mei_me
soundcore              16384  1 snd
shpchp                 36864  0
ie31200_edac           16384  0
mac_hid                16384  0
intel_smartconnect     16384  0
nf_conntrack_ipv4      16384  8
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
xt_conntrack           16384  16
ip6table_filter        16384  1
ip6_tables             28672  1 ip6table_filter
sch_fq_codel           20480  6
nf_conntrack_netbios_ns    16384  0
nf_conntrack_broadcast    16384  1 nf_conntrack_netbios_ns
nf_nat_ftp             16384  0
nf_nat                 32768  1 nf_nat_ftp
nf_conntrack_ftp       20480  1 nf_nat_ftp
nf_conntrack           131072  8  xt_conntrack,nf_conntrack_ipv6,nf_conntrack_ipv4,nf_nat,nf_nat_ftp,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_conntrack_ftp
libcrc32c              16384  2 nf_conntrack,nf_nat
parport_pc             36864  1
iptable_filter         16384  1
ppdev                  20480  0
lp                     20480  0
parport                49152  3 parport_pc,lp,ppdev
ip_tables              28672  1 iptable_filter
x_tables                40960  13  ip6table_filter,xt_conntrack,iptable_filter,xt_LOG,xt_tcpudp,xt_addrtype,ip6t_rt,ip6_tables,ipt_REJECT,ip_tables,xt_limit,xt_hl,ip6t_REJECT
autofs4                40960  2
hid_plantronics        16384  0
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  3 usbhid,hid_generic,hid_plantronics
nvidia_drm             40960  2
nvidia_modeset       1110016  15 nvidia_drm
nvidia              14360576  616 nvidia_uvm,nvidia_modeset
drm_kms_helper        172032  1 nvidia_drm
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
i2c_i801               28672  0
drm                   401408  5 drm_kms_helper,nvidia_drm
ahci                   36864  3
r8169                  86016  0
ipmi_devintf           20480  0
libahci                32768  1 ahci
mii                    16384  1 r8169
ipmi_msghandler        53248  2 ipmi_devintf,nvidia
video                  45056  0

```
```

lo        no frequency information.

enp4s0    no frequency information.

wlx<IF from MAC [IF2]>  11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Current Frequency:2.447 GHz (Channel 8)

```

---

### Post by praseodym on 2019-01-01
```
modinfo r8188eu | grep firm
```

gives no output, while

```
modinfo rtl8xxxu | grep firm
firmware:       rtlwifi/rtl8192cufw_TMSC.bin
firmware:       rtlwifi/rtl8192cufw_B.bin
firmware:       rtlwifi/rtl8192cufw_A.bin
firmware:       rtlwifi/rtl8723aufw_B_NoBT.bin
firmware:       rtlwifi/rtl8723aufw_B.bin
firmware:       rtlwifi/rtl8723aufw_A.bin
```
showing some. "linux-firmware" from 18.10 shows some files, however, if the driver is not referring to it, it makes no sense. You can uninstall the drivers via
```

sudo dkms remove rtlwifi-new/0.6 --all
sudo rm -r /usr/src/rtlwifi-new-0.6 
```
and reboot.

Maybe this device contains a fixed firmware which cannot be changed?! Try this one from Larry Finger instead

```
git clone git://github.com/lwfinger/rtl8188eu
sudo dkms add ./rtl8188eu
sudo dkms build 8188eu/1.0
sudo dkms install 8188eu/1.0
```
Here, it has a FW file. Reboot and show
```
dmesg | grep 8188
lsmod
```

---

### Post by Andre12345 on 2019-01-01
iwlist chan shows no changes. One is using channels 1-11, and the other 1-13.

```

[    3.105648] r8188eu: module is from the staging directory, the quality is unknown, you have been warned.
[    3.117901] Chip Version Info: CHIP_8188E_Normal_Chip_TSMC_D_CUT_1T1R_RomVer(0)
[    3.145118] usbcore: registered new interface driver r8188eu
[    3.149707] Error: Driver 'r8188eu' is already registered, aborting...
[    3.441469] r8188eu 3-1:1.0 wlx503eaa6f7dfd: renamed from wlan0
[    3.447111] usb 1-1.4: RTL8188CU rev A (TSMC) 1T1R, TX queues 2, WiFi=1, BT=0, GPS=0, HI PA=0
[    3.447112] usb 1-1.4: RTL8188CU MAC: 74:da:38:f0:3c:bf
[    9.300670] R8188EU: assoc success

```

```

Module                  Size  Used by
pci_stub               16384  1
vboxpci                24576  0
vboxnetadp             28672  0
vboxnetflt             28672  0
vboxdrv               471040  3 vboxpci,vboxnetadp,vboxnetflt
arc4                   16384  2
binfmt_misc            20480  1
ip6t_REJECT            16384  1
nf_reject_ipv6         16384  1 ip6t_REJECT
nf_log_ipv6            16384  5
xt_hl                  16384  22
ip6t_rt                16384  3
snd_hda_codec_hdmi     49152  1
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
kvm_intel             212992  0
kvm                   598016  1 kvm_intel
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
hid_plantronics        16384  0
pcbc                   16384  0
rtl8xxxu              122880  0
mac80211              778240  1 rtl8xxxu
r8188eu               421888  0
aesni_intel           188416  0
uvcvideo               86016  0
aes_x86_64             20480  1 aesni_intel
crypto_simd            16384  1 aesni_intel
cfg80211              622592  2 mac80211,r8188eu
joydev                 24576  0
glue_helper            16384  1 aesni_intel
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
nf_conntrack_ipv6      20480  8
nf_defrag_ipv6         36864  1 nf_conntrack_ipv6
videobuf2_core         40960  2 videobuf2_v4l2,uvcvideo
snd_usb_audio         196608  6
videodev              184320  3 videobuf2_core,videobuf2_v4l2,uvcvideo
snd_usbmidi_lib        32768  1 snd_usb_audio
snd_hda_codec_realtek   106496  1
media                  40960  2 videodev,uvcvideo
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
ipt_REJECT             16384  1
nf_reject_ipv4         16384  1 ipt_REJECT
snd_hda_intel          40960  10
snd_hda_codec         126976  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
nf_log_ipv4            16384  5
nf_log_common          16384  2 nf_log_ipv4,nf_log_ipv6
snd_hda_core           81920  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
snd_hwdep              20480  2 snd_usb_audio,snd_hda_codec
snd_pcm                98304  5 snd_hda_codec_hdmi,snd_hda_intel,snd_usb_audio,snd_hda_codec,snd_hda_core
snd_seq_midi           16384  0
intel_cstate           20480  0
snd_seq_midi_event     16384  1 snd_seq_midi
intel_rapl_perf        16384  0
snd_rawmidi            32768  2 snd_seq_midi,snd_usbmidi_lib
xt_LOG                 16384  10
input_leds             16384  0
serio_raw              16384  0
snd_seq                65536  2 snd_seq_midi,snd_seq_midi_event
xt_limit               16384  13
xt_tcpudp              16384  18
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
xt_addrtype            16384  4
snd_timer              32768  2 snd_seq,snd_pcm
snd                    81920  45 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_usb_audio,snd_usbmidi_lib,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi
mei_me                 40960  0
intel_smartconnect     16384  0
mei                    90112  1 mei_me
nvidia_uvm            757760  0
soundcore              16384  1 snd
lpc_ich                24576  0
mac_hid                16384  0
ie31200_edac           16384  0
shpchp                 36864  0
nf_conntrack_ipv4      16384  8
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
xt_conntrack           16384  16
sch_fq_codel           20480  10
ip6table_filter        16384  1
ip6_tables             28672  1 ip6table_filter
nf_conntrack_netbios_ns    16384  0
nf_conntrack_broadcast    16384  1 nf_conntrack_netbios_ns
nf_nat_ftp             16384  0
nf_nat                 32768  1 nf_nat_ftp
nf_conntrack_ftp       20480  1 nf_nat_ftp
nf_conntrack          131072  8 xt_conntrack,nf_conntrack_ipv6,nf_conntrack_ipv4,nf_nat,nf_nat_ftp,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_conntrack_ftp
libcrc32c              16384  2 nf_conntrack,nf_nat
parport_pc             36864  1
ppdev                  20480  0
iptable_filter         16384  1
lp                     20480  0
parport                49152  3 parport_pc,lp,ppdev
ip_tables              28672  1 iptable_filter
x_tables               40960  13 ip6table_filter,xt_conntrack,iptable_filter,xt_LOG,xt_tcpudp,xt_addrtype,ip6t_rt,ip6_tables,ipt_REJECT,ip_tables,xt_limit,xt_hl,ip6t_REJECT
autofs4                40960  2
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  3 usbhid,hid_generic,hid_plantronics
nvidia_drm             40960  2
nvidia_modeset       1110016  11 nvidia_drm
nvidia              14360576  449 nvidia_uvm,nvidia_modeset
drm_kms_helper        172032  1 nvidia_drm
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   401408  5 drm_kms_helper,nvidia_drm
r8169                  86016  0
mii                    16384  1 r8169
i2c_i801               28672  0
ahci                   36864  3
ipmi_devintf           20480  0
libahci                32768  1 ahci
ipmi_msghandler        53248  2 ipmi_devintf,nvidia
video                  45056  0

```

---

### Post by praseodym on 2019-01-01
Lets see
```

sudo modprobe -rfv r8188eu
sudo modprobe -v 8188eu #withour "r" if you updated the driver
```

---

### Post by Andre12345 on 2019-01-02
sudo modprobe -rfv r8188eu
```
rmmod r8188eu
```

sudo modprobe -v 8188eu
```
insmod /lib/modules/4.15.0-43-generic/updates/dkms/8188eu.ko
```

No reboot?

---

### Post by praseodym on 2019-01-02
No, now show

```
iwlist chan
dmesg | egrep 'firm|8188'
```

---

### Post by Andre12345 on 2019-01-02
The WiFi signal is much worse with the last change on both dongles.

```
wlx74da38f03cbf  13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
wlx503eaa6f7dfd  11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Current Frequency=2.447 GHz (Channel 8)

enp4s0    no frequency information.

lo        no frequency information.
```

```

[    0.030723] Spectre V2 : Enabling Restricted Speculation for firmware calls
[    3.105648] r8188eu: module is from the staging directory, the quality is unknown, you have been warned.
[    3.117901] Chip Version Info: CHIP_8188E_Normal_Chip_TSMC_D_CUT_1T1R_RomVer(0)
[    3.145118] usbcore: registered new interface driver r8188eu
[    3.149707] Error: Driver 'r8188eu' is already registered, aborting...
[    3.441469] r8188eu 3-1:1.0 wlx503eaa6f7dfd: renamed from wlan0
[    3.447111] usb 1-1.4: RTL8188CU rev A (TSMC) 1T1R, TX queues 2, WiFi=1, BT=0, GPS=0, HI PA=0
[    3.447112] usb 1-1.4: RTL8188CU MAC: 74:da:38:f0:3c:bf
[    3.447113] usb 1-1.4: rtl8xxxu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[    9.300670] R8188EU: assoc success
[ 4251.874682] R8188EU: indicate disassoc
[ 4252.876544] R8188EU: indicate disassoc
[ 4256.620741] usb 1-1.4: RTL8188CU rev A (TSMC) 1T1R, TX queues 2, WiFi=1, BT=0, GPS=0, HI PA=0
[ 4256.620742] usb 1-1.4: RTL8188CU MAC: 74:da:38:f0:3c:bf
[ 4256.620744] usb 1-1.4: rtl8xxxu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[ 4259.256668] R8188EU: assoc success
[ 4368.270196] usbcore: deregistering interface driver r8188eu
[ 4368.270356] R8188EU: indicate disassoc
[ 4398.809261] Chip Version Info: CHIP_8188E_Normal_Chip_TSMC_D_CUT_1T1R_RomVer(0)
[ 4398.831508] usbcore: registered new interface driver r8188eu
[ 4398.833212] r8188eu 3-1:1.0 wlx503eaa6f7dfd: renamed from wlan0
[ 4398.874180] R8188EU: Firmware Version 11, SubVersion 1, Signature 0x88e1
[ 4400.348835] R8188EU: INFO indicate disassoc
[ 4401.615062] R8188EU: INFO assoc success
[ 5671.202901] R8188EU: INFO indicate disassoc
[ 5672.200925] R8188EU: INFO indicate disassoc
[ 5672.318188] usb 1-1.4: disconnecting
[ 5675.923195] usb 1-1.4: RTL8188CU rev A (TSMC) 1T1R, TX queues 2, WiFi=1, BT=0, GPS=0, HI PA=0
[ 5675.923196] usb 1-1.4: RTL8188CU MAC: 74:da:38:f0:3c:bf
[ 5675.923198] usb 1-1.4: rtl8xxxu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[ 5677.236813] R8188EU: INFO indicate disassoc
[ 5678.545067] R8188EU: INFO assoc success

```

---

### Post by praseodym on 2019-01-02
Ok, that didnt work:
```

sudo dkms remove 8188eu/1.0 --all
sudo rm -r /usr/src/8188eu/1.0
```
Running out of ideas

---

### Post by Andre12345 on 2019-01-03
Ok, so it looks like a firmware problem in the WiFi dongle?
I will look if changing the channel on the other WiFi router will give a strong enough signal. Channel 13 is not in use by anyone so I picked this channel for best performance :)

Anyway thanks for the help, I'm still puzzled how you know all these commands. Searching don't show much solutions and tips and tricks to try.

---

### Post by praseodym on 2019-01-03
Maybe its not a "problem". If the FW is fixed it might be a chipset for the US or similar market restricting to 11 channels because of laws. Where did you buy it? Maybe you get it refunded

Edit: Lets try this one

```
echo 'options cfg80211 ieee80211_regdom="EU"' | sudo tee /etc/modprobe.d/cfg80211_options.conf
```
Reboot

---

### Post by Andre12345 on 2019-01-04
Very nice :)
One has 14 channels, the other still 11
```

wlx503eaa6f7dfd  11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Current Frequency:2.447 GHz (Channel 8)

wlx74da38f03cbf  14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
enp4s0    no frequency information.

lo        no frequency information.

```

---

### Post by praseodym on 2019-01-04
Ok, lets try
```

echo 'options cfg80211 ieee80211_regdom="NL"' | sudo tee /etc/modprobe.d/cfg80211_options.conf
```
Reboot and show
```
iwlist chan
dmesg | grep 80211
```

---

### Post by Andre12345 on 2019-01-05
I buy both WiFi dongles on amazon.

```

lo        no frequency information.

wlx74da38f03cbf  13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
wlx503eaa6f7dfd  11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Current Frequency=2.447 GHz (Channel 8)

enp4s0    no frequency information.

```

```

[    3.403592] cfg80211: Loading compiled-in X.509 certificates for regulatory database
[    3.418164] cfg80211: Loaded X.509 cert 'sforshee: 00b28ddf47aef9cea7'
[     3.438057] WARNING: CPU: 0 PID: 3 at  /build/linux-vxxS7y/linux-4.15.0/net/wireless/reg.c:894  regdb_fw_cb+0x47/0x110 [cfg80211]
[    3.438057] Modules linked in:  x86_pkg_temp_thermal(+) intel_powerclamp uvcvideo(+) videobuf2_vmalloc  mac80211 videobuf2_memops r8188eu(C+) coretemp videobuf2_v4l2  videobuf2_core videodev media cfg80211 kvm_intel kvm joydev irqbypass  crct10dif_pclmul snd_hda_codec_realtek snd_hda_codec_generic  crc32_pclmul ghash_clmulni_intel snd_hda_intel pcbc nf_conntrack_ipv6  nf_defrag_ipv6 snd_hda_codec ipt_REJECT aesni_intel nf_reject_ipv4  snd_hda_core snd_hwdep nf_log_ipv4 nf_log_common aes_x86_64 snd_seq_midi  crypto_simd glue_helper snd_seq_midi_event xt_LOG snd_rawmidi cryptd  snd_pcm snd_seq intel_cstate intel_rapl_perf xt_limit input_leds  xt_tcpudp serio_raw xt_addrtype snd_seq_device snd_timer nvidia_uvm(POE)  snd mei_me mei lpc_ich soundcore ie31200_edac mac_hid shpchp  intel_smartconnect nf_conntrack_ipv4
[    3.438102] RIP: 0010:regdb_fw_cb+0x47/0x110 [cfg80211]

```

---

### Post by praseodym on 2019-01-06
Ok, so they sold a stick to NL with US firmware and one with external FW and module options. Obviously, no chance to change that

---

### Post by Andre12345 on 2019-01-08
Ok, thanks for the effort. At least I learned some new commands.

---

