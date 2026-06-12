---
title: "Choppy Totem/VLC playback"
date: 2009-09-18
forum: New to Ubuntu
---

### Post by oohbuntoo on 2009-09-18
I am wondering if there is a way to get smooth video playback through VLC or Totem?  My playback is a lil' choppy for saved video files and DVDs.  Audio files play great.  Are there any special codecs or plugins I'm missing?  I've watched a couple of clips on YouTube of Jaunty systems with video playback that looks smoother than mine.

---

### Post by NoaHall on 2009-09-18
Is your graphics card installed? 

System -> Admin -> Hardware drivers

Is your system 32 bit or 64 bit?

---

### Post by Perfect Storm on 2009-09-18
Install **libdvdcss2**

Check medibuntu repository for that task; [http://www.medibuntu.org/](http://www.medibuntu.org/)

---

### Post by oohbuntoo on 2009-09-18
@NoaHall:  AMD 64, hardware drivers installed.

---

### Post by NoaHall on 2009-09-18
The problem is just in VLC/Totem?
What's your system specs?
also, do what AI suggested, and see if anything's better.

---

### Post by oohbuntoo on 2009-09-18
@NoaHall: MPlayer, VLC, and Totem are all a lil' choppy.  YouTube, Hulu, Dailymotion, etc, all playback fine in Chromium.

Toshiba Satellite L335D-S7901 
AMD Turion X2 Dual Core 64
3GB SDRAM
250GB HDD
Jaunty Jackalope 9.04

Working on AI's advice...

---

### Post by oohbuntoo on 2009-09-18
@NoaHall: MPlayer, VLC, and Totem are all a lil' choppy.  YouTube, Hulu, Dailymotion, etc, all playback fine in Chromium.

Toshiba Satellite L335D-S7901 
AMD Turion X2 Dual Core 64
3GB SDRAM
250GB HDD
Jaunty Jackalope 9.04

Working on AI's advice...

---

### Post by NoaHall on 2009-09-18
Well, your system should be running it fine... Is compiz disabled/effects off?

---

### Post by Cresho on 2009-09-18
I have problems with jaunty myself.  I went back to hardy heron.  Karmic koala works fine.

I would wait for karmic koala.

The reason I have issues with jaunty is because of full video playback on flash and slowdowns on 3d games.

I have a 8800gtx
6400 black edition cpu dual core
4gb ram.  64bit.  32bit as well

its the os itself that causes problems on some hardware.  Its probably my nvidia chipsets on my motherboard.

Karmic koala is excellent and better than jaunty or hardy on my current setup

I recommend you wait for karmic and avoid this issue since it could be hardware/driver related.  Other than that, softwares work good.


TRY SMPLAYER  #sudo apt-get install smplayer

in the video property use opengl.  it could help but i doubt.  this setup works excellent in hardy heron.  I run that in kubuntu karmic koala and its fine.  Jaunty....sucks on my system


One major reason why i dont use karmic koala beta, just for you guys info, is I have this stupid application that runs 100% all the time and makes my cpu hot!  its funny though i can do everything else fine.  It's in beta and im sure they will get this resolved.

---

### Post by philinux on 2009-09-18
> **Cresho said:**
> I have problems with jaunty myself.  I went back to hardy heron.  Karmic koala works fine.

I would wait for karmic koala.

The reason I have issues with jaunty is because of full video playback on flash and slowdowns on 3d games.

I have a 8800gtx
6400 black edition cpu dual core
4gb ram.  64bit.  32bit as well

its the os itself that causes problems on some hardware.  Its probably my nvidia chipsets on my motherboard.

Karmic koala is excellent and better than jaunty or hardy on my current setup

I recommend you wait for karmic and avoid this issue since it could be hardware/driver related.  Other than that, softwares work good.


TRY SMPLAYER  #sudo apt-get install smplayer

in the video property use opengl.  it could help but i doubt.  this setup works excellent in hardy heron.  I run that in kubuntu karmic koala and its fine.  Jaunty....sucks on my system


One major reason why i dont use karmic koala beta, just for you guys info, is I have this stupid application that runs 100% all the time and makes my cpu hot!  its funny though i can do everything else fine.  It's in beta and im sure they will get this resolved.

Still alpha and very buggy as expected.
[http://ubuntuforums.org/showthread.php?t=1133054](http://ubuntuforums.org/showthread.php?t=1133054)

---

### Post by shae on 2009-09-19
What type of video card do you have?

---

### Post by oohbuntoo on 2009-09-19
@NoaHall:  Compiz is running.

---

### Post by NoaHall on 2009-09-19
Try turning compiz off, and see if anything is better.

---

### Post by oohbuntoo on 2009-09-19
@NoaHall:  How do you turn Compiz off?

---

### Post by oohbuntoo on 2009-09-19
@shae: Where do I go to find that out??

---

### Post by NoaHall on 2009-09-19
System -> Preferences -> Appearance -> Visual Effects -> None

---

### Post by oohbuntoo on 2009-09-19
I turned Compiz off.  Playback in VLC is very smooth now.  Unfortunately the lower half of my screen is now black and the only thing I can see in this new black area is my GnomeDo Docky.  What just happened??  Also, is there a way I can have smooth playback and run Compiz simultaneously???

---

### Post by shae on 2009-09-19
At the top of:
```
glxinfo
```

---

### Post by Cresho on 2009-09-19
ya you can have both compiz fusion and a video player running at the same time.  It depends on hardware.  I use smplayer with opengl video acceleration and run compiz in hardy heron.

---

