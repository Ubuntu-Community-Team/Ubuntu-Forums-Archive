---
title: "Acer Aspire L3600 - WiFi hard blocked"
date: 2017-11-22
forum: Networking &amp; Wireless
---

### Post by dalekky on 2017-11-22
I have an Acer Aspire L3600. It is not a laptop but has laptop parts inside. There is NO physical switch to turn WiFi on or off. There is NO physical built-in keyboard with WiFi fn switch keys (you have to plug your own keyboard in).

rfkill list all results in -

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

I've tried several different WiFi cards - all same result.

I am reluctant to buy an external USB WiFi dongle to try if that is going to be hard blocked too.
What do I do to get this working?
How do I unblock this hard blocked WiFi card with no switch?

---

### Post by chili555 on 2017-11-22
Is the module acer-wmi loaded? Check:```
lsmod | grep acer
```Does it help to unload it?```
sudo modprobe -r acer-wmi
sudo rfkill unblock all
rfkill list all
```If it helps, we can make it permanent.

---

### Post by dalekky on 2017-11-22
There is no acer-wmi module present. grep returns no results.

---

### Post by chili555 on 2017-11-22
Any wmi or laptop modules at all? Please show us the entire: ```
lsmod
```

---

### Post by dalekky on 2017-11-22
```
Module                  Size  Used by
gpio_ich               16384  0
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
snd_hda_intel          40960  3
snd_hda_codec         135168  3 snd_hda_codec_realtek,snd_hda_codec_generic,snd_hda_intel
snd_hda_core           73728  4 snd_hda_codec_realtek,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
arc4                   16384  2
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               106496  3 snd_hda_codec,snd_hda_intel,snd_hda_core
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
iwl3945                69632  0
snd_rawmidi            32768  1 snd_seq_midi
iwlegacy              102400  1 iwl3945
mac80211              737280  2 iwl3945,iwlegacy
cfg80211              565248  3 iwl3945,iwlegacy,mac80211
coretemp               16384  0
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
serio_raw              16384  0
snd_timer              32768  2 snd_pcm,snd_seq
snd                    81920  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
joydev                 20480  0
input_leds             16384  0
soundcore              16384  1 snd
shpchp                 36864  0
lpc_ich                24576  0
8250_fintek            16384  0
mac_hid                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
uas                    24576  0
usb_storage            69632  1 uas
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  2 hid_generic,usbhid
i915                 1208320  4
psmouse               131072  0
ahci                   36864  2
libahci                32768  1 ahci
firewire_ohci          40960  0
video                  40960  1 i915
i2c_algo_bit           16384  1 i915
pata_acpi              16384  0
firewire_core          65536  1 firewire_ohci
crc_itu_t              16384  1 firewire_core
e1000e                237568  0
drm_kms_helper        155648  1 i915
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
ptp                    20480  1 e1000e
sysimgblt              16384  1 drm_kms_helper
pps_core               20480  1 ptp
fb_sys_fops            16384  1 drm_kms_helper
drm                   364544  6 i915,drm_kms_helper
fjes                   28672  0


```

---

### Post by chili555 on 2017-11-22
I see nothing in your lsmod that relates to the keymap, wmi, etc. Typically, in a laptop, a helper module like the aforementioned acer-wmi translates key presses into action. For example, on my laptop, F8 turns the wireless on and off. My helper module is thinkpad_acpi.

I assume that the simple act of:```
sudo rfkill unblock all
rfkill list all
```...does nothing; or does it?

If unblock all doesn't help, then harder measures are needed: [http://madwifi-project.org/wiki/UserDocs/MiniPCI](http://madwifi-project.org/wiki/UserDocs/MiniPCI) 

Also check here: [http://forum.notebookreview.com/threads/aspire-5633-wlmi-replacing-the-wifi-card.732714/](http://forum.notebookreview.com/threads/aspire-5633-wlmi-replacing-the-wifi-card.732714/) And here: [https://ubuntuforums.org/showthread.php?t=2355144](https://ubuntuforums.org/showthread.php?t=2355144)

I am sorry that I have no better suggestions.

---

### Post by dalekky on 2017-11-22
As I said. This isn't a laptop. It's an Acer Aspire L3600. It looks like this: [https://imagebin.ca/v/3iEvRF7UT07l](https://imagebin.ca/v/3iEvRF7UT07l)

sudo rfkill unblock all has no effect.

device remains hard blocked

---

### Post by dalekky on 2017-11-23
This unit is also sold as a VeritonL460 if that helps. The WiFi card I have however was bought separately and did not come with the machine.

---

### Post by chili555 on 2017-11-23
I fully realize that it isn’t a laptop.

Since unblock all has no effect, then the tape trick is the only remaining possibility I know of. Since you added the card later, I assume you know how to get it out, tape a pin and replace it.

---

### Post by dalekky on 2017-12-05
I can't figure out which pin is pin 13.
The diagram on the link shows:

```
1  key  3  5  7  9 11 13 15 ...
2  key  4  6  8 10 12 14 16 ...
```

But every wifi card I've ever seen (including my one) looks like this:

```
1  3  5  7  9 11 13 15 key 17 19 21 23 25 27 29 31 33...
2  4  6  8 10 12 14 16 key 18 20 22 24 26 28 30 32 34... etc
```

So are the pins to the left of the key not numbered? 

and the link to the picture supposedly showing a photo is a dead link.

---

### Post by chili555 on 2017-12-06
Does your card look like this? [https://www.youtube.com/watch?v=yzAKcmlaH1M&t=3s](https://www.youtube.com/watch?v=yzAKcmlaH1M&t=3s) Perhaps it is pin 20.

---

### Post by praseodym on 2017-12-06
Tried resetting your BIOS to default settings?

---

### Post by dalekky on 2017-12-07
Yes, it's mini pci express, so it looks like that with the same size keyed edge connector, but the PCB itself is a bit longer.

---

### Post by chili555 on 2017-12-07
> **dalekky said:**
> Yes, it's mini pci express, so it looks like that with the same size keyed edge connector, but the PCB itself is a bit longer.Does it indeed have 52 pins in total? Did you try pin 20? You can always remove the tape later if that's not it.

---

### Post by dalekky on 2017-12-08
Yes, there are 52 pins in total. I haven't had an opportunity to try taping pin 20 yet. I'll do it tomorrow if I have time.

---

