---
title: "Lenovo Thinkpad T430u unable to connect to wifi"
date: 2013-12-03
forum: Networking &amp; Wireless
---

### Post by geraldvillorente on 2013-12-03
I just got my Thinkpad T430u and I installed Ubuntu 13.10 on it. In the beginning of the setup I manage to connect to wifi but after more or less 2 minutes it got disconnected. I tried to reconnect but I'm not able to connect anymore. So I decided to connect via eth0 (wired) to install all updates. After the installation of OS I tried to connect to wifi again but still I can't establish a successful conis nection.

This thread is very similar but no solution posted - [http://ubuntuforums.org/showthread.php?t=2059189](http://ubuntuforums.org/showthread.php?t=2059189)

lspci:

```
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation UM77 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 3D controller: NVIDIA Corporation GF117M [GeForce 610M/710M / GT 620M/625M/630M/720M] (rev a1)
03:00.0 Network controller: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter (rev 01)
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01)
04:00.1 SD Host controller: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 07)
```

lsmod:

```
btrfs                 815968  0 
raid6_pq               97812  1 btrfs
zlib_deflate           26885  1 btrfs
xor                    21411  1 btrfs
ufs                    74590  0 
qnx4                   13317  0 
hfsplus               102646  0 
hfs                    54590  0 
minix                  36111  0 
ntfs                   96882  0 
msdos                  17332  0 
jfs                   180909  0 
xfs                   884143  0 
libcrc32c              12615  2 xfs,btrfs
reiserfs              245794  0 
ext2                   72832  0 
nfnetlink_queue        18117  0 
nfnetlink_log          17908  0 
nfnetlink              14606  2 nfnetlink_log,nfnetlink_queue
dm_crypt               22728  1 
michael_mic            12612  0 
arc4                   12608  0 
x86_pkg_temp_thermal    14162  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm_intel             138538  0 
kvm                   431315  1 kvm_intel
lib80211_crypt_tkip    17619  0 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
parport_pc             32701  0 
aesni_intel            55624  4042 
wl                   4207474  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  1 lrw
ppdev                  17671  0 
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
joydev                 17377  0 
cryptd                 20329  2023 ghash_clmulni_intel,aesni_intel,ablk_helper
bnep                   19564  2 
rfcomm                 69070  12 
btusb                  28267  0 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
bluetooth             371874  22 bnep,btusb,rfcomm
videobuf2_core         40469  1 uvcvideo
videodev              133390  2 uvcvideo,videobuf2_core
snd_hda_codec_hdmi     41276  1 
snd_hda_codec_realtek    51465  1 
psmouse                97626  0 
snd_hda_intel          48171  3 
snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
thinkpad_acpi          80701  0 
lib80211               14352  2 wl,lib80211_crypt_tkip
serio_raw              13413  0 
cfg80211              479757  1 wl
microcode              23518  0 
nvram                  14362  1 thinkpad_acpi
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30095  1 snd_seq_midi
rtsx_pci_ms            18151  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
memstick               16760  1 rtsx_pci_ms
snd_hwdep              13602  1 snd_hda_codec
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_timer              29433  2 snd_pcm,snd_seq
snd                    69141  18 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,thinkpad_acpi,snd_seq_device,snd_seq_midi
mei_me                 18421  0 
soundcore              12680  1 snd
mei                    77692  1 mei_me
tpm_tis                19123  0 
lpc_ich                21080  0 
mac_hid                13205  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 53014  0 
hid                   101512  2 hid_generic,usbhid
rtsx_pci_sdmmc         23527  0 
i915                  655752  4 
nouveau               943295  0 
ahci                   25819  2 
libahci                31898  1 ahci
r8169                  67341  0 
mxm_wmi                13021  1 nouveau
sdhci_pci              18985  0 
sdhci                  42630  1 sdhci_pci
ttm                    83995  1 nouveau
mii                    13934  1 r8169
i2c_algo_bit           13413  2 i915,nouveau
rtsx_pci               45546  2 rtsx_pci_ms,rtsx_pci_sdmmc
drm_kms_helper         52651  2 i915,nouveau
drm                   296739  7 ttm,i915,drm_kms_helper,nouveau
wmi                    19070  2 mxm_wmi,nouveau
video                  19318  2 i915,nouveau
```

lshw -class network:

```
*-network               
       description: Wireless interface
       product: BCM4313 802.11bgn Wireless Network Adapter
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 2c:d0:5a:b2:0a:21
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.141 (r415941) latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:17 memory:f4700000-f4703fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 07
       serial: 08:9e:01:a0:b0:90
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.1.106 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:45 ioport:3000(size=256) memory:f3c04000-f3c04fff memory:f3c00000-f3c03fff
```

iwconfig eth1:

```
eth1      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

ifconfig eth1:

```
eth1      Link encap:Ethernet  HWaddr 2c:d0:5a:b2:0a:21  
          inet6 addr: fe80::2ed0:5aff:feb2:a21/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:114 errors:0 dropped:0 overruns:0 frame:38968
          TX packets:520 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20728 (20.7 KB)  TX bytes:114712 (114.7 KB)
          Interrupt:17 
```

Any ideas?

---

### Post by varunendra on 2013-12-04
Please do -
```
sudo apt-get purge bcmwl-kernel-source
```
Then reboot.

This will purge the proprietary wl driver and on next boot, the native brcmsmac driver will load which works better with BCM4313 card.

---

