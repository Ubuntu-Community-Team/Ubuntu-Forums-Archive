---
title: "TL-WN881ND Wi-Fi hotspot: low download speed"
date: 2019-01-06
forum: Networking &amp; Wireless
---

### Post by anticlimactic on 2019-01-06
Hi! I have Ubuntu 18.04 PC with wired internet connection (~90 Mbits/s) and PCI-E Wi-Fi TP-Link TL-WN881ND (EU) Ver.2.0 card, working in Wi-Fi hotspot mode.
My Ubuntu OS recognized it automatically upon installation, but when I connect my Mint laptop (or Android smartphone) to it, the download speed is very low: about 600 - 800 Kbits/s (tested via *Iperf*). In the meantime, upload speed is much greater: ~6 Mbits/sec.
I've done some searching around, turned off the power saving feature, switched antennas using *ant-sel* flag, but nothing helped.
I've also downloaded and installed driver from the [official manufacturer's site]("https://static.tp-link.com/TL-WN881ND_2.0_LinuxDriverSetup.zip"), but it didn't help me either.
Will appreciate any advice.

---

### Post by praseodym on 2019-01-06
So, you are forwarding the LAN connection via the wireless device, correct?

You have two different LAN cards, Realtek r8169 driver can be changed

```
sudo apt-get install r8168-dkms dkms build-essential
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```
Normally, the other card loads two drivers, 8139too and 8139cp, check
```

lsmod
```
If so, blacklist 8139cp as well and reboot

---

### Post by anticlimactic on 2019-01-06
> **praseodym said:**
> So, you are forwarding the LAN connection via the wireless device, correct?
Yep, my ISP cable is connected to **enp5s0 **and I'm forwarding it to [B]wlp1s0.
[/B]
> You have two different LAN cards, Realtek r8169 driver can be changed
Yes, I have another LAN card installed (**enp4s1**), I'm gonna use it to make wired connection to another PC.
_____________________________________________________________________________________

Anyway, I've blacklisted r8169 and 8139cp and rebooted, but the Wi-Fi bandwidth change is very-very small (increased only by ~100 Kbits/sec).

I've uploaded fresh diagnostics file, please take a look: [http://paste.ubuntu.com/p/nHY783xQHF/](http://paste.ubuntu.com/p/nHY783xQHF/)

---

### Post by praseodym on 2019-01-06
Try deactivating IPv6 and show "lsmod" completely

---

### Post by anticlimactic on 2019-01-06
> **praseodym said:**
> Try deactivating IPv6
[Done.]("https://linuxconfig.org/how-to-disable-ipv6-address-on-ubuntu-18-04-bionic-beaver-linux")

> show "lsmod" completely
```
vladimir@Vovan-PC:~$ lsmodModule                  Size  Used by
ipt_MASQUERADE         16384  1
nf_nat_masquerade_ipv4    16384  1 ipt_MASQUERADE
xt_conntrack           16384  1
ipt_REJECT             16384  2
nf_reject_ipv4         16384  1 ipt_REJECT
xt_tcpudp              16384  4
iptable_filter         16384  1
nf_nat_h323            20480  0
nf_conntrack_h323      73728  1 nf_nat_h323
nf_nat_pptp            16384  0
nf_nat_proto_gre       16384  1 nf_nat_pptp
nf_conntrack_pptp      16384  1 nf_nat_pptp
nf_conntrack_proto_gre    16384  1 nf_conntrack_pptp
nf_nat_tftp            16384  0
nf_conntrack_tftp      16384  1 nf_nat_tftp
nf_nat_sip             20480  0
nf_conntrack_sip       28672  1 nf_nat_sip
nf_nat_irc             16384  0
nf_conntrack_irc       16384  1 nf_nat_irc
nf_nat_ftp             16384  0
nf_conntrack_ftp       20480  1 nf_nat_ftp
iptable_nat            16384  1
nf_conntrack_ipv4      16384  3
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
nf_nat_ipv4            16384  1 iptable_nat
nf_nat                 32768  9 nf_nat_masquerade_ipv4,nf_nat_irc,nf_nat_ftp,nf_nat_ipv4,nf_nat_tftp,nf_nat_pptp,nf_nat_h323,nf_nat_proto_gre,nf_nat_sip
nf_conntrack          131072  19 xt_conntrack,nf_nat_masquerade_ipv4,nf_nat_irc,nf_conntrack_ipv4,nf_nat,nf_conntrack_tftp,nf_nat_ftp,nf_conntrack_pptp,ipt_MASQUERADE,nf_nat_ipv4,nf_nat_tftp,nf_conntrack_sip,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_irc,nf_conntrack_proto_gre,nf_conntrack_ftp,nf_nat_h323,nf_nat_sip
libcrc32c              16384  2 nf_conntrack,nf_nat
ccm                    20480  6
appletalk              36864  0
ipx                    28672  0
p8023                  16384  1 ipx
psnap                  16384  2 appletalk,ipx
p8022                  16384  1 ipx
llc                    16384  2 p8022,psnap
snd_hda_codec_hdmi     49152  1
snd_hda_codec_realtek   106496  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
snd_hda_intel          40960  6
snd_hda_codec         126976  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
snd_hda_core           81920  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
snd_hwdep              20480  1 snd_hda_codec
snd_pcm                98304  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
mxm_wmi                16384  0
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
snd_seq                65536  2 snd_seq_midi,snd_seq_midi_event
pcbc                   16384  0
arc4                   16384  2
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
snd_timer              32768  2 snd_seq,snd_pcm
rtl8192ee             110592  0
aesni_intel           188416  4
btcoexist             135168  1 rtl8192ee
rtl_pci                32768  1 rtl8192ee
aes_x86_64             20480  1 aesni_intel
rtlwifi                77824  3 rtl_pci,btcoexist,rtl8192ee
snd                    81920  23 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi
crypto_simd            16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
intel_cstate           20480  0
intel_rapl_perf        16384  0
mac80211              778240  3 rtl_pci,rtlwifi,rtl8192ee
joydev                 24576  0
soundcore              16384  1 snd
serio_raw              16384  0
cfg80211              622592  2 rtlwifi,mac80211
input_leds             16384  0
shpchp                 36864  0
intel_pch_thermal      16384  0
idma64                 20480  0
virt_dma               16384  1 idma64
sch_fq_codel           20480  7
mei_me                 40960  0
intel_lpss_pci         20480  0
intel_lpss             16384  1 intel_lpss_pci
mei                    90112  1 mei_me
wmi                    24576  1 mxm_wmi
acpi_pad              180224  0
mac_hid                16384  0
parport_pc             36864  1
ppdev                  20480  0
lp                     20480  0
parport                49152  3 parport_pc,lp,ppdev
ip_tables              28672  2 iptable_filter,iptable_nat
x_tables               40960  6 xt_conntrack,iptable_filter,xt_tcpudp,ipt_MASQUERADE,ipt_REJECT,ip_tables
autofs4                40960  2
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  2 usbhid,hid_generic
i915                 1617920  29
i2c_algo_bit           16384  1 i915
drm_kms_helper        172032  1 i915
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
psmouse               147456  0
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
i2c_i801               28672  0
8139too                36864  0
ahci                   36864  2
8139cp                 28672  0
drm                   401408  17 drm_kms_helper,i915
mii                    16384  2 8139cp,8139too
r8168                 524288  0
libahci                32768  1 ahci
video                  45056  1 i915
pinctrl_sunrisepoint    28672  0
```

Hmm... that's weird, looks like 8139cp is up and running, but it shouldn't be... Here's my **etc/modprobe.d/blacklist.conf**:

```
# This file lists those modules which we don't want to be loaded by# alias expansion, usually so some other driver will be loaded for the
# device instead.


# evbug is a debug tool that should be loaded explicitly
blacklist evbug


# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd


# replaced by e100
blacklist eepro100


# replaced by tulip
blacklist de4x5


# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394


# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m


# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2


# replaced by p54pci
blacklist prism54


# replaced by b43 and ssb.
blacklist bcm43xx


# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps


# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi


# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp


# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr


# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist r8169
blacklist 8139cp
```

---

### Post by praseodym on 2019-01-06
Ok:
```

sudo modprobe -rfv 8139too 8139cp
sudo modprobe -v 8139too
sudo depmod -a
sudo update-initramfs -u
```

---

### Post by anticlimactic on 2019-01-06
Done. 8139cp is gone now, but bandwidth is still the same. Here's the latest diag file:  [http://paste.ubuntu.com/p/G3GMxgt3dj/](http://paste.ubuntu.com/p/G3GMxgt3dj/)
And lsmod (just in case):
```
vladimir@Vovan-PC:~/Desktop$ sudo lsmodModule                  Size  Used by
ipt_MASQUERADE         16384  1
nf_nat_masquerade_ipv4    16384  1 ipt_MASQUERADE
xt_conntrack           16384  1
ipt_REJECT             16384  2
nf_reject_ipv4         16384  1 ipt_REJECT
xt_tcpudp              16384  4
iptable_filter         16384  1
nf_nat_h323            20480  0
nf_conntrack_h323      73728  1 nf_nat_h323
nf_nat_pptp            16384  0
nf_nat_proto_gre       16384  1 nf_nat_pptp
nf_conntrack_pptp      16384  1 nf_nat_pptp
nf_conntrack_proto_gre    16384  1 nf_conntrack_pptp
nf_nat_tftp            16384  0
nf_conntrack_tftp      16384  1 nf_nat_tftp
nf_nat_sip             20480  0
nf_conntrack_sip       28672  1 nf_nat_sip
nf_nat_irc             16384  0
nf_conntrack_irc       16384  1 nf_nat_irc
nf_nat_ftp             16384  0
nf_conntrack_ftp       20480  1 nf_nat_ftp
iptable_nat            16384  1
nf_conntrack_ipv4      16384  3
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
nf_nat_ipv4            16384  1 iptable_nat
nf_nat                 32768  9 nf_nat_masquerade_ipv4,nf_nat_irc,nf_nat_ftp,nf_nat_ipv4,nf_nat_tftp,nf_nat_pptp,nf_nat_h323,nf_nat_proto_gre,nf_nat_sip
nf_conntrack          131072  19 xt_conntrack,nf_nat_masquerade_ipv4,nf_nat_irc,nf_conntrack_ipv4,nf_nat,nf_conntrack_tftp,nf_nat_ftp,nf_conntrack_pptp,ipt_MASQUERADE,nf_nat_ipv4,nf_nat_tftp,nf_conntrack_sip,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_irc,nf_conntrack_proto_gre,nf_conntrack_ftp,nf_nat_h323,nf_nat_sip
libcrc32c              16384  2 nf_conntrack,nf_nat
ccm                    20480  9
appletalk              36864  0
ipx                    28672  0
p8023                  16384  1 ipx
psnap                  16384  2 appletalk,ipx
p8022                  16384  1 ipx
llc                    16384  2 p8022,psnap
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
kvm_intel             212992  0
mxm_wmi                16384  0
snd_hda_codec_hdmi     49152  1
kvm                   598016  1 kvm_intel
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
snd_hda_codec_realtek   106496  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
pcbc                   16384  0
snd_hda_intel          40960  6
snd_hda_codec         126976  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
snd_hda_core           81920  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
snd_hwdep              20480  1 snd_hda_codec
snd_pcm                98304  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
arc4                   16384  2
rtl8192ee             110592  0
snd_seq                65536  2 snd_seq_midi,snd_seq_midi_event
aesni_intel           188416  6
btcoexist             135168  1 rtl8192ee
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
rtl_pci                32768  1 rtl8192ee
aes_x86_64             20480  1 aesni_intel
joydev                 24576  0
snd_timer              32768  2 snd_seq,snd_pcm
rtlwifi                77824  3 rtl_pci,btcoexist,rtl8192ee
crypto_simd            16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
input_leds             16384  0
intel_cstate           20480  0
mac80211              778240  3 rtl_pci,rtlwifi,rtl8192ee
intel_rapl_perf        16384  0
snd                    81920  23 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi
serio_raw              16384  0
soundcore              16384  1 snd
cfg80211              622592  2 rtlwifi,mac80211
shpchp                 36864  0
idma64                 20480  0
virt_dma               16384  1 idma64
mei_me                 40960  0
mei                    90112  1 mei_me
intel_pch_thermal      16384  0
intel_lpss_pci         20480  0
intel_lpss             16384  1 intel_lpss_pci
sch_fq_codel           20480  7
wmi                    24576  1 mxm_wmi
mac_hid                16384  0
acpi_pad              180224  0
parport_pc             36864  1
ppdev                  20480  0
lp                     20480  0
parport                49152  3 parport_pc,lp,ppdev
ip_tables              28672  2 iptable_filter,iptable_nat
x_tables               40960  6 xt_conntrack,iptable_filter,xt_tcpudp,ipt_MASQUERADE,ipt_REJECT,ip_tables
autofs4                40960  2
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  2 usbhid,hid_generic
i915                 1617920  28
i2c_algo_bit           16384  1 i915
8139too                36864  0
drm_kms_helper        172032  1 i915
mii                    16384  1 8139too
psmouse               147456  0
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
i2c_i801               28672  0
fb_sys_fops            16384  1 drm_kms_helper
ahci                   36864  2
drm                   401408  17 drm_kms_helper,i915
libahci                32768  1 ahci
r8168                 524288  0
video                  45056  1 i915
pinctrl_sunrisepoint    28672  0

```

---

### Post by anticlimactic on 2019-01-07
Also switched my Wi-Fi hotspot from WPA/WPA2 to WEP mode using *nm-connection-editor* tool, but it didn't help either...

---

