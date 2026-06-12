---
title: "recording studio"
date: 2009-12-18
forum: New to Ubuntu
---

### Post by fred_dude on 2009-12-18
:guitar:Hi All,
want software that will allow me to play guitar into pc and add drums and other instruments. like a music studio.Any help appreciated.love this linux so far,bit of a steep learning curve for a newby.

thanx fred

---

### Post by Cheesemill on 2009-12-18
Check out [Ubuntu Studio]("http://ubuntustudio.org/").

It's basically standard Ubuntu but with loads of music production apps installed and slightly tweaked to give better audio performance.

If you already have standard Ubuntu installed then you can change it to Ubuntu Studio by typing the following into a terminal.
```
sudo aptitude update && sudo aptitude install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt
```

See here for more info:
[https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu](https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu)

---

### Post by seeker5528 on 2009-12-18
> **fred_dude said:**
> :guitar:Hi All,
want software that will allow me to play guitar into pc and add drums and other instruments.

One of your most basic options for this is Audacity, which will allow multitrack recording with editing and FX capabilities.

The guitar you can plug directly in to the microphone jack if you want to record it clean and add FX later or if you have FX boxes you run through it's best to plug those in to the line in jack.

To do guitar FX in real time on the computer there is a program called Creox, which uses the Jack audio connection kit, so if you look into some of the recording software that uses jack, jack supports chaining the output of one program to the input of another.

Haven't got into this stuff much myself so I can't tell you a lot about how the software works, but I expect it's probably a little easier to get going, in particular if you are new to Ubuntu/Linux, if you start with a fresh install of Ubuntu Studio, as opposed to adding the Ubuntu Studio stuff to a stock install of Ubuntu, that is assuming this is a new installation and you don't have a lot invested in it yet.

Later, Seeker

---

### Post by fred_dude on 2009-12-18
thanx alot guys.

Fred

---

### Post by themusicalduck on 2009-12-18
Ardour is very good too for recording.

---

