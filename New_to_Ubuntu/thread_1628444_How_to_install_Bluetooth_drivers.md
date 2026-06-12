---
title: "How to install Bluetooth drivers?"
date: 2010-11-22
forum: New to Ubuntu
---

### Post by camn on 2010-11-22
Hello... While looking through the options in my BIOS I found that my computer apparently has Bluetooth... How would I go about installing drivers? I have a Dell Vostro 1500.

---

### Post by florus on 2010-11-22
Go to System>Preferences>Startup Applications, and check that Bluetooth manager is ticked.

---

### Post by camn on 2010-11-22
> **florus said:**
> Go to System>Preferences>Startup Applications, and check that Bluetooth manager is ticked.

It is, but when I go to System>Preferences>Bluetooth it says that my computer does not have any Bluetooth adapters plugged in.

---

### Post by camn on 2010-11-26
Bump...?

---

### Post by eltntawy on 2011-12-09
i have some problem like this 
the computer view my Bluetooth device but it doesn't work.

and this some output

$ hcitool dev
Devices:

devices nothing.

$ dmesg|tail
[ 4424.563567] usb 1-1.1: new full speed USB device number 21 using ehci_hcd
[ 4424.657659] hub 1-1.1:1.0: USB hub found
[ 4424.657821] hub 1-1.1:1.0: 3 ports detected
[ 4424.927328] usb 1-1.1.1: new full speed USB device number 22 using ehci_hcd
[ 4425.024773] input: HID 413c:8161 as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1.1/1-1.1.1:1.0/input/input20
[ 4425.025051] generic-usb 0003:413C:8161.0008: input,hidraw1: USB HID v1.11 Keyboard [HID 413c:8161] on usb-0000:00:1a.0-1.1.1/input0
[ 4425.095081] usb 1-1.1.2: new full speed USB device number 23 using ehci_hcd
[ 4425.193936] input: HID 413c:8162 as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1.2/1-1.1.2:1.0/input/input21
[ 4425.194227] generic-usb 0003:413C:8162.0009: input,hidraw2: USB HID v1.11 Mouse [HID 413c:8162] on usb-0000:00:1a.0-1.1.2/input0
[ 4693.398916] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=600

---

### Post by 3rdalbum on 2011-12-09
Your Bluetooth switch needs to be "on" before Ubuntu will detect it. Most laptops have a switch or physical button you need to push to actually turn on the Bluetooth module.

---

### Post by Mad Banaan on 2011-12-25
I have the same problem
The switch in preferences not able to switch on.
It says in the desktop that it is on. And according to Dell I should be able to have it working.

I have 11.10 And Dell Vostro 3550
Maybe all of this helps:

```
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
	Subsystem: Dell Device [1028:04b3]
	Kernel driver in use: r8169
--
09:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
	Subsystem: Dell Device [1028:0205]
	Kernel driver in use: ath9k
```

```
Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  0 
parport_pc             36962  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_idt      70553  1 
binfmt_misc            17540  1 
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
uvcvideo               72711  0 
videodev               92992  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
dell_laptop            13831  0 
snd_hda_intel          33390  2 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
dcdbas                 14490  1 dell_laptop
arc4                   12529  2 
btusb                  18600  1 
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
psmouse                73882  0 
serio_raw              13166  0 
bluetooth             166112  13 bnep,rfcomm,btusb
ath9k                 127538  0 
mac80211              462092  1 ath9k
ath9k_common           13839  1 ath9k
ath9k_hw              312914  2 ath9k,ath9k_common
ath                    24067  2 ath9k,ath9k_hw
snd_seq_midi_event     14899  1 snd_seq_midi
cfg80211              199587  3 ath9k,mac80211,ath
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi                    19256  1 dell_wmi
mei                    41480  0 
i915                  566827  3 
drm_kms_helper         42558  1 i915
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
drm                   236290  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
ums_realtek            13272  0 
usb_storage            57901  1 ums_realtek
uas                    18027  0 
ahci                   26002  2 
libahci                26861  1 ahci
xhci_hcd               82820  0 
r8169                  52788  0 

```

```
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
```

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"telenet-69BBB"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:25:F2:B8:64:1A   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=54/70  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:97   Missed beacon:0
```

---

### Post by dddtc on 2012-01-27
Same here. Same laptop movel (Dell Vostro 3550) with the same issue.

---

### Post by dddtc on 2012-01-27
Problem explained:
[https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/875842](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/875842)

Ubuntu is incorrectly detecting Bluetooth on a system that doesn't have one.

---

### Post by Mad Banaan on 2012-02-25
Your link worked for me, thx!

---

