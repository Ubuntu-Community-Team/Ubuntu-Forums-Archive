---
title: "Atheros AR9485"
date: 2013-11-28
forum: Networking &amp; Wireless
---

### Post by jindra.eleron on 2013-11-28
Hi, I saw post about this, but resolution didn't working. So I am creating new thread. I cant turn on wifi on my new ntb. It doesn't have hardware switch, Fn F2 does nothing, so these are my resoluts from terminal: 

muff@muff-X550VC:~$ sudo lshw -C network
[sudo] password for muff: 
  *-network DISABLED      
       description: Wireless interface
       product: AR9485 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 24:0a:64:78:e3:a3
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.8.0-33-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f7900000-f797ffff memory:f7980000-f798ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168 PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.2
       bus info: pci@0000:04:00.2
       logical name: eth0
       version: 0a
       serial: d8:50:e6:21:ad:36
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8411-1_0.0.3 06/18/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:d000(size=256) memory:f2104000-f2104fff memory:f2100000-f2103fff
muff@muff-X550VC:~$ lspci -nn | grep -e 0280 -e 0200
03:00.0 Network controller [0280]: Atheros Communications Inc. AR9485 Wireless Network Adapter [168c:0032] (rev 01)
04:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 0a)
muff@muff-X550VC:~$ iwconfig
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

eth0      no wireless extensions.

muff@muff-X550VC:~$ rfkill list all
0: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
muff@muff-X550VC:~$ lsmod
Module                  Size  Used by
nls_utf8               12493  1 
isofs                  39211  1 
parport_pc             27504  0 
ppdev                  12817  0 
bnep                   17669  2 
rfcomm                 37420  0 
uvcvideo               71279  0 
videobuf2_vmalloc      12920  1 uvcvideo
videobuf2_memops       13042  1 videobuf2_vmalloc
videobuf2_core         39161  1 uvcvideo
videodev               95806  2 uvcvideo,videobuf2_core
coretemp               13131  0 
snd_hda_codec_hdmi     36186  1 
snd_hda_codec_realtek    63791  1 
joydev                 17097  0 
kvm_intel             126842  0 
snd_hda_intel          38307  9 
kvm                   376505  1 kvm_intel
snd_hda_codec         117617  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80890  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
arc4                   12543  2 
ath9k                 134875  0 
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
aesni_intel            18156  0 
aes_i586               16995  1 aesni_intel
snd_seq_midi           13132  0 
xts                    12749  1 aesni_intel
ath9k_common           13783  1 ath9k
snd_seq_midi_event     14475  1 snd_seq_midi
ath9k_hw              398477  2 ath9k_common,ath9k
snd_rawmidi            25114  1 snd_seq_midi
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
lrw                    13057  1 aesni_intel
ath                    19187  3 ath9k_common,ath9k,ath9k_hw
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
nouveau               838609  0 
gf128mul               14503  2 lrw,xts
mac80211              526519  1 ath9k
ablk_helper            13357  1 aesni_intel
snd_timer              24411  2 snd_pcm,snd_seq
ath3k                  12790  0 
cryptd                 15613  1 ablk_helper
i915                  539721  6 
btusb                  17986  0 
ttm                    71289  1 nouveau
drm_kms_helper         47545  2 i915,nouveau
psmouse                81065  0 
cfg80211              436243  3 ath,ath9k,mac80211
drm                   228489  9 ttm,i915,drm_kms_helper,nouveau
bluetooth             202232  12 bnep,ath3k,btusb,rfcomm
snd                    56485  28 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              12600  1 snd
i2c_algo_bit           13197  2 i915,nouveau
asus_nb_wmi            12734  0 
microcode              18286  0 
asus_wmi               23517  1 asus_nb_wmi
sparse_keymap          13658  1 asus_wmi
mxm_wmi                12893  1 nouveau
video                  18894  3 i915,nouveau,asus_wmi
serio_raw              13031  0 
rtsx_pci_ms            12875  0 
wmi                    18590  3 mxm_wmi,nouveau,asus_wmi
mei                    36197  0 
mac_hid                13037  0 
lpc_ich                16925  0 
memstick               15842  1 rtsx_pci_ms
lp                     13299  0 
parport                40753  3 lp,ppdev,parport_pc
rtsx_pci_sdmmc         17238  0 
rtsx_pci               32831  2 rtsx_pci_ms,rtsx_pci_sdmmc
r8169                  61543  0 
ahci                   25507  3 
libahci                26108  1 ahci
muff@muff-X550VC:~$ 




Can anyone help, please? :( 

old threat : [http://ubuntuforums.org/showthread.php?t=1846107](http://ubuntuforums.org/showthread.php?t=1846107)
Ntb : Asus x550VC, i5 core, os - only ubuntu..

---

### Post by Bucky Ball on 2013-11-28
Can you plug in an ethernet cable, do an update and check Additional Drivers?

---

