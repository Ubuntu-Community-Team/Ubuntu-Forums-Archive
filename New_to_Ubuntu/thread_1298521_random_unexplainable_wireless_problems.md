---
title: "random unexplainable wireless problems"
date: 2009-10-22
forum: New to Ubuntu
---

### Post by asuastrophysics on 2009-10-22
Hi everyone, 

I've been using ubuntu for about a year now, but no matter how much I learn about the operating system, I can never figure this out.

About once every 2-3 weeks, without fail, my atheros drivers randomly stop working. I can view networks, but can't connect to any of them. Network manager just times out. Often, I'll have to restart my computer up to 5 times. Sometimes, that doesn't even work. I'll try loading and unloading the driver. Again, sometimes this works, sometimes it doesn't. 

Could anyone help shed some light as to what may be causing this?

here is the output of ifconfig:
```
root@girdy-laptop:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:68:3f:42:80  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:94 errors:0 dropped:0 overruns:0 frame:0
          TX packets:94 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9872 (9.8 KB)  TX bytes:9872 (9.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:e1:11:4c:fd  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:e1ff:fe11:4cfd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2447 (2.4 KB)  TX bytes:8442 (8.4 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-E1-11-4C-FD-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

About two weeks ago, I had a device called "pan0" in this list. After unloading and reloading the driver, it never came back. It has been replaced with wmaster0.

This is a Atheros AR5X chipset. I'm running ubuntu 9.04 on an Acer Aspire 4720z.

[SIZE="4"]Thanks for any help in advance [/SIZE] :guitar:

---

### Post by asuastrophysics on 2009-10-22
Here is the important part of lspci: 
```
04:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)

```

---

### Post by undecim on 2009-10-22
I think that with Atheros, there are some modules that interfere with each other. It may be that due to different hardware timing, sometimes the wrong modules are loaded before the right ones...

Though even after perusing many pages of the realm of infnite knowledge known as Google, I can't seem to find which modules those are...

Perhapse this could help diagnostics though: run this command once in a terminal when your wireless card is working:```
lsmod > lsmod.out.good
```and this once when it fails:```
lsmod > lsmod.out.bad
```(Note: they don't have to be run in that order)

Then post the contents of the files lsmod.out.good and lsmod.out.bad from your home directory.

---

### Post by asuastrophysics on 2009-10-22
> **undecim said:**
> I think that with Atheros, there are some modules that interfere with each other. It may be that due to different hardware timing, sometimes the wrong modules are loaded before the right ones...

Though even after perusing many pages of the realm of infnite knowledge known as Google, I can't seem to find which modules those are...

Perhapse this could help diagnostics though: run this command once in a terminal when your wireless card is working:```
lsmod > lsmod.out.good
```and this once when it fails:```
lsmod > lsmod.out.bad
```(Note: they don't have to be run in that order)

Then post the contents of the files lsmod.out.good and lsmod.out.bad from your home directory.

Here's the good. It's running now. ```
Module                  Size  Used by
ath5k                 116864  0 
binfmt_misc            18572  1 
ppdev                  16904  0 
i915                   77960  2 
drm                   123232  3 i915
input_polldev          12688  0 
lp                     19588  0 
parport                49584  2 ppdev,lp
snd_hda_intel         559028  3 
arc4                   10240  2 
snd_pcm_oss            52352  0 
snd_mixer_oss          24960  1 snd_pcm_oss
ecb                    11392  2 
snd_pcm                99464  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0 
snd_seq_oss            41984  0 
snd_seq_midi           15744  0 
snd_rawmidi            33920  1 snd_seq_midi
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
joydev                 20864  0 
mac80211              251528  1 ath5k
acer_wmi               26736  0 
sdhci_pci              16896  0 
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34064  2 snd_pcm,snd_seq
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                64028  0 
video                  29844  0 
intel_agp              39408  1 
led_class              13064  2 ath5k,acer_wmi
ricoh_mmc              12544  0 
sdhci                  27396  1 sdhci_pci
pcspkr                 11136  0 
serio_raw              14468  0 
iTCO_wdt               21712  0 
iTCO_vendor_support    12420  1 iTCO_wdt
snd                    78920  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm
cfg80211               43680  2 ath5k,mac80211
output                 11648  1 video
ohci1394               42164  0 
ieee1394              108288  1 ohci1394
tg3                   143364  0 
fbcon                  49792  0 
tileblit               11264  1 fbcon
font                   17024  1 fbcon
bitblit                14464  1 fbcon
softcursor             10368  1 bitblit
```

---

