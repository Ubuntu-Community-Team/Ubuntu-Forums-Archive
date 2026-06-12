---
title: "Ubuntu 18.04 LTS remains in Airplane mode"
date: 2018-05-15
forum: Networking &amp; Wireless
---

### Post by tuddungoggo on 2018-05-15
Hello, is there a way to turn off or toggle off Airplane mode? I read that in 18.04 there is no way to do this and it seems to be a persistent problem. I am unable to turn Wi-Fi back on as well as Bluetooth. Any help would be greatly appreciated. thanks!

---

### Post by wildmanne39 on 2018-05-15
*Thread moved to **Networking & Wireless for a more appropriate fit**.*

---

### Post by tuddungoggo on 2018-05-15
> **wildmanne39 said:**
> *Thread moved to **Networking & Wireless for a more appropriate fit**.*

Thank you

---

### Post by chili555 on 2018-05-16
Have you tried the physical switch?

Please run and post:```
rfkill list all
lsmod
```What brand and model of computer is it?

---

### Post by tuddungoggo on 2018-05-16
> **chili555 said:**
> Have you tried the physical switch?

Please run and post:```
rfkill list all
lsmod
```What brand and model of computer is it?

Yep, I tried the hardware switch, and that did not work as well. I have to pretty much be hardwired in via RJ-45/Ethernet now on my Computer to get any type of Network connectivity. With that said, here is the output you requested:


```

lamidotijjo ~ $ rfkill list all
0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
lamidotijjo ~ $ lsmod
Module                  Size  Used by
rndis_host             16384  0
cdc_ether              16384  1 rndis_host
usbnet                 45056  2 rndis_host,cdc_ether
mii                    16384  1 usbnet
cdc_acm                32768  0
nls_iso8859_1          16384  1
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
kvm_intel             204800  0
kvm                   593920  1 kvm_intel
irqbypass              16384  1 kvm
intel_cstate           20480  0
arc4                   16384  2
intel_rapl_perf        16384  0
uvcvideo               86016  0
snd_hda_codec_hdmi     49152  1
iwldvm                229376  0
input_leds             16384  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
mac80211              778240  1 iwldvm
snd_hda_codec_conexant    24576  1
videobuf2_v4l2         24576  1 uvcvideo
snd_hda_codec_generic    73728  1 snd_hda_codec_conexant
joydev                 24576  0
videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2
snd_seq_midi           16384  0
serio_raw              16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
wmi_bmof               16384  0
snd_hda_intel          40960  6
videodev              184320  3 uvcvideo,videobuf2_core,videobuf2_v4l2
snd_rawmidi            32768  1 snd_seq_midi
thinkpad_acpi          94208  1
media                  40960  2 uvcvideo,videodev
iwlwifi               278528  1 iwldvm
snd_hda_codec         126976  4 snd_hda_intel,snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_codec_generic
snd_hda_core           81920  5 snd_hda_intel,snd_hda_codec_conexant,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic
ip6t_REJECT            16384  1
snd_hwdep              20480  1 snd_hda_codec
nf_reject_ipv6         16384  1 ip6t_REJECT
nvram                  16384  1 thinkpad_acpi
cfg80211              622592  3 iwlwifi,mac80211,iwldvm
lpc_ich                24576  0
snd_pcm                98304  4 snd_hda_intel,snd_hda_codec,snd_hda_core,snd_hda_codec_hdmi
nf_log_ipv6            16384  5
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
shpchp                 36864  0
xt_hl                  16384  22
mei_me                 40960  0
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
mei                    90112  1 mei_me
ip6t_rt                16384  3
snd_timer              32768  2 snd_seq,snd_pcm
snd                    81920  24 snd_hda_intel,snd_hwdep,snd_hda_codec_conexant,snd_seq,snd_hda_codec,snd_timer,thinkpad_acpi,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_pcm
soundcore              16384  1 snd
mac_hid                16384  0
nf_conntrack_ipv6      20480  8
nf_defrag_ipv6         36864  1 nf_conntrack_ipv6
ipt_REJECT             16384  1
nf_reject_ipv4         16384  1 ipt_REJECT
nf_log_ipv4            16384  5
nf_log_common          16384  2 nf_log_ipv6,nf_log_ipv4
xt_LOG                 16384  10
xt_limit               16384  13
xt_tcpudp              16384  18
xt_addrtype            16384  4
nf_conntrack_ipv4      16384  8
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
xt_conntrack           16384  16
ip6table_filter        16384  1
ip6_tables             28672  1 ip6table_filter
nf_conntrack_netbios_ns    16384  0
nf_conntrack_broadcast    16384  1 nf_conntrack_netbios_ns
nf_nat_ftp             16384  0
nf_nat                 32768  1 nf_nat_ftp
nf_conntrack_ftp       20480  1 nf_nat_ftp
nf_conntrack          131072  8 nf_conntrack_ipv6,nf_conntrack_ftp,nf_conntrack_ipv4,nf_conntrack_broadcast,nf_nat_ftp,nf_conntrack_netbios_ns,xt_conntrack,nf_nat
libcrc32c              16384  2 nf_conntrack,nf_nat
sch_fq_codel           20480  3
parport_pc             36864  0
ppdev                  20480  0
iptable_filter         16384  1
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
ip_tables              28672  1 iptable_filter
x_tables               40960  13 xt_LOG,ipt_REJECT,ip_tables,iptable_filter,xt_tcpudp,xt_limit,ip6t_REJECT,ip6table_filter,xt_addrtype,ip6t_rt,xt_conntrack,ip6_tables,xt_hl
autofs4                40960  2
algif_skcipher         16384  0
af_alg                 24576  1 algif_skcipher
dm_crypt               36864  2
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  2 hid_generic,usbhid
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
i915                 1617920  21
pcbc                   16384  0
i2c_algo_bit           16384  1 i915
aesni_intel           188416  1243
drm_kms_helper        167936  1 i915
aes_x86_64             20480  1 aesni_intel
crypto_simd            16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
cryptd                 24576  624 crypto_simd,ghash_clmulni_intel,aesni_intel
psmouse               147456  0
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
ahci                   36864  3
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
libahci                32768  1 ahci
sdhci_pci              28672  0
e1000e                249856  0
sdhci                  49152  1 sdhci_pci
drm                   401408  15 i915,drm_kms_helper
ptp                    20480  1 e1000e
pps_core               20480  1 ptp
wmi                    24576  1 wmi_bmof
video                  40960  2 thinkpad_acpi,i915




```

The Computer is a Lenovo Thinkpad X220.

---

### Post by chili555 on 2018-05-16
Please try an experiment; from the terminal:```
sudo modprobe -r thinkpad_acpi
```Now try the physical switch. Any improvement?

Doesn't your X220 have a wireless switch on the left side? What is the position of this switch? [https://www.laptopmag.com/images/uploads/ppress/43833/lenovo%20thinkpad%20x230_g13.jpg](https://www.laptopmag.com/images/uploads/ppress/43833/lenovo%20thinkpad%20x230_g13.jpg)

---

### Post by tuddungoggo on 2018-05-16
> **chili555 said:**
> Please try an experiment; from the terminal:```
sudo modprobe -r thinkpad_acpi
```Now try the physical switch. Any improvement?

Doesn't your X220 have a wireless switch on the left side? What is the position of this switch? [https://www.laptopmag.com/images/uploads/ppress/43833/lenovo%20thinkpad%20x230_g13.jpg](https://www.laptopmag.com/images/uploads/ppress/43833/lenovo%20thinkpad%20x230_g13.jpg)

Gah, that was it, I feel like a fool now. It was the physical switch on the left side of the laptop. Thanks!

---

### Post by chili555 on 2018-05-16
No worries at all. We've all done it a time or two! Glad it's working.

---

