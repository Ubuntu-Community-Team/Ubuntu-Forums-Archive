---
title: "Inspiron 1440 Laptop - No Sound"
date: 2009-10-11
forum: New to Ubuntu
---

### Post by drrrvarghese on 2009-10-11
Hi ,

Can anyone help me to get sound driver for ubuntu for Inspiron 1440 laptop. Or the procedure to get the sound enbled. Iam  new to linux.
 With Thanks in Advance

---

### Post by Styx on 2009-10-12
Hi

Nice to have you on the right system. To be able to help you, it would be nice if you could tell us more about your problem. 
1. what flavor of ubunut do you have? (ubuntu 9.04?)
2. can you finde the sound card in you system?
3. do you have no sound at all?
4. If you know this -- do you use Pulseaudio or alsa?


Lot of questions he.
First thing you might want to do is check if the valume ist turned up on all volume meters -- i know sounds stupid but but the front volume meter is often turned down.

you can post the output of 
```
lshw -class multimedia
```
It might help to finde what sount card you are using.

By the way this is an old thread you schould think of opening a new one

---

