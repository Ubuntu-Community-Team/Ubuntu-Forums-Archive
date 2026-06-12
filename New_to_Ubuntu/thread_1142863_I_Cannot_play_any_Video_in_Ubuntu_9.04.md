---
title: "I Cannot play any Video in Ubuntu 9.04"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by luckydeveloper on 2009-04-29
Hi,

I cannot play any video file in ubuntu 9.04. **I have installed all the gstreamer plugins for all video formats**... I have tried in **VLC, MPLAYER and totem.**

When i right click a video file and click 'play'... the software (vlc,totem and mplayer) just opens and closes immediately. this happens when i load the video file from the software (FILE->Open ) also.. 

what should i do now... Please help. :confused:

---

### Post by Paqman on 2009-04-29
Is it just one video file, or all of them? Try and play a video from your Examples folder (inside your Home folder)

---

### Post by luckydeveloper on 2009-04-29
ya.. even those examples are causing the same problem

---

### Post by Paqman on 2009-04-30
What codecs did you install and how did you install them? Have you tried uninstalling everything you installed and starting from scratch?

---

### Post by nhasian on 2009-04-30
I dont think its a codec problem.  VLC has all the codecs built in and luckydeveloper said that VLC didnt work either.

luckydeveloper, can you run vlc from a terminal so you can see any error messages as they are outputted?  I'm thinking your having trouble reading the file for some reason.  Have you tried playing a video file from a thumbdrive?

---

### Post by paranoidandroidz on 2009-04-30
I am also having this problem 

Any video file I open, doesnt matter what format all open then close within a couple of seconds, I ve tried 3 or 4 different players all the same result. The same video files run perfect off a different system.

---

### Post by paranoidandroidz on 2009-04-30
Im getting a bad allocation error

[????????] x11 video output error: X11 request 132.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  132 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  81
  Current serial number in output stream:  82
Segmentation fault


if i run: 
vlc --vout x11 /home/d/thesimpsons.avi

Most videos run fine, a couple cut out after 4 seconds. Anyone offer any ideas to fix this?

---

### Post by paranoidandroidz on 2009-04-30
Well I have a temp fix

I opened VLC Player

Tools>Preferences>Video>

and Changed Output to X11 video output

---

### Post by &#1575;&#1604;&#1586;&#1575;&#1607;&#1585; &#1575;&#1604;&#1602;&#1604;&#1605;&#1608;&#1606;&#1610; on 2009-04-30
i have the same problem
it's a divers issue
it's Ubuntu 9.04 not supporting intel integrated graphics yet (at least thats the case for me)

i was able to play videos using Mplayer for windows inside wine but that was not a good experience ... to slow ... but they play at least :) 


just waiting to the drivers to get updated !!! :popcorn:

---

### Post by luckydeveloper on 2009-04-30
i have switched to 8.04 temporarily unitl 9.04 starts working in intel based chips correctly and until all the bugs are fixed in it...

In 8.04 i have no such headaches.. thank god :-)

---

### Post by levicivita on 2009-05-02
> **paranoidandroidz said:**
> Well I have a temp fix

I opened VLC Player

Tools>Preferences>Video>

and Changed Output to X11 video output

I have Ubuntu 9.04 and my video card is an ATI 4890, and I use the fglrx driver.  Whenever I'd enable Compiz, I couldn't play videos full screen with any movie player.  I had to disable special effects, but then the interface looked bare and ugly.  However thanks to your advice above all the problems have been fixed!

---

