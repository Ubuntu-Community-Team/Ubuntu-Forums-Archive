---
title: "Install wireless driver mediatek mt7630e"
date: 2014-06-18
forum: Networking &amp; Wireless
---

### Post by Vyivrain on 2014-06-18
[COLOR=#000000]Hello, I'm trying to install wi-fi driver, but as a beginner don't know what to do, googling didn't do much.So this is information after this commands:
[/COLOR]```
vyivrain@vyivrain-X550VB:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04 LTS"
Linux vyivrain-X550VB 3.13.0-29-generic #53-Ubuntu SMP Wed Jun 4 21:00:20 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```[COLOR=#000000]

[/COLOR]```
vyivrain@vyivrain-X550VB:~$ lspci -nnk | grep -iA2 net
03:00.0 Network controller [0280]: MEDIATEK Corp. MT7630e 802.11bgn Wireless Network Adapter [14c3:7630]
    Subsystem: Foxconn International, Inc. Device [105b:e074]
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5289] (rev 01)
--
04:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0a)
    Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
    Kernel driver in use: r8169
```[COLOR=#000000]

[/COLOR]```
vyivrain@vyivrain-X550VB:~$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.
```[COLOR=#000000]

[/COLOR]```
vyivrain@vyivrain-X550VB:~$ rfkill list all
0: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
```[COLOR=#000000]

[/COLOR]```
vyivrain@vyivrain-X550VB:~$ lsmod
Module                  Size  Used by
btrfs                 835954  0 
raid6_pq               97812  1 btrfs
xor                    21411  1 btrfs
ufs                    74890  0 
qnx4                   13317  0 
hfsplus               107516  0 
hfs                    54677  0 
minix                  36140  0 
ntfs                   97369  0 
msdos                  17332  0 
jfs                   181348  0 
xfs                   912173  0 
libcrc32c              12644  2 xfs,btrfs
bnep                   19624  2 
rfcomm                 69160  0 
bluetooth             395423  10 bnep,rfcomm
snd_hda_codec_hdmi     46207  1 
snd_hda_codec_realtek    61438  1 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
joydev                 17381  0 
videodev              134688  2 uvcvideo,videobuf2_core
asus_nb_wmi            16990  0 
asus_wmi               24191  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
intel_rapl             18773  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm_intel             143060  0 
kvm                   451511  1 kvm_intel
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
psmouse               102222  0 
snd_hda_intel          52355  3 
serio_raw              13462  0 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
lpc_ich                21080  0 
snd                    69238  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
rtsx_pci_ms            18151  0 
memstick               16966  1 rtsx_pci_ms
soundcore              12680  1 snd
mei_me                 18627  0 
mei                    82276  1 mei_me
i915                  783703  4 
nouveau              1097199  1 
mxm_wmi                13021  1 nouveau
ttm                    85115  1 nouveau
drm_kms_helper         52758  2 i915,nouveau
drm                   302817  8 ttm,i915,drm_kms_helper,nouveau
wmi                    19177  3 mxm_wmi,nouveau,asus_wmi
mac_hid                13205  0 
video                  19476  3 i915,nouveau,asus_wmi
i2c_algo_bit           13413  2 i915,nouveau
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 52570  0 
hid                   106148  2 hid_generic,usbhid
rtsx_pci_sdmmc         23274  0 
ahci                   25819  2 
r8169                  67581  0 
libahci                32168  1 ahci
rtsx_pci               45956  2 rtsx_pci_ms,rtsx_pci_sdmmc
mii                    13934  1 r8169
```[COLOR=#000000]

[/COLOR][COLOR=#000000]And after this point I don't know, what to do. Thx for answering.[/COLOR]

---

### Post by cqfd93 on 2014-09-01
Hi,

Check out comment #161 (and if it doesn't work for you, comment #125) of bug #1220146

[https://bugs.launchpad.net/ubuntu/+s...6/comments/161]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1220146/comments/161")
[https://bugs.launchpad.net/ubuntu/+s...6/comments/125]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1220146/comments/125")

Hope this helps

---

