---
title: "Skype Sound Does Not Work - PulseAudio Problems?"
date: 2010-03-23
forum: New to Ubuntu
---

### Post by wbar2 on 2010-03-23
I have Ubuntu Karmic (9.10) 64-bit installed. I just installed Skype 2.1.0.81 Beta for the 64-bit system. **Sound works on my system (login, Rythmbox, etc.) but not in Skype.** My webcam in Skype works fine.

In Skype I go to Options... Sound Devices. The only option for Microphone, Speakers, and Ringing is PulseAudio server (local). There are no other options.

I have attempted [_the instructions on this page_]("http://www.pulseaudio.org/wiki/PerfectSetup") under Skype, and they did not help (most of the steps had already been completed, or could not be completed since I have no other options in Skype preferences).

I have read [_this post_]("http://ubuntuforums.org/showthread.php?t=1435996&highlight=skype+sound+-working") on making sure sound preferences are setup correctly, but I see no option for Skype under system sound preferences.

I also checked [_this post_]("http://ubuntuforums.org/showthread.php?t=1429013&highlight=skype+sound+-working"), but the person just solved his problem by upgrading to 9.10, which I already have. [_This person_]("http://ubuntuforums.org/showthread.php?t=1428547&highlight=skype+sound+-working") upgraded Skype to the version I have and solved his problem, but I am already running that version. I have also installed "skysentials" package, but that did not help.
[B]
[COLOR="DarkSlateBlue"]The only possible solution that I see is from [_this page of release notes_.]("https://developer.skype.com/LinuxSkype/ReleaseNotes") It states: "*When PulseAudio is enabled in the audio settings, only that specific entry will be available; to change the settings, use the PulseAudio manager tool that is bundled with your distribution*." I have no idea what this PulseAudio manager tool is, and the link they give on that page is broken.[/COLOR][/B] Does anyone know what this is or another possible solution? Thanks!

I also saw that this might be helpful in troubleshooting. Here is the lsmod output from the terminal:```


Module                  Size  Used by
binfmt_misc            10220  1 
ppdev                   8232  0 
snd_hda_codec_atihdmi     4320  1 
arc4                    2144  2 
ecb                     3296  2 
snd_hda_codec_idt      73008  1 
snd_hda_intel          31880  2 
snd_hda_codec          87584  3 snd_hda_codec_atihdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               9352  1 snd_hda_codec
snd_seq_dummy           3460  0 
iptable_filter          3872  0 
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
ip_tables              21200  1 iptable_filter
x_tables               25832  1 ip_tables
uvcvideo               65260  0 
videodev               43360  1 uvcvideo
v4l1_compat            16644  2 uvcvideo,videodev
v4l2_compat_ioctl32    13344  1 videodev
snd_rawmidi            27296  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
ath5k                 137352  0 
mac80211              210040  1 ath5k
ath                    10304  1 ath5k
snd_pcm                93160  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
fglrx                2234552  33 
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    77096  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_seq_oss,snd_pcm_oss,snd_mixer_oss,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
soundcore               9088  1 snd
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
shpchp                 37756  0 
amd64_edac_mod         26688  0 
edac_core              48876  1 amd64_edac_mod
psmouse                57124  0 
serio_raw               6596  0 
cfg80211              109144  3 ath5k,mac80211,ath
i2c_piix4              11728  0 
joydev                 13088  0 
lirc_ene0100            9444  0 
lirc_dev               13928  1 lirc_ene0100
lp                     11908  0 
hp_accel               12480  0 
parport                40528  2 ppdev,lp
lis3lv02d               9312  1 hp_accel
input_polldev           4720  1 lis3lv02d
led_class               5256  2 ath5k,hp_accel
usb_storage            66304  0 
r8169                  38884  0 
mii                     6368  1 r8169
video                  23612  0 
output                  3680  1 video
```

---

### Post by wbar2 on 2010-03-23
I solved the issue.

I found this documentation to be very helpful:
[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

I installed Pulse Audio Volume Controller (pavucontrol). The issue was that the system sound effects were set too low. Apparently Skype's sound is set to that same level. So I just turned up the system sound effects and everything works fine with Skype's sound now.

---

### Post by 3rdalbum on 2010-03-23
Sorry I couldn't get to your issue sooner, I was sleeping. I would have noted that Ubuntu's Pulseaudio management program is when you left-click on the volume control on your panel and choose "Sound Preferences".

If anyone is still running 9.04 and wants a Pulseaudio control program, they can install the 'padevchooser' application from Synaptic.

---

### Post by wbar2 on 2010-03-24
No problem. I appreciate the help. I would add that the Pulseaudio management program was not in my Sound Preferences even in 9.10. I did not have it until I installed pavucontrol, and it is now located in the Sound menu under Applications. Thanks!

---

### Post by wilsontp on 2010-03-28
I have ubuntu 9.10, and an hp tx2525nr with a built-in webcam.
 
I noticed my internal microphones aren't working with skype.
 
Then I noticed they aren't working at all.
 
If anyone can help me, please let me know.

---

