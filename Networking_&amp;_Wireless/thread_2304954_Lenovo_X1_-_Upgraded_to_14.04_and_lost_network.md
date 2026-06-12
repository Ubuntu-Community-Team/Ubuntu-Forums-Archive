---
title: "Lenovo X1 - Upgraded to 14.04 and lost network"
date: 2015-12-01
forum: Networking &amp; Wireless
---

### Post by scott96 on 2015-12-01
I just did an in-place upgrade from 12.04 to 14.04 and have lost the network.  Neither the usb ethernet dongle (Asix) nor the wifi are working.  When checking with ```
ip link list
``` nothing shows up, so I added wlan0 and eth1 to /etc/network/interfaces, but no luck.  ```
modprobe asix
``` returns nothing and ```
modprobe iwlwifi
``` returns ```
modprobe: ERROR: ../libkmod/libkmod-module.c:809 kmod_module_insert_module() oculd not find module by name='iwlwifi'
modprobe: ERROR: could not insert 'iwlwifi': Function not implemented

```

Some general info:
```
#lsb_release -a
Distributor ID: Ubuntu
Description: Ubuntu 14.04.3 LTS
Release: 14.04
Codename: trusty

#uname -r
3.13.0-68-generic

```
I have tried to boot into an older kernel but holding shift during boot does nothing. I also modified /etc/boot/grub to change the grub timeout to -1 but that didn't do anything either.

The update destroyed the desktop, so I need to reinstall it (freezing when I try to log in) but I'm stuck without network.

---

### Post by praseodym on 2015-12-01
Install the package "linux-image-extra-3.13.0-68-generic" from here

[http://packages.ubuntu.com/search?keywords=linux-image-extra-3.13.0-68-generic&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=linux-image-extra-3.13.0-68-generic&searchon=names&suite=all&section=all)

---

### Post by david470 on 2015-12-01
Coworker working on the same issue as Scott:
After installing the package via USB mount I get dependency errors. Specifically missing dependencies "crda" and "wireless-crda". I can't install these dependencies because the network isn't connected without them.

---

### Post by praseodym on 2015-12-02
Search these files also on "packages.ubuntu.com"

---

### Post by scott96 on 2015-12-03
I was able to get eth0 up and it gets an IP but is unable to talk to the outside world.  I checked the same connection on another machine and it's good so there's an issue with the routing on the Lenovo.  Pinging 8.8.8.8 results in 100% packet loss.

---

### Post by scott96 on 2015-12-03
It looks like the asix module is working but not being used...?  Could that be the source of the network problem?

```
Module                  Size  Used by
ip6table_filter        12815  0 
ip6_tables             27025  1 ip6table_filter
iptable_filter         12810  0 
ip_tables              27239  1 iptable_filter
x_tables               34059  4 ip6table_filter,ip_tables,iptable_filter,ip6_tables
dm_crypt               23177  0 
rfcomm                 69160  0 
bnep                   19624  2 
bluetooth             391136  10 bnep,rfcomm
parport_pc             32701  0 
ppdev                  17671  0 
binfmt_misc            17468  1 
nfs                   236726  0 
nls_iso8859_1          12713  1 
lockd                  93977  1 nfs
sunrpc                289260  2 nfs,lockd
fscache                63988  1 nfs
arc4                   12608  2 
intel_rapl             18773  0 
uvcvideo               80885  0 
x86_pkg_temp_thermal    14205  0 
iwldvm                232285  0 
videobuf2_vmalloc      13216  1 uvcvideo
snd_hda_codec_hdmi     46368  1 
intel_powerclamp       14705  0 
videobuf2_memops       13362  1 videobuf2_vmalloc
mac80211              630728  1 iwldvm
coretemp               13435  0 
snd_hda_codec_realtek    65812  1 
videobuf2_core         40664  1 uvcvideo
**asix                   38914  0 **
videodev              134688  2 uvcvideo,videobuf2_core
kvm                   455843  0 
**usbnet                 43913  1 asix**
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
mii                    13934  2 asix,usbnet
ghash_clmulni_intel    13216  0 
snd_hda_intel          56531  0 
iwlwifi               169932  1 iwldvm
snd_hda_codec         193017  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
aesni_intel            55624  0 
snd_hwdep              13602  1 snd_hda_codec
aes_x86_64             17131  1 aesni_intel
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
cfg80211              484040  3 iwlwifi,mac80211,iwldvm
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
joydev                 17381  0 
snd_rawmidi            30144  1 snd_seq_midi
serio_raw              13462  0 
wmi                    19177  0 
thinkpad_acpi          81013  1 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
nvram                  14411  1 thinkpad_acpi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
snd                    69322  12 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,thinkpad_acpi,snd_seq_device,snd_seq_midi
mei_me                 18627  0 
soundcore              12680  1 snd
mei                    82276  1 mei_me
shpchp                 37032  0 
mac_hid                13205  0 
lpc_ich                21080  0 
intel_smartconnect     12619  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
usb_storage            62209  0 
i915                  788212  2 
ahci                   34091  3 
libahci                32716  1 ahci
psmouse               106692  0 
i2c_algo_bit           13413  1 i915
sdhci_pci              23172  0 
drm_kms_helper         55071  1 i915
sdhci                  43015  1 sdhci_pci
drm                   303102  3 i915,drm_kms_helper
video                  19476  1 i915
```

---

### Post by praseodym on 2015-12-03
Deactivate the firewall:
```

sudo apt-get remove --purge ufw gufw
sudo iptables -t filter -n -L -v
sudo iptables -F
sudo iptables -X
sudo service network-manager restart
ifconfig -a
route -n
dmesg | grep asix
```

---

### Post by scott96 on 2015-12-03
I think installing the kernel module did the trick, but the wireless was still software blocked so I unblocked it with
```
rfkill unblock all
```
Still no usb ethernet, but it's a moot point now.  I'm backing it up and installing fresh.

---

