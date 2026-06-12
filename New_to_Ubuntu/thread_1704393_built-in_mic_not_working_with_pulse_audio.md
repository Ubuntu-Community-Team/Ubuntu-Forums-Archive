---
title: "built-in mic not working with pulse audio"
date: 2011-03-10
forum: New to Ubuntu
---

### Post by bnjmnwroberts on 2011-03-10
So the built-in mic on my e-machines m-250 ( same as acer aspire one netbook)is not recognized by pulse. I can record on sound recorder, but I absolutely cannot get it to work on g-mail voice and video. I have the alsa mixer, and everything else, and I have set it up numerous times so that it should work but all i get is static from my speakers. When I boot the system up, ( which is ubuntu10.10 maverick meerkat only)it says pulse config. per user session, sane disabled. Anyone out there have a frickin' clue? I don't. I'd appreciate any help I can get on this issue. Thanks.
P.S. My video works fine.

---

### Post by Wobblybob on 2011-03-13
I got my mic working on my lappy [sony] using this which I found on the forum somewhere it may work 4 you!

In a Terminal

sudo gedit /etc/modprobe.d/alsa-base.conf

add this line at the end of the file;

options snd-hda-intel model = auto

and re save

---

