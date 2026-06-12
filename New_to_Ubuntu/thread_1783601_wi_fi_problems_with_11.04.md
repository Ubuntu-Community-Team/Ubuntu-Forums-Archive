---
title: "wi fi problems with 11.04"
date: 2011-06-15
forum: New to Ubuntu
---

### Post by lash94 on 2011-06-15
Hello, i have a hp mini 110 but ubuntu is unable to detect any connection. i need to install someting? change version of ubuntu?

---

### Post by jtarin on 2011-06-15
What have you done to try and connect? How do you connect? Wireless, cable, adsl or other?

---

### Post by Zachzee on 2011-06-15
well some more details could be good. first of all does it have built in Wi-Fi capabilities. Second are you using the built in. if not are you using a D-link, N-link, etc.... because i know that usually i had to install drivers for D-links/ N-links on older systems. also it seems that there has been similar posts for hp laptops with ubuntu but i am not sure about 11.04. so you try this old thread
[http://ubuntuforums.org/showthread.php?t=545960](http://ubuntuforums.org/showthread.php?t=545960)
 sorry if none of this helps, but good luck

---

### Post by lash94 on 2011-06-15
i'm trying to connect to a wireless connection, it worked fine un win xp, but now it's unable to detect any conection

---

### Post by wildmanne39 on 2011-06-16
> **lash94 said:**
> i'm trying to connect to a wireless connection, it worked fine un win xp, but now it's unable to detect any conection
Hi, run this command in a termninal
```
lspci
```
and post the information here.

---

### Post by dFlyer on 2011-06-16
> **lash94 said:**
> Hello, i have a hp mini 110 but ubuntu is unable to detect any connection. i need to install someting? change version of ubuntu?

Did you test it via the live desktop and was it able to connect than?

---

### Post by jtarin on 2011-06-16
> **wildmanne39 said:**
> Hi, run this command in a termninal
```
lspci
```
and post the information here.wildmanne39 wants you to run this command and post it also ```
lsmod
``` .....he's just too shy to ask.:p

---

### Post by lash94 on 2011-06-16
00:00.0 host bridge: intel corporationmobile 945GME express memory controler hub (rev 03)
00:02.0 VGA compatible controller: intel corporation mobile 945GME express integrated graphics controller (rev 03)
00:02.0 display controller: intel corporation mobile 945GM/GMS/GME, 943/940GML express integrated graphics controller (rev 03)
00:1b.0 audio device: inter comporation N10/ICH 7 family high definition audio controller (rev 02)
00:1c.0 pci bridge: intel corporation N10/ICH family PCI express port 1 (rev 02)
00:1c.1 pci bridge: intel corporation N10/ICH family PCI express port 2 (rev 02)
00:1d.0 usb controller: intel corporation N10/ICH 7 family USB UHCI controller #1 (rev 02)
00:1d.1 USB controller: intel corporation N10/ICH 7 family USB UHCI controller #2 (rev 02)
00:1d.2 USB controller: intel corporation N10/ICH 7 family USB UHCI controller #3 (rev 02)
00:1d.3 USB controller: intel corporation N10/ICH 7 family USB UHCI controller #4 (rev 02)
00:1d.7 USB controller: intel corporation N10/ICH 7 family USB2 EHCI controller (rev 02)
00:1e.0 PCI bridge: intel corporation 82801 mobile PCI bridge (rev e2)
00:1f.0 ISA bridge: intel corporation 82801GBM (ICH7-M) LPC interface bridge (rev 02)
00:1f.2 IDE interface: intel corporation 82801GBM/GHM (ICH7 family) SATA IDE controller (rev 02)
01:00.0 network controller: broadcom corporation BCM4312 802.11b/g LP-PHY (rev01)
02:00.0 ethernet controller: atheros communications AR8132 fast ethernet (rev c0)

---

### Post by lash94 on 2011-06-16
lsmod:

snd_hda_codec_idt     60357  1
snd_hda_intel         24140  2
snd_hda_codec         90901  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep             13274  1 snd_hda_codec
arc4                  12473  2
snd_pcm               80244  2 snd_hda_intel.snd_hda_codec
b43                  296610  0
i915                 450944  3
snd_seq_midi          13132  0
snd_rawmidi           25269  1 snd_seq_midi
mac80211             257001  1 b43
snd_seq_midi_event    14475  1 snd_seq_midi
snd_seq               51291  2 snd_seq_midi,snd_seq_midi_event
joydev                17322  0
hp_wmi                13418  0
sparse_keymap         13666  1 hp_wmi
drm_kms_helper        40745  1 i915
snd_timer             28659  2 snd_pcm,snd_seq
uvcvideo              66851  0
snd_seq_device        14110  3 snd_seq_midi,snd_rawmidi,snd_seq
videodev              75143  1 uvcvideo
cfg80211             156212  2 b43,mac80211
drm                  180037  4 i915,drm_kms_helper
psmouse               73312  0
snd                   55295  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw             12990  0
soundcore             12600  1 smd
12c_algo_bit          13184  1 i915
snd_page_alloc        14073  2 snd_hda_intel,snd_pcm
video                 18951  1 i915
lp                    13349  0
parport               36746  3 parport_pc.ppdev, lp
ssb                   45942  1 b43
atl1c                 36237  0

---

### Post by fooman on 2011-06-16
have you checked to see if there are drivers available in "additional drivers"?  to check and see....do as described in this post:

[http://ubuntuforums.org/showpost.php?p=10946763&postcount=2](http://ubuntuforums.org/showpost.php?p=10946763&postcount=2)

---

### Post by lash94 on 2011-06-16
it worked!!  thank you

---

