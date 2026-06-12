---
title: "WiFi networks not detected"
date: 2013-10-06
forum: Networking &amp; Wireless
---

### Post by ram10 on 2013-10-06
Dear all ,

I am running ubuntu 13.04 on a Dell studio 1558 laptop. I was using my WiFi but today it got disconnected all of a sudden and now my laptop is not detecting any wifi network. My mobile can detect the wifi network so i am guessing the problem is with my machine and not the router. I have a broadcomm driver installed in my laptop. Please let me know what more details you will be needing to solve this issue.

 Any help will be appreciated.

Regards,
Ram

---

### Post by Hadaka on 2013-10-06
Hi, please post the output of..
```
lspci -nnk | grep -iA3 net
lsmod
rfkill list all
```
thanks.

---

### Post by ram10 on 2013-10-06
Thank you very much for your reply Hadaka.  I tried and what you said and my system has thrown out a bit lengthy output. Unfortunately I am using my mobile as I am unable to get my system online. So if you could tell me what variables you are looking for in the output I could enter it manually and post it here.

---

### Post by Hadaka on 2013-10-06
Hi, on the first command..
{lspci} I need the 2 [14e4XXXX] numbers
{lsmod} Tell me if it says WL or b43
{rfkill} any YES
thanks.

---

### Post by ram10 on 2013-10-06
Rfkill says no, lsmod says wl but there is only one instance under network controller where lspci says 14e4 :4353 and Ethernet controller says 10ec:8168

---

### Post by Hadaka on 2013-10-06
Hi, you are going to need a wired connection, does this
work wired? If not, perhaps you can "borrow" one.
meantime try this..
```
sudo modpobe -rf wl
sudo modprobe -v wl
```
thanks.

---

### Post by ram10 on 2013-10-07
Wired connection works perfectly though.
Modprobe throws this
insmod /lib/modules/3.8.0-31-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.8.0-31-generic/updates/dkms/wl.ko

---

### Post by Hadaka on 2013-10-07
ok, from a wired connection please do and post..
```
lsmod
sudo modprobe -rf wl
sudo modprobe -v wl
dmesg | grep wlan0
```
thanks

---

### Post by nathanservicesinc2 on 2013-10-07
You may have to do like I did and download IPTABLES and XINTED; these will help you analyze where your conncections are missing.   There is a manual that comes with them so you'll have to learn the command line to work with them.

---

### Post by ram10 on 2013-10-08
well this might be of some help 
dmesg throws this
[   28.982735] eth1: Broadcom BCM4353 802.11 Hybrid Wireless Controller 6.20.155.1 (r326264)
[   29.000387] init: plymouth-stop pre-start process (1592) terminated with status 1
[   29.142870] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[   29.143079] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[   52.011251] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[   84.941028] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)


[B]
lsmod[/B]
Module                  Size  Used by
lib80211_crypt_tkip    17379  0 
lib80211               14352  1 lib80211_crypt_tkip
pci_stub               12622  1 
vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             23479  0 
vboxdrv               320461  3 vboxnetadp,vboxnetflt,vboxpci
parport_pc             28152  0 
ppdev                  17073  0 
bnep                   18036  2 
rfcomm                 42641  0 
bluetooth             228808  10 bnep,rfcomm
snd_hda_codec_hdmi     41169  1 
joydev                 17377  0 
coretemp               13355  0 
kvm_intel             132891  0 
kvm                   443165  1 kvm_intel
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
snd_hda_codec_idt      50434  1 
snd_hda_intel          43729  5 
snd_hda_codec         194782  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
wmi                    19070  1 dell_wmi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
video                  19390  0 
radeon                942029  3 
dell_laptop            17369  0 
dcdbas                 14397  1 dell_laptop
ttm                    83187  1 radeon
snd                    68876  20 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
drm_kms_helper         49394  1 radeon
mac_hid                13205  0 
intel_ips              17978  0 
uvcvideo               80847  0 
drm                   286028  5 ttm,drm_kms_helper,radeon
mei                    41158  0 
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40513  1 uvcvideo
i2c_algo_bit           13413  1 radeon
psmouse                95905  0 
microcode              22881  0 
videodev              129260  2 uvcvideo,videobuf2_core
serio_raw              13215  0 
lpc_ich                17061  0 
soundcore              12680  1 snd
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
ahci                   25731  5 
libahci                31364  1 ahci
firewire_ohci          40103  0 
firewire_core          64508  1 firewire_ohci
sdhci_pci              18590  0 
r8169                  67466  0 
crc_itu_t              12707  1 firewire_core
sdhci                  32522  1 sdhci_pci

modprobe
insmod /lib/modules/3.8.0-31-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.8.0-31-generic/updates/dkms/wl.ko

---

### Post by Hadaka on 2013-10-08
Hi, from a wired connection please do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
```
also check network mgr. and verify that
Enable Wireless and Enable Network are checked.
thanks

---

