---
title: "Wifi trouble after sleep since 19.10 upgrade"
date: 2019-11-02
forum: Networking &amp; Wireless
---

### Post by linus2 on 2019-11-02
After I upgraded my 19.04 install to 19.10 at my hp zbook 14  g2 i7-5500U the wifi stops working after a sleeping for some time, (~30 sec sleep seems to not trigger this but 30min does). The network manager can still list the networks even though it seems a bit unstable, but cannot connect properly to a network until I reboot, logout-login does not help.

restarting nwm won't help:
```
&#10140;  ~ sudo service network-manager stop
&#10140;  ~ sudo service network-manager start
```


```
&#10140;  ~  lshw
 *-network
                description: Wireless interface
                product: Wireless 7265
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlo1
                version: 48
                serial: 34:02:86:8a:d5:b3
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=5.3.0-050300rc5-generic firmware=17.3216344376.0 ip=192.168.43.228 latency=0 link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:53 memory:c1100000-c1101fff

```

while working:
```
&#10140;  ~ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp0s25: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether 30:8d:99:15:ac:d5 brd ff:ff:ff:ff:ff:ff
3: wlo1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether 34:02:86:8a:d5:b3 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.20/24 brd 192.168.1.255 scope global dynamic noprefixroute wlo1
       valid_lft 43002sec preferred_lft 43002sec
    inet6 fe80::6386:28c4:87f7:c375/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever


```

while not working:
```
&#10140;  ~ ip a 
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp0s25: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether 30:8d:99:15:ac:d5 brd ff:ff:ff:ff:ff:ff
3: wlo1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether 34:02:86:8a:d5:b3 brd ff:ff:ff:ff:ff:ff

```

Anyone got any further hints or ways to troubleshoot/diagnose?

---

### Post by jeremy31 on 2019-11-02
Try ```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
sudo iwconfig wlo1 power off
```
Reboot
These commands should keep wifi power management off

---

### Post by linus2 on 2019-11-02
Thanks for your suggestion, used your commands and did not get any error codes, but same problem seems to persist, unfortunately.

---

### Post by wildmanne39 on 2019-11-02
*Thread moved to **Networking & Wireless a more appropriate sub-forum**.*

---

### Post by linus2 on 2019-11-17
Made some progress and thought this might help someone else.
After running lsmod (output below) it seems like a few drivers are related to the wlan and reloading all seems to solve the problem per session as a workaround:

```

&#10140;  ~ sudo rmmod iwlmvm   
&#10140;  ~ sudo rmmod iwlwifi 
&#10140;  ~ sudo rmmod mac80211 
&#10140;  ~ sudo rmmod cfg80211
&#10140;  ~ sudo modprobe iwlmvm
&#10140;  ~ sudo modprobe mac80211
&#10140;  ~ sudo modprobe iwlwifi
&#10140;  ~ sudo modprobe cfg80211
&#10140;  ~ sudo modprobe iwlmvm 
```

I'll try to narrow down the problem but as it occurs not until after about 30min of sleep its kind of tedious.
This is my lsmod output, maybe someone give me a hint:
```

&#10140;  ~ lsmod 
Module                  Size  Used by
rfcomm                 81920  4
nf_tables             135168  0
nfnetlink              16384  1 nf_tables
ccm                    20480  6
cmac                   16384  1
bnep                   24576  2
uvcvideo               98304  0
videobuf2_vmalloc      20480  1 uvcvideo
videobuf2_memops       20480  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
videobuf2_common       53248  2 videobuf2_v4l2,uvcvideo
btusb                  57344  0
btrtl                  20480  1 btusb
btbcm                  16384  1 btusb
btintel                24576  1 btusb
videodev              208896  3 videobuf2_v4l2,uvcvideo,videobuf2_common
bluetooth             573440  31 btrtl,btintel,btbcm,bnep,btusb,rfcomm
mc                     53248  4 videodev,videobuf2_v4l2,uvcvideo,videobuf2_common
ecdh_generic           16384  2 bluetooth
ecc                    28672  1 ecdh_generic
binfmt_misc            24576  1
nls_iso8859_1          16384  1
intel_rapl_msr         20480  0
mei_hdcp               24576  0
snd_hda_codec_realtek   114688  1
snd_hda_codec_generic    81920  1 snd_hda_codec_realtek
ledtrig_audio          16384  2 snd_hda_codec_generic,snd_hda_codec_realtek
snd_hda_codec_hdmi     61440  1
snd_hda_intel          49152  4
snd_hda_codec         131072  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
snd_hda_core           90112  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
snd_hwdep              20480  1 snd_hda_codec
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
snd_seq_midi           20480  0
intel_rapl_common      24576  1 intel_rapl_msr
snd_seq_midi_event     16384  1 snd_seq_midi
x86_pkg_temp_thermal    20480  0
intel_powerclamp       20480  0
coretemp               20480  0
snd_rawmidi            36864  1 snd_seq_midi
kvm_intel             278528  0
kvm                   647168  1 kvm_intel
irqbypass              16384  1 kvm
intel_cstate           20480  0
intel_rapl_perf        20480  0
iwlmvm                397312  0
joydev                 24576  0
mac80211              847872  1 iwlmvm
snd_seq                69632  2 snd_seq_midi,snd_seq_midi_event
libarc4                16384  1 mac80211
input_leds             16384  0
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
serio_raw              20480  0
wmi_bmof               16384  0
hp_wmi                 16384  0
snd_timer              36864  2 snd_seq,snd_pcm
sparse_keymap          16384  1 hp_wmi
iwlwifi               348160  1 iwlmvm
rtsx_pci_ms            24576  0
mei_me                 40960  1
cfg80211              712704  3 iwlmvm,iwlwifi,mac80211
memstick               20480  1 rtsx_pci_ms
snd                    86016  19 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi
mei                   110592  3 mei_hdcp,mei_me
soundcore              16384  1 snd
hp_accel               28672  0
hp_wireless            16384  0
lis3lv02d              24576  1 hp_accel
input_polldev          20480  1 lis3lv02d
tpm_infineon           20480  0
mac_hid                16384  0
sch_fq_codel           20480  2
parport_pc             40960  0
ppdev                  24576  0
lp                     20480  0
parport                53248  3 parport_pc,lp,ppdev
ip_tables              32768  0
x_tables               40960  1 ip_tables
autofs4                45056  2
amdgpu               4190208  0
amd_iommu_v2           20480  1 amdgpu
gpu_sched              32768  1 amdgpu
crct10dif_pclmul       16384  1
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
rtsx_pci_sdmmc         28672  0
i915                 1941504  14
aesni_intel           372736  6
radeon               1478656  1
aes_x86_64             20480  1 aesni_intel
crypto_simd            16384  1 aesni_intel
cryptd                 24576  2 crypto_simd,ghash_clmulni_intel
glue_helper            16384  1 aesni_intel
ttm                   106496  2 amdgpu,radeon
i2c_algo_bit           16384  3 amdgpu,radeon,i915
drm_kms_helper        184320  3 amdgpu,radeon,i915
psmouse               155648  0
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
ahci                   40960  2
libahci                32768  1 ahci
i2c_i801               32768  0
lpc_ich                24576  0
rtsx_pci               69632  2 rtsx_pci_sdmmc,rtsx_pci_ms
drm                   491520  10 gpu_sched,drm_kms_helper,amdgpu,radeon,i915,ttm
e1000e                258048  0
wmi                    32768  2 hp_wmi,wmi_bmof
video                  49152  1 i915

```

---

