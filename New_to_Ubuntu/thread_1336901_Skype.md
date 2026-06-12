---
title: "Skype"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by herbertportillo on 2009-11-25
I just bought a Microsoft LifeCam Cinema today, and I connected it to the computer and it recognized it at '/dev/audio1' and '/dev/video0'. I have Cheese, and I can see myself and I can take pictures and record video.

I'm trying to get it to work in Skype, but I can't even test it in the program. Any and all help is appreciated. Thx.

---

### Post by G-Com on 2009-11-25
> **herbertportillo said:**
> I just bought a Microsoft LifeCam Cinema today, and I connected it to the computer and it recognized it at '/dev/audio1' and '/dev/video0'. I have Cheese, and I can see myself and I can take pictures and record video.

I'm trying to get it to work in Skype, but I can't even test it in the program. Any and all help is appreciated. Thx.
Ububtu looks like it has a Skype alternative called Ekiga.

Applications>>Internet>>Ekiga Software.

---

### Post by herbertportillo on 2009-11-25
I had Ekiga on Jaunty, but it was removed from Karmic. I never used  Ekiga anyways even when I had it. I'm trying to get the webcam to work in Skype. Does anyone know how it could work?

---

### Post by werecatomega on 2009-11-25
i know how to make it work.

right click the menu bar and press "edit menus"

from there go to internet, click skype and press properties. from there, replace the command with this

bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype'

it should work from there when you load up skype. it worked for me at least.

---

### Post by herbertportillo on 2009-11-25
No, sorry, I had already tried that. Nothing happens.

---

### Post by herbertportillo on 2009-11-25
I can see myself in Cheese, so something is going right. I just can't seem to figure out how to make Skype work. Any and all help is appreciated.

---

### Post by herbertportillo on 2009-11-25
Hmm, it just started working :)

---

### Post by Sealbhach on 2009-11-25
> **herbertportillo said:**
> Hmm, it just started working :)

That's good, however you did it.;)

.

---

### Post by leorolla on 2009-11-26
How did you install Skype on Ubuntu?

I'm also having problems with Ekiga, and this is the main reason why I still keep the Windows partition.

---

### Post by herbertportillo on 2009-11-27
I just went to skype.com.

Here's the link if you want to look at it. It's easy to install. Just download the .deb for your computer's architecture and double-click it and it'll install. Cheers.

[http://www.skype.com/download/skype/linux/choose/](http://www.skype.com/download/skype/linux/choose/)

---

### Post by MSPdwalt on 2011-08-31
What's your opinion of the cam? How well does it work in Lucid?

---

### Post by cariboo on 2011-08-31
This thread is over two years old, please start a new one, as this one is closed.

---

