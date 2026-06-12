---
title: "Ubuntu 18.04 Minimum Connectivity with DLink - DWA131"
date: 2018-12-15
forum: Networking &amp; Wireless
---

### Post by theasianmamba24 on 2018-12-15
Novice Ubuntu user here, I have installed **Ubuntu 18.04 LTS** and I'm having issues with the connection. I have issues connecting to my university WiFi. The USB adapter (**DLink - DWA131**) works fine with Windows 10, but it's buggy with **Ubuntu 18.04 LTS**. The network adapter in my laptop is **Intel Wireless-N 7260**, and it's already buggy before I even install Ubuntu. I am currently connected via Bluetooth tethering, and it's also quite buggy as I get disconnected randomly when my phone is less than 1 meters away.

**Here's my pastebin:**
[http://paste.ubuntu.com/p/BZthFpgy4Z/](http://paste.ubuntu.com/p/BZthFpgy4Z/)

***lsusb*** gave me this:

```
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 010: ID 2001:3319 D-Link Corp. 
Bus 002 Device 023: ID 04f3:0085 Elan Microelectronics Corp. 
Bus 002 Device 005: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 002 Device 025: ID 8087:07dc Intel Corp. 
Bus 002 Device 003: ID 04f2:b3d6 Chicony Electronics Co., Ltd 
Bus 002 Device 024: ID 1a40:0101 Terminus Technology Inc. Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

I ran this command in the terminal and I got the the results:
***sudo lshw -class network***

```
  *-network DISABLED               description: Wireless interface
       product: Wireless 7260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlp4s0
       version: 63
       serial: 0c:8b:fd:0e:0e:07
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.15.0-42-generic firmware=17.948900127.0 latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:49 memory:b0500000-b0501fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.1
       bus info: pci@0000:05:00.1
       logical name: enp5s0f1
       version: 14
       serial: 08:9e:01:c3:cf:b4
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8411-2_0.0.1 07/08/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:19 ioport:3000(size=256) memory:b0404000-b0404fff memory:b0400000-b0403fff
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       bus info: usb@2:7
       logical name: wlx409bcd056453
       serial: 40:9b:cd:05:64:53
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8xxxu driverversion=4.15.0-42-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11
  *-network:1
       description: Ethernet interface
       physical id: 2
       logical name: bnep0
       serial: 0c:8b:fd:0e:0e:0b
       capabilities: ethernet physical
       configuration: broadcast=yes ip=192.168.44.195 multicast=yes



```

I have also tried:
[I][B]sudo apt update
sudo apt-get dist-upgrade
sudo add-apt-repository ppa:hanipouspilot/rtlwifi[/B][/I]

It turns out that none of the solutions above worked. **May someone suggest a solution that could fix the WiFi and Bluetooth connectivity issues? Thank you.**

---

### Post by praseodym on 2018-12-15
Check if 2 drivers are loaded
```

lsmod
```

---

### Post by theasianmamba24 on 2018-12-15
Thanks for the reply, I got a following results after running the command:

```
Module                  Size  Used byrfcomm                 77824  4
cmac                   16384  1
bnep                   20480  2
uvcvideo               86016  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
videobuf2_core         40960  2 videobuf2_v4l2,uvcvideo
videodev              184320  3 videobuf2_core,videobuf2_v4l2,uvcvideo
hid_multitouch         20480  0
media                  40960  2 videodev,uvcvideo
rtl8xxxu              122880  0
btusb                  45056  0
btrtl                  16384  1 btusb
btbcm                  16384  1 btusb
btintel                16384  1 btusb
bluetooth             548864  33 btrtl,btintel,btbcm,bnep,btusb,rfcomm
ecdh_generic           24576  2 bluetooth
nls_iso8859_1          16384  1
arc4                   16384  4
iwlmvm                364544  0
mac80211              778240  2 iwlmvm,rtl8xxxu
iwlwifi               282624  1 iwlmvm
cfg80211              622592  3 iwlmvm,iwlwifi,mac80211
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
kvm_intel             212992  0
kvm                   598016  1 kvm_intel
irqbypass              16384  1 kvm
intel_cstate           20480  0
intel_rapl_perf        16384  0
snd_hda_codec_realtek   106496  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
rtsx_pci_ms            20480  0
memstick               16384  1 rtsx_pci_ms
snd_hda_codec_hdmi     49152  1
snd_hda_intel          40960  8
snd_hda_codec         126976  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
joydev                 24576  0
input_leds             16384  0
acer_wmi               20480  0
sparse_keymap          16384  1 acer_wmi
serio_raw              16384  0
wmi_bmof               16384  0
mei_me                 40960  0
snd_hda_core           81920  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
snd_hwdep              20480  1 snd_hda_codec
snd_pcm                98304  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
mei                    90112  1 mei_me
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                65536  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
snd_timer              32768  2 snd_seq,snd_pcm
snd                    81920  27 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi
intel_smartconnect     16384  0
soundcore              16384  1 snd
lpc_ich                24576  0
shpchp                 36864  0
mac_hid                16384  0
sch_fq_codel           20480  10
parport_pc             36864  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 parport_pc,lp,ppdev
ip_tables              28672  0
x_tables               40960  1 ip_tables
autofs4                40960  2
algif_skcipher         16384  0
af_alg                 24576  1 algif_skcipher
dm_crypt               40960  1
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  4 usbhid,hid_multitouch,hid_generic
i915                 1617920  38
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
pcbc                   16384  0
rtsx_pci_sdmmc         24576  0
i2c_algo_bit           16384  1 i915
drm_kms_helper        172032  1 i915
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
aesni_intel           188416  4
aes_x86_64             20480  1 aesni_intel
crypto_simd            16384  1 aesni_intel
psmouse               147456  0
i2c_i801               28672  0
drm                   401408  19 drm_kms_helper,i915
glue_helper            16384  1 aesni_intel
cryptd                 24576  4 crypto_simd,ghash_clmulni_intel,aesni_intel
ahci                   36864  3
rtsx_pci               65536  2 rtsx_pci_sdmmc,rtsx_pci_ms
r8169                  86016  0
libahci                32768  1 ahci
mii                    16384  1 r8169
wmi                    24576  2 acer_wmi,wmi_bmof
video                  45056  2 acer_wmi,i915



```

---

### Post by praseodym on 2018-12-16
Its only one. What about the internal Intel card?! Why using a dongle?

---

### Post by theasianmamba24 on 2018-12-16
The Intel card works but it's faulty. It's been faulty since the Windows 8.1 / Windows 10 update, so I had to get a dongle to replace it. Both adapters are getting low connectivity somehow.

---

### Post by praseodym on 2018-12-16
Try for the internal card
```

echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi-11n.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```

---

### Post by theasianmamba24 on 2018-12-18
I ran the code and I received this output:
[I][B]options iwlwifi 11n_disable=1
modprobe: FATAL: Module iwlwifi is in use.[/B][/I]

It shows that the same output even if I turn off the WiFi, the connection remains the same. Is it possible that I have to disable the adapter first?

---

### Post by praseodym on 2018-12-18
Reboot?

---

### Post by jeremy31 on 2018-12-18
Redo the file
```
sudo -H gedit /etc/modprobe.d/iwlwifi.conf
```
Add the following for contents
```
# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
```

I would suggest ```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
systemctl restart network-manager.service
```
See if that improves anything

---

### Post by theasianmamba24 on 2018-12-18
**[COLOR=#000000]@[/COLOR][COLOR=#000000]praseodym[/COLOR][COLOR=#000000] [/COLOR]**Thanks for the reply, but rebooting didn't help.

**@jeremy31**Thanks for your reply, I have tried the solution you proposed, but I don't think it improved the connection. The connectivity remains at the same level, basically being able to connect to a modem is based on luck at the moment.

---

### Post by jeremy31 on 2018-12-20
See if the dongle works better with ```
sudo apt-get install git build-essential dkms
git clone https://github.com/Mange/rtl8192eu-linux-driver.git
sudo dkms add ./rtl8192eu-linux-driver
sudo dkms install rtl8192eu/1.0
echo "blacklist rtl8xxxu" | sudo tee /etc/modprobe.d/rtl8xxxu.conf
```

Reboot, go into BIOS settings and disable Secure Boot

---

### Post by theasianmamba24 on 2018-12-21
**@jeremy31** The last solution worked and the signal has improved significantly. Thank you!

---

