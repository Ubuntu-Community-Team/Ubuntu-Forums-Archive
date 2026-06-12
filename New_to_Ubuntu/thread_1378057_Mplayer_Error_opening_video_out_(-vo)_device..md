---
title: "Mplayer: Error opening video_out (-vo) device."
date: 2010-01-11
forum: New to Ubuntu
---

### Post by Sugi on 2010-01-11
How do I fix this?  I kept getting this error over two different computers.  Trying to play movie files on mplayer.
Error opening/initializing the selected video_out (-vo) device.

Specs:
Ubuntu 9.10 64 bit
Ubuntu-Restricted-Extras
Mplayer 2:1.0
Avi files


Thanks,
Sugi

---

### Post by falconindy on 2010-01-11
use 'mplayer -vo help' to get a list of valid video output devices. Specify them manually using 'mplayer -vo <device> <file>'.

---

### Post by Sugi on 2010-01-11
Which one would I pick for avis, mkv, and wma?  They don't clearly state it.

mplayer -vo directfb oranges.avi

So like that?  How would I find out which device to pick for my file type?

Thanks,
Sugi

---

### Post by bogdan.veringioiu on 2010-01-11
Hi.

Try:
```
mplayer -vo xv oranges.avi
or
mplayer -vo x11 oranges.avi
```

I think it should work with both.
Cheers
Bogdan

---

### Post by Sugi on 2010-01-11
Thanks both of them work with both file types. :)

Sugi

---

### Post by bogdan.veringioiu on 2010-01-11
You can write down the vo option in the config file of mplayer, so
you avoid writing the full command every time.
You can edit the config file:
gedit $HOME/.mplayer/config

add a line:
vo=xv
and you're done.

Bogdan

---

### Post by gradinaruvasile on 2010-01-11
> **Sugi said:**
> Which one would I pick for avis, mkv, and wma?  They don't clearly state it.

mplayer -vo directfb oranges.avi

So like that?  How would I find out which device to pick for my file type?

Thanks,
Sugi

vo is the video out device. It doesnt deal with codecs. 
Generally -vo xv is the best solution, 
Unless you have nvidia card that supports vdpau hardware decoding and play 1080p movies. In that caes its "-vo vdpau -vc ffh264vdpau" (ffmpeg12vdpau,ffh264vdpau,ffwmv3vdpau,ffvc1vdpau are the valid vc options depending on the encoding).

---

