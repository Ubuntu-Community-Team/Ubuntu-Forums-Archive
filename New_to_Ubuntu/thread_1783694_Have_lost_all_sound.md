---
title: "Have lost all sound?"
date: 2011-06-16
forum: New to Ubuntu
---

### Post by Old-un on 2011-06-16
I am running Xubuntu 11.04 and for some reason the computer nolonger produces any sound? I cannot play CD's. I can watch video's but there no sound. When i start up Skype i can nolonger make a test call. I can see who i am chatting with but that's it. Would it be worth me doing a new install of Xubuntu? Please help someone?

---

### Post by iclestu on 2011-06-16
> **Old-un said:**
> I am running Xubuntu 11.04 and for some reason the computer nolonger produces any sound? I cannot play CD's. I can watch video's but there no sound. When i start up Skype i can nolonger make a test call. I can see who i am chatting with but that's it. Would it be worth me doing a new install of Xubuntu? Please help someone?

Your sound card/chipset showing ok?

do

```
sudo lspci
``` 

and post results

---

### Post by Old-un on 2011-06-16
I opened a terminal and typed: sudo lspci and here is the output.

 00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:11.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 10)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]
02:00.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
02:01.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)

Hope someone can help me out here

---

### Post by iclestu on 2011-06-16
> **Old-un said:**
> I opened a terminal and typed: sudo lspci and here is the output.

 00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:11.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 10)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]
02:00.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
02:01.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)

Hope someone can help me out here

run

```
aplay -l
```

---

### Post by iclestu on 2011-06-16
oooo- and 

```
sudo lsmod
```

---

### Post by Old-un on 2011-06-16
_The output from aplay -l_
 
**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: IXP [ATI IXP], device 1: ATI IXP IEC958 [ATI IXP IEC958 (AC97)]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

_The output from lsmod _

Module                  Size  Used by
snd_usb_audio          91410  3 
snd_atiixp             19400  5 
snd_hwdep              13274  1 snd_usb_audio
snd_ac97_codec        105614  1 snd_atiixp
ac97_bus               12642  1 snd_ac97_codec
tuner_simple           18134  1 
tuner_types            18907  1 tuner_simple
snd_usbmidi_lib        24388  1 snd_usb_audio
snd_pcm                80244  4 snd_usb_audio,snd_atiixp,snd_ac97_codec
wm8775                 12902  1 
snd_seq_midi           13132  0 
tda9887                17887  1 
snd_rawmidi            25269  2 snd_usbmidi_lib,snd_seq_midi
radeon                896428  2 
snd_seq_midi_event     14475  1 snd_seq_midi
tda8290                22227  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
tuner                  26802  2 
snd                    55295  25 snd_usb_audio,snd_hwdep,snd_atiixp,snd_ac97_codec,snd_usbmidi_lib,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cx25840                48549  1 
ati_agp                13202  0 
ttm                    65184  1 radeon
drm_kms_helper         40745  1 radeon
soundcore              12600  1 snd
drm                   180037  4 radeon,ttm,drm_kms_helper
ppdev                  12849  0 
ivtv                  143431  0 
cx2341x                27688  1 ivtv
psmouse                73312  0 
snd_page_alloc         14073  2 snd_atiixp,snd_pcm
v4l2_common            16757  5 wm8775,tuner,cx25840,ivtv,cx2341x
pwc                    82651  0 
tveeprom               17009  1 ivtv
i2c_piix4              13095  0 
i2c_algo_bit           13184  2 radeon,ivtv
k8temp                 12872  0 
serio_raw              12990  0 
videodev               75143  7 wm8775,tuner,cx25840,ivtv,cx2341x,v4l2_common,pwc
parport_pc             32111  1 
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
firewire_ohci          31504  0 
8139too                23208  0 
firewire_core          56138  1 firewire_ohci
8139cp                 22497  0 
sata_sil               13278  2 
crc_itu_t              12627  1 firewire_core
pata_atiixp            12968  0

---

### Post by iclestu on 2011-06-16
try

```
sudo modprobe snd_atiixp
```

if that doesnt work, try this:

> 
"My notebook is possibly the most Linux-incompatible machine that's ever  been made. Here's a tip: Don't buy an Asus A6R. It's one of the worst  notebooks I've ever owned. 
      Sound didn't work straight off. The notebook has an IXP SB400  AC'97 Audio Controller, according to Ubuntu's Device Manager. If you've  got the same sound card, and want to get it working, you need to do two  things. 
      (1) Double-click the speaker icon in Ubuntu's system tray and  click Edit -> Preferences in the Volume Control window that appears.  In the list, look for the Master Surround entry, and put a checkbox in  it. Then look for External Amplifier and put a check in it. Click the  Close button then click the Switches tab in the Volume Control window.  Remove the check against External Amplifier. 
      (2) Then click the Playback tab and click the Speaker icon beneath  the Master Surround slider, so that it's no longer muted. Then adjust  the slider. Playback some audio and you should find everything now  works. Basically, the Master Surround slider is now your volume slider.  Weird, but true. To make the system tray applet use the Master Surround  to control the volume, right-click the system tray speaker icon, select  Preferences, and select Master Surround in the list. "


from here: [http://ubuntuforums.org/archive/index.php/t-365342.html](http://ubuntuforums.org/archive/index.php/t-365342.html)

---

### Post by iclestu on 2011-06-16
did you get it running?

---

### Post by Old-un on 2011-06-16
I opened a terminal and typed sudo modprobe snd_atiixp but that didn't work so i am now looking at the second option. I shall let you know if it works.

---

### Post by yetiman64 on 2011-06-16
I think you have a settings problem. I had a similar problem just after installing Xubuntu yesterday, my hardware is fine in the other 6 linux installs here and it showed up fine in the steps below. I found one of the settings in the following proceedure was muted (can't remember which it was - the mute buttons are at the bottom of the sliders and will have a red cross on them, I suspect it was the pulseaudio one).

On the indicator plugin on your panel, click the sound icon and choose "sound preferences" > Hardware Tab, highlight your sound device (if it is not there the hardware is not recognized) and set it for the correct output eg. I use stereo analog duplex here for stereo output and microphone inputs, mainly check the device is active. Go to the "output tab" and ensure the device is selected in the main window and the connector at the bottom is set for your output type (eg. if using speakers or headphones).

If all is ok with the above, right click the desktop and go to Applications > Multimedia > Mixer, for the sound card select your device (eg here it's HDA ATI SB (alsa mixer)) > select controls, and tick "master" now in the main window check it is not muted and is turned up. Under sound card again select "playback: Internal audio .... (Pulseaudio Mixer)" do the same as for your sound card, ensure it is not muted and turn the sliders up full.

Finer control over audio and devices can be gained by installing padevchooser (pulse audio device chooser). This will allow you to choose device monitors as well as the devices themselves (handy for recording). It will also allow you to set levels and check for muted devices far more easily.

---

### Post by Old-un on 2011-06-16
Finally! I downloaded PulseAudio Manager from Ubuntu's Software Centre and then clicked on the volume icon in the bottom left-hand corner and from the drop-down menu opposite Sound card i selected, Playback: Internal Audio Analogue Stereo (PulseAudio Mixer) and now i can listen to CD's, Video's and use the likes of Skype once again.

Big thanks to iclestu + yetiman64 for all the help and advice.

---

