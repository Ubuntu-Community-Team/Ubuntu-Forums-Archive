---
title: "Sound will not work in 8.0.4"
date: 2009-04-12
forum: New to Ubuntu
---

### Post by strackan on 2009-04-12
Just upgraded to 8.0.4 and have no sound working.

I know there are some forums already on this, but I've been troubleshooting all day without success, and would like to just start from scratch. Can someone please help me out? Here's some initial info:

strackan@strackan:~$ asoundconf list
Names of available sound cards:
pcsp
Intel

---

### Post by MontelEdwards on 2009-05-06
hmmm,
most of the time when i lose sound i either have to restart pulseaudio, or when im lazy i just restart

---

### Post by acimmarusti on 2009-05-06
Ok, lets start from scratch. Open up a terminal, and type the following:

```

speaker-test -c2 -l5 -twav

```

You should hear a lady's voice saying front right and left several times. Do you hear that?

If you don't hear anything, try typing: *alsamixer*

And now increase volume with the up arrows. When you are done press escape.

Retry the speaker-test.

---

### Post by MontelEdwards on 2009-05-06
Well chances are that if he cant hear anything, that wont work.
But anyways i forgot.
Go to volume control and i think it is prefences and select channels and check PCM then make sure it is turned up.

---

