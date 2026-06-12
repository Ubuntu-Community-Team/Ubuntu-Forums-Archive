---
title: "Wi-fi hard blocked, rfkill unblock aint working UBUNTU 14.04"
date: 2016-12-12
forum: Networking &amp; Wireless
---

### Post by torresmo on 2016-12-12
Tried rebooting, restoring bios default, unblocking via rfkill unblock but cant figure out how to proceed

lspci

```
00:00.0 Host bridge: Intel Corporation Broadwell-U Host Bridge -OPI (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Broadwell-U Integrated Graphics (rev 09)
00:03.0 Audio device: Intel Corporation Broadwell-U Audio Controller (rev 09)
00:14.0 USB controller: Intel Corporation Wildcat Point-LP USB xHCI Controller (rev 03)
00:16.0 Communication controller: Intel Corporation Wildcat Point-LP MEI Controller #1 (rev 03)
00:1b.0 Audio device: Intel Corporation Wildcat Point-LP High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #1 (rev e3)
00:1c.2 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #3 (rev e3)
00:1c.3 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #4 (rev e3)
00:1c.4 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #5 (rev e3)
00:1d.0 USB controller: Intel Corporation Wildcat Point-LP USB EHCI Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation Wildcat Point-LP LPC Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation Wildcat Point-LP SATA Controller [AHCI Mode] (rev 03)
00:1f.3 SMBus: Intel Corporation Wildcat Point-LP SMBus Controller (rev 03)
06:00.0 Network controller: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 07)
08:00.0 3D controller: NVIDIA Corporation Device 1299 (rev a1)
```

lsusb

```
Bus 001 Device 002: ID 8087:8001 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 002 Device 004: ID 064e:920b Suyin Corp. 
Bus 002 Device 003: ID 1532:011b Razer USA, Ltd 
Bus 002 Device 002: ID 1532:0037 Razer USA, Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

lsmod


```
Module                  Size  Used by
bbswitch               13943  0 
nvram                  14411  0 
input_polldev          13896  0 
rfcomm                 69160  0 
bnep                   19624  2 
bluetooth             391136  10 bnep,rfcomm
binfmt_misc            17468  1 
nls_iso8859_1          12713  1 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
rts5139               335409  0 
joydev                 17381  0 
dell_led               12920  1 
snd_hda_codec_realtek    75588  1 
snd_hda_codec_generic    68898  1 snd_hda_codec_realtek
snd_hda_codec_hdmi     51975  1 
dell_wmi               12761  0 
sparse_keymap          13948  1 dell_wmi
mxm_wmi                13021  0 
xhci_quirk             17436  0 
arc4                   12608  2 
dell_laptop            18168  0 
x86_pkg_temp_thermal    14205  0 
coretemp               13435  0 
dcdbas                 14928  1 dell_laptop
kvm_intel             143187  0 
kvm                   455794  1 kvm_intel
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
snd_seq_midi           13324  0 
ath9k                 164164  0 
snd_seq_midi_event     14899  1 snd_seq_midi
ath9k_common           13551  1 ath9k
aesni_intel            55624  0 
snd_hda_intel          30779  5 
snd_hda_controller     31921  1 snd_hda_intel
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
ath9k_hw              453856  2 ath9k_common,ath9k
snd_rawmidi            30144  1 snd_seq_midi
snd_hda_codec         139695  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
snd_hwdep              13602  1 snd_hda_codec
mac80211              630728  1 ath9k
snd_pcm               102099  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_page_alloc         18710  3 snd_pcm,snd_hda_intel,snd_hda_controller
parport_pc             32701  0 
cfg80211              484040  3 ath,ath9k,mac80211
ppdev                  17671  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
i915_bdw              843134  7 
psmouse               106647  0 
snd_timer              29482  2 snd_pcm,snd_seq
lpc_ich                21080  0 
serio_raw              13462  0 
mei_me                 18627  0 
snd                    69322  22 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
mei                    82276  1 mei_me
shpchp                 37032  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
soundcore              12680  2 snd,snd_hda_codec
intel_ips              18664  1 i915_bdw
drm_kms_helper         55071  1 i915_bdw
i2c_algo_bit           13413  1 i915_bdw
wmi                    19177  3 dell_led,dell_wmi,mxm_wmi
i2c_designware_platform    12960  0 
i2c_designware_core    14768  1 i2c_designware_platform
mac_hid                13205  0 
acpi_pad               17926  0 
btrfs                 835994  0 
xor                    21411  1 btrfs
raid6_pq               97812  1 btrfs
libcrc32c              12644  1 btrfs
hid_generic            12548  0 
usbhid                 48432  0 
hid                   106059  2 hid_generic,usbhid
nvidia_drm             14707  0 
nvidia_modeset        777238  1 nvidia_drm
drm                   303102  6 i915_bdw,drm_kms_helper,nvidia_drm
nvidia              11930797  1 nvidia_modeset
ahci                   34091  3 
libahci                32716  1 ahci
r8169                  71677  0 
mii                    13934  1 r8169
video                  19476  1 i915_bdw
```

---

### Post by praseodym on 2016-12-12
Any button/switch/key or key combo?

---

### Post by torresmo on 2016-12-12
theres none

---

### Post by chili555 on 2016-12-12
> **torresmo said:**
> theres noneWhat make and model is the computer?

---

### Post by torresmo on 2016-12-12
> **chili555 said:**
> What make and model is the computer?
its a dell inspiron 5458

---

### Post by chili555 on 2016-12-12
The Quickstart Guide suggests that you* do* have a key.

[ATTACH=CONFIG]272682[/ATTACH]

---

