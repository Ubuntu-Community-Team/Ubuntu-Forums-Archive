---
title: "bluetooth doesn't work xubuntu 14.04"
date: 2014-07-21
forum: Networking &amp; Wireless
---

### Post by hasan9 on 2014-07-21
I searched of forum but I couldn't anything the fact I don't no what I write. I am new user ubuntu

My computer hp 550 I used xubuntu 14.04 but bluetooth doesn't work 

I tryed this code but doesn't work 

[COLOR=#2C001E][FONT=Ubuntu]bluetooth-applet   code didn't find 


[/FONT][/COLOR]_***hasan@hasan-HP-550:~$ rfkill list***_
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

_***hasan@hasan-HP-550:~$ lspci***_
00:00.0 Host bridge: Intel Corporation Mobile GME965/GLE960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GME965/GLE960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GME965/GLE960 Integrated Graphics Controller (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82562GT 10/100 Network Connection (rev 03)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 03)
10:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)

_***hasan@hasan-HP-550:~$ lsusb***_
Bus 002 Device 003: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 002 Device 002: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub




***_hasan@hasan-HP-550:~$ lsmod_***
Module                  Size  Used by
wl                   3999690  0 
lib80211               14040  1 wl
btusb                  27580  0 
bnep                   18895  2 
rfcomm                 53664  4 
bluetooth             342206  11 bnep,btusb,rfcomm
hp_wmi                 13702  0 
binfmt_misc            13140  1 
sparse_keymap          13708  1 hp_wmi
arc4                   12536  2 
snd_hda_codec_analog    14537  1 
snd_hda_intel          42730  6 
snd_hda_codec         164067  2 snd_hda_intel,snd_hda_codec_analog
snd_hwdep              13272  1 snd_hda_codec
iwl4965               106859  0 
snd_pcm                85501  2 snd_hda_codec,snd_hda_intel
iwlegacy               88016  1 iwl4965
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
mac80211              546051  2 iwl4965,iwlegacy
i915                  705659  4 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25135  1 snd_seq_midi
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
cfg80211              409394  4 wl,iwl4965,iwlegacy,mac80211
snd_timer              28584  2 snd_pcm,snd_seq
drm_kms_helper         47182  1 i915
drm                   244037  5 i915,drm_kms_helper
snd                    60871  22 snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_hda_codec_analog,snd_seq_midi
coretemp               13195  0 
joydev                 17101  0 
i2c_algo_bit           13197  1 i915
soundcore              12600  1 snd
wmi                    18673  1 hp_wmi
serio_raw              13230  0 
lpc_ich                16864  0 
video                  18903  1 i915
mac_hid                13037  0 
parport_pc             31981  0 
ppdev                  17391  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
hid_generic            12492  0 
usbhid                 46997  0 
hid                    87604  2 hid_generic,usbhid
psmouse                91329  0 
ahci                   25579  2 
libahci                27082  1 ahci
e1000e                223034  0 
ptp                    18445  1 e1000e
pps_core               18799  1 ptp

---

### Post by jeremy31 on 2014-07-21
The main issue is that the bluetooth isn't found for whatever reason.  I would expect to see an intel device in the lsusb.  Is there a reason you know of that the wl module is loaded?

Does it have bluetooth available in windows?

---

### Post by hasan9 on 2014-07-22
my english not good and yes bluetooth works on windows and it works on wifislax live cd

---

### Post by jeremy31 on 2014-07-22
> **hasan9 said:**
> my english not good and yes bluetooth works on windows and it works on wifislax live cd

Do you know if lsusb works on wifislax or if there is a similar command?  If you can please post results

---

