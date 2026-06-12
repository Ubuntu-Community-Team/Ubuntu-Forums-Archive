---
title: "no sound in Java"
date: 2010-08-23
forum: New to Ubuntu
---

### Post by Zenmij on 2010-08-23
I am trying to listen to this web-based shortwave radio receiver here:
websdr.ewi.utwente.nl:8901/

but am unable to get any sound. The pavucontrol applet does not show any playback (unlike as usual in Firefox).


Any ideas?

---

### Post by kaldor on 2010-08-24
I have sound problems when using IcedTea/OpenJDK. If I were you, I'd install the real Java.

In the Software Centre, install sun-java6-plugin and sun-java6-jdk (though the latter may not be needed) and you should be good to go.

---

### Post by kaldor on 2010-08-24
Weird, can't edit my post.

I wanted to say that my audio works fine on the link you gave.

---

### Post by Zenmij on 2010-08-25
Thanks for the response but still no sound even with both of those packages. Very odd and disappointing!

UPDATE: I read somewhere that sound won't intialise in Java if a pulseaudio app is open, well it got me thinking - I only had the vol control open - (I usually always have it open) - closed it, and I finally get sound in the link..

---

### Post by jebradley on 2011-02-25
I just found the following link:
[http://www.dh1tw.de/websdr-java-ubuntu-linux-how-to-make-it-work](http://www.dh1tw.de/websdr-java-ubuntu-linux-how-to-make-it-work)
that helped me solve the problem. Over the past few months, I've jumped through a lot of hoops with no success, and I thought something else might have shown up since my last attempt. This article solved the problem for me. 

Good luck! (Sorry that websdr.ewi.utwente.nl:8901/ is currently off the air, but [www.w4mq.com](www.w4mq.com) has a similar sdr setup).

---

