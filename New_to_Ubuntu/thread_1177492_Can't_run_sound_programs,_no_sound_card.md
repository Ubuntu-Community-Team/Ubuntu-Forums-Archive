---
title: "Can't run sound programs, no sound card?"
date: 2009-06-03
forum: New to Ubuntu
---

### Post by Nythain on 2009-06-03
Ok, so i re-formatted and re-installed today, upgrading to Jaunty from Intrepid, thinking, this can only be a good idea. Well, all goes well, untill i try to run mocp. It spews forth some error about alsa no card 0 etc. so i get to investigating. Next i try alsamixer, it spews forth some other error (btw all of these will be posted with relevent info). So i dig deeper and this is pretty much all i can find out, but cant make heads or tails out of any of it.
```

cat /proc/asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xf9ff8000 irq 20

lspci | grep -i audio
00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)

lsmod | grep -i snd
snd_hda_intel         435636  0 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62628  9 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm

sudo lshw -C sound
*-multimedia            
      description: Audio device
      product: MCP73 High Definition Audio
      vendor: nVidia Corporation
      physical id: 9
      bus info: pci@0000:00:09.0
      version: a1
      width: 32 bits
      clock: 66MHz
      capabilities: pm msi bus_master cap_list
      configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel

```and here's the errors both mocp and alsamixer are spittin at me
```

alsamixer
alsamixer: function snd_ctl_open failed for default: No such file or directory

mocp
Running the server...
Trying ALSA...
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM default

```i can only assume at this point that possibly alsa just doesnt know what driver to use for the card or doesnt know the card exists or whatnot, but im sound device and driver retarded, any help would be appreciated... thanks

*Edit Solved my problem by apt-get --purge remove alsa-base alsa-utils linux-sound-base then re-installing them... not sure how to mark thread as solved the correct way, so i just added it to the title :P

---

### Post by b@sh_n3rd on 2009-06-03
I'm not quite sure of this, but I'll try to help you with what I know. What would ```
# aplay -l
``` give you? Furthermore, what happens if you try; ```
# sudo alsamixer
``` instead of entering it as a normal user?

---

### Post by Don1500 on 2009-06-03
do this:
[http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html)

---

