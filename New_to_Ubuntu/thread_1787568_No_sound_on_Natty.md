---
title: "No sound on Natty"
date: 2011-06-21
forum: New to Ubuntu
---

### Post by Blojic on 2011-06-21
Good Afternoon,

I have an obscure Philips Freevents X56 laptop and have just upgraded to Natty from a clean install of Lucid and can't hear any sound.

Sound hasn't been a problem in the past and has worked out-of-the-box with Feisty/Gutsy/Karmic/Lucid. Has there been any fundamental changes to the sound system in Natty that I should be looking into?

The laptop is connected via phono leads to a big hifi amplifier and speakers and if I turn the sound up on the amp full-whack til the speakers are humming I can hear the sound VERY faintly so it's having a stab at it.

I'm not too good at diagnostics, so any help would be appreciated. I've tried the obvious volume sliders.

Thanks,

---

### Post by rbowen1 on 2011-06-21
This could be a issue with your amplifier and speakers.  Can you get hold of a standard desktop speakers to test.   Other wise you can try the tips on this link.   [http://ubuntuforums.org/showthread.php?t=205449&highlight=NVIDIA+GeForce4](http://ubuntuforums.org/showthread.php?t=205449&highlight=NVIDIA+GeForce4)

---

### Post by smurphy_it on 2011-06-21
I haven't messed with audio in some time, but I'm sure folks will need some more information.  Post the results of these two commands please.

```
sudo lspci |grep [Aa]udio
```

```
sudo lsmod
```

---

### Post by computerandu on 2011-06-21
> **Blojic said:**
> Good Afternoon,

I have an obscure Philips Freevents X56 laptop and have just upgraded to Natty from a clean install of Lucid and can't hear any sound.

Sound hasn't been a problem in the past and has worked out-of-the-box with Feisty/Gutsy/Karmic/Lucid. Has there been any fundamental changes to the sound system in Natty that I should be looking into?

The laptop is connected via phono leads to a big hifi amplifier and speakers and if I turn the sound up on the amp full-whack til the speakers are humming I can hear the sound VERY faintly so it's having a stab at it.

I'm not too good at diagnostics, so any help would be appreciated. I've tried the obvious volume sliders.

Thanks,


First thing to check...

Go in Sound Preference (by clicking on the speaker icon in the panel)...Check if it is muted there?

---

### Post by Blojic on 2011-06-21
Output of sudo lspci |grep [Aa]udio

```
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
```

Output of sudo lsmod

```
Module                  Size  Used by
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_si3054    12924  1 
snd_hda_codec_realtek   255820  1 
joydev                 17322  0 
arc4                   12473  2 
snd_atiixp_modem       18624  0 
snd_hda_intel          24140  2 
snd_via82xx_modem      18305  0 
iwl3945               130113  0 
snd_hda_codec          90901  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_seq_midi           13132  0 
snd_intel8x0m          18493  0 
iwlcore               148965  1 iwl3945
mac80211              257001  2 iwl3945,iwlcore
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_ac97_codec        105614  3 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m
i915                  450944  3 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80244  7 snd_hda_codec_si3054,snd_atiixp_modem,snd_via82xx_modem,snd_hda_intel,snd_hda_codec,snd_intel8x0m,snd_ac97_codec
snd_timer              28659  2 snd_seq,snd_pcm
cfg80211              156212  3 iwl3945,iwlcore,mac80211
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         40745  1 i915
drm                   180037  4 i915,drm_kms_helper
snd                    55295  18 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_atiixp_modem,snd_via82xx_modem,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_intel8x0m,snd_rawmidi,snd_ac97_codec,snd_seq,snd_pcm,snd_timer,snd_seq_device
psmouse                73312  0 
soundcore              12600  1 snd
snd_page_alloc         14073  5 snd_atiixp_modem,snd_via82xx_modem,snd_hda_intel,snd_intel8x0m,snd_pcm
serio_raw              12990  0 
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
firewire_ohci          31504  0 
8139too                23208  0 
firewire_core          56138  1 firewire_ohci
8139cp                 22497  0 
sdhci_pci              13623  0 
ahci                   21591  2 
crc_itu_t              12627  1 firewire_core
sdhci                  22720  1 sdhci_pci
libahci                25548  1 ahci

```

@computerandu: Yes, I've tried that.Not muted

@rbowen1: I haven't got any to hand, no. But I get no sound from the internal laptop speakers if I unplug the lead, so I can't see that's the problem.

Thankyou all for your time. I'll have a read through your links. Any other ideas?

Thanks,

---

### Post by smurphy_it on 2011-06-21
Apparently you aren't the only one that experiences some issues after upgrading, when it comes to sound.

You could try checking all switches for the sound, and ensure "none" of them are muted.  Done by right clicking sound icon on your panel, select open volume control, click the "preferences" button.  Put a check box by all of the switches.

Also, in a terminal can you provide the information from this file.  It could be an option which has to be modified.

```
sudo cat /etc/modprobe.d/alsa-base.conf
```

---

### Post by smurphy_it on 2011-06-21
Also, I assume natty is like some previous version of Ubuntu and running pulse audio.  So you might want to try deleting your pulse directory.  Do the following: (this includes a backup), and I'm assuming you are in your home's user directory.

```
tar -cf pulsebkup.tar .pulse
```
```
rm -r .pulse
```

1st one backs up the pulse directory, second one deletes the .pulse directory and anything under it (recursively).

If sound still doesn't work, you might want to try logging out, and then back in.

---

### Post by Blojic on 2011-06-21
Output of sudo cat /etc/modprobe.d/alsa-base.conf

```
# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2

```

```
tar -cf pulsebkup.tar .pulse
rm -r .pulse
```

No difference :o(

---

### Post by Blojic on 2011-06-21
I've also ran that Alsa thingy, results here: -
[http://www.alsa-project.org/db/?f=7073f0e4d67087e9305d3db6fb3423784cc1bf3c]("http://www.alsa-project.org/db/?f=7073f0e4d67087e9305d3db6fb3423784cc1bf3c")
if it helps.

---

### Post by smurphy_it on 2011-06-21
As this is an update, would I be correct in assuming there is no "older kernel" to test ?

Perhaps you can update to a later kernel to see if that fixes your issue.
Otherwise, you could try filing a bug report ( [https://bugs.launchpad.net/](https://bugs.launchpad.net/) )  They would have much more experience with this kind of issue.

---

### Post by smurphy_it on 2011-06-21
Another thing you could try, is messing with the "options" by replacing them with vendor.  As yours is a Realtek, I'd try this.

```
sudo nano /etc/modprobe.d/alsa-base
```

Goto the bottom of the file, and add this line:

options snd-hda-intel model=realtek

May or may not work.  For other "options" to use, have a look at this webpage:

[http://ubuntuforums.org/showthread.php?t=314383](http://ubuntuforums.org/showthread.php?t=314383)

---

### Post by nigeldodd on 2011-08-21
same problem for me with Ubuntu 11.04 on a Philips Freevents laptop. No sound. Microphone works though.

---

### Post by rafe101 on 2011-08-23
I too have lost sound. This is on a computer running Mythtv, so now I have no TV, music, or movies, which is not fun.

Everything had been working great until I added a second capture card. I have since reinstalled Ubuntu 4 times. With each of the two capture cards alone and now with no capture cards installed. I still haven't gotten sound back.

No analog whatsoever even after fresh installs. I did have HDMI sound almost working (but that was a couple installs ago). It was very choppy and would quit altogether after a few seconds of playing a video or audio source.

I am using onboard AMD audio. I have checked all the levels and am out of ideas short of buying a new soundcard. This just doesn't make any sense since it used to work.

---

### Post by rafe101 on 2011-08-24
Please, no one waste any time thinking about my issue. It was a hardware problem. Fried onboard sound processor. A new PCI card and everything works.

---

### Post by emwu on 2011-08-27
> **nigeldodd said:**
> same problem for me with Ubuntu 11.04 on a Philips Freevents laptop. No sound. Microphone works though.

Try:

sudo gedit /etc/modprobe.d/alsa-base.conf

add following line at the end:

options snd-hda-intel model=generic

then restart


In my case (Philips Freevents X52) it worked

based on:  [http://www.webupd8.org/2010/11/fix-hda-intel-realtek-alc887-no-sound.html](http://www.webupd8.org/2010/11/fix-hda-intel-realtek-alc887-no-sound.html)

---

