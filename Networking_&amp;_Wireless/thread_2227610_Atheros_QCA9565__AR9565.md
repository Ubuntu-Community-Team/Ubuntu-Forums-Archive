---
title: "Atheros QCA9565 / AR9565"
date: 2014-06-03
forum: Networking &amp; Wireless
---

### Post by Edwin_Camero on 2014-06-03
Hi this is Edwin, 

I wanted to get help in fixing my wireless connection on my laptop. My unit is Dell Inspiron 14, Im using Ubuntu 12.04 LTS.

I got connected to our wireless connection the firstday, but on the second day and still counting, I cannot.. :(

Please help me get this fixed,

attached is my wireless info (just read how to do it in one of the posts in this forum.) 

Thanks!

---

### Post by Edwin_Camero on 2014-06-03
Hope this details helps

```
sudo lshw -C network
[sudo] password for edwin: 
  *-network UNCLAIMED     
       description: Network controller
       product: QCA9565 / AR9565 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f7900000-f797ffff memory:f7980000-f798ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 08
       serial: e0:db:55:c8:3a:96
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.104 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:59 ioport:e000(size=256) memory:f7804000-f7804fff memory:f7800000-f7803fff

```
```
sudo lshw -C network
[sudo] password for edwin: 
  *-network UNCLAIMED     
       description: Network controller
       product: QCA9565 / AR9565 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f7900000-f797ffff memory:f7980000-f798ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 08
       serial: e0:db:55:c8:3a:96
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.104 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:59 ioport:e000(size=256) memory:f7804000-f7804fff memory:f7800000-f7803fff

```
```
edwin@edwin-Inspiron-3437:~$ lspci -nnk | grep -iA2 net
06:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
    Subsystem: Dell Device [1028:020c]
    Kernel modules: wl
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 08)
    Subsystem: Dell Device [1028:05f3]
    Kernel driver in use: r8169

iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.
```

```
edwin@edwin-Inspiron-3437:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
```

```
edwin@edwin-Inspiron-3437:~$ lsmod
Module                  Size  Used by
parport_pc             32867  0 
ppdev                  17114  0 
rfcomm                 47562  12 
bnep                   18240  2 
btusb                  22432  0 
joydev                 17694  0 
coretemp               13642  0 
kvm_intel             137888  0 
kvm                   422160  1 kvm_intel
ghash_clmulni_intel    13221  0 
aesni_intel            51134  0 
cryptd                 20531  2 ghash_clmulni_intel,aesni_intel
aes_x86_64             17256  1 aesni_intel
snd_hda_codec_realtek    46366  1 
dell_wmi               12682  0 
sparse_keymap          13891  1 dell_wmi
snd_hda_codec_hdmi     36726  1 
dell_laptop            17426  0 
dcdbas                 14491  1 dell_laptop
dm_multipath           23306  0 
scsi_dh                14589  1 dm_multipath
snd_seq_midi           13325  0 
snd_rawmidi            30750  1 snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61931  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
microcode              23030  0 
snd_hda_intel          43682  5 
snd_hda_codec         188269  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              17765  1 snd_hda_codec
snd_pcm                97523  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_timer              29990  2 snd_seq,snd_pcm
uvcvideo               78117  0 
videobuf2_core         33025  1 uvcvideo
videodev              125126  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12861  1 uvcvideo
videobuf2_memops       13405  1 videobuf2_vmalloc
ath3k                  12918  0 
mac_hid                13254  0 
bluetooth             212001  25 rfcomm,bnep,btusb,ath3k
wl                   4108704  0 
nouveau               924024  0 
i915_hsw              620520  3 
ttm                    88495  1 nouveau
drm_kms_helper         49259  2 nouveau,i915_hsw
snd                    83674  20 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_rawmidi,snd_seq,snd_seq_device,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_timer
psmouse               102759  0 
bbswitch               13612  0 
serio_raw              13216  0 
drm                   290595  6 nouveau,i915_hsw,ttm,drm_kms_helper
mxm_wmi                13022  1 nouveau
i2c_algo_bit           13565  2 nouveau,i915_hsw
video                  19653  2 i915_hsw,nouveau
cfg80211              208382  1 wl
intel_ips              18332  1 i915_hsw
soundcore              15092  1 snd
wmi                    19257  3 dell_wmi,nouveau,mxm_wmi
lib80211               14382  1 wl
snd_page_alloc         18573  2 snd_hda_intel,snd_pcm
lp                     17800  0 
parport                46563  3 parport_pc,ppdev,lp
dm_raid45              78156  0 
ahci                   25869  2 
libahci                31434  1 ahci
r8169                  62741  0 
xor                    17153  1 dm_raid45
dm_mirror              22204  0 
dm_region_hash         20962  1 dm_mirror
dm_log                 18565  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 781180  0 
zlib_deflate           27140  1 btrfs
libcrc32c              12645  1 btrfs
```

```
edwin@edwin-Inspiron-3437:~$ sudo cat /var/log/syslog | grep -e b43 -e wl -e firmware -e wlan0 | tail -n35
Jun  2 15:02:19 edwin-Inspiron-3437 kernel: [17450.859080] usb 1-1.6: device firmware changed
Jun  3 16:07:26 edwin-Inspiron-3437 kernel: [   13.518788] wl: module license 'unspecified' taints kernel.
Jun  3 16:07:26 edwin-Inspiron-3437 NetworkManager[988]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jun  3 17:25:48 edwin-Inspiron-3437 kernel: [   15.772159] wl: module license 'unspecified' taints kernel.
Jun  3 17:25:48 edwin-Inspiron-3437 NetworkManager[989]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jun  3 17:26:53 edwin-Inspiron-3437 kernel: [   13.786218] wl: module license 'unspecified' taints kernel.
Jun  3 17:26:53 edwin-Inspiron-3437 NetworkManager[1012]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jun  3 18:04:46 edwin-Inspiron-3437 kernel: [   13.579282] wl: module license 'unspecified' taints kernel.
Jun  3 18:04:46 edwin-Inspiron-3437 NetworkManager[961]: <info> monitoring kernel firmware directory '/lib/firmware'.
```

---

### Post by slickymaster on 2014-06-03
Hi Edwin_Camero, I edited you're previous post, adding the necessary code tags because not only terminal output posted as plain text loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand, but also because the use of 'Code' tags makes the post clean, compact and more appealing, thus getting more attention from readers.

[Here's a tutorial]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") on how to use [CODE] tags in your posts.

---

### Post by Edwin_Camero on 2014-06-03
ohh okay, thanks for arranging them for me... :)

---

### Post by chili555 on 2014-06-03
Please open a terminal and do:```
sudo apt-get purge bcmwl-kernel-source
```Reboot and then post:```
modinfo ath9k | grep 0036
```Thanks.

---

### Post by Edwin_Camero on 2014-06-04
Im done doing those, whats next please...
I still cant connect.. :(

---

### Post by Edwin_Camero on 2014-06-04
adding to that after I run the first code -- I also cant connect to my wired connection... :(
I really dont know what is happening.. please help me.. 

I just run the first codes on my posts, that restores my wired connection back...

wireless connection not solved though...

---

### Post by deadflowr on 2014-06-04
> **chili555 said:**
> Reboot and then **post**:```
modinfo ath9k | grep 0036
```Thanks.
Please post the output for this.

---

### Post by Edwin_Camero on 2014-06-04
edwin@edwin-Inspiron-3437:~$ modinfo ath9k | grep 0036
edwin@edwin-Inspiron-3437:~$

---

### Post by Edwin_Camero on 2014-06-04
just that, nothing happened

---

### Post by Edwin_Camero on 2014-06-04
edwin@edwin-Inspiron-3437:~$ modinfo ath9k | grep 0036
edwin@edwin-Inspiron-3437:~$

---

### Post by chili555 on 2014-06-04
Please open a terminal and run:

```
uname -r
```
Is your kernel version annotated '-pae'? If so, please get a working wired ethernet connection and then do:

```
sudo apt-get install linux-backports-modules-cw-3.10-precise-generic-pae
```
If not, then:

```
sudo apt-get install linux-backports-modules-cw-3.10-precise-generic
```
Detach the ethernet and do:

```
sudo modprobe ath9k
```
Your wireless should now be working.

---

