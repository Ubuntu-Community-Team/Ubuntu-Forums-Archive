---
title: "Issue with WiFi driver RTL8192eu"
date: 2016-11-02
forum: Networking &amp; Wireless
---

### Post by karlkimber6994 on 2016-11-02
Hello everyone! So I've got a very difficult WiFi USB, its a Realtek, RTL8192eu, and it took me days of messing around to get it to work on the first computer, now I've gotten this computer wired up & have another laptop I'd like to get it working on which is a bit older, running 14.04 32 bit.. I figure maybe there's a way to copy the driver files or to repackage them as a .deb perhaps? I've tried the PPA "Hanipouspilot", doesn't seem to work unfortunately.
[COLOR=#000000][I]My apologies if I'm missing anything, I very rarely post on any forums! 

relevant:
0bda:818b Realtek semiconductor Corp

[/I][/COLOR]

---

### Post by jeremy31 on 2016-11-03
Moved to networking
See the wireless script link in my signature and post results

---

### Post by chili555 on 2016-11-03
Is this the post you followed?

[http://askubuntu.com/questions/741559/wireless-adapter-realtek-0bda818b-problems-used-to-sometimes-connect-now-n](http://askubuntu.com/questions/741559/wireless-adapter-realtek-0bda818b-problems-used-to-sometimes-connect-now-n)

---

### Post by karlkimber6994 on 2016-11-04
Nope that is not the post I followed Chili555, but that is the PPA I tried to use.
And I'm not sure how this wireless script thing works?? 
Is there not a way I can just copy the drivers from one computer to another? I've already got it working on the one.
Charger broke on the one I'm moving the drivers onto, gonna have to order one tomorrow - hoping factory direct carries one but not sure :(

The wireless USB is a Realtek RTL8192eu, 300MBPS IEEE802.11N *0bda:818b Realtek semiconductor Corp*

---

### Post by chili555 on 2016-11-04
> Is there not a way I can just copy the drivers from one computer to another?Sure. If your kernel version, headers and all compile tools are exactly the same versions. If not, well, it's hit-or-miss.

Don't you think we should instead troubleshoot why the very same driver you already installed from the PPA isn't working? Isn't it logical that if you copied over the driver from another computer and loaded it, the same unresolved trouble would still not allow the wireless to work?

What is the result when you try to load the driver?```
sudo modprobe 8192eu
rfkill list all
```

---

### Post by karlkimber6994 on 2016-11-04
I've tried the RFkill unblock all stuff, I've tried the Modprobe 8192eu.. I don't think I had that PPA install the driver the first time either, it was a long time ago and I don't know.. 
Isn't there any way I can find out more about the driver being used on the computer that works? Isn't there some kind of .inf file or something like that? 
I've done the modprobes, 8192eu, rtl8192eu, rt8192eu, several combinations.. none seem to work. :(

---

### Post by chili555 on 2016-11-04
Did you install the package  rtl8192eu-dkms from the PPA?```
sudo dkms status
```

---

### Post by karlkimber6994 on 2016-12-02
Yes I tried installing it from that PPA, rtl8192eu-dkms. exactly like that.
Unfortunately the charger for this laptop broke, I'm ordering one today or tomorrow once I can get to a store that sells prepaid cards
Sorry for the late reply. didn't count on that happening

---

### Post by karlkimber6994 on 2017-01-11
Hi everyone! Really sorry for the delay! I ended up buying a new charger(and a RAM upgrade too), only to find out it was NOT the charger, but the DC plug inside of the laptop! and WOW is the Inspiron Mini 10v ever a pain to get apart! 
Okay so let's get to work now, shall we?

"sudo dkms status" output:



ndiswrapper, 1.59, 3.13.0-107-generic, i686: installed
rtl8192eu, 4.3.1.1.11320.20140505: added
rtl8192eu, 4.3.1.1.11320.20140505~trusty1: added
rtlwifi-new, 0.10~trusty, 3.13.0-107-generic, i686: installed
rtlwifi-new, 0.10~trusty, 4.2.0-42-generic, i686: installed
rtlwifi-new, 0.10~trusty, 4.4.0-59-generic, i686: installed

---

### Post by chili555 on 2017-01-11
Let's see how many dozen of those drivers loaded and probably conflict!!```
lsmod | grep -e ndis -e rtl
dmesg | grep rtl
```

---

### Post by karlkimber6994 on 2017-01-12
lsmod | grep -e ndis -e rtl
~
btrtl                  16384  1 btusb
bluetooth             466944  25 bnep,btbcm,btrtl,btusb,rfcomm,btintel

dmesg | grep rtl
~
[   24.096567] Modules linked in: joydev input_leds snd_hda_intel snd_hda_codec serio_raw b43 snd_hda_core lpc_ich bcma mac80211 btusb i915 btrtl snd_hwdep btbcm cfg80211 btintel snd_pcm rfcomm bnep bluetooth drm_kms_helper snd_seq_midi drm snd_seq_midi_event snd_rawmidi snd_seq snd_seq_device snd_timer i2c_algo_bit snd fb_sys_fops syscopyarea shpchp soundcore sysfillrect sysimgblt video parport_pc ppdev mac_hid lp parport psmouse r8169 pata_acpi mii ssb fjes
[   24.120556] Modules linked in: joydev input_leds snd_hda_intel snd_hda_codec serio_raw b43 snd_hda_core lpc_ich bcma mac80211 btusb i915 btrtl snd_hwdep btbcm cfg80211 btintel snd_pcm rfcomm bnep bluetooth drm_kms_helper snd_seq_midi drm snd_seq_midi_event snd_rawmidi snd_seq snd_seq_device snd_timer i2c_algo_bit snd fb_sys_fops syscopyarea shpchp soundcore sysfillrect sysimgblt video parport_pc ppdev mac_hid lp parport psmouse r8169 pata_acpi mii ssb fjes
[   24.122761] Modules linked in: joydev input_leds snd_hda_intel snd_hda_codec serio_raw b43 snd_hda_core lpc_ich bcma mac80211 btusb i915 btrtl snd_hwdep btbcm cfg80211 btintel snd_pcm rfcomm bnep bluetooth drm_kms_helper snd_seq_midi drm snd_seq_midi_event snd_rawmidi snd_seq snd_seq_device snd_timer i2c_algo_bit snd fb_sys_fops syscopyarea shpchp soundcore sysfillrect sysimgblt video parport_pc ppdev mac_hid lp parport psmouse r8169 pata_acpi mii ssb fjes

---

### Post by chili555 on 2017-01-13
Usually, the 'modules linked in' message follows a kernel oops; a bigger issue than wireless. I suggest that you look at the log to see what happened just before the 24.09xx timestamp and try to fix it:```
dmesg | less
```*less* will allow you to scroll back and forth to see what's going wrong. Get out of* less* with q.

We also see the driver for, I assume, your internal wireless device:> [ 24.096567] Modules linked in: joydev input_leds snd_hda_intel snd_hda_codec serio_raw [COLOR="#FF0000"]b43 [/COLOR]snd_hda_core lpc_ich [COLOR="#FF0000"]bcma[/COLOR] mac80211 btusb i915 btrtl snd_hwdep btbcm cfg80211 btintel snd_pcm rfcomm bnep bluetooth drm_kms_helper snd_seq_midi drm snd_seq_midi_event snd_rawmidi snd_seq snd_seq_device snd_timer i2c_algo_bit snd fb_sys_fops syscopyarea shpchp soundcore sysfillrect sysimgblt video parport_pc ppdev mac_hid lp parport psmouse r8169 pata_acpi mii ssb fjesWhy are you wanting to get the tricky USB going when you have an internal that ought to work perfectly?

Also, please show us:```
sudo dpkg -s rtl8192eu-dkms
```

---

### Post by karlkimber6994 on 2017-01-13
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 4.4.0-59-generic (buildd@lcy01-11) (gcc version 4.8.4 (Ubuntu 4.8.4-2ubuntu1~14.04.3) ) #80~14.04.1-Ubuntu SMP Fri Jan 6 18:02:23 UTC 2017 (Ubuntu 4.4.0-59.80~14.04.1-generic 4.4.35)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] x86/fpu: Legacy x87 FPU detected.
[    0.000000] x86/fpu: Using 'lazy' FPU context switches.
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000007f6cffff] usable
[    0.000000] BIOS-e820: [mem 0x000000007f6d0000-0x000000007f6e1fff] ACPI data
:


that is what I got for first one, and for second:



Package: rtl8192eu-dkms
Status: install ok installed
Priority: optional
Section: misc
Installed-Size: 9093
Maintainer: Dmitry Tunin <hanipouspilot@gmail.com>
Architecture: all
Version: 4.3.1.1.11320.20140505~trusty1
Depends: dkms (>= 1.95)
Description: rtl8192eu driver in DKMS format.




I'm trying to make the USB work because I have a +9 DBi antenna that is on my USB WiFi stick and when I go out its great for a longer range connection

---

### Post by karlkimber6994 on 2017-01-13
I just found THIS and now it works :O I can't believe it! I'm honestly shocked!
github.com/Mange/rtl8192eu-linux-driver

---

