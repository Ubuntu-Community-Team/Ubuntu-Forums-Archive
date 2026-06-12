---
title: "sound?"
date: 2009-11-22
forum: New to Ubuntu
---

### Post by dbch on 2009-11-22
NO sound.  Ever.  Got Volume Applet 2.22.2 and Alsa Mixer.
I bought this computer used with ubuntu on it.  What's up?

---

### Post by quinnten83 on 2009-11-22
well, how about a little bit more information, then?
We can't guess what is happening by tapping into our psychic powers.
First of, brand type, motherboard, souncard info. Is it a laptop, a desktop, a netbook?
You bought it with Ubuntu on it, which version? Hardy, gutsy, jaunty?
Did you upgrade to Karmic, how did you do that? a complete reinstall?
Was the sound working before? Did you tinker with it? Did you maybe by accident muted the sound in the pulseaudio configuration.
Which version are you running now?
Could you do a "sudo lspci" and post the results?

We need more info, otherwise, the way wrote down your post, people will think it's just flamebait and you won't get help.

---

### Post by dbch on 2009-11-22
Huh?  Huh?  and Huh?

I bought this thing at free geek - if you've heard of it - so its a bunch of stuff put together.  Dell mostly.  It came with a green sheet with the specs on it but I can't find it now (moved recently too).  I'm looking for this stuff on the computer but I can't find it anywhere - I think I saw it once.

The version is hardy.

Never used the sound - thought it was off.  Upped to max and nothing.  They only have a 7 day warranty and they don't do repairs.

In the sound preferences window I hit 'test' and let it go for like 5 minutes - it never quit.
Its got marked for a sound at login and logout but I've never heard one.

---

### Post by dbch on 2009-11-22
oh.  desktop.

---

### Post by camaron1 on 2009-11-22
Have a look at these threads:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by dbch on 2009-11-22
Ok.  I have a sound card and alphamixer is not mute.  Hitting play on the login sound in the sound preferences window brings nothing.  So repair shop?

And I still keep getting greyed out and no response and have to unplug from the wall.

Repair shop?  

I just want to be sure before I commit any cash.


There was a note on the computer stating that if I had any questions that I should ask them here.

---

### Post by frenchn00b on 2009-11-22
Could you post : 

```
lsmod | grep snd

cat /etc/modprobe.d/sound.conf 

lsusb 



```

---

### Post by dbch on 2009-11-25
dbch@freegeek:~$ lsmod | grep snd
snd_intel8x0           35356  3 
snd_ac97_codec        101028  1 snd_intel8x0
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78724  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  3 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  15 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm

dbch@freegeek:~$ cat /etc/modprobe.d/sound.conf
cat: /etc/modprobe.d/sound.conf: No such file or directory

dbch@freegeek:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

