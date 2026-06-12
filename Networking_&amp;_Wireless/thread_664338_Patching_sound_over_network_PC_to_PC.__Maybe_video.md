---
title: "Patching sound over network PC to PC.  Maybe video too.  Is it possible?"
date: 2008-01-11
forum: Networking &amp; Wireless
---

### Post by Mysticle31 on 2008-01-11
I bought my dad a laptop for chirstmas and it's running Ubuntu.

He uses it in the living room while watching TV and eating and what not.  

He has a TV and a Stereo system in the living room.

I recently got a good idea.  I have an old Dell laptop that is about 800mhz, maybe even a ghz.  It has TV out and a soundcard.

I would like to patch audio from my dad's new laptop to my old dell and hook my old dell up to his sound system.  That way system sounds, online videos, movies, songs..whatever will play over the wireless though the Dell and to his sound system.

Is something like this possible?

How about video?  It would be cool if I could bring in movies from my hard disk and plug it either into the dell or his laptop and not even worry about DVDs (I rip all the movies I buy to keep them all in one portable place).

---

### Post by HermanAB on 2008-01-11
Yes, with tools like edna, netcat, sox, vlc and nfs.

1. A music server:
[http://aeronetworks.ca/ogg2mp3-howto.html](http://aeronetworks.ca/ogg2mp3-howto.html)

2. Piping music around the house:

Your PC: 192.168.1.100
nc -l -p 55555 | sox -t wav - -t ossdsp /dev/audio

Dads PC: 192.168.1.101
nc 192.168.1.100 55555 < britney.wav

TIMTOWTDI

Cheers,

Herman

---

