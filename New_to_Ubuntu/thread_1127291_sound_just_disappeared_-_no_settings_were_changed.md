---
title: "sound just disappeared - no settings were changed"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by LTFC2020 on 2009-04-16
hi
I tried to listen to a youtube video but no sound
between now and last time I used my speakers all I have done is mount/ unmount a flash drive and plug in a new mouse - I cannot think why either of these actions would have an effect on the sound
any ideas?

---

### Post by DeonS on 2009-04-16
Hi LTFC,

could you please try running the following command in your terminal to see if it fixes the your problem

```
alsa force-reload
```

A message box will appear that says "Volume Control" has quit unexpectedly,
please click the reload button and your sound should be working again.

Regards

Deon

---

### Post by LTFC2020 on 2009-04-16
ok thanks I tried that but no luck, this is what the terminal output:


richard@richard-laptop:~$ alsa force-reload
Terminating processes: 6582 6836.
mkdir: cannot create directory `/var/run/alsa': Permission denied
/sbin/alsa: Warning: Failed to create /var/run/alsa/. 
/sbin/alsa: Warning: Not keeping list of removed modules because /var/run/alsa is absent.
It will not be possible automatically to reload these modules. 
Unloading ALSA sound driver modules:/sbin/alsa: 219: cannot create /var/run/alsa/modules-removed: Directory nonexistent
 snd-atiixp-modem snd-via82xx-modem snd-intel8x0m snd-intel8x0 snd-ac97-codec snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
mkdir: cannot create directory `/var/run/alsa': Permission denied
Loading ALSA sound driver modules: (none to reload).
richard@richard-laptop:~$

---

### Post by DeonS on 2009-04-16
Has your sound stopped working completely or only with youtube videos?
Have you checked to see if maybe by accident your volume was muted?
If you restart your laptop, does the problem return?

---

### Post by LTFC2020 on 2009-04-16
hi
i checked the:
alsa mixer volume control settings for mute etc
tried my secondary browser (epiphany)
tried playing a tune through rhythem box in case it was an online issue
I also tried a restart
so I`m a bit stumped really
any ideas?

---

### Post by LTFC2020 on 2009-04-16
hi
I booted my xp partition and the problem was the same there too
must be hardware related and not ubuntu
think the sound card has gone maybe - this is an old computer
thanks for your help anyway

---

### Post by ramsesdm on 2009-10-03
hi, i had the same problem and it worked for me, thanks


> **DeonS said:**
> Hi LTFC,

could you please try running the following command in your terminal to see if it fixes the your problem

```
alsa force-reload
```

A message box will appear that says "Volume Control" has quit unexpectedly,
please click the reload button and your sound should be working again.

Regards

Deon

---

