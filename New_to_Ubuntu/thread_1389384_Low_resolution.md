---
title: "Low resolution"
date: 2010-01-24
forum: New to Ubuntu
---

### Post by Palmerin on 2010-01-24
Hi, I'm absolutely new to Linux in general and Ubuntu specifically.
I just installed Ubuntu 9.10 on my ASUS laptop.
The problem is that I can't bring my screen resolution above 800x600.
when I run the [FONT=monospace]"[/FONT]lspci | grep VGA" command, this is what I get:
```
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)
```Any suggestions?

Thanks.

---

### Post by Mariane on 2010-01-24
I had the same thing, it was due to a module called NVIDIA accelerated graphics card driver. If you can access system/hardware drivers (kde, but gnome has something similar - these are general menu paths and not directorie names) try to disable that module and reboot. 

But maybe you can't access this, it is possible that you can only see the top left part of your screen. 

If you can't do this the only way I know is to install Ubuntu 9.04 and wait until someone sorts out the problem before switching to 9.10

There could be other ways to sort it out, for example a command line way of saying : disable the NVIDIA module, but I don't know any. 

Best of luck

Mariane

---

### Post by Palmerin on 2010-01-24
I can access that part and I can see the whole screen, still, it tells me that there are no proprietary drivers in use.

Thanks!

Palmer.

---

### Post by Palmerin on 2010-01-24
I've run the following command succesfuly:

xrandr --newmode "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync

That should add the 1024x768 resoltion to the list and it should allow me to change it. Still, when I type xrandr, it tells me that the maximum resolution for this monitor is 800x600.
Also, another weird thing is that when I type "runx" it tells me that the user is not authorized to do it.

Help please!

Thanks,

Palmer.

---

### Post by halitech on 2010-01-24
SIS cards suck when it comes to Linux and being supported. There is a long thread which may have help for you here

[http://ubuntuforums.org/showpost.php?p=8716413&postcount=304](http://ubuntuforums.org/showpost.php?p=8716413&postcount=304)

---

### Post by RedRat on 2010-01-24
First off, how big is your screen and what kind of video card does it have? Nvidia, I am thinking but you might want to know for sure. But if it is the Nvidia card, I would suggest that you install the Nvidia drivers from synaptic. It appears to be running in plain-jane vga mode.

---

### Post by Mariane on 2010-01-24
I wish I could help more than that... 

I didn't even know there was a runx command, I use startx to manually launch the X server after booting in terminal mode. 

I know it's a lot of trouble but as you have just installed 9.10 you probably don't have a lot of data to back up, if any, so I would really advise you to try to install 9.04 and see if the display is properly configured there. 

Mariane

---

### Post by Palmerin on 2010-01-24
Thanks!

This seems to be the solution for my problem.
I can't download the driver because Rapidshare has been bitching on me for not having an account for weeks now, but I found an older version of the driver on another website that is also linked on the thread and it took care of the issue.

Thanks again, and if you know where I can find the newer version, it will be appreciated.

Palmer.

---

### Post by RedRat on 2010-01-24
> **Palmerin said:**
> Thanks!

This seems to be the solution for my problem.
I can't download the driver because Rapidshare has been bitching on me for not having an account for weeks now, but I found an older version of the driver on another website that is also linked on the thread and it took care of the issue.

Thanks again, and if you know where I can find the newer version, it will be appreciated.

Palmer.
What are you doing with rapidshare??? The driver is in synaptic or on the Nvidia site for download! What site are you downloading this from? I would be leery of any non-linux site. You might even try Envyng, which is also in Synaptic.

---

### Post by Palmerin on 2010-01-24
> **halitech said:**
> SIS cards suck when it comes to Linux and being supported. There is a long thread which may have help for you here

[http://ubuntuforums.org/showpost.php?p=8716413&postcount=304](http://ubuntuforums.org/showpost.php?p=8716413&postcount=304)

This was the solution, the card is not Nvidia, it's SiS.

Thank you all.

---

### Post by halitech on 2010-01-24
guess it pays to actually read the problem and not assume the OP has equipment they don't actually have when they have stated what they have

---

### Post by aimwin on 2010-05-04
Do you still have the problems?

Try this one and see if it can help.
[http://ubuntuforums.org/showthread.php?p=9231489](http://ubuntuforums.org/showthread.php?p=9231489)

---

