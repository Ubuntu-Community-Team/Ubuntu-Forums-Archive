---
title: "Audacity - no sound?"
date: 2009-04-08
forum: New to Ubuntu
---

### Post by Nutopia on 2009-04-08
Hi,

I'm using Ubuntu 8.04. I've installed Audacity and am trying to play some music, but I can't hear anything. I've searched the web and found this is a common problem. However, nothing I've found has fixed my problem. I keep getting the "Error while opening audio device" message.

Anyone have suggestions on how to troubleshoot this?

---

### Post by durand on 2009-04-08
You may need to change the device that it plays through in preferences. Go to Edit > Preferences and change the Playback Device to something else. That may do the trick.

BTW, Audacity is for editing music, and it is not meant to be a full featured music player.

---

### Post by Nutopia on 2009-04-08
I've tried changing the device, but the only one that doesn't cause an error is 'HDA Intel Digital' which is not hooked up.

Yes, I'm trying to edit some music. :guitar:

---

### Post by durand on 2009-04-08
Hmm, try opening a terminal (Applications > Accessories > Terminal) and run:```
pasuspender audacity
```
This will suspend pulseaudio and you might have more luck however it does mean that you can't run any other music applications while audacity is running.

---

### Post by Nutopia on 2009-04-08
That hasn't made a difference - same error.

---

### Post by Temposs on 2009-04-08
What durand recommends may work.

The problem with Audacity is that it uses a special audio processor called JACK and doesn't have an interface into pulseaudio, which is the overarching audio system that Ubuntu uses.

The effect is that Audacity wants to hog your audio system. You'll notice that if you turn on Audacity right after you boot up, it should work fine. The problem is when you have other programs open that have played audio, like firefox/flash, rhythmbox, totem, etc...

So, if you start Audacity normally, you have to close all those programs down before you open Audacity, and then Audacity will play your sound.

---

### Post by Temposs on 2009-04-08
You may notice that once you do as I suggest above, if you try to play sound on any other program, the sound is muted, but sound still works in Audacity. You have to close Audacity and the program on which you were trying to play sound in order to get sound to play on other programs again.

It's a pain, but Audacity can be worth it :-)

---

### Post by durand on 2009-04-08
Unfortunately, the sound system doesn't seem to be the problem here. I don't have jack and it still works fine, with pulseaudio and other applications playing :(. I guess you just need to wait for more suggestions. You should also try the Multimedia forum: [http://ubuntuforums.org/forumdisplay.php?f=334](http://ubuntuforums.org/forumdisplay.php?f=334)

---

