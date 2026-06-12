---
title: "agian with the no sound"
date: 2010-02-18
forum: New to Ubuntu
---

### Post by papahonk on 2010-02-18
ok  would adding a linux compatible sound card to my desktop help with my no sound? if so  what brand and model?

---

### Post by nikhilbhardwaj on 2010-02-18
does your current sound card not work??
post the details 
people at this forum will be able to help you up and running with sound on your current box

---

### Post by papahonk on 2010-02-18
some have tried  here is the original post..   

[http://ubuntuforums.org/showthread.php?t=1407127](http://ubuntuforums.org/showthread.php?t=1407127)




 i've been fighting with no sound for awhile now the post Lidex wanted me to follow was a little to complicated for me just yet. need to read more  but tough with homework and all just looking for a quicker fix i guess.. 

right now im trying to get my vid fixed on my laptop as well to many things breaking at once lol

---

### Post by nikhilbhardwaj on 2010-02-19
well looks like you've tried a lot of things 
read this too 
[http://wiki.archlinux.org/index.php/Advanced_Linux_Sound_Architecture](http://wiki.archlinux.org/index.php/Advanced_Linux_Sound_Architecture)

you can skip the initial section read from configuration

```

sudo amixer set Master 90% unmute
sudo amixer set PCM 85% unmute

aplay /usr/share/sounds/alsa/Front_Center.wav

```

if that works
then we can get onto saving the alsa state

let me know what happens
you may not have 
/usr/share/sounds/alsa/Front_Center.wav
you can replace this with any other wav file that you download

---

### Post by papahonk on 2010-02-19
Setting default sound card




```
ls -l /sys/module/snd/holders
total 0
lrwxrwxrwx 1 root root 0 2010-02-19 15:14 snd_ac97_codec -> ../../snd_ac97_codec
lrwxrwxrwx 1 root root 0 2010-02-19 15:14 snd_intel8x0 -> ../../snd_intel8x0
lrwxrwxrwx 1 root root 0 2010-02-19 15:14 snd_mixer_oss -> ../../snd_mixer_oss
lrwxrwxrwx 1 root root 0 2010-02-19 15:14 snd_pcm -> ../../snd_pcm
lrwxrwxrwx 1 root root 0 2010-02-19 15:14 snd_pcm_oss -> ../../snd_pcm_oss
lrwxrwxrwx 1 root root 0 2010-02-19 15:14 snd_rawmidi -> ../../snd_rawmidi
lrwxrwxrwx 1 root root 0 2010-02-19 15:14 snd_seq -> ../../snd_seq
lrwxrwxrwx 1 root root 0 2010-02-19 15:14 snd_seq_device -> ../../snd_seq_device
lrwxrwxrwx 1 root root 0 2010-02-19 15:14 snd_seq_dummy -> ../../snd_seq_dummy
lrwxrwxrwx 1 root root 0 2010-02-19 15:14 snd_seq_midi -> ../../snd_seq_midi
lrwxrwxrwx 1 root root 0 2010-02-19 15:14 snd_seq_oss -> ../../snd_seq_oss
lrwxrwxrwx 1 root root 0 2010-02-19 15:14 snd_timer -> ../../snd_timer

```

it was wanting me to default intel8x0 index=0 and 
pcsp index=1 

since i didnt even see pcsp listed i am assuming i dont have to worry 
about indexing it to 1
  right?

---

### Post by papahonk on 2010-02-19
```
 lsmod|grep '^snd' | column -t
snd_intel8x0            30104   2
snd_ac97_codec      101536  1   snd_intel8x0
snd_pcm_oss           37472   0
snd_mixer_oss         16220   1   snd_pcm_oss
snd_pcm                 76480   3   snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy       2752    0
snd_seq_oss           29216   0
snd_seq_midi           6656    0
snd_rawmidi            22336   1   snd_seq_midi
snd_seq_midi_event  7036    2   snd_seq_oss,snd_seq_midi
snd_seq                  50896   6   snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer               21540   2   snd_pcm,snd_seq
snd_seq_device        7208    5   snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                        61188   16  snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc      9124    2   snd_intel8x0,snd_pcm

```

now this is a little different then what they list. with this im over my head. does the single digit  say what order it is indexed in ? it also asks for this


```
ls -l /dev/snd
total 0
drwxr-xr-x  2 root root       60 2010-02-19 08:01 by-path
crw-rw----+ 1 root audio 116,  0 2010-02-19 08:01 controlC0
crw-rw----+ 1 root audio 116, 24 2010-02-19 08:01 pcmC0D0c
crw-rw----+ 1 root audio 116, 16 2010-02-19 08:11 pcmC0D0p
crw-rw----+ 1 root audio 116, 25 2010-02-19 08:01 pcmC0D1c
crw-rw----+ 1 root audio 116, 18 2010-02-19 08:01 pcmC0D2p
crw-rw----+ 1 root audio 116,  1 2010-02-19 08:01 seq
crw-rw----+ 1 root audio 116, 33 2010-02-19 08:01 timer

```

it says that "If you have at least the devices **controlC0** and **pcmC0D0p** or similar, then your sound modules have been detected and loaded properly."

and i do. I'm  not sure about the first line though its not like what they show in their example

---

### Post by papahonk on 2010-02-19
now im just grasping as i cant seem to go any further i did unmute things and turned them up  but i cant remember  how to log on to root  to do this. 

```
honaker@honaker-desktop:~$ alsamixer
honaker@honaker-desktop:~$ # amixer set Master 90% unmute
honaker@honaker-desktop:~$ # amixer set PCM 85% unmute
honaker@honaker-desktop:~$ # aplay /usr/share/sounds/alsa/Front_Center.wav
honaker@honaker-desktop:~$ 
honaker@honaker-desktop:~$ alsamixer
honaker@honaker-desktop:~$ # alsaconf
honaker@honaker-desktop:~$ 
honaker@honaker-desktop:~$ alsaconf
You must be root to use this script.
honaker@honaker-desktop:~$ # gpassword -a honaker audio
honaker@honaker-desktop:~$ # gpassword -a honaker audio
honaker@honaker-desktop:~$ # gpassword -a mike audio
honaker@honaker-desktop:~$ # alsactl store
honaker@honaker-desktop:~$ alsactl store
alsactl: save_state:1530: Cannot open /etc/asound.state for writing: Permission denied
honaker@honaker-desktop:~$ 

```

so know im going to go take a nap and hope it makes more since when i get up

---

### Post by nikhilbhardwaj on 2010-02-20
try sudo alsactl store
for the permission error

open a root shell with sudo -s
and then try all of the following commands

amixer set Master 90% unmute
amixer set PCM 85% unmute
aplay /usr/share/sounds/alsa/Front_Center.wav
do you hear a sound after that

ideally you should get something like

Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono

---

### Post by papahonk on 2010-02-21
loaded xp back on and still no sound   know speakers are ok, ordered new sound card  we will see  what happens once i get it in, thanks for all the help

---

