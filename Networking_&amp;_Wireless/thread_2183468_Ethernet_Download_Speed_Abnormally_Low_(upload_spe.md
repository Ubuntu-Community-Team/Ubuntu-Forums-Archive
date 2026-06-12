---
title: "Ethernet Download Speed Abnormally Low (upload speed is fine, wireless is also fine)"
date: 2013-10-25
forum: Networking &amp; Wireless
---

### Post by iarenoob on 2013-10-25
Today, my download speed over ethernet suddenly dropped to nearly non-existent levels while my upload speeds remained more or less normal.  Wireless speeds are also normal.  Something similar has happened once or twice before but the problem usually went away by itself after awhile/after reboot, this time it's staying.  As far as I can tell the problem began when I was about halfway through the update to 13.10 so I'm not sure if the update has anything to do with it.

My speedtest looks like this:
[IMG]http://www.speedtest.net/result/3055917377.png[/IMG]

ifconfig:
```

eth0      Link encap:Ethernet  HWaddr 00:90:f5:d0:e5:12            inet addr:130.126.211.166  Bcast:130.126.211.255  Mask:255.255.252.0
          inet6 addr: fe80::290:f5ff:fed0:e512/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:45443 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29907 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:29007939 (29.0 MB)  TX bytes:16457785 (16.4 MB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2656 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2656 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:320771 (320.7 KB)  TX bytes:320771 (320.7 KB)


wlan0     Link encap:Ethernet  HWaddr 58:91:cf:27:66:45  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:51394 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57437 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:45565082 (45.5 MB)  TX bytes:48937940 (48.9 MB)



```

lsmod:
```

Module                  Size  Used by
r8169                  67341  0 
mii                    13934  1 r8169
pci_stub               12622  1 
vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             23479  0 
vboxdrv               320455  3 vboxnetadp,vboxnetflt,vboxpci
cuse                   13274  3 
joydev                 17377  0 
parport_pc             32701  0 
ppdev                  17671  0 
rfcomm                 69070  0 
bnep                   19564  2 
bluetooth             371874  10 bnep,rfcomm
snd_hda_codec_hdmi     41276  1 
snd_hda_codec_via      27860  1 
binfmt_misc            17468  1 
ip6t_REJECT            12910  1 
xt_hl                  12521  6 
ip6t_rt                13507  3 
nf_conntrack_ipv6      18938  7 
nf_defrag_ipv6         34616  1 nf_conntrack_ipv6
ipt_REJECT             12541  1 
xt_LOG                 17718  10 
xt_limit               12711  13 
xt_tcpudp              12884  22 
xt_addrtype            12635  4 
hid_generic            12548  0 
nf_conntrack_ipv4      15012  7 
arc4                   12608  2 
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
usbhid                 53014  0 
xt_conntrack           12760  14 
hid                   101512  2 hid_generic,usbhid
uvcvideo               80885  0 
iwldvm                237440  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
x86_pkg_temp_thermal    14162  0 
ip6table_filter        12815  1 
intel_powerclamp       14705  0 
videobuf2_core         40469  1 uvcvideo
coretemp               13435  0 
mac80211              596969  1 iwldvm
videodev              133390  2 uvcvideo,videobuf2_core
kvm_intel             138538  0 
kvm                   431315  1 kvm_intel
crct10dif_pclmul       14289  0 
ip6_tables             27025  1 ip6table_filter
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
nf_conntrack_netbios_ns    12665  0 
nf_conntrack_broadcast    12589  1 nf_conntrack_netbios_ns
nf_nat_ftp             12741  0 
nf_nat                 26653  1 nf_nat_ftp
aesni_intel            55624  2 
aes_x86_64             17131  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
nf_conntrack_ftp       18608  1 nf_nat_ftp
cryptd                 20329  3 ghash_clmulni_intel,aesni_intel,ablk_helper
nf_conntrack           91736  8 nf_nat_ftp,nf_conntrack_netbios_ns,nf_nat,xt_conntrack,nf_conntrack_broadcast,nf_conntrack_ftp,nf_conntrack_ipv4,nf_conntrack_ipv6
iptable_filter         12810  1 
ip_tables              27239  1 iptable_filter
x_tables               34059  13 ip6table_filter,xt_hl,ip_tables,xt_tcpudp,xt_limit,xt_conntrack,xt_LOG,iptable_filter,ip6t_rt,ipt_REJECT,ip6_tables,xt_addrtype,ip6t_REJECT
snd_hda_intel          48171  3 
snd_hda_codec         188738  3 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
dm_multipath           22843  0 
scsi_dh                14882  1 dm_multipath
snd_rawmidi            30095  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
microcode              23518  0 
i915                  655752  3 
iwlwifi               165398  1 iwldvm
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
psmouse                97626  0 
cfg80211              479757  3 iwlwifi,mac80211,iwldvm
serio_raw              13413  0 
snd                    69141  17 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_via,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
rtsx_pci_ms            18151  0 
drm_kms_helper         52651  1 i915
memstick               16760  1 rtsx_pci_ms
mei_me                 18421  0 
lpc_ich                21080  0 
drm                   296739  4 i915,drm_kms_helper
mei                    77692  1 mei_me
soundcore              12680  1 snd
i2c_algo_bit           13413  1 i915
wmi                    19070  0 
mac_hid                13205  0 
video                  19318  1 i915
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
btrfs                 815968  0 
xor                    21411  1 btrfs
zlib_deflate           26885  1 btrfs
raid6_pq               97812  1 btrfs
libcrc32c              12615  1 btrfs
rtsx_pci_sdmmc         23527  0 
rtsx_pci               45546  2 rtsx_pci_ms,rtsx_pci_sdmmc
ahci                   25819  2 
libahci                31898  1 ahci
dm_mirror              22056  0 
dm_region_hash         20784  1 dm_mirror
dm_log                 18411  2 dm_region_hash,dm_mirror

```

lspci -v (just the relevant parts)
```

03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5289 (rev 01)
    Subsystem: CLEVO/KAPOK Computer Device 0240
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at f7c00000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 00
    Capabilities: [b0] MSI-X: Enable- Count=1 Masked-
    Capabilities: [d0] Vital Product Data
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 00-00-00-00-00-00-00-00
    Kernel driver in use: rtsx_pci


03:00.2 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0a)
    Subsystem: CLEVO/KAPOK Computer Device 0240
    Flags: bus master, fast devsel, latency 0, IRQ 47
    I/O ports at e000 [size=256]
    Memory at f0004000 (64-bit, prefetchable) [size=4K]
    Memory at f0000000 (64-bit, prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 01
    Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
    Capabilities: [d0] Vital Product Data
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [160] Device Serial Number 01-00-00-00-68-4c-e0-00
    Kernel driver in use: r8169

```

I have tried installing the r8168 driver from realtek, no noticeable changes occurred so I removed it afterwards.

---

### Post by iarenoob on 2013-10-25
Update: Problem seems to have gone away by itself again, I have no clue what happened.
Update2: Problem spontaneously appears again, no idea what's going on.

---

