---
title: "sound not working on sony vaio VPCEB16FG"
date: 2010-09-20
forum: New to Ubuntu
---

### Post by bhavya juneja on 2010-09-20
Hi all,
It's a weird problem I have. 
First of all, I installed ubuntu and had no sound at all, so I googled a  lot and found that my alsa driver need to be upgraded from 1.0.21 to  1.0.23. So I did that and sound was there. Later I found that my sound  works only on either music player(including rhythmbox, banshee, vlc  etc.) or flash player(mainly youtube). 
Now, when I reboot I can choose any one of them to have sound. If I  first start youtube then rhythmbox will not even play music(vlc shows  video but no sound) and if I choose any player than youtube will show  only video with no sound.

I found a [[COLOR=Navy]link[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/183917") which says it's kind of bug. But I could not resolve anything from it

---

### Post by lbrty on 2010-09-20
Did you install all the necessary codecs in the Software Center (this is for VLC media player, Rhythmbox, etc)? If you do not install the codecs for certain files, they will not play properly.

---

### Post by bhavya juneja on 2010-09-21
Thanks for replying, and yes I have but I don't think that is the problem. The link I got says that some people having the same problem corrected it by installing libflashsuppport which is not available now. And hence I don't know what to do, but probably the problem is with flash player..

---

### Post by lkjoel on 2010-09-24
> **bhavya juneja said:**
> Thanks for replying, and yes I have but I don't think that is the problem. The link I got says that some people having the same problem corrected it by installing libflashsuppport which is not available now. And hence I don't know what to do, but probably the problem is with flash player..
Try Fix your sound! in my signature.
Then use Post-Fix your sound! in my signature.

---

### Post by bhavya juneja on 2010-09-27
I am sorry but I actually didn't understand what your link is doing. Is it replacing PulseAudio with OSS?? 

If yes, what difference is there in between both of them??

---

### Post by Rbiswas5888 on 2011-02-06
Try to install driver from Synaptic Package Manager for advance driver Installation :lolflag::lolflag:
:KS:KS ITS WORK FOR ME :KS:KS

---

### Post by lkjoel on 2011-02-06
> **bhavya juneja said:**
> I am sorry but I actually didn't understand what your link is doing. Is it replacing PulseAudio with OSS?? 

If yes, what difference is there in between both of them??

It does replace PulseAudio with OSS.
The difference is that OSS was created before PulseAudio and ALSA.
PulseAudio is in beta, while OSS is stable.

---

### Post by Rbiswas5888 on 2011-02-07
Synaptic Package Manager there is lot of alsa driver just  install it it works for me without any prob. :lolflag::lolflag::lolflag::lolflag:

---

### Post by Niels_D on 2011-02-07
Check the primary selected sound device.
With my VAIO VPC-E it was set to HDMI. :lolflag:

---

