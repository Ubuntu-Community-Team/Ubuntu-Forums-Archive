---
title: "Can't connect to websites which reside in my home country only"
date: 2017-04-21
forum: Networking &amp; Wireless
---

### Post by Wise Ferret on 2017-04-21
Hello! I live in Israel, and recently my ubuntu 17.04 stopped connecting to all websites which reside in Israel, tested on firefox and chromium (the connection to websites which reside in other countries is fine).
Other machines (mac, win, android...) on the same wireless router connect without problems to all websies.
Disconnecting and connectiung the router doesn't help, forgetting the wireless network on ubuntu and re-connecting to it doesn't help.

Here is some of the system info:```
yotam@ape:~$ lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
	Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:8554]
	Kernel driver in use: r8169
	Kernel modules: r8169
04:00.0 Network controller [0280]: Ralink corp. RT5392 PCIe Wireless Network Adapter [1814:5392]
	Subsystem: D-Link System Inc RT5392 PCIe Wireless Network Adapter [1186:3c0b]
	Kernel driver in use: rt2800pci
	Kernel modules: rt2800pci
yotam@ape:~$ lsusb
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 003 Device 002: ID 03f0:8c07 Hewlett-Packard Digital Stereo Headset
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
yotam@ape:~$ iwconfig
wlan0     IEEE 802.11  ESSID:"adi&amp;yotam"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: C8:D3:A3:EF:19:7A   
          Bit Rate=86.7 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=61/70  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:22  Invalid misc:369   Missed beacon:0

eth0      no wireless extensions.

lo        no wireless extensions.

yotam@ape:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
yotam@ape:~$ lsmod
Module                  Size  Used by
ip6table_filter        16384  0
ip6_tables             28672  1 ip6table_filter
iptable_filter         16384  0
ccm                    20480  3
nvidia_uvm            643072  2
joydev                 20480  0
snd_usb_audio         184320  4
input_leds             16384  0
snd_usbmidi_lib        32768  1 snd_usb_audio
snd_hda_codec_hdmi     49152  1
binfmt_misc            20480  1
eeepc_wmi              16384  0
asus_wmi               28672  1 eeepc_wmi
sparse_keymap          16384  1 asus_wmi
intel_rapl             20480  0
snd_hda_codec_realtek    90112  1
x86_pkg_temp_thermal    16384  0
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
intel_powerclamp       16384  0
coretemp               16384  0
kvm                   593920  0
snd_hda_intel          36864  8
snd_hda_codec         126976  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
irqbypass              16384  1 kvm
snd_hda_core           81920  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hwdep              16384  2 snd_hda_codec,snd_usb_audio
crct10dif_pclmul       16384  0
snd_pcm               102400  5 snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_hda_core,snd_hda_codec_hdmi
crc32_pclmul           16384  0
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
ghash_clmulni_intel    16384  0
pcbc                   16384  0
snd_rawmidi            32768  2 snd_seq_midi,snd_usbmidi_lib
arc4                   16384  2
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
aesni_intel           167936  6
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
rt2800pci              16384  0
rt2800mmio             16384  1 rt2800pci
aes_x86_64             20480  1 aesni_intel
rt2800lib              94208  2 rt2800mmio,rt2800pci
snd_timer              32768  2 snd_seq,snd_pcm
crypto_simd            16384  1 aesni_intel
rt2x00pci              16384  1 rt2800pci
glue_helper            16384  1 aesni_intel
rt2x00mmio             16384  2 rt2800mmio,rt2800pci
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
rt2x00lib              53248  5 rt2800lib,rt2x00pci,rt2800mmio,rt2x00mmio,rt2800pci
intel_cstate           20480  0
intel_rapl_perf        16384  0
mac80211              782336  3 rt2800lib,rt2x00pci,rt2x00lib
snd                    77824  37 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_usb_audio,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_usbmidi_lib,snd_seq_device,snd_hda_codec_realtek,snd_pcm
cfg80211              602112  2 rt2x00lib,mac80211
eeprom_93cx6           16384  1 rt2800pci
lpc_ich                24576  0
mei_me                 40960  0
mei                   102400  1 mei_me
soundcore              16384  1 snd
shpchp                 36864  0
wmi                    16384  1 asus_wmi
mac_hid                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
ip_tables              24576  1 iptable_filter
x_tables               36864  4 ip_tables,iptable_filter,ip6table_filter,ip6_tables
autofs4                40960  2
hid_generic            16384  0
usbhid                 53248  0
hid                   114688  2 hid_generic,usbhid
nvidia_drm             49152  2
nvidia_modeset        811008  9 nvidia_drm
drm_kms_helper        151552  1 nvidia_drm
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   352256  5 nvidia_drm,drm_kms_helper
nvidia              12460032  202 nvidia_modeset,nvidia_uvm
ahci                   36864  2
r8169                  81920  0
libahci                32768  1 ahci
mii                    16384  1 r8169
fjes                   73728  0
video                  40960  1 asus_wmi
```
Any ideas?

---

### Post by wildmanne39 on 2017-04-21
Do what is in post 9 at the following link:

[https://ubuntuforums.org/showthread.php?t=2358610](https://ubuntuforums.org/showthread.php?t=2358610)

Does that fix your issue?

---

### Post by Wise Ferret on 2017-04-21
Ne, restarting the network manager service doesn't help.

---

### Post by wildmanne39 on 2017-04-21
Did you change your settings in network manager as the screehshots in that link showed to do? there was more to it then just restarting network manager.
Thanks

---

### Post by Wise Ferret on 2017-04-21
Seems to be solved, thanks :-)

---

### Post by wildmanne39 on 2017-04-21
Your welcome!
Enjoy!:)

---

### Post by Wise Ferret on 2017-04-21
I was too early to rejoice.
This worked for several minutes, and now I am again blocked from all Israeli sites. It seems to block mesd about 80% of the time.
Any kind of help will be welcome.

---

### Post by nathan-linux-sa on 2017-04-22
What is the error that you get?
Is your PC behind a firewall that does content filtering?
Your issue sounds like a GEO-IP filtering of some sort or content filtering.

---

### Post by Wise Ferret on 2017-04-22
I am not getting any error - just a page saying no connection could be established (as if the network was down).
I am not behind any firewall.
On the one hand, the fact that this does not occure 100% of the time suggests it's something to do with my ISP, which uses the same IP for many users.
On the other hand, the fact that this happens only on my linux machine and not on the mac, android and windows machines in the house suggests that I should be able to do something to solve it.

Please let me know if I can give you more data.

---

### Post by shedokan on 2017-04-24
I had the same problem just now, I couldn't connect to any website under the domain co.il
Since I am running Ubuntu inside a vm, changing the DNS inside didn't help.
I fixed it by removing the DNS addresses from my windows host, and it worked.

Are you inside of a VM?

---

### Post by Wise Ferret on 2017-04-25
I'm not inside of a VM, but since the problem appeared after several updates to DNS-related packages and seems to have disappeared for several days now after onther round of such updates, this might have been a mysterious bug of sorts.

---

