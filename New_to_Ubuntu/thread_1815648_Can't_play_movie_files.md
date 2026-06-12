---
title: "Can't play movie files"
date: 2011-07-31
forum: New to Ubuntu
---

### Post by Fillet on 2011-07-31
Hi
Brand new to this so know nothing. If i play a video file with VLC, Banshee, Movie Player, etc. and try to adjust anything on the screen from volume to switching to full screen everything just goes mad, a screen comes up loading something and then takes me back to the login screen. Would love to be able to watch my movies in full screen so if you know of anything that might help shoot...
Thanks

---

### Post by Rex Bouwense on 2011-07-31
We would love to help you if you provided us with a bit more information.
What version are you using?
What have you got under the hood of your machine?
Is this the only problem that you have had so far?
The more information that you provide the people on the forums the easier it becomes to diagnose and hopefully solve your problem.

By the way welcome to the forums.  Enjoy.

---

### Post by Fillet on 2011-07-31
i've got a Fujitsu Siemens Li1705.
Intel Core Due CPU T2450@2GHz, 1Gb RAM. I'm runnig Ubuntu 11.04 on a 13Gb partition, dual boot with windows 7, but have hardly used any of the memory on that partition. Not sure if that helps...let me know if there is anything else you specifically want to know...

---

### Post by CatKiller on 2011-07-31
> **Fillet said:**
> a screen comes up loading something and then takes me back to the login screen. 

> **Fillet said:**
> i've got a Fujitsu Siemens Li1705.

Sounds like an X server crash. I don't think there's a great deal of information about Via graphics out there. It might be possible to turn off hardware acceleration of video output.

That's all I've got, I'm afraid :(

---

### Post by Fillet on 2011-08-01
Thanks, i played around trying to figure out how to do that, but no luck...could you please step me through it?

---

### Post by huntt on 2011-08-01
Try to install some other softwares like VLC to play the movies and will definitely play.

---

### Post by Fillet on 2011-08-01
I do have VLC...it plays the file, but if i try to do anything like switch to fullscreen or just change the volume the whole system fails and goes back to the login screen. It did the same thing with all the media players i tried and i tried playing a variety of different formats and files, so i dont think its the player...might be a driver problem?? dont think its my graphics card because i can play movies without any problems with windows...

---

### Post by CatKiller on 2011-08-01
> **Fillet said:**
> Thanks, i played around trying to figure out how to do that, but no luck...could you please step me through it?

I can try :)

In VLC, select Tools -> Preferences -> Video. Uncheck Accelerated video output (Overlay). If that doesn't work, it's possible that changing the Output method (on the same screen) will help.

You'll probably need to restart VLC for the settings to take effect.

---

### Post by Jouke S on 2011-08-01
Have you installed video codec packages? 
type 'sudo apt-get install ubuntu-restricted-extras' in a Terminal

it sounds like a driver issue though :\

---

### Post by Vaphell on 2011-08-01
long story short fs amilo 1705 is crap. I had the dubious honor to fight it for almost 2 years. I've seen it working well only once with some beta drivers installed on a specific kernel version of 8.04. Maybe something has changed and via started to support linux as they promised long time ago, but somehow i doubt :)

---

### Post by Fillet on 2011-08-02
i've installed the codecs and whatever drivers and add-ons i could find. if i open vlc and switch to fullscreen and then open a video it plays in fullscreen, but still when i do something like click on the screen the same thing happens...i guess its some compatability thing with the driver...so i'm screwed then?

---

### Post by qyot27 on 2011-08-02
This sounds vaguely like something that was happening to me yesterday with UMPlayer (although I wasn't trying to run it fullscreen).  At a certain point during playback, the screen would freak out and drop me back to GDM.  And yes, the chipset was also VIA (the motherboard is an MS-7312).

Try switching the video and audio renderers.  The defaults might be xv (for video) and alsa (for audio).  If I recall correctly, I was able to eliminate the issue by switching video to gl2 and audio to pulse.  VLC should have similar options.

---

### Post by Fillet on 2011-08-04
@ catkiller. You are a legend. Thanks, just got around to your suggestion and it works 100%. 

Thanks for everyones help.

Cheers

---

