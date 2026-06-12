---
title: "No sound from the front 3.5mm stereo jack"
date: 2011-03-20
forum: New to Ubuntu
---

### Post by Nikola Georgiev on 2011-03-20
The reason I mention this as a problem is, because the sound from the front is louder.

The front 3.5mm stereo jack isn't working. B.U. (Before Ubuntu) I was with Windows XP. A.U. I have sound only from the back jack.



Just to understand it easier:
Front:
[http://i55.tinypic.com/nlxx91.jpg](http://i55.tinypic.com/nlxx91.jpg)
Back:
[http://i54.tinypic.com/dewu8k.jpg](http://i54.tinypic.com/dewu8k.jpg)

My audio card is built-in:
```
Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
```



Edit: I know the best way is to get myself a decent audio card, but I don't have the money yet.

---

### Post by durand on 2011-03-20
I've got a similar card so it should work. Open a terminal (Applications > Accessories > Terminal). Type in alsamixer and press enter. Move from side to side and check that none of the options are muted. There should be no MM under any of the levels. If there is, press M. Press Esc to quit.

---

### Post by Nikola Georgiev on 2011-03-20
> **durand said:**
> I've got a similar card so it should work. Open a terminal (Applications > Accessories > Terminal). Type in alsamixer and press enter. Move from side to side and check that none of the options are muted. There should be no MM under any of the levels. If there is, press M. Press Esc to quit.

Line was muted. Set it to max. Esc. No restart. Still no sound from the front.

---

### Post by durand on 2011-03-20
Press tab and check the other options as well, also, F6 and change the sound card to another.

---

### Post by Nikola Georgiev on 2011-03-21
> **durand said:**
> Press tab and check the other options as well, also, F6 and change the sound card to another.
One of the "Capture" options is muted too.
Also, Mic, Mic Boost, Mic Boost, Beep.
Line is set to the max, but still have those "MM" under it.

In "Select Sound Card" there are 3 options: 
- default
0 HDA Intel
enter device name...

What should I do there?

---

### Post by durand on 2011-03-21
Hmm, You've only got one sound card so I don't think you need F6. Uhm, I'm not really sure now. Check that you have the right settings in System > Preferences > Sound. You can unmute stuff by pressing M in alsamixer but I don't think that will fix your problem.

If you get [paman]("apt://paman") from the repos, you should be able to overboost your sound which will make it louder. That might help you. Once installed, press Alt + F2, and type in paman to run it.

---

### Post by Nikola Georgiev on 2011-03-21
> **durand said:**
> Hmm, You've only got one sound card so I don't think you need F6. Uhm, I'm not really sure now. Check that you have the right settings in System > Preferences > Sound. You can unmute stuff by pressing M in alsamixer but I don't think that will fix your problem.

If you get [paman]("apt://paman") from the repos, you should be able to overboost your sound which will make it louder. That might help you. Once installed, press Alt + F2, and type in paman to run it.


[http://i56.tinypic.com/2dr6ot4.png](http://i56.tinypic.com/2dr6ot4.png)
When I open that falling menu, I can't (wtf?) make a screenshot.  But there are some options like
Analog surround 5.0 output
Analog surround 4.0 output
Analog stereo input
etc...
I tried them all. Still no sound from the front jack.

I tried overboosting, but it distorts the sound.

---

### Post by durand on 2011-03-22
Hmm, weird. I'm not realy sure :( Maybe someone else will know, otherwise, file a bug at launchpad.net: [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

