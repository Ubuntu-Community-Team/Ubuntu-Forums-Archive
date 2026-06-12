---
title: "Wireless networks are disabled."
date: 2011-06-27
forum: New to Ubuntu
---

### Post by parkerskouson on 2011-06-27
Hello.

Ok.. I booted my computer today and I tried to connect to my WiFi and it said WiFi was disabled. I have no idea how to fix this and I really need it fixed.... 

Pleas Help

---

### Post by josephmills on 2011-06-27
could you open your terminal and type in ```
rfkill list all 
```then```
lspci -nn
```and a ```
lsmod
```then paste all here thanks

---

### Post by parkerskouson on 2011-06-27
Here you go...


0: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes



00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
00:1f.6 Signal processing controller [1180]: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem [8086:2932] (rev 03)
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)




Module                  Size  Used by
parport_pc             26058  0 
ppdev                   5556  0 
binfmt_misc             6599  1 
snd_hda_codec_intelhdmi     9812  1 
snd_hda_codec_conexant    30003  1 
joydev                  8767  0 
arc4                    1165  2 
snd_hda_intel          22235  2 
snd_hda_codec          87552  3 snd_hda_codec_intelhdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
i915                  295435  4 
snd_seq_midi            4588  0 
drm_kms_helper         30200  1 i915
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
drm                   168060  4 i915,drm_kms_helper
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
ath5k                 130083  0 
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              231959  1 ath5k
hp_wmi                  5223  0 
ath                     8153  1 ath5k
cfg80211              144694  3 ath5k,mac80211,ath
snd                    49038  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              26566  2 i915
psmouse                59033  0 
serio_raw               4022  0 
led_class               2633  1 ath5k
i2c_algo_bit            5168  1 i915
video                  18712  1 i915
output                  1883  1 video
agpgart                32011  2 drm,intel_agp
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
usb_storage            40204  0 
ahci                   19198  2 
libahci                21728  1 ahci
r8169                  36521  0 
mii                     4425  1 r8169

---

### Post by josephmills on 2011-06-27
> **parkerskouson said:**
> Here you go...


0: phy0: Wireless LAN
[COLOR="Red"]	Soft blocked: yes[/Color]
	Hard blocked: no
1: hp-wifi: Wireless LAN[COLOR="red"]
	Soft blocked: yes
	Hard blocked: yes


[/COLOR]
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
00:1f.6 Signal processing controller [1180]: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem [8086:2932] (rev 03)
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
[COLOR="red"]02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)

[/COLOR]


Module                  Size  Used by
parport_pc             26058  0 
ppdev                   5556  0 
binfmt_misc             6599  1 
snd_hda_codec_intelhdmi     9812  1 
snd_hda_codec_conexant    30003  1 
joydev                  8767  0 
arc4                    1165  2 
snd_hda_intel          22235  2 
snd_hda_codec          87552  3 snd_hda_codec_intelhdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
i915                  295435  4 
snd_seq_midi            4588  0 
drm_kms_helper         30200  1 i915
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
drm                   168060  4 i915,drm_kms_helper
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
[COLOR="Red"]ath5k                 130083  0 [/COLOR]
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
[COLOR="red"]mac80211              231959  1 ath5k[/COLOR]
hp_wmi                  5223  0 
[COLOR="red"]ath                     8153  1 ath5k[/COLOR]
[COLOR="red"]cfg80211              144694  3 ath5k,mac80211,ath[/COLOR]
snd                    49038  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              26566  2 i915
psmouse                59033  0 
serio_raw               4022  0 
[COLOR="red"]led_class               2633  1 ath5k[/COLOR]
i2c_algo_bit            5168  1 i915
video                  18712  1 i915
output                  1883  1 video
agpgart                32011  2 drm,intel_agp
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
usb_storage            40204  0 
ahci                   19198  2 
libahci                21728  1 ahci
r8169                  36521  0 
mii                     4425  1 r8169

turn on your wireless switch if it is a dell fn+f2 then do a ```
rfkill unblock all 
``` then ```
sudo modprobe ath5k
```
anything ? if not we will look at your blacklist file

---

### Post by parkerskouson on 2011-06-27
That didnt do anything... It is a HP not a Dell FYI.

---

### Post by josephmills on 2011-06-27
> **parkerskouson said:**
> That didnt do anything... It is a HP not a Dell FYI.

ok hit the wireless switch or button on the computer then do a ```
rfkill list all 
```paste it here  i wonder if hp_wmi is getting in the way we will see here .

---

### Post by parkerskouson on 2011-06-27
Didnt fix it. here is the code if needed.


0: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: no

---

### Post by josephmills on 2011-06-27
> 0: phy0: Wireless LAN
[COLOR="red"]Soft blocked: yes[/COLOR]
Hard blocked: no
1: hp-wifi: Wireless LAN
[COLOR="Red"]Soft blocked: yes[/COLOR]
Hard blocked: no


we want it to say all "no" now do a ```
sudo rfkill unblock all 
``` nothing do a ```
sudo rfkill unblock wifi 
``` still nothing try ```
rfkill unblock wlan
```anything ?

---

### Post by parkerskouson on 2011-06-27
Perfect!!! Fixed everything. Will mark as solved momentarily!

Thanks so much

Parker

---

### Post by josephmills on 2011-06-27
glad to see it is working reboot just to make sure if it stops we will put the rfkill in local.rc so it will run that code on start up

---

### Post by Neoncamouflage on 2011-06-27
This happens to me whenever my computer gets shut off without doing the proper shutdown. All I have to do is right click the connection icon - enable networking. That may help if it happens again.

---

