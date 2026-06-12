---
title: "6 channel surround sound"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by Jakey_TheSnake on 2009-04-14
Is a problem for me, so unfortunately, I've been reduced to asking for help. 

```
jake@jake-desktop:~$ lspci -v | grep audio
00:05.0 Multimedia audio controller: nVidia Corporation nForce Audio Processing Unit (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)

``` 

I believe that would be helpful. However, I don't know what my *exact* nForce chipset model name is, if someone could tell me how to find out I'd be very appreciative. 

6 channel worked on XP ages ago when I had it installed, now when I change my preferences to 6ch I only get sound out of the front two, no matter the "surround jack mode". 

This has been bugging me for quite a while now, help would be appreciated. 

Thanks, 

Jake

---

### Post by Jakey_TheSnake on 2009-04-14
bump.

---

### Post by fooman on 2009-04-14
i was able to get sound to all 6 (5.1) of my speakers by following this guide:

[http://ubuntuforums.org/showthread.php?t=795525](http://ubuntuforums.org/showthread.php?t=795525)

thankfully, i did not have to go any further than "the easy way".  :p

of course,  i did still have to play around with the alsamixer a bit to get it right....surround jack mode, channel mode, etc.  try a few different combinations to try and get all the speakers working.

hope that helps.

---

### Post by chrisinspace on 2009-04-28
I don't know if you're still looking for an answer to this, but I followed this guide:

[http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy]("http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy")

---

