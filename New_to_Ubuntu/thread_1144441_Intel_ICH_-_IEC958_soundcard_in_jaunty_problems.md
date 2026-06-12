---
title: "Intel ICH - IEC958 soundcard in jaunty problems"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by Ragged on 2009-04-30
Hi,
I have an issue with my Intel ICH - IEC958 soundcard. I've tried a few fixes, but to no avail. I have checked the alsamixer and it is unmuted. I would appreciate some help, as I have been poking at this problem for a few hours now. I am running 9.04, but it didn't work in Intrepid either.

---

### Post by spiderbatdad on 2009-04-30
did you try editing the file /etc/modprode.d/alsa-base.conf adding the line 
```
options snd-intel8x0 index=-1

```You will need to reboot and check alsa mixer again for master and pcm

If that doesn't work, perhaps check blacklist.conf and comment out
```
#blacklist snd_intel8x0m
```But then remove the entry made in alsa-base.conf

---

### Post by Ragged on 2009-04-30
sorry if I seem completely unaware, but where would I enter /etc/modprode.d/alsa-base.conf if I enter it directly into the terminal, I get no such file or directory. some help for a complete n00b please

---

### Post by spiderbatdad on 2009-04-30
open a terminal. Applications >> Accessories >> Terminal.
Then enter:
```
gksu gedit /etc/modprobe.d/alsa-base.conf

to edit blacklist:

gksu gedit /etc/modprobe.d/blacklist.conf
```
You will need to save any file you edit by clicking the floppy disk icon near the top of the window of the file you are editing.

commenting out is accomplished by putting a # in front of the option. This causes the line to be ignored.

---

### Post by Ragged on 2009-04-30
that got me to the alsa-base.conf but when I try to save it tells me: could not find 
/etc/modprobe.d/alsa-base.conf

any suggestions?

---

### Post by spiderbatdad on 2009-04-30
so you saw the text file...edited it, and then tried to save, but got that message? It wasn't a blank file when it opened right?

---

### Post by Ragged on 2009-04-30
I edited the blacklist; there was no change

---

### Post by Ragged on 2009-04-30
it was a blank file when it opened

---

### Post by Ragged on 2009-04-30
> **spiderbatdad said:**
> so you saw the text file...edited it, and then tried to save, but got that message? It wasn't a blank file when it opened right?
  it was a blank file when it opened

---

### Post by spiderbatdad on 2009-04-30
Edit:If it was blank, you had a typo.

It sounds like gedit is misbehaving. Try a command line text editor:
```
sudo nano /etc/modprobe.d/alsa-base.conf
```This should open a file full of text. Use arrow key to move to the end of the file and add your line at the end. Hit ctrl+o to save, then enter to confirm, then ctrl+x to exit. Remember you will need to reboot to see any change. If it doesnt work. Go back, comment the line with #, or remove it. Then try editing blacklist.conf and put the # infront of #blacklist snd_intel8x0m

---

### Post by Ragged on 2009-04-30
I think I've performed these actions properly, but I still have no sound. Is there any other reason that would keep the audio from working? the sound card is part of the motherboard, which obviously works, but, perhaps I might have some other hardware issue?

---

### Post by spiderbatdad on 2009-04-30
some more information might be helpful. If you could copy/paste into another post the output of these two commands:
```
aplay -l
lsmod
```I have to go now, but this may help someone else to help you. Will check your progress later.

You might also try running:
```
sudo modprobe snd_intel8x0 
``` then logout and back in.

---

