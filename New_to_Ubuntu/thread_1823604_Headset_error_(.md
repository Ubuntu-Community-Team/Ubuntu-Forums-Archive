---
title: "Headset error :("
date: 2011-08-12
forum: New to Ubuntu
---

### Post by abeng on 2011-08-12
Night all :D

I have acer aspire one 522 it working well and nice, but there is small problem with the headset jack
whenever I plug headset on it, it wont work and no notification :(

I don´t know what´s happen but I´m really sure the netbook did´nt recognize the jack

---

### Post by abeng on 2011-08-13
bump :(

---

### Post by 3rdalbum on 2011-08-13
Merely plugging the headset into the jack won't cause audio to be redirected into it. You need to go to the Sound Preferences (under the speaker icon in the panel) and actually choose the headset jack as the Output device there.

Have you tried this?

---

### Post by abeng on 2011-08-13
> **3rdalbum said:**
> Merely plugging the headset into the jack won't cause audio to be redirected into it. You need to go to the Sound Preferences (under the speaker icon in the panel) and actually choose the headset jack as the Output device there.

Have you tried this?

hello bro :D

hem it seems nothing change because I already set the sound preferences, the problem now my netbook doesnt recognize the sound card I dont really know what´s the problem 

this is my sound card I get using lspci command on terminal
ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)

---

### Post by 3rdalbum on 2011-08-13
> If anyone was following this, I removed ~/.asoundrc and I have sound again.

From another forum post I found on Google regarding this card.

Otherwise, it should Just Work. It's not new enough to cause problems as far as I know.

---

### Post by abeng on 2011-08-13
do you think I have to fresh install? I

---

### Post by 3rdalbum on 2011-08-13
> **abeng said:**
> do you think I have to fresh install? I

No, you shouldn't have to fresh install.

Does the sound work if you create a new user account and log into that?

---

### Post by abeng on 2011-08-13
> **3rdalbum said:**
> No, you shouldn't have to fresh install.

Does the sound work if you create a new user account and log into that?
nope nothing change, the sound still not going out

---

### Post by Sleepy-zz-John on 2011-08-24
> **3rdalbum said:**
> Merely plugging the headset into the jack won't cause audio to be redirected into it. You need to go to the Sound Preferences (under the speaker icon in the panel) and actually choose the headset jack as the Output device there.

Have you tried this?
I have the same Aspire One 522 netbook running on Natty,  and I have the same problem.   No output from the earphone jack.  Neither does the built-in mic or external mic socket work,  yet I've proved all the hw is OK because they all work on Windows once I've installed Acer's Windows drivers.

But I'm puzzled by your comment about choosing the headset jack in Sound Preferences 'cos I can't find that choice.  I have however chosen "Internal Audio 1 output/1 input Analog Stereo Duplex" instead of the rear HDMI digital, and I do have audio output from the built in speaker.

Not sure if I've missed something or what since we're both on Natty with the same netbook :confused:

---

