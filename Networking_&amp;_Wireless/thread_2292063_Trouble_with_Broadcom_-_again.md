---
title: "Trouble with Broadcom - again"
date: 2015-08-24
forum: Networking &amp; Wireless
---

### Post by landersohn-m on 2015-08-24
I have a (new) Lenovo Y70.
I installed Xbuntu 14.04 on it but upgraded the kernel to the vivid kernel 3.19

I cannot get my wireless crd to work:
lspci -v reports 
BCM4352 802.11ac (rev 03)

accoridng to all posts, the bcmwl-kernel-source driver should work. However, if I install this driver and load wl, dmesg says that I have a
BCM43b1 802.11
wireless card.
I also get this in dmesg 8.5 sec after boot or so. It appears as if my kernel is very confused about my wireless car.
Does aybody have any ideas?

Thanks

---

### Post by Hadaka on 2015-08-24
try this post #6
[http://ubuntuforums.org/showthread.php?t=2289270&](http://ubuntuforums.org/showthread.php?t=2289270&)

---

### Post by landersohn-m on 2015-08-25
Thanks but unfortunately it didn't work for me.
I downloaded the deb files but dkms fails to build wl. Get a fatal error when I try to install

---

### Post by landersohn-m on 2015-08-25
Update:
I tried the bcmwl-kernel-source package from longsleep for the 3.19 kernel (Vivid). It seems to install fine, no errors but when I boot, I see the following in dmesg when the cfg80211 driver loads:
[    8.138263] wl: module license 'MIXED/Proprietary' taints kernel.
[    8.138265] Disabling lock debugging due to kernel taint
[    8.140013] wl: module verification failed: signature and/or  required key missing - tainting kernel

Is this maybe the reason the card won't work? How do I get this key?
Thanks

---

### Post by Hadaka on 2015-08-25
Hi, did you unload the old driver first?
```
sudo modprobe -rfv wl
 sudo apt-get remove --purge bcmwl-kernel-source
```
Please provide a print out of the error message.
thsnks.

---

### Post by landersohn-m on 2015-08-25
Yes, I unloaded the drivers. I don't get any more error messages that the dmesg I have posted but wicd simply does not see the card, neither does ifconfig after a networking restart.
I now actually think the driver loads but something disables the card in hardware (see lspci and lshw outputs below):
looks like the card wants to use the wl driver but somehow the network is DISABLED (from lshw). I have made sure that in the BIOS the Wireless LAN setting is Enabled.
Ran rfkill unblock all, still no change.


Output from lspci -v is:
08:00.0 Network controller: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter (rev 03)
    Subsystem: Lenovo Device 0623
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at d1600000 (64-bit, non-prefetchable) [size=32K]
    Memory at d1400000 (64-bit, non-prefetchable) [size=2M]
    Capabilities: [48] Power Management version 3
    Capabilities: [58] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [68] Vendor Specific Information: Len=44 <?>
    Capabilities: [ac] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [13c] Device Serial Number ac-d1-00-ff-ff-00-00-01
    Capabilities: [150] Power Budgeting <?>
    Capabilities: [160] Virtual Channel
    Kernel driver in use: wl



Output from lshw is:
        *-pci:2
             description: PCI bridge
             product: 8 Series/C220 Series Chipset Family PCI Express Root Port #2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: d5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 memory:d1400000-d16fffff
           *-network DISABLED
                description: Wireless interface
                product: BCM4352 802.11ac Wireless Network Adapter
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:08:00.0
                logical name: wlan1
                version: 03
                serial: ac:d1:b8:e1:31:a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=6.30.223.248 (r487574) latency=0 multicast=yes wireless=IEEE 802.11abg
                resources: irq:17 memory:d1600000-d1607fff memory:d1400000-d15fffff

---

### Post by chili555 on 2015-08-25
> when I boot, I see the following in dmesg when the cfg80211 driver loads:
[ 8.138263] wl: module license 'MIXED/Proprietary' taints kernel.
[ 8.138265] Disabling lock debugging due to kernel taint
[ 8.140013] wl: module verification failed: signature and/or required key missing - tainting kernelThese messages are trivial and may safely be ignored. It simply means that the bcmwl driver is proprietary and that it is added to the kernel, it is no longer free and open source; it is mixed.

This is probably why it doesn't work:> *-network [COLOR="#FF0000"]DISABLED[/COLOR]
description: Wireless interface
product: BCM4352 802.11ac Wireless Network Adapter
vendor: Broadcom CorporationThis usually means that the hardware switch or key combination is set to turn the wireless off. What does this report?```
rfkill list all
lsmod
```

---

### Post by landersohn-m on 2015-08-25
xyz@somewhere: ~$ rfkill list all
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
4: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
7: phy3: Wireless LAN
    Soft blocked: no
    Hard blocked: no

lsmod | grep wl

wl                   6369280  0 
cfg80211              524288  3 wl,mac80211,rt2x00lib

I did find a post that seemed to indicate module ideadpad_laptop gets in the way. I'll try a restart with this module blacklisted and see what happens.
I tried rfkill unblock all, tried the airplane mode button on the laptop, all to no avail.

---

### Post by landersohn-m on 2015-08-25
I blacklisted ideapad_laptop as suggested in some other posts, still the same result:
rfkill shows the card as not blocked but lshw shows the network as disabled.

---

### Post by Hadaka on 2015-08-25
please post the output of ..
```
lsmod
lsusb
```
thanks

---

### Post by landersohn-m on 2015-08-25
See below.
lsusb shows a wireless dongle (Buffalo) which I am using to work around this issue

abc@lxyz:~$ lsmod
Module                  Size  Used by
ipt_MASQUERADE         16384  1 
nf_nat_masquerade_ipv4    16384  1 ipt_MASQUERADE
iptable_filter         16384  1 
iptable_nat            16384  1 
nf_conntrack_ipv4      16384  1 
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
nf_nat_ipv4            16384  1 iptable_nat
nf_nat                 24576  2 nf_nat_ipv4,nf_nat_masquerade_ipv4
nf_conntrack          106496  4 nf_nat,nf_nat_ipv4,nf_nat_masquerade_ipv4,nf_conntrack_ipv4
ip_tables              28672  2 iptable_filter,iptable_nat
x_tables               36864  3 ip_tables,ipt_MASQUERADE,iptable_filter
bridge                110592  0 
stp                    16384  1 bridge
llc                    16384  2 stp,bridge
ctr                    16384  3 
ccm                    20480  3 
bbswitch               16384  0 
pci_stub               16384  1 
vboxpci                24576  0 
vboxnetadp             28672  0 
vboxnetflt             28672  0 
vboxdrv               450560  3 vboxnetadp,vboxnetflt,vboxpci
rfcomm                 69632  12 
bnep                   20480  2 
binfmt_misc            20480  1 
arc4                   16384  2 
intel_rapl             20480  0 
wl                   6369280  0 
hid_logitech_hidpp     20480  0 
rt2800usb              28672  0 
rt2x00usb              24576  1 rt2800usb
rt2800lib              90112  1 rt2800usb
uvcvideo               90112  0 
rt2x00lib              57344  3 rt2x00usb,rt2800lib,rt2800usb
snd_hda_codec_hdmi     53248  1 
mac80211              708608  3 rt2x00lib,rt2x00usb,rt2800lib
videobuf2_vmalloc      16384  1 uvcvideo
btusb                  40960  0 
videobuf2_memops       16384  1 videobuf2_vmalloc
snd_hda_codec_realtek    81920  1 
videobuf2_core         53248  1 uvcvideo
bluetooth             491520  22 bnep,btusb,rfcomm
snd_hda_codec_generic    69632  1 snd_hda_codec_realtek
v4l2_common            16384  1 videobuf2_core
iosf_mbi               16384  1 intel_rapl
crc_ccitt              16384  1 rt2800lib
videodev              159744  3 uvcvideo,v4l2_common,videobuf2_core
hid_logitech_dj        20480  0 
hid_multitouch         20480  0 
media                  24576  2 uvcvideo,videodev
dm_multipath           24576  0 
x86_pkg_temp_thermal    16384  0 
intel_powerclamp       20480  0 
joydev                 20480  0 
coretemp               16384  0 
rtsx_pci_ms            20480  0 
kvm_intel             151552  0 
memstick               20480  1 rtsx_pci_ms
scsi_dh                16384  1 dm_multipath
snd_hda_intel          32768  5 
kvm                   479232  1 kvm_intel
cfg80211              524288  3 wl,mac80211,rt2x00lib
snd_hda_controller     32768  1 snd_hda_intel
snd_seq_midi           16384  0 
snd_hda_codec         143360  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_seq_midi_event     16384  1 snd_seq_midi
snd_hwdep              20480  1 snd_hda_codec
snd_rawmidi            32768  1 snd_seq_midi
crct10dif_pclmul       16384  0 
crc32_pclmul           16384  0 
ghash_clmulni_intel    16384  0 
aesni_intel           172032  7 
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
psmouse               114688  0 
cryptd                 20480  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
mei_me                 20480  0 
serio_raw              16384  0 
snd_timer              32768  2 snd_pcm,snd_seq
wmi                    20480  0 
shpchp                 40960  0 
mei                    90112  1 mei_me
lpc_ich                24576  0 
mac_hid                16384  0 
snd                    86016  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              16384  2 snd,snd_hda_codec
ie31200_edac           16384  0 
edac_core              53248  1 ie31200_edac
parport_pc             32768  0 
ppdev                  20480  0 
lp                     20480  0 
parport                45056  3 lp,ppdev,parport_pc
btrfs                 937984  0 
xor                    24576  1 btrfs
raid6_pq               98304  1 btrfs
dm_mirror              24576  0 
dm_region_hash         24576  1 dm_mirror
dm_log                 20480  2 dm_region_hash,dm_mirror
hid_generic            16384  0 
usbhid                 53248  0 
hid                   110592  6 hid_multitouch,hid_generic,usbhid,hid_logitech_dj,hid_logitech_hidpp
i915                 1048576  5 
i2c_algo_bit           16384  1 i915
drm_kms_helper        126976  1 i915
rtsx_pci_sdmmc         24576  0 
ahci                   36864  4 
r8169                  81920  0 
drm                   344064  6 i915,drm_kms_helper
libahci                32768  1 ahci
rtsx_pci               49152  2 rtsx_pci_ms,rtsx_pci_sdmmc
mii                    16384  1 r8169
video                  20480  1 i915



abc@xyz:~$ lsusb
Bus 004 Device 002: ID 8087:8000 Intel Corp. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 8087:8008 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 009: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 008: ID 058f:6254 Alcor Micro Corp. USB Hub
Bus 001 Device 007: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 006: ID 0489:e07a Foxconn / Hon Hai 
Bus 001 Device 005: ID 5986:055e Acer, Inc 
Bus 001 Device 004: ID 0457:1067 Silicon Integrated Systems Corp. 
Bus 001 Device 003: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 001 Device 002: ID 0411:01a2 BUFFALO INC. (formerly MelCo., Inc.) WLI-UC-GNM Wireless LAN Adapter [Ralink RT8070]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by jeremy31 on 2015-08-25
I would try ```
sudo ifconfig wlan1 up
```

---

### Post by landersohn-m on 2015-08-25
Below. The Buffalo USB device is a network dongle I use to get wireless

abc@xyz:~$ lsmod
Module                  Size  Used by
ipt_MASQUERADE         16384  1 
nf_nat_masquerade_ipv4    16384  1 ipt_MASQUERADE
iptable_filter         16384  1 
iptable_nat            16384  1 
nf_conntrack_ipv4      16384  1 
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
nf_nat_ipv4            16384  1 iptable_nat
nf_nat                 24576  2 nf_nat_ipv4,nf_nat_masquerade_ipv4
nf_conntrack          106496  4 nf_nat,nf_nat_ipv4,nf_nat_masquerade_ipv4,nf_conntrack_ipv4
ip_tables              28672  2 iptable_filter,iptable_nat
x_tables               36864  3 ip_tables,ipt_MASQUERADE,iptable_filter
bridge                110592  0 
stp                    16384  1 bridge
llc                    16384  2 stp,bridge
ctr                    16384  3 
ccm                    20480  3 
bbswitch               16384  0 
pci_stub               16384  1 
vboxpci                24576  0 
vboxnetadp             28672  0 
vboxnetflt             28672  0 
vboxdrv               450560  3 vboxnetadp,vboxnetflt,vboxpci
rfcomm                 69632  12 
bnep                   20480  2 
binfmt_misc            20480  1 
arc4                   16384  2 
intel_rapl             20480  0 
wl                   6369280  0 
hid_logitech_hidpp     20480  0 
rt2800usb              28672  0 
rt2x00usb              24576  1 rt2800usb
rt2800lib              90112  1 rt2800usb
uvcvideo               90112  0 
rt2x00lib              57344  3 rt2x00usb,rt2800lib,rt2800usb
snd_hda_codec_hdmi     53248  1 
mac80211              708608  3 rt2x00lib,rt2x00usb,rt2800lib
videobuf2_vmalloc      16384  1 uvcvideo
btusb                  40960  0 
videobuf2_memops       16384  1 videobuf2_vmalloc
snd_hda_codec_realtek    81920  1 
videobuf2_core         53248  1 uvcvideo
bluetooth             491520  22 bnep,btusb,rfcomm
snd_hda_codec_generic    69632  1 snd_hda_codec_realtek
v4l2_common            16384  1 videobuf2_core
iosf_mbi               16384  1 intel_rapl
crc_ccitt              16384  1 rt2800lib
videodev              159744  3 uvcvideo,v4l2_common,videobuf2_core
hid_logitech_dj        20480  0 
hid_multitouch         20480  0 
media                  24576  2 uvcvideo,videodev
dm_multipath           24576  0 
x86_pkg_temp_thermal    16384  0 
intel_powerclamp       20480  0 
joydev                 20480  0 
coretemp               16384  0 
rtsx_pci_ms            20480  0 
kvm_intel             151552  0 
memstick               20480  1 rtsx_pci_ms
scsi_dh                16384  1 dm_multipath
snd_hda_intel          32768  5 
kvm                   479232  1 kvm_intel
cfg80211              524288  3 wl,mac80211,rt2x00lib
snd_hda_controller     32768  1 snd_hda_intel
snd_seq_midi           16384  0 
snd_hda_codec         143360  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_seq_midi_event     16384  1 snd_seq_midi
snd_hwdep              20480  1 snd_hda_codec
snd_rawmidi            32768  1 snd_seq_midi
crct10dif_pclmul       16384  0 
crc32_pclmul           16384  0 
ghash_clmulni_intel    16384  0 
aesni_intel           172032  7 
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
psmouse               114688  0 
cryptd                 20480  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
mei_me                 20480  0 
serio_raw              16384  0 
snd_timer              32768  2 snd_pcm,snd_seq
wmi                    20480  0 
shpchp                 40960  0 
mei                    90112  1 mei_me
lpc_ich                24576  0 
mac_hid                16384  0 
snd                    86016  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              16384  2 snd,snd_hda_codec
ie31200_edac           16384  0 
edac_core              53248  1 ie31200_edac
parport_pc             32768  0 
ppdev                  20480  0 
lp                     20480  0 
parport                45056  3 lp,ppdev,parport_pc
btrfs                 937984  0 
xor                    24576  1 btrfs
raid6_pq               98304  1 btrfs
dm_mirror              24576  0 
dm_region_hash         24576  1 dm_mirror
dm_log                 20480  2 dm_region_hash,dm_mirror
hid_generic            16384  0 
usbhid                 53248  0 
hid                   110592  6 hid_multitouch,hid_generic,usbhid,hid_logitech_dj,hid_logitech_hidpp
i915                 1048576  5 
i2c_algo_bit           16384  1 i915
drm_kms_helper        126976  1 i915
rtsx_pci_sdmmc         24576  0 
ahci                   36864  4 
r8169                  81920  0 
drm                   344064  6 i915,drm_kms_helper
libahci                32768  1 ahci
rtsx_pci               49152  2 rtsx_pci_ms,rtsx_pci_sdmmc
mii                    16384  1 r8169
video                  20480  1 i915


abc@xyz:~$ lsusb
Bus 004 Device 002: ID 8087:8000 Intel Corp. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 8087:8008 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 009: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 008: ID 058f:6254 Alcor Micro Corp. USB Hub
Bus 001 Device 007: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 006: ID 0489:e07a Foxconn / Hon Hai 
Bus 001 Device 005: ID 5986:055e Acer, Inc 
Bus 001 Device 004: ID 0457:1067 Silicon Integrated Systems Corp. 
Bus 001 Device 003: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 001 Device 002: ID 0411:01a2 BUFFALO INC. (formerly MelCo., Inc.) WLI-UC-GNM Wireless LAN Adapter [Ralink RT8070]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by landersohn-m on 2015-08-25
Yehaa, that worked, thank you so much!

---

### Post by Hadaka on 2015-08-25
GREAT ! glad its working.

@jeremy31...pffft...right make it look easy ;)

---

