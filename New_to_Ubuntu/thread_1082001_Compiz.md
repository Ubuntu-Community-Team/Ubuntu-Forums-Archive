---
title: "Compiz"
date: 2009-02-27
forum: New to Ubuntu
---

### Post by theozzlives on 2009-02-27
Every time I enable effects (either compiz --replace or in visual effects), my screen goes blank except the wallpaper. 

My GPU is a Intel 82845G/GL[Brookdale-G]/GE, I ran compiz-check and it checks out fine, it worked under 8.04

I'm left hard booting, any suggestions would be appreciated.

---

### Post by halovivek on 2009-02-27
Yes it is giving problem in ubuntu 8.10. i am getting the problem in flicker screen while watching movies. so i use to disable and use it.

---

### Post by abn91c on 2009-02-27
compiz will not work with intel 845 series video and ubuntu 8.10 due to a bug in the driver, no updates available,just disabling desktop effect or removing compiz will ressolve you problem

---

### Post by theozzlives on 2009-02-27
> **abn91c said:**
> compiz will not work with intel 845 series video and ubuntu 8.10 due to a bug in the driver, no updates available,just disabling desktop effect or removing compiz will ressolve you problem

Well that pisses me off. What if I download Alpha 5 of Jaunty?

---

### Post by abn91c on 2009-02-27
> **theozzlives said:**
> Well that pisses me off. What if I download Alpha 5 of Jaunty?
search the jaunty posts, as I use kubuntu 8.10 and I dont know if its fixed in 9.04 :confused:

---

### Post by theozzlives on 2009-02-27
> **abn91c said:**
> search the jaunty posts, as I use kubuntu 8.10 and I dont know if its fixed in 9.04 :confused:

Well I tried the upgrade and fresh install, both craped out on me so I guess I need a video card.

---

### Post by overdrank on 2009-02-27
> **theozzlives said:**
> Well I tried the upgrade and fresh install, both craped out on me so I guess I need a video card.

Hi and if you had no issues with Hardy 8.04 you may choose to stick with it. :)

---

### Post by steveneddy on 2009-02-27
> **overdrank said:**
> Hi and if you had no issues with Hardy 8.04 you may choose to stick with it. :)

My recommendation also.

---

### Post by Maheriano on 2009-02-28
Use more descriptive thread titles or everyone here could just make posts titled, "Ubuntu."

---

### Post by vikramaditya on 2009-02-28
Have you tried using desktop effects under a different theme?  It seems the default "Human" theme might have a bug or two to sort out.  Just a thought...

---

### Post by theozzlives on 2009-02-28
> **vikramaditya said:**
> Have you tried using desktop effects under a different theme?  It seems the default "Human" theme might have a bug or two to sort out.  Just a thought...

I use the Crux theme.

---

### Post by sadiqdude on 2009-02-28
usually destop effects work good if u have a dedicated graphics card it is better if u have nvidia gpu

---

### Post by Maheriano on 2009-03-02
> **theozzlives said:**
> My title is Compiz which happens to be the problem!!! Try not to be such an ****!

I wasn't being an ***, I was trying to help you and everyone else. I realize Compiz is the problem but under your logic you could have named the thread, "Ubuntu." Or, "Computer" or even, "Electrical Device." My point is I normally skip over threads that don't have proper naming and are too generic, which I'm sure a lot of others do as well. If you want more help then you should have named it, "Enabling Compiz Effects Causes Screen To Go Blank."

Next time when someone tries to help you, don't be such an ***.

---

### Post by theozzlives on 2009-03-12
for anyone with the same chipset, I found a solution. Just modify your xorg.conf with the following:
```
Section "Device"
 Identifier "Configured Video Device"
 Driver "intel"
 Option "AccelMethod" "XAA"
EndSection

Section "Monitor"
 Identifier "Configured Monitor"
EndSection

Section "Screen"
 Identifier "Default Screen"
 Monitor "Configured Monitor"
 Device "Configured Video Device"
EndSection


```

---

