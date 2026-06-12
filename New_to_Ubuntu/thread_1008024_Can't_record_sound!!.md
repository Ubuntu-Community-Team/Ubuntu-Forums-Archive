---
title: "Can't record sound!?!?"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by fknyeah on 2008-12-11
Hey all,

I'm using Ubuntu 8.10, happily switched to Ubuntu a couple months ago after putting up with too much for too long from windows machines.  

I was hoping to use Skype to talk with my dad across the country, but my computer no longer seems to record sound.  The video works fine, I guess, (is there any way to make it perform better?).  Before I switched though, the computer recorded sound all by itself, now I can't get it to register a peep or a yell.

I'm running on a Dell Vostro 1500 and will happily provide any other information you may need.

Thanks a Ton!
Sam FK

---

### Post by jamesrl on 2008-12-11
your soundcard is misconfigured.  Can you find out what your sound card is?
Do something like: (ls pci)
```
lspci | grep audio
```
or sudo lshw (and search for audio device yourself in the output).
Then you can have more info on googling how to get your sound card to work properly

---

### Post by ruha on 2008-12-11
have you checked if your microphone is muted? 

terminal > gnome-volume-control.
If you can't see the volume setting for the microphone, go to edit > preferences and mark everything.

---

### Post by nhasian on 2008-12-11
double click on the audio icon in the system tray (next to the date & time)

change the device the Alsa mixer, then click on the Options tab.  You may have more than one Input Source.  For example on my HP laptop I have four different Input Sources.  I have one called Front Mic and another called Mic.  One for the front mic jack and the other for the built in mic in the monitor.  Once you set it to the correct source you should be able to record sound.

---

### Post by fknyeah on 2008-12-11
Thanks so much!

---

