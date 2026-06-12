---
title: "Flash no longer works after &quot;recommended&quot; updates"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by rutherforddigsby on 2009-12-15
Hi, I'm running ubuntu 9.10. Last night i installed all the "recommended" updates. Everything installed quickly and all was seemingly well. After reboot i noticed the my display appeared smaller (fonts, icons, everything in general). I tried changing the display settings within the GUI, no luck, no big deal. Then I tried to watch a video on hulu. I got the "install flash" message. I installed it > nothing. I completely removed it then installed through synaptic several times, still no luck. If anyone has had similar issues with updates wiping out flash please help. thanks

---

### Post by pieman711 on 2009-12-16
I had something very similar with 8.10. After installing a recommended flash update it no longer works and it says I have to install it. everything else appears fine though.

---

### Post by laidback on 2009-12-16
Check whether you have :-

swfdec-mozilla 
or
Gnash...

installed. If so remove them (synaptic), it might help.

---

### Post by pieman711 on 2009-12-16
I started a thread about a week ago that got plenty of suggestions ([http://ubuntuforums.org/showthread.php?t=1351156](http://ubuntuforums.org/showthread.php?t=1351156)) unfortunatly when I posted it i was having some trouble with a very poor wifi signal and hadn't realised it actually posted (i've only just seen the thread and replies there!)

I'll give it a go next time I get a chance and let you know if any of them work.

---

### Post by philinux on 2009-12-16
> **rutherforddigsby said:**
> Hi, I'm running ubuntu 9.10. Last night i installed all the "recommended" updates. Everything installed quickly and all was seemingly well. After reboot i noticed the my display appeared smaller (fonts, icons, everything in general). I tried changing the display settings within the GUI, no luck, no big deal. Then I tried to watch a video on hulu. I got the "install flash" message. I installed it > nothing. I completely removed it then installed through synaptic several times, still no luck. If anyone has had similar issues with updates wiping out flash please help. thanks

Two commands and then report back.

```
sudo updatedb

no output from that it updates its locate database.

locate libflashplayer.so


```

---

