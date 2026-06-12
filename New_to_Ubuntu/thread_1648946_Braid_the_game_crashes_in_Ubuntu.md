---
title: "Braid the game crashes in Ubuntu"
date: 2010-12-19
forum: New to Ubuntu
---

### Post by hanzj on 2010-12-19
Braid does not work in Linux. It starts fine and I can get to the house and enter the door for World 2, but it crashes.


You can test it yourself with a donation of any amount at [http://humblebundle.com]("http://humblebundle.com/")

---

### Post by hanzj on 2010-12-19
~$  lspci | grep VGA
05:00.0 VGA compatible controller: ATI Technologies Inc R480 [Radeon X850XT Platinum (PCIE)]

---

### Post by Joeb454 on 2010-12-19
Do you get any output if you run it from the terminal and reproduce the crash? This may give a specific reason for it.

---

### Post by hanzj on 2010-12-19
all it says is "segmentation fault"

---

### Post by JudGer on 2010-12-21
Exactly the same problem here

```
$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc M56P [Radeon Mobility X1600]

```

Seems to be a problem with the radeon-driver?

---

### Post by Tekmoor on 2010-12-25
Braid doesn't start at all for me in Ubuntu, I get a black screen and then it crashes with no errors or any messages in the terminal. I also have an ATI card...

---

### Post by Lefke123 on 2010-12-29
Alright, I managed to fix it for myself. I **disabled S3TC compression** via Driconf (apt-get install driconf), after installing the **x84** version of Braid. That did the trick for me.

---

### Post by Tekmoor on 2011-01-05
Mine worked after I installed the latest proprietary ATI drivers and then installed the braid-linux-build2.run.bin version of Braid! :D

---

### Post by hanzj on 2011-01-06
Tekmoor,
which proprietary drivers? and where do you get them?

Also, what's your ATI video card model?

---

### Post by Tekmoor on 2011-01-06
I simply got them from here: [http://support.amd.com/](http://support.amd.com/)

I have a Mobility Radeon HD 3400. After trying out Braid I've noticed it runs quite sluggish when there are fancy lighting effects on-screen, I may have to resort to playing in Windows...

Hope that helps!

---

### Post by hanzj on 2011-01-08
tekmoor,
thanks.

I'm getting the "ATI Catalyst Proprietary Display Driver" from [http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.1&product=&lang=us&rev=9.3&ostype=Linux%20x86](http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.1&product=&lang=us&rev=9.3&ostype=Linux%20x86).
If I don't plan on playing any games, is it still a good idea to get this 80 MB run file?

---

### Post by hanzj on 2011-01-08
oh, I it seems i just had to download all the stuff from Update manager (after a fresh UBuntu install), and I also did 
sudo add-apt-repository ppa:xorg-edgers/ppa



HOWEVER, Revenge of the Titans still crashes. 8-(

---

### Post by Tekmoor on 2011-01-09
> **hanzj said:**
> tekmoor,
thanks.

I'm getting the "ATI Catalyst Proprietary Display Driver" from [http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.1&product=&lang=us&rev=9.3&ostype=Linux%20x86](http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.1&product=&lang=us&rev=9.3&ostype=Linux%20x86).
If I don't plan on playing any games, is it still a good idea to get this 80 MB run file?
Hey hanzj, If you're not having any problems then I don't think there's any real reason to install it, if you're having trouble with your games/video it may help fix the issue.

---

