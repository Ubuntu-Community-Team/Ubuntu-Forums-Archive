---
title: "Ubuntu 14.04 - Wi-Fi continuously disconnecting after 5 mins"
date: 2014-05-08
forum: Networking &amp; Wireless
---

### Post by erichs on 2014-05-08
Hi,

I have been having problems with my Wi-Fi in Ubuntu 14.04. I am connected (in this case with 3 bars) and for no apparent reason it disconnects after 5 mins or so. It does not automatically reconnect when this happens which suggests to me that it is not an issue to do with the quality of the connection. In order to solve this I have to disable and re-enable Wi-Fi manually in order for it to work again, and this continues all day which after a while becomes more than just a slight annoyance. 

Help please :)

> 
lspci00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5)
00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d5)
00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d5)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM87 Express LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
01:00.0 3D controller: NVIDIA Corporation GK107M [GeForce GT 745M] (rev ff)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723AE PCIe Wireless Network Adapter
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)


> 
sudo lshw -C network

  *-network               
       description: Wireless interface
       product: RTL8723AE PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 24:0a:64:dd:5b:fa
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8723ae driverversion=3.13.0-24-generic firmware=N/A ip=192.168.1.150 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 ioport:d000(size=256) memory:f7900000-f7903fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 0c
       serial: 54:be:f7:43:9e:73
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-2_0.0.1 02/06/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:46 ioport:c000(size=256) memory:f7800000-f7800fff memory:f2100000-f2103fff


> 
 lsmodModule                  Size  Used by
ctr                    13049  1 
ccm                    17773  1 
bbswitch               13943  0 
nvram                  14411  0 
bnep                   19624  2 
rfcomm                 69160  8 
snd_hda_codec_hdmi     46207  1 
snd_hda_codec_realtek    61438  1 
binfmt_misc            17468  1 
hid_generic            12548  0 
usbhid                 52616  0 
uvcvideo               80885  0 
hid                   106148  2 hid_generic,usbhid
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
btusb                  32412  0 
bluetooth             395423  22 bnep,btusb,rfcomm
nls_iso8859_1          12713  1 
arc4                   12608  2 
mxm_wmi                13021  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm_intel             143060  0 
kvm                   451511  1 kvm_intel
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
rtl8723ae              86464  0 
aesni_intel            55624  2 
rtl_pci                26690  1 rtl8723ae
snd_hda_intel          52355  7 
rtlwifi                63475  2 rtl_pci,rtl8723ae
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
mac80211              626489  3 rtl_pci,rtlwifi,rtl8723ae
snd_hwdep              13602  1 snd_hda_codec
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
joydev                 17381  0 
snd_pcm               102099  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
serio_raw              13462  0 
snd_rawmidi            30144  1 snd_seq_midi
i915                  783485  5 
cfg80211              484040  2 mac80211,rtlwifi
lpc_ich                21080  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
mei_me                 18627  0 
snd_timer              29482  2 snd_pcm,snd_seq
snd                    69238  24 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
mei                    82274  1 mei_me
soundcore              12680  1 snd
drm_kms_helper         52758  1 i915
drm                   302817  4 i915,drm_kms_helper
i2c_algo_bit           13413  1 i915
mac_hid                13205  0 
video                  19476  1 i915
wmi                    19177  1 mxm_wmi
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
r8169                  67581  0 
psmouse               102222  0 
ahci                   25819  3 
mii                    13934  1 r8169
libahci                32168  1 ahci




---

### Post by w00sterf1 on 2014-05-08
This might be a similar situation as in the bug I have reported: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1315470](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1315470)
"wlan0 gets disconnected randomly and can not reconnect"

---

