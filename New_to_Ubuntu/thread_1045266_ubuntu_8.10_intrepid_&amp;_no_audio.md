---
title: "ubuntu 8.10 intrepid &amp; no audio"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by Geemonster on 2009-01-20
I got 8.10 intrepid as part of a dual boot at Xmas.
I've been plagued by the lack of audio for skype,and now VLC which has it's own codec pack.
   Im thinking to myself,was it worth the disc space it takes up?
We're not all geeks,ubuntu is far from user friendly,for the newbie.
   I'd stick with Windows newbies,im close to reformatting this whole HD for Windows.

---

### Post by meindian523 on 2009-01-20
Do you need help or have you made up your mind?If you need help,putting in statements like > Im thinking to myself,was it worth the disc space it takes up?
We're not all geeks,ubuntu is far from user friendly,for the newbie.
   I'd stick with Windows newbies,im close to reformatting this whole HD for Windows. is not going to help.If you've made up your mind,then it was a waste of your  time just posting this thread.

---

### Post by Geemonster on 2009-01-20
Im just really annoyed and don't know if i can be helped,i've been trying to get Skype audio for over 2 weeks on and off.
   Now i've lost my VLC audio,and have to keep force closing it.
Im not impressed.

---

### Post by linux_tech on 2009-01-20
Skype requires snd-pcm-oss and snd-mixer-oss
In terminal type:
```
lsmod
``` (you can look for them in the list)
If you don't have these modules, you can load them. Type 
```
sudo modprobe snd-pcm-oss
sudo modprobe snd-mixer-oss

```

---

### Post by Geemonster on 2009-01-20
Thanx for your input!
I'll give it a try. :)

---

### Post by Geemonster on 2009-01-20
No go!
I've had enough.

---

### Post by linux_tech on 2009-01-20
skype and pulse audio  do not get along-
see if this helps
In terminal- temporarily, stop pulseaudio
```
killall pulseaudio
```
then test skype

---

### Post by kansasnoob on 2009-01-20
There's a fair chance that this would get you straightened out:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

But nothing I know of will solve impatience.

---

### Post by linux_tech on 2009-01-20
You should also install esound-
```
sudo apt-get install esound
```

Usually pulseaudio also needs to be removed, see these articles:
[http://townx.org/blog/elliot/skype-ubuntu-intrepid-ibex-8-10](http://townx.org/blog/elliot/skype-ubuntu-intrepid-ibex-8-10)
[http://anojrs.blogspot.com/2008/12/ubuntu-810-resolving-skype-sound-issues.html](http://anojrs.blogspot.com/2008/12/ubuntu-810-resolving-skype-sound-issues.html)
[http://www.econowics.com/news-from-the-net/170/skype-problem-with-audio-playback-ubuntu-810-intrepid-ibex/](http://www.econowics.com/news-from-the-net/170/skype-problem-with-audio-playback-ubuntu-810-intrepid-ibex/)

---

### Post by floatingpoint on 2009-01-20
I'd just like to sat that I installed 8.10 over Windows about 3 weeks ago, without a Windows partition for back up, and didn't have any problems with audio. Or anything else. Any trouble I've encountered, I've done a bit of googling and a bunch of searching these forums, and it's worked like a charm every time. So far I've found Ubuntu/Linux to be much more functional and helpful than Windows (for one thing, this forum is 999999999999x better than any Microsoft troubleshooter) and I have very little real knowledge about computers. 

So please don't try and put new users off just because your personal experience hasn't been perfect.

---

### Post by meindian523 on 2009-01-21
Please don't reward bad behaviour.

[http://ubuntuforums.org/showthread.php?t=634322](http://ubuntuforums.org/showthread.php?t=634322)

---

