---
title: "Getting sound to work in Jaunty 64-bit"
date: 2009-06-29
forum: New to Ubuntu
---

### Post by RichterAzael on 2009-06-29
Ok so I've got Jaunty installed on my laptop and running but sound is not working. How would I go about fixing this?
Edit: Thought I'd add that it worked just fine before in Hardy Heron 64-bit.

---

### Post by fooman on 2009-06-29
have you checked that nothing is muted or just turned down all the way in the alsa mixer?

right click on the speaker/volume icon that is in the top panel and choose "open volume control" from the list.

when the alsa mixer opens,  check that PCM and master are turned up all the way and are not muted.

---

### Post by RichterAzael on 2009-06-29
everything is turned up and nothing is muted at all. I'm not exactly sure what to do but here is some info that I got from running some commands (ie lspci, lsmod, etc)

richter@richter-laptop:~$ cat /proc/asound/cards  
  0 [Intel          ]: HDA-Intel - HDA Intel  
                       HDA Intel at 0xf4600000 irq 22  
 richter@richter-laptop:~$  
 

 00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)  
     Subsystem: Gateway 2000 Device 0690  
     Flags: bus master, fast devsel, latency 0, IRQ 22  
     Memory at f4600000 (64-bit, non-prefetchable) [size=16K]  
     Capabilities: <access denied>  
     Kernel driver in use: HDA Intel  
     Kernel modules: snd-hda-intel  
 

 ichter@richter-laptop:~$ lsmod |grep snd  
 snd_hda_intel         557492  4  
 snd_pcm_oss            52352  0  
 snd_mixer_oss          24960  1 snd_pcm_oss  
 snd_pcm                99336  2 snd_hda_intel,snd_pcm_oss  
 snd_seq_dummy          11524  0  
 snd_seq_oss            41984  0  
 snd_seq_midi           15744  0  
 snd_rawmidi            33920  1 snd_seq_midi  
 snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi  
 snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event  
 snd_timer              34064  2 snd_pcm,snd_seq  
 snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq  
 snd                    78792  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 soundcore              16800  1 snd  
 snd_page_alloc         18704  2 snd_hda_intel,snd_pcm  
 

  0 snd_hda_intel  
 

 **** List of PLAYBACK Hardware Devices ****  
 card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]  
   Subdevices: 0/1  
   Subdevice #0: subdevice #0  
 card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]  
   Subdevices: 1/1  
   Subdevice #0: subdevice #0  
 

 **** List of CAPTURE Hardware Devices ****  
 card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]  
   Subdevices: 2/2  
   Subdevice #0: subdevice #0  
   Subdevice #1: subdevice #1

---

### Post by RichterAzael on 2009-06-29
got sound working thanks to this post/thread:

[http://ubuntuforums.org/showthread.php?t=1137610&highlight=gateway](http://ubuntuforums.org/showthread.php?t=1137610&highlight=gateway)

---

