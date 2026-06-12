---
title: "nvidia s-video out not working"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by chilimac02 on 2009-05-17
My config:
9.04 ubuntu
tx1320us
  nvivida gforce go (256mb) - 185 driver

somewhere (don't remember) I read that I should press fn+f4 to send the signal to the tv... doesn't work for me. 

the screen blinks on the tv and the laptop, but nothing changes...

-Justin

---

### Post by Terry of Astoria on 2009-05-17
Try the screen resolution panel in Ubuntu under preferences.

---

### Post by chilimac02 on 2009-05-17
yeah, there is no "screen resolution" option there. If you mean "display" then you should know that I get an error saying my video configuration doesn't work, use Nvidia settings. 

When I use nvidia settings, I cannot get it to read any other monitor. I don't know how, that's the point of me asking.

---

### Post by fooman on 2009-05-17
open a terminal and type or copy/paste:

```
gksudo nvidia-settings
```when it opens,  look in > x server display configuration 

*if* your s-video is connected form your computer to the tv,  you *should* see 2 screens

if you do see 2 screens....click on "configure" and choose either "separate x screen" or "twinview"

when your done setting up the screens...click "save to x configuration file"

---

### Post by Terry of Astoria on 2009-05-18
Have you installed the Nvidia drivers? Under Hardware Drivers (8.10) in the System menu?
  If not, do and then this stuff should work. Just a suggestion . . .

---

### Post by chilimac02 on 2009-05-19
Alright boys, here is the pic of the Nvidia settings program, since THERE IS NO "SCREEN RESOLUTION" option under 'System'.

[IMG]http://www.otecology.com/stuff/Screenshot.png[/IMG]

When the s-video plug is inserted, I still have no 2nd monitor showing, even when I click "detect displays". It is obviously trying to do something though. Is it something simple like disabling compiz or something I've overlooked?

---

### Post by chilimac02 on 2009-05-19
And this is the other shot that you may want to see...

[IMG]http://www.otecology.com/stuff/Screenshot1.png[/IMG]

---

### Post by chilimac02 on 2009-05-21
So... Nobody cares??

---

