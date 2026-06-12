---
title: "Sound problems with new install of 10.10"
date: 2010-10-30
forum: New to Ubuntu
---

### Post by ozmart2010 on 2010-10-30
I am a newbie to Linux. I installed 10.10 today and all seems well except there is no sound. Mute is off and Ubuntu recognizes the soundcard. The speakers are okay and work fine in WinXP. I searched the forum and found some commands which I ran (see below). Can anyone plse help me with this (and plse assume I know nothing which pretty close to the mark)?

Here is the output:

martin@martin-G41MT-D3:~$ lspci |grep Audio
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
martin@martin-G41MT-D3:~$ 


martin@martin-G41MT-D3:~$ lsmod |grep snd
snd_hda_codec_realtek   217980  1 
snd_hda_intel          22107  0 
snd_usb_audio          86704  1 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
snd_pcm                71475  3 snd_hda_intel,snd_hda_codec,snd_usb_audio
snd_hwdep               5040  2 snd_hda_codec,snd_usb_audio
snd_usbmidi_lib        17413  1 snd_usb_audio
snd_seq_midi            4588  0 
snd_rawmidi            17783  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    49006  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_hwdep,snd_usbmidi_lib,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
martin@martin-G41MT-D3:~$

---

### Post by georgetom on 2010-10-30
Did you also check in System>Preferences>Sound that volumes levels are fine in all the tabs?

---

### Post by ozmart2010 on 2010-10-30
Yes, all those volume level settings are okay.

---

### Post by ozmart2010 on 2010-10-30
Anyone? Thks.

---

### Post by oneNF on 2010-10-30
I have no answer for you i'm afraid but the sticky at the top of the general forum may help. it provides work arounds for known 10,10 bugs. I believe there are some known issues with sound this release.

cheers

---

### Post by ozmart2010 on 2010-10-30
From what I can glean from here : [http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)
it may possibly be my ALSA package. This page is somewhat hard to follow, for me at least but I have found out that I am running the Advanced Linux Sound Architecture Driver Version 1.0.23.

I also ran the speaker test...but there was no sound:
speaker-test -Dplughw:0,0 -c2 

speaker-test 1.0.23

Playback device is plughw:0,0
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 1048576
Period size range from 32 to 524288
Using max buffer size 1048576
Periods = 4
was set period_size = 262144
was set buffer_size = 1048576
 0 - Front Left
 1 - Front Right
Time per period = 11.035875
 0 - Front Left
 1 - Front Right
Time per period = 11.027954
 0 - Front Left
 1 - Front Right
Time per period = 11.027975
 0 - Front Left
 1 - Front Right

There must be a sound guru out there?? Not sure what to do next!

---

### Post by ozmart2010 on 2010-10-30
I've also been following this page: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

however, no luck so far. 

One thing I found in System>Admin>Users>Advanced settings>user priveleges, use audio devices was not ticked. I ticked it but nothing so far, so will try a reboot and see what happens.

---

### Post by ozmart2010 on 2010-10-31
I still have no sound despite everything. I would like to persevere with Ubuntu but if I can't get sound then there is not much point. Can anyone offer a solution, or is there some other support method I can try?

Thks.

---

### Post by G-Fresh on 2010-10-31
I'm sorry I can't help but I am suffering from the same problem.  In addition to the sound not working the desktop has resized itself too.  

Can anyone help?

---

### Post by ozmart2010 on 2010-11-01
I found this troubleshooter which I am trying now. Hopefully this will get some results.

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

---

### Post by cboxhero on 2010-11-02
It might just be your speakers or computer. On my laptop sometimes if I cut the power on it the headphones will stop working. I just unplug them for a while and plug them back in. If that doesn't help I don't know much else to do. It could have even possibly been a screw up with the packages that were installed. I really hope someone will come along and help you out.

---

### Post by ozmart2010 on 2010-11-02
I got yo Step 7 and then got an error:
"$ gnome-alsamixer (gnome-alsamixer:2046): GLib-GObject-CRITICAL **: g_type_instance_get_private: assertion `instance != NULL && instance->g_class != NULL' failed
 (gnome-alsamixer:2046): GLib-GObject-CRITICAL **: g_type_instance_get_private: assertion `instance != NULL && instance->g_class != NULL' failed
Segmentation fault"


I'm not 100% sure what I did but I think I uninstalled the Gnome-Alsa mixer and then I installed something just called 'Alsa mixer' from the software centre, plus the GUI. I opened the gui and selected the output column and the sound suddenly came to life!

---

### Post by LADmaticCA on 2010-11-02
Others, with your sound hardware, managed to get it working in the link below by installing the backports package.

[http://ubuntuforums.org/archive/index.php/t-1439408.html](http://ubuntuforums.org/archive/index.php/t-1439408.html)

That was for 10.04, since you're using 10.10 the install command would be:

```
sudo apt-get install linux-backports-modules-alsa-maverick-generic
```

After rebooting, check System>Preferences>Sound for any muting and try to play audio.


*Edit
Great you got it working!

---

