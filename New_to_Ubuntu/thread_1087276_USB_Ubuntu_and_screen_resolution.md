---
title: "USB Ubuntu and screen resolution"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by Zieb on 2009-03-04
Hey, I'm having a tiny problem with my USB live version of Ubuntu.  The screen resolution is off 9all my evolution mail screen doesn't fit for example), and the resolution options aren't fixing it.  They seem really low (800 X 600 is the highest) on my widescreen display.  Any advice?

---

### Post by JPtux on 2009-03-04
Try installing the drivers using envy.

```
sudo apt-get install envyng
```
```
envyng -k
```
choose the recomended driver, click on apply settings and restart X. (Ctr-alt-backspace). DO NOT RESTART THE COMPUTER.

NOTE: you might have to choose a driver and click on apply settings then restart X after every reboot. I have to do this with my live usb. 

I hope it helps.

---

### Post by Zieb on 2009-03-15
Sorry for the late reply, I've been away from the computer for awhile.

When I type that I get:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package envyng

---

### Post by Zieb on 2009-03-18
Anybody have any advice here?

---

### Post by batharoy on 2009-03-18
```
sudo apt-get install envyng-core

```

Or use Synaptic.

Use this to run it.
```
envyng -t
```

---

### Post by Zieb on 2009-03-19
> **batharoy said:**
> ```
sudo apt-get install envyng-core

```

Or use Synaptic.

Use this to run it.
```
envyng -t
```
After doing this do I restart X as suggested above?

---

### Post by LowSky on 2009-03-19
yes

---

### Post by Zieb on 2009-03-19
> **LowSky said:**
> yes

A quick, stupid question, then: What should happen when I restart X?  I get a black screen with some stuff on it about battery life or some such, and nothing else happens.  Is there so button combination I should know to get everything started up again?

---

