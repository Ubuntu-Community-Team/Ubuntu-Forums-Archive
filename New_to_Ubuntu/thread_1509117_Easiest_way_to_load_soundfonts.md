---
title: "Easiest way to load soundfonts?"
date: 2010-06-13
forum: New to Ubuntu
---

### Post by kultrva on 2010-06-13
Hi. I am somewhat new to Ubuntu (I'm running 10.04), and so far I prefer it over Windows 7. However, there is one issue that I am having trouble with.

In Windows, I use Guitar Pro 5 all the time. I found TuxGuitar and it looks good enough. Unfortunately, the MIDI sounds that I currently have are atrocious. I downloaded the FluidSynth soundfont, but loading it has been impossible for me so far.

I have tried working with Qsynth and Jack with no luck. Jack always comes up with Xruns and crashes. I have looked through many tutorials and nothing is working.

Basically, all I want to do is use TuxGuitar with decent soundfonts. If anybody could tell me the easiest way to do this I would be very grateful.

Thanks.

---

### Post by gorgon on 2010-06-14
Hi,

you should use the real-time kernel if Jack is giving xruns.
sudo apt-get install linux-rt

If you still get problems with xruns after this, try to increase the 'frames/periods' in Jacks setup.

Dont know about soundfonts at all. good luck!

---

