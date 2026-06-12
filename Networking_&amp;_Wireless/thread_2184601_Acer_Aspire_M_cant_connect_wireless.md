---
title: "Acer Aspire M cant connect wireless"
date: 2013-10-29
forum: Networking &amp; Wireless
---

### Post by mubly80 on 2013-10-29
I am a beginner, I downloaded Ubuntu today (12.04) and erased my existing OS (Win 8) and everything seems to be working fine except I have no option to connect wirelessly, my ethernet cable connects me but thats all I can get. I tried rfkill list all, and nothing is blocked. I have installed all the drivers, looked at many forums and they arent helping me at all. I use this laptop for college so any help would be just awesome.

---

### Post by Hadaka on 2013-10-29
Hi,please post the output of..
```
lspci -nn | grep 0280
rfkill list all
lsmod
```
thanks

---

### Post by mubly80 on 2013-10-30
How do i copy the contents of the terminal?

---

### Post by Hadaka on 2013-10-30
Hi, highlight,copy and paste.
If you dont know how to copy and paste i suggest
you google..HOW TO COPY AND PASTE
good luck

---

### Post by mubly80 on 2013-10-31
method@BitchStewie:~$ lspci -nn / grep 0280
Usage: lspci [<switches>]

Basic display modes:
-mm        Produce machine-readable output (single -m for an obsolete format)
-t        Show bus tree

Display options:
-v        Be verbose (-vv for very verbose)
-k        Show kernel drivers handling each device
-x        Show hex-dump of the standard part of the config space
-xxx        Show hex-dump of the whole config space (dangerous; root only)
-xxxx        Show hex-dump of the 4096-byte extended config space (root only)
-b        Bus-centric view (addresses and IRQ's as seen by the bus)
-D        Always show domain numbers

Resolving of device ID's to names:
-n        Show numeric ID's
-nn        Show both textual and numeric ID's (names & numbers)
-q        Query the PCI ID database for unknown ID's via DNS
-qq        As above, but re-query locally cached entries
-Q        Query the PCI ID database for all ID's via DNS

Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]    Show only devices in selected slots
-d [<vendor>]:[<device>]            Show only devices with specified ID's

Other options:
-i <file>    Use specified ID database instead of /usr/share/misc/pci.ids.gz
-p <file>    Look up kernel modules in a given file instead of default modules.pcimap
-M        Enable `bus mapping' mode (dangerous; root only)

PCI access options:
-A <method>    Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>    Set PCI access parameter (see `-O help' for a list)
-G        Enable PCI access debugging
-H <mode>    Use direct hardware access (<mode> = 1 or 2)
-F <file>    Read PCI configuration dump from a given file
method@BitchStewie:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
method@BitchStewie:~$ lsmod
Module                  Size  Used by
hid_multitouch         17407  0 
bnep                   18258  2 
uvcvideo               82214  0 
rfcomm                 47864  12 
hid_generic            12540  0 
usbhid                 47346  1 hid_multitouch
hid                   105582  3 hid_multitouch,hid_generic,usbhid
videobuf2_core         40785  1 uvcvideo
videodev              130053  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
btusb                  22431  0 
bluetooth             247165  24 bnep,rfcomm,btusb
parport_pc             28284  0 
ppdev                  17113  0 
snd_hda_codec_realtek    79916  1 
snd_hda_codec_hdmi     37463  1 
nls_iso8859_1          12713  1 
coretemp               13596  0 
snd_hda_intel          44339  7 
kvm_intel             137899  0 
snd_hda_codec         141761  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
kvm                   455932  1 kvm_intel
ghash_clmulni_intel    13259  0 
snd_hwdep              13668  1 snd_hda_codec
snd_pcm               102477  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
aesni_intel            55495  0 
snd_seq_midi           13324  0 
snd_rawmidi            30417  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
ablk_helper            13597  1 aesni_intel
cryptd                 20501  3 ghash_clmulni_intel,aesni_intel,ablk_helper
lrw                    13294  1 aesni_intel
snd_seq                61930  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29989  2 snd_pcm,snd_seq
joydev                 17613  0 
aes_x86_64             17255  1 aesni_intel
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  620571  4 
xts                    12922  1 aesni_intel
drm_kms_helper         49597  1 i915
drm                   287564  5 i915,drm_kms_helper
psmouse                97873  0 
gf128mul               14951  2 lrw,xts
snd                    69533  23 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13215  0 
soundcore              12680  1 snd
i2c_algo_bit           13564  1 i915
rtsx_pci_ms            13180  0 
mei                    41820  0 
microcode              23017  0 
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
wmi                    19256  0 
mac_hid                13253  0 
lpc_ich                17144  0 
memstick               16605  1 rtsx_pci_ms
video                  19652  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
rtsx_pci_sdmmc         17800  0 
r8169                  68716  0 
rtsx_pci               34530  2 rtsx_pci_ms,rtsx_pci_sdmmc
ahci                   25879  3 
libahci                31606  1 ahci
method@BitchStewie:~$ 


I tried using the ctrl c command, doesnt work linux haha.

---

### Post by Hadaka on 2013-10-31
Hi,please COPY and paste these comands into a terminal..
```
lspci -nnk | grep -iA3 net
dmesg | grep rt2
```
then copy and paste the results
thanks.

---

### Post by mubly80 on 2013-10-31
method@BitchStewie:~$ lspci -nnk | grep -iA3 net
04:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 63)
	Subsystem: Intel Corporation Dual Band Wireless-N 7260 [8086:4060]
05:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5287] (rev 01)
	Subsystem: Acer Incorporated [ALI] Device [1025:079b]
--
05:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 14)
	Subsystem: Acer Incorporated [ALI] Device [1025:079b]
	Kernel driver in use: r8169
	Kernel modules: r8169
method@BitchStewie:~$ dmesg | grep rt2
method@BitchStewie:~$

---

