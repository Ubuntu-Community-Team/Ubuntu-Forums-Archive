---
title: "Sound problems"
date: 2010-03-13
forum: New to Ubuntu
---

### Post by mro_k on 2010-03-13
Hi!

I have a fujitsu siemens notebook with ubuntu. Recently I've discovered that it has no sound. I have no idea why it happened. The last thing I did was to install and then delete skype client (downloaded form skype.com) But I am not sure it has anything to do with it.
In the preferences/sound I always had *autodetect* option and it worked fine but not anymore. When I manually try to choose *HDA Intel Alsa*, I get the following error message. (see attachment) Could this be the problem? Is there a simple way to solve it?

---

### Post by joe.beard on 2010-03-13
Is the required module loaded? What sound card do you have and what is the output to lsmod?

---

### Post by mro_k on 2010-03-13
joe.beard,

I hate to admit it, but I have no idea how to check whether the modules are loaded and how to check output to Ismod.

If you could describe step by step where I can look it up, perhaps I could manage it.

---

### Post by Daveth on 2010-03-13
he is expecting you to type
```
lsmod
```
into a terminal, which you will find under Application/ accessories/terminal. It will scroll out a huge list of stuff which you can cut and paste back to him. 
That said, have you tried setting it from Autodetect to Pulseaudio and see what that does? I do find the settings sometimes fall over, and a few changes sometimes get things back the way they were. We are all sitting here assuming, of course, that your sound was lovely and full beforehand!!

---

### Post by mro_k on 2010-03-14
No, Pulseaudio does not work either. Yes, I had no problem with the sound before. That is why I was so surprised to discover that it does not function any more. :(
Here is the output from lsmod:

```
Module                  Size  Used by
aes_i586               15744  1 
aes_generic            35880  1 aes_i586
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56212  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
arc4                    9856  2 
ecb                    10752  2 
iwl3945                97912  0 
snd_hda_intel         436148  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
mac80211              217592  1 iwl3945
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
psmouse                61972  0 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
fglrx                2081668  34 
pcspkr                 10496  0 
serio_raw              13444  0 
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
video                  25872  0 
led_class              12036  1 iwl3945
joydev                 18368  0 
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
output                 11008  1 video
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
intel_agp              34108  0 
agpgart                42696  2 fglrx,intel_agp
cfg80211               38288  2 iwl3945,mac80211
snd                    62756  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
usbhid                 42336  0 
r8169                  40836  0 
mii                    13312  1 r8169
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
```

---

### Post by mro_k on 2010-03-15
Uff, I did it hard way. Instead of searching the error in 9.04 I just upgraded to 9.10. So far everything functions, including sound.
Anyway, thanks for responding.

---

