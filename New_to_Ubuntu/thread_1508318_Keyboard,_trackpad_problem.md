---
title: "Keyboard, trackpad problem"
date: 2010-06-12
forum: New to Ubuntu
---

### Post by The Eight-Bit Link on 2010-06-12
My keyboard and trackpad don't work. Also, my soundcard doesn't seem to work either. Help please.

---

### Post by an0dos on 2010-06-12
What type of computer do you have (manufacturer and model)? What version of Ubuntu are you running?

---

### Post by The Eight-Bit Link on 2010-06-12
dell inspiron 2500, ubuntu 10.04. I think all hardware, minus usb screen, and network isn't working. That, or my guidepoint serial trackpad isn't working.

---

### Post by an0dos on 2010-06-13
> **The Eight-Bit Link said:**
> dell inspiron 2500, ubuntu 10.04. I think all hardware, minus usb screen, and network isn't working. That, or my guidepoint serial trackpad isn't working.

I looked up the Dell Inspiron 2500. Does your computer have only a Pentium III processor and 64 MB of ram? 

If that is the case, then your computer is a bit too old to run the full version of Ubuntu 10.04. You should look into lighter-weight linux distributions like puppy linux (although I think puppy may require more RAM than that). You can also check out damn-small-linux

If that is not the case, then post your processor and RAM information.

---

### Post by The Eight-Bit Link on 2010-06-13
No, it has  celron clocking at 1ghz, and 316 mb of ram. This isn't a stock dell, my friend. However, I got my keyboard back by enabling seral and parallel in the bios setings.

---

### Post by The Eight-Bit Link on 2010-06-13
Bump.
Also, my keyboard works if I open the bios settings menu on startup.

---

### Post by an0dos on 2010-06-13
To get your sound working please refer to the procedures in this thread: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

or run the following commands in the terminal and post the output here:

```
lspci
```
```
aplay -l
```
```
dpkg -l | grep "ALSA"
```

If your video card is listed when you run "aplay -l", then your sound is probably muted. In which case run:
```
alsamixer
``` and adjust the sound.

---

### Post by The Eight-Bit Link on 2010-06-13
But what about my trackpad and keyboard? The board only works itf on startup I open the bios menu.

---

### Post by an0dos on 2010-06-13
> **The Eight-Bit Link said:**
> But what about my trackpad and keyboard? The board only works itf on startup I open the bios menu.

I read several accounts of people running linux on a Dell Inspiron 2500.It is possible that something in your BIOS is mis-configured. Have you tried resetting your BIOS settings to their defaults?

---

### Post by an0dos on 2010-06-13
You should also check out this thread: [http://ubuntuforums.org/showthread.php?t=522513](http://ubuntuforums.org/showthread.php?t=522513). It seems that the keyboard connector can come loose, hence it may also be a hardware problem.

---

### Post by The Eight-Bit Link on 2010-06-16
Bump
Still having no luck. The connector should be fine, it works in the bios. Also, this doesn't help me with my trackpad problem. The built in one still doesn't work.

---

