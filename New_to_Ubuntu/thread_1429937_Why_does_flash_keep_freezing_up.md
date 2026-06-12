---
title: "Why does flash keep freezing up?"
date: 2010-03-14
forum: New to Ubuntu
---

### Post by TurnOfTide on 2010-03-14
For some reason both streaming videos AND games will freeze up and become unresponsive. This isn't a network latency issue as this never happened on the same machine with Windows Xp/windows 7. Infact it almost goes beyond just flash as it just happened right now while I was typing this. It occurs for 1-3 seconds.

---

### Post by NightwishFan on 2010-03-14
Flash is not exactly coded well on Linux. Are you using 64-bit? Also how did you install the flash plugin, and what graphics card do you have?

---

### Post by TurnOfTide on 2010-03-15
32 bit.... I have a 64bit processor but it wouldn't install ubuntu 64bit... I did run windows 7 64bit though.

My gfx card is Nvidia 8800 GTX I believe...., the GTX part I am not 100% sure about. it is pretty decent card.

I must have installed flash when I was automatically prompted/when I first used firefox and went to youtube....

TBH, all of firefox seems slower compared to my windows experience... as I'm no windows right now.

---

### Post by NightwishFan on 2010-03-15
It is possible Firefox is slower, but unlikely. Check if flash is installed in Synaptic Package Manager. The package is flashplugin-nonfree. If it is not installed there, remove it from Firefox and install that package. Please note that flash is coded much better on Windows (it is not open source so we cant help that) than it is on Linux.

The only tip I can think of is to turn off 3d desktop effects while watching flash. That tends to help some people.

64-bit Ubuntu has no downsides to 32-bit Ubuntu, so feel free to use it if you want.

---

### Post by QIII on 2010-03-15
There is a common misconception that the open source community somehow has any influence on how Flash performs on Linux.

Flash is proprietary.  It is produced by Adobe, not by anyone in the Linux community.

Its performance on Linux is abysmal because the Linux version does not work well.

There is a Linux team at Adobe working on it.  I am sure they are diligent and working as hard and honestly as they can.  I am also sure that they have limited resources.

Consider this:  Place yourself in Adobe's position.  Would it make better sense for you to expend most of your effort and resources on a more common platform with a vastly larger user base, or to expend a lot of effort and resources on a relatively small user base?

Adobe is going where the money is.  That is what businesses do.

---

### Post by TurnOfTide on 2010-03-15
Well I'm not critizing anyone, I just want flash to be operable.....


So I have adobe-flashplugin installed and not the flashplugin-nonfree  ...


SO, should I get the flashplugin-nonfree ?

---

### Post by QIII on 2010-03-15
I am surprised that a 64 bit Ubuntu distribution will not run on 64 bit machine architecture...

Anyway.

Try the other option.  It's worth a try.  Generally, I'd stick with what is in the repos unless you know what you are doing.  (I use the 64 bit Beta from Adobe.)

But what I am saying is that no matter which option you choose, you may not get the smooth results you get in Windows.  The driving factor here is Flash itself.

Make sure swfdec and gnash (Flash alternatives that don't work very well) are disabled in any case.  They conflict with Flash.

---

### Post by NightwishFan on 2010-03-15
I think one links to the other, but flashplugin-nonfree or flashplugin-installer is the correct one.

---

