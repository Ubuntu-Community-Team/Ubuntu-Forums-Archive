---
title: "No sound although headphones are working ok"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by a_satari on 2009-05-01
hi. I'm trying to get the sound to work. It works when I plug my head phones in (although too quiet) but my laptop speakers don't come on. I've increased all the volumes to max. from the top left corner. 

I've tried searching the forums and reading a few beginners guides to no avail. I've read through [https://help.ubuntu.com/community/SoundTroubleshooting#Basic%20Troubleshooting%20Steps](https://help.ubuntu.com/community/SoundTroubleshooting#Basic%20Troubleshooting%20Steps)

It seems too complicated. 

I'm using Xubuntu ver:9.04.

Thank you.

PS I can't find the volume control at the top right hand corner any more. Where did it go?

ali

---

### Post by Yondergod22 on 2009-05-01
I think you need drivers for your speakers or sound card. 
but im no linux expert so don't quote me on that.

---

### Post by guitar_man on 2009-05-01
is this the first time you encounter this problem?
Do you dual boot on other OS?
I think th problem is in your laptop..try booting any windows OS and see if the sound is ok....

---

### Post by original_jamingrit on 2009-05-01
If there is just faint sound coming in through you headphones, then it would seem that for some reason, your speaker and headphones aren't getting enough power (the speakers will probably need more power to play, explaining why you can't hear them at all).

So, your drivers should be fine, unless for some funny reason your laptop requires extra drivers for your speakers (which is highly unlikely).

I'm not sure what kind of volume control you would normally use in Xubuntu, but open up your terminal, and simply type in the command
```
alsamixer
```, which should give you the full mixer, and show you whatever you might have missed.  (it should be simple enough to use, just press up or down to set the volume, and press left and right to switch between controls).

This could possibly be a problem with pulseaudio (Ubuntu and Xubuntu's default sound service), so come back if alsamixer doesn't help.

---

### Post by a_satari on 2009-05-02
The sound is now working. I tried combinations of everything in alsamixer, everntually I turned external amp off and the sound blased out of the speakers at full volume, giving me quite a fright!

Does any one know why the external amp is set to on as default? Do most people have an external amp? Did I switch it on and then think that this was default?

Thanks Yondergod22, guitar_man and original_jamingrit for your help.  

Ali

---

