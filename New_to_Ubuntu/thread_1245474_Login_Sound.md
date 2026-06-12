---
title: "Login Sound"
date: 2009-08-20
forum: New to Ubuntu
---

### Post by Def_101 on 2009-08-20
I have done hours of search but still haven't found an answer for my problem so here it is.

Recently I noticed my login sound hasn't been drumming when i login.

I checked my sounds and made sure the ubuntu theme was being used and playing correctly.

I then checked to see if my login window preference was set correctly and I found out that the check box was unchecked and the tone was set to none?????. So I set it to login-desktop.ogg. But know it only plays staticgarbledlogin.ogg.

I have tried the tone in the ubuntu sound file and it works properly. It plays properly in the system, pref, sound, ubuntu theme. But when I go into login window pref i get the same static garble.

I am out of thoughts for this so if I could recieve some help it would be greatly appreciated.

---

### Post by bandgeek on 2009-08-20
Set it to question.wav

---

### Post by Def_101 on 2009-08-20
> **bandgeek said:**
> Set it to question.wav

That is the login ready sound file. I am having issues with the successful login sound the drums.

I should add though that the wav files sound proper just not the ogg?

---

### Post by lisati on 2009-08-20
> **Def_101 said:**
> That is the login ready sound file. I am having issues with the successful login sound the drums.

I should add though that the wav files sound proper just not the ogg?

I wish to confirm that on my system question.wav plays on appearence of the login screen and desktop-login.ogg plays on successful logon

---

### Post by Def_101 on 2009-08-21
bump

now today my sound in general sounds distorted

---

### Post by Def_101 on 2009-08-21
I am now thinking it maybe a gstreamer codec or a codec in gnome giving me the hassel.
Any ideas or stuff to try would be appreciated, I may try and uninstall and reinstall my audio driver.

---

### Post by Def_101 on 2009-08-22
To update I have recently updated my alsa driver from 1.0.18 to 1.0.20 using this site

"http://webupd8.blogspot.com/2009/08/how-to-upgrade-to-alsa-1020-on-ubuntu.html?dsq=15231619#comment-15231619"

I am still not getting clear login sound

---

### Post by Def_101 on 2009-08-23
I have fixed it for know by using sound converter to convert the desktop-login.ogg to desktop-login.wav, and i saved it in my home folder.

 I am still wondering why my login preference window only plays .wav files correctly and not .ogg?????? Most of the default sounds in my jaunty are .ogg???

I will let you now what I find out.

---

### Post by lelamal on 2009-09-30
Hi, I have the same problem, but your method didn't work here. I tried also [this solution]("http://ubuntuforums.org/showpost.php?p=7924832&postcount=9"), but no joy. Both the .ogg file and its .wav incarnation work properly if played manually. But still, no login sound...

---

### Post by hansdown on 2009-09-30
Hi lelamal.

There is another setting to look at.

Click system> preferences> sound> sounds.

make sure the "play alerts and sound effects" box is checked.

---

### Post by lelamal on 2009-10-16
> **hansdown said:**
> Hi lelamal.

There is another setting to look at.

Click system> preferences> sound> sounds.

make sure the "play alerts and sound effects" box is checked.

Hi hansdown, and thanks for your advice. Somehow I forgot to subscribe to this thread, sorry for replying only now. Unfortunately, that option has always been checked, so no login sound as yet. However, I decided to have a fresh installation once Karmic Koala is out, to get rid of all these minor annoyances accumulated along the path of my first year with Ubuntu. Many thanks anyway!

---

### Post by hansdown on 2009-10-16
Best of luck lelamal.

Hope it works well.

---

