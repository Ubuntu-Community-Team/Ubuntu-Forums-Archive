---
title: "Broadcom BCM4352 Bluetooth not detected - Ubuntu 14.04"
date: 2014-09-08
forum: Networking &amp; Wireless
---

### Post by polochamps on 2014-09-08
Hi!

I just installed Ubuntu 14.04 on my desktop. Additonal drivers says that's it's using the Broadcom proprietary drivers. Wifi is detected but the Bluetooth is not.
If someone could help me with my current problem, I would very much appreciate it.

Thank you!

---

### Post by sheldon-corey on 2014-09-09
outputs from the following would be nice:

uname -r 
rfkill list bluetooth (or rfkill list all )

also is the bluetooth deamon bluez installed and working  (can confirm via a look in network connections or the network applet (where you see wifi/widi networks normally )


please advise with said outputs and maybe myself or someone else can be more help..

---

### Post by polochamps on 2014-09-09
Hi!

Yes the Bluetooth daemon is in the hardware settings and when I clicked it it says "No Bluetooth adapters found". Also no bluetooth detected on network settings.

> $ uname -r
3.13.0-35-generic

> $ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no



Thank you!

---

### Post by polochamps on 2014-09-15
Bump

---

### Post by praseodym on 2014-09-15
Please show the outputs of
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
```

---

### Post by polochamps on 2014-09-17
```
lspci -nnk | grep -iA2 net
00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection I217-V [8086:153b] (rev 05)
    Subsystem: ASUSTeK Computer Inc. Device [1043:859f]
    Kernel driver in use: e1000e

03:00.0 Network controller [0280]: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device [1043:855c]
    Kernel driver in use: wl
```

```
lsusb
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 0b05:17cf ASUSTek Computer, Inc. 
Bus 003 Device 005: ID 0bc2:a0a4 Seagate RSS LLC 
Bus 003 Device 003: ID 1b1c:1b07 Corsair 
Bus 003 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

```
lsmod
Module                  Size  Used by
usb_storage            62209  1 
rfcomm                 69160  0 
bnep                   19624  2 
bluetooth             391136  10 bnep,rfcomm
binfmt_misc            17468  1 
nls_iso8859_1          12713  1 
snd_hda_codec_hdmi     46368  1 
joydev                 17381  0 
eeepc_wmi              13151  0 
asus_wmi               24191  1 eeepc_wmi
sparse_keymap          13948  1 asus_wmi
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
lib80211_crypt_tkip    17619  0 
kvm                   451511  0 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
snd_hda_codec_realtek    65580  1 
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
serio_raw              13462  0 
snd_hda_intel          56451  5 
nvidia              10675249  50 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
wl                   4207846  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
lib80211               14381  2 wl,lib80211_crypt_tkip
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
cfg80211              484040  1 wl
snd                    69322  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
mei_me                 18627  0 
mei                    82276  1 mei_me
lpc_ich                21080  0 
soundcore              12680  1 snd
drm                   303102  2 nvidia
mac_hid                13205  0 
parport_pc             32701  0 
wmi                    19177  1 asus_wmi
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 52570  0 
hid                   106148  2 hid_generic,usbhid
psmouse               106678  0 
ahci                   25819  4 
libahci                32716  1 ahci
e1000e                254433  0 
ptp                    18933  1 e1000e
pps_core               19382  1 ptp
video                  19476  1 asus_wmi
```

Thank you!

---

### Post by praseodym on 2014-09-17
```
Bus 003 Device 004: ID 0b05:17cf ASUSTek Computer, Inc. 
```

Here we go:

[http://ubuntuforums.org/showthread.php?t=2231813](http://ubuntuforums.org/showthread.php?t=2231813)

---

### Post by polochamps on 2014-09-17
Thank you [[COLOR=#000000]praseodym[/COLOR]]("http://ubuntuforums.org/member.php?u=1411497")! After reading it, I think I'm not that knowledgeable to compile and build my own kernel yet. Awts.

---

### Post by polochamps on 2014-09-17
I did this and my bluetooth was detected but doesn't work again after reboot.

```
sudo -i
modprobe btusb
echo "0b05 17cf" >> /sys/bus/usb/drivers/btusb/new_id
```

I saw this here and they released a patch for Oneiric and Precise.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/906832](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/906832)

---

### Post by praseodym on 2014-09-17
Try this one-liner:

```
echo 'install btusb modprobe --ignore-install btusb ; /bin/echo "0b05 17cf" > /sys/bus/usb/drivers/btusb/new_id' | sudo tee /etc/modprobe.d/btusb.conf
```
Reload the module:
```

sudo modprobe -rfv btusb
sudo modprobe -v btusb
```
It adds the device ID whenever the module is loaded.

---

### Post by polochamps on 2014-09-17
Hi [[COLOR=#000000]praseodym[/COLOR]]("http://ubuntuforums.org/member.php?u=1411497")!

I tried doing your solution but the result the same when I did this...

```
sudo -i
modprobe btusb
echo "0b05 17cf" >> /sys/bus/usb/drivers/btusb/new_id
```

Not detected upon reboot.

Thank you

---

