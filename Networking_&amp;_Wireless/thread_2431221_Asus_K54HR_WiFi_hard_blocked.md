---
title: "Asus K54HR WiFi hard blocked"
date: 2019-11-13
forum: Networking &amp; Wireless
---

### Post by simoneg on 2019-11-13
Hi,

I have a laptop (Asus K54HR) with dual boot (Ubuntu 19.04 and Win10), on linux wifi is hard blocked, on win10 everything works fine.

I already tried some settings found online, I reinstalled ubuntu, I restore bios to default, there is no physical switch.

Any help?

---

### Post by kc1di on 2019-11-13
Normally there will be an fn key combo that will turn on the wifi card.   However the user's manual for your Laptop say's the following about wireless
"Bluetooth / Wireless Indicator
This is only applicable on models with internal Bluetooth (BT)
and built-in wireless LAN. This indicator will light to show that
the Notebook PC&#8217;s built-in Bluetooth (BT) function is activated.
When the built-in wireless LAN is enabled, this indicator will also
light. **(Windows software settings are necessary.)**"
Notice that it says windows software is needed.  
But Please go to a terminal and type this command and post the output back here. ```
rfkill list all
```

---

### Post by simoneg on 2019-11-14
I have a Fn+F2 switch, it seems to work only on software layer.

rfkill list all
```

0: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```

---

### Post by kc1di on 2019-11-14
Please go to a terminal and copy and paste this command  and post the output here. ```
sudo lshw -C network
```

---

### Post by simoneg on 2019-11-15
sudo lshw -C network
```

  *-network DISABLED        
       description: Wireless interface
       product: RT5390 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: 00
       serial: e0:06:e6:9c:1b:bf
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=5.0.0-36-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:dea00000-dea0ffff
  *-network
       description: Ethernet interface
       product: AR8151 v2.0 Gigabit Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: enp5s0
       version: c0
       serial: 30:85:a9:05:4e:e1
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.1-NAPI duplex=full ip=192.168.99.186 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:39 memory:dd600000-dd63ffff ioport:9000(size=128)

```

---

### Post by praseodym on 2019-11-15
Could be an "Asus classic". Please run

```
echo "options asus_nb_wmi wapf=1" | sudo tee /etc/modprobe.d/asus.conf 
```

and reboot. Please show
```

lsmod
rfkill list
```afterwards

---

### Post by simoneg on 2019-11-16
A little better but it still doesn't work: wifi is green on boot, when I press Fn+F2 wifi led turns on/off

I also tried wapf values 0,1,2,3,4

lsmod
```

Module                  Size  Used by
nls_utf8               16384  1
isofs                  49152  1
uvcvideo               98304  0
videobuf2_vmalloc      20480  1 uvcvideo
videobuf2_memops       20480  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
videobuf2_common       53248  2 videobuf2_v4l2,uvcvideo
videodev              208896  3 videobuf2_v4l2,uvcvideo,videobuf2_common
snd_hda_codec_realtek   118784  1
mc                     53248  4 videodev,videobuf2_v4l2,uvcvideo,videobuf2_common
intel_rapl_msr         20480  0
snd_hda_codec_generic    81920  1 snd_hda_codec_realtek
intel_rapl_common      24576  1 intel_rapl_msr
rt2800pci              16384  0
rt2800mmio             20480  1 rt2800pci
x86_pkg_temp_thermal    20480  0
ledtrig_audio          16384  2 snd_hda_codec_generic,snd_hda_codec_realtek
rt2800lib             131072  2 rt2800mmio,rt2800pci
intel_powerclamp       20480  0
snd_hda_codec_hdmi     61440  1
rt2x00pci              16384  1 rt2800pci
coretemp               20480  0
snd_hda_intel          49152  4
rt2x00mmio             16384  2 rt2800mmio,rt2800pci
rt2x00lib              61440  5 rt2x00mmio,rt2x00pci,rt2800mmio,rt2800pci,rt2800lib
snd_hda_codec         131072  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
kvm_intel             278528  0
mac80211              851968  3 rt2x00pci,rt2x00lib,rt2800lib
snd_hda_core           90112  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
kvm                   651264  1 kvm_intel
snd_hwdep              20480  1 snd_hda_codec
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
cfg80211              712704  2 rt2x00lib,mac80211
irqbypass              16384  1 kvm
snd_seq_midi           20480  0
radeon               1478656  12
eeprom_93cx6           16384  1 rt2800pci
ttm                   106496  1 radeon
snd_seq_midi_event     16384  1 snd_seq_midi
drm_kms_helper        184320  1 radeon
libarc4                16384  1 mac80211
drm                   491520  6 drm_kms_helper,radeon,ttm
snd_rawmidi            36864  1 snd_seq_midi
i2c_algo_bit           16384  1 radeon
fb_sys_fops            16384  1 drm_kms_helper
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
crct10dif_pclmul       16384  1
crc32_pclmul           16384  0
sysimgblt              16384  1 drm_kms_helper
ghash_clmulni_intel    16384  0
mei_hdcp               24576  0
snd_seq                69632  2 snd_seq_midi,snd_seq_midi_event
asus_nb_wmi            28672  0
asus_wmi               32768  1 asus_nb_wmi
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
joydev                 28672  0
snd_timer              36864  2 snd_seq,snd_pcm
input_leds             16384  0
cryptd                 24576  1 ghash_clmulni_intel
sparse_keymap          16384  1 asus_wmi
snd                    86016  19 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi
mei_me                 40960  1
soundcore              16384  1 snd
mac_hid                16384  0
mei                   110592  3 mei_hdcp,mei_me
serio_raw              20480  0
intel_cstate           20480  0
intel_rapl_perf        20480  0
sch_fq_codel           20480  2
parport_pc             40960  0
ppdev                  24576  0
lp                     20480  0
parport                53248  3 parport_pc,lp,ppdev
ip_tables              32768  0
x_tables               40960  1 ip_tables
autofs4                45056  2
psmouse               155648  0
i2c_i801               32768  0
ahci                   40960  4
lpc_ich                24576  0
libahci                32768  1 ahci
atl1c                  53248  0
wmi                    32768  1 asus_wmi
video                  49152  1 asus_wmi

```

rfkill list
```

0: asus-wlan: Wireless LAN
 Soft blocked: no
 Hard blocked: no
1: phy0: Wireless LAN
 Soft blocked: no
 Hard blocked: yes

```

---

### Post by simoneg on 2019-11-17
Any help will be greatly appreciated

wireless-info
[https://paste.ubuntu.com/p/NQM67hZnF5/](https://paste.ubuntu.com/p/NQM67hZnF5/)

---

### Post by praseodym on 2019-11-17
Do not press Fn combo after rebooting, but show
```

rfkill list
```
If it is soft blocked, then run
```

sudo rfkill unblock all
```

---

### Post by simoneg on 2019-11-17
Reboot, login, but still hard blocked

rfkill list
```

0: asus-wlan: Wireless LAN
 Soft blocked: no
 Hard blocked: no
1: phy0: Wireless LAN
 Soft blocked: no
 Hard blocked: yes

```

---

### Post by praseodym on 2019-11-17
Any button, switch, key or key combo? If yes, press that combo/key repeatedly or permanently during bootup

---

### Post by simoneg on 2019-11-18
Fn+F2 is the combo to turn on/off WiFi.
When is bootup? After bios, before login?

---

### Post by simoneg on 2019-11-21
I tried to press combo repeatedly and permanently without any success, wifi is still hard blocked.

Any idea?
It worked well on Ubuntu and works well on Win 10, what happened? what is it that has set the switch from wifi to hard blocked?

---

