---
title: "Wireless Networking just... stopped."
date: 2014-05-10
forum: Networking &amp; Wireless
---

### Post by vcell on 2014-05-10
So last night I was on my wireless network. Then suddenly... it stopped. No connection. In fact, my Dell Inspiron 1545 didn't detect any networks. I checked the basic stuff and the laptop is not in airplane mode and wireless networking is turned on. Every other connected device in the house is fine, so it's not the network. When I try to force it to connect, it can't find the network.

Right now I'm connected by network cable. Is there anything else I can check? I don't think it's Ubuntu or anything like that, because it was originally fine, and everything that's supposed be on, is on. Maybe it's hardware?

--Vcell

---

### Post by vcell on 2014-05-10
Does this help?

sudo lshw -C network

  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:26:5e:1d:35:68
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.20.155.1 (r326264) latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:25:64:40:93:8c
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 duplex=full ip=192.168.1.6 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:44 memory:f68fc000-f68fffff ioport:de00(size=256)

---

### Post by kc1di on 2014-05-10
could you list the output of ```
lsmod
```
also ```
rfkill list all
```

---

### Post by vcell on 2014-05-10
_***list all***_
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no[U][I][B]


lsmod[/B][/I][/U]
Module                  Size  Used by
bnep                   19210  2 
rfcomm                 59026  0 
bluetooth             341971  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  17423  0 
binfmt_misc            17268  1 
snd_hda_codec_idt      45221  1 
snd_hda_intel          43326  5 
snd_hda_codec         169608  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                94597  3 snd_hda_intel,snd_hda_codec
joydev                 17329  0 
snd_seq_midi           13132  0 
snd_rawmidi            25157  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                55716  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               72275  0 
i915                  615880  3 
lib80211_crypt_tkip    17502  0 
wl                   2902529  0 
videobuf2_core         39385  1 uvcvideo
snd_timer              28930  2 snd_pcm,snd_seq
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
videodev              107944  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      13048  1 uvcvideo
drm_kms_helper         47306  1 i915
cfg80211              416271  1 wl
drm                   247722  4 i915,drm_kms_helper
snd                    61270  19 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                92648  0 
videobuf2_memops       13170  1 videobuf2_vmalloc
lib80211               14040  2 lib80211_crypt_tkip,wl
dell_laptop            17209  0 
dell_wmi               12665  0 
serio_raw              13189  0 
dcdbas                 14456  1 dell_laptop
sparse_keymap          13658  1 dell_wmi
gpio_ich               13278  0 
i2c_algo_bit           13316  1 i915
wmi                    18744  1 dell_wmi
lpc_ich                16987  0 
mac_hid                13077  0 
soundcore              12600  1 snd
snd_page_alloc         18398  2 snd_hda_intel,snd_pcm
video                  19046  1 i915
lp                     13359  0 
parport                40930  3 parport_pc,ppdev,lp
hid_generic            12492  0 
usbhid                 47620  0 
hid                    87771  2 hid_generic,usbhid
ums_realtek            17992  0 
usb_storage            48631  1 ums_realtek
ahci                   25703  2 
libahci                30834  1 ahci
sky2                   53656  0

---

### Post by Hadaka on 2014-05-10
hi, please post the output of ...
```
lsb_release -a
lspci -n | grep 14e
```
thanks

---

### Post by kc1di on 2014-05-10
Try purging bcmwl-kernel-source ```
sudo apt-get purge bcmwl-kernel-source
``` 
then reboot and reinstall bcmwl-kernel-source  then issue this command ```
modprobe wl 
``` 
wait a minute and see if you have wireless.

---

### Post by vcell on 2014-05-13
Dave, now my network options doesn't even have the option of wireless. So... THAT no es bueno. Can I undo the bcmwl-kernel-source purge?

Hadaka, that output is:
**lsb_release -a**
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

**lspci -n | grep 14e**
0c:00.0 0280: 14e4:4315 (rev 01)

---

### Post by Hadaka on 2014-05-13
hi, please do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```

---

### Post by vcell on 2014-05-13
Thanks, Hadaka. That did the trick. Had to reboot first, but all is well again. Thank you.

---

### Post by Hadaka on 2014-05-13
Great ! glad you got it working .

---

