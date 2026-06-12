---
title: "No sound"
date: 2010-02-28
forum: New to Ubuntu
---

### Post by Joe_Ib on 2010-02-28
Hello everyone just recently I installed Ubuntu 9.04 and upgraded it to 9.10 no problem during that.  I then transfered my music back on to hard drive and checked to see if it worked.  Sounded great install xp in a virtual box and now I have no more sound and cant figure out what has happened.  Nor do i know how to go about figuring out how to fix this problem. any would is appreciated.

---

### Post by dmaxel on 2010-02-28
Hmmm, there are a few things that you could try.

First, make sure that you don't have accidentally muted your speakers in any way.

Second, go to your Sound Preferences and make sure that it lists a device under the Hardware tab (can't do anything if Ubuntu can't find it!)

Finally, if you don't have mute, but Ubuntu detects a sound card, go into your terminal and type in ```
alsamixer
```and make sure that Front and Master Front (where available) aren't set at 0%.

Those are about the only suggestions I can make so far.

---

### Post by fr3ak.m3 on 2010-03-01
Hope these may help

[http://www.khattam.info/2009/09/09/solved-sound-problem-in-ubuntu-9-10-karmic-koala-alpha-4-due-to-pulseaudio/](http://www.khattam.info/2009/09/09/solved-sound-problem-in-ubuntu-9-10-karmic-koala-alpha-4-due-to-pulseaudio/)

[http://freakingtips.com/2009/09/03/ubuntu-karmic-koala-sound/](http://freakingtips.com/2009/09/03/ubuntu-karmic-koala-sound/)

---

### Post by Joe_Ib on 2010-03-01
So I tried both links and checked to see if anything was muted sound card is reconized and there everything seems to be working and there just not the sound the other thing i just noticed is that if i watch a video on youtube or something a 2:45 video is over in under a minute... so i don't even know what it is now.

---

### Post by Pritamsng on 2010-03-01
Check the links this may help you..
 
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) 
 
[http://linuximagination.blogspot.com/2010/03/basic-troubleshooting-steps-for-sound.html](http://linuximagination.blogspot.com/2010/03/basic-troubleshooting-steps-for-sound.html) 
 
[http://linuximagination.blogspot.com/2010/02/how-to-restart-alsa-sound-driver-in.html](http://linuximagination.blogspot.com/2010/02/how-to-restart-alsa-sound-driver-in.html)
 
[http://linuximagination.blogspot.com/2010/02/enabling-microphone-on-ubuntu.html](http://linuximagination.blogspot.com/2010/02/enabling-microphone-on-ubuntu.html)

---

### Post by Joe_Ib on 2010-03-01
Sorry for long reply but when i did alsamixer master was at 0 thanks.

---

### Post by stevek123 on 2010-03-01
I found this thread a whole ago. I nned to follow it every time I update the kernel (GGRRRRR). It a great guide. = Comprehensive Sound Problems Guide. 
I suggest bookmarking it...you'll need it sometime.
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
Good luck

---

