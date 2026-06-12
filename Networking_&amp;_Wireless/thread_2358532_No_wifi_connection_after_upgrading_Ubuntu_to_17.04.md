---
title: "No wifi connection after upgrading Ubuntu to 17.04"
date: 2017-04-14
forum: Networking &amp; Wireless
---

### Post by Caleb012 on 2017-04-14
I am unable to connect either via ethernet or wirelessly. If I boot up under "Advances Options", "Recovery Mode" I am able to connect. Thanks for any help you might give.........

---

### Post by wildmanne39 on 2017-04-14
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by Caleb012 on 2017-04-14
dcdbas                 16384  0
snd_hda_codec_analog    16384  1
snd_hda_codec_generic    73728  1 snd_hda_codec_analog
snd_hda_intel          36864  3
snd_hda_codec         126976  3 snd_hda_intel,snd_hda_codec_analog,snd_hda_codec_generic
snd_hda_core           81920  4 snd_hda_intel,snd_hda_codec,snd_hda_codec_analog,snd_hda_codec_generic
snd_hwdep              16384  1 snd_hda_codec
input_leds             16384  0
joydev                 20480  0
snd_pcm               102400  3 snd_hda_intel,snd_hda_codec,snd_hda_core
kvm                   593920  0
irqbypass              16384  1 kvm
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
serio_raw              16384  0
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_seq,snd_pcm
lpc_ich                24576  0
snd                    77824  16 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_hda_codec_analog,snd_timer,snd_rawmidi,snd_hda_codec_generic,snd_seq_device,snd_pcm
soundcore              16384  1 snd
shpchp                 36864  0
mac_hid                16384  0
8812au               1703936  0
cfg80211              602112  1 8812au
parport_pc             32768  1
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
ip_tables              24576  0
x_tables               36864  1 ip_tables
autofs4                40960  2
hid_generic            16384  0
i915                 1449984  104
psmouse               139264  0
video                  40960  1 i915
i2c_algo_bit           16384  1 i915
drm_kms_helper        151552  1 i915
pata_acpi              16384  0
usbhid                 53248  0
tg3                   163840  0
hid                   114688  3 hid_generic,usbhid
ptp                    20480  1 tg3
pps_core               20480  1 ptp
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   352256  7 i915,drm_kms_helper
fjes                   73728  0

---

### Post by wildmanne39 on 2017-04-14
Can you try those commands again run each line separately, run the first line then hit enter, then run the second line and hit enter and so on, then follow the directions in my first post that tells you how to put the information between code tags, and include all the information in one post.
Thanks

---

### Post by Caleb012 on 2017-04-14
Sorry....will try again......

---

### Post by wildmanne39 on 2017-04-14
Nothing to worry about if you have questions please ask.

---

### Post by Caleb012 on 2017-04-14
```
Module                  Size  Used by
snd_hda_codec_analog    16384  1
snd_hda_codec_generic    73728  1 snd_hda_codec_analog
dcdbas                 16384  0
snd_hda_intel          36864  3
snd_hda_codec         126976  3 snd_hda_intel,snd_hda_codec_analog,snd_hda_codec_generic
snd_hda_core           81920  4 snd_hda_intel,snd_hda_codec,snd_hda_codec_analog,snd_hda_codec_generic
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               102400  3 snd_hda_intel,snd_hda_codec,snd_hda_core
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
kvm                   593920  0
irqbypass              16384  1 kvm
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
serio_raw              16384  0
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
joydev                 20480  0
input_leds             16384  0
snd_timer              32768  2 snd_seq,snd_pcm
snd                    77824  16 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_hda_codec_analog,snd_timer,snd_rawmidi,snd_hda_codec_generic,snd_seq_device,snd_pcm
lpc_ich                24576  0
shpchp                 36864  0
soundcore              16384  1 snd
mac_hid                16384  0
8812au               1703936  0
cfg80211              602112  1 8812au
parport_pc             32768  1
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
ip_tables              24576  0
x_tables               36864  1 ip_tables
autofs4                40960  2
hid_generic            16384  0
i915                 1449984  107
psmouse               139264  0
video                  40960  1 i915
pata_acpi              16384  0
tg3                   163840  0
usbhid                 53248  0
i2c_algo_bit           16384  1 i915
drm_kms_helper        151552  1 i915
hid                   114688  3 hid_generic,usbhid
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
ptp                    20480  1 tg3
pps_core               20480  1 ptp
drm                   352256  7 i915,drm_kms_helper
fjes                   73728  0

```

---

### Post by wildmanne39 on 2017-04-14
This is an issue with 17.04 and several adapters, this fix works for certain wifi issues, that have been reported here to bugzilla.
[https://bugzilla.gnome.org/show_bug.cgi?id=780119](https://bugzilla.gnome.org/show_bug.cgi?id=780119)

Open the file with your text editor, if you need more directions just ask:
```
sudo -H gedit /etc/NetworkManager/NetworkManager.conf
```
add lines
```
[device]
wifi.scan-rand-mac-address=0
```
Save and close file then reboot.

This is for the wifi only, I think it will work, if it does the wifi still usually needs a new driver but it is hard to tell since all the information I asked for did not get posted.

---

### Post by Caleb012 on 2017-04-14
I very much appreciate your help. I am sorry I failed to get all the info you asked for.......being new to Linux puts me at a disadvantage, I was able to get wi-fi working though a wired connection still doesn't work. Thanks very much!

---

### Post by wildmanne39 on 2017-04-14
That is okay, when in doubt just ask for clarification.

Please start a new thread for your wired connection and see if it will connect if you open a browser.

I suspect you may have connection issues with the wifi that we will have to work through.

I would update 17.04 and make sure all updates are installed.

---

### Post by maurizio-firmani on 2017-04-15
Thanks, same problem here after upgrading to 17.04 (Gnome flavour): with this, I've got my TP-LINK USB stick working now!

---

### Post by Cybermutt on 2017-07-07
Excellent.  I fought with this problem for days before coming across with this fix.  Many thanks for saving a few more gray hairs.

---

