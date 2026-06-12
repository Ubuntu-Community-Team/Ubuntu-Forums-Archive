---
title: "Painfully Slow!"
date: 2009-09-27
forum: New to Ubuntu
---

### Post by DarthSpirit on 2009-09-27
I have it installed inside a Windows environment (Vista) but its slower than slow and the web pages never come up it just sits there with the little disc spinning and a blank page. I am using firefox. If I install Opera into it will it change Windows to Opera as well? Just cannot figure out why its so slow. I am new to the Linux software so be gentle please.

---

### Post by Schendje on 2009-09-27
> **DarthSpirit said:**
> I have it installed inside a Windows environment (Vista) but its slower than slow and the web pages never come up it just sits there with the little disc spinning and a blank page. I am using firefox.
How do you mean, inside a Windows environment? Did you use a virtual machine? Or Wubi?

> **DarthSpirit said:**
> If I install Opera into it will it change Windows to Opera as well? Just cannot figure out why its so slow.
It sounds like a networking problem, really. But no, it will only install Opera on Ubuntu and leave Windows alone.

> **DarthSpirit said:**
> I am new to the Linux software so be gentle please.
Don't worry, we won't bite. Welcome! :D

---

### Post by Finalfantasykid on 2009-09-27
Since you installed it inside of windows, you are now having your computer run two operating systems at the same time, and the secondary OS will have less priority than the main one(Windows in this case).  This is especially true if you don't have very much ram.

---

### Post by Ugz907 on 2009-09-27
Yeah i'd have to agree, not sure what's up with wubi-installer, but i think i may try a full install to one of my free 500g hdd.  I currently am having a ridiculous slow opening and closing of apps, lack of special effects, etc. etc., to be expected really on a new install (ohso familiar with vista custom installs and the quirkyness that it implies)... really just want to find out what all i have to do to get this beast running on all four cores, smoothly, with max graphical settings/bells/whistles etc.
 
now i heard rumor that ati video cards are a pain, any help on manipulation through the terminal etc would be much abliged XD  other than that im going to continue to look around hopefully i find some good info, or someone can link me some.

---

### Post by grturner on 2009-09-27
ATI simply just doesnt really care much about linux, well... much about anything in general. They've just dropped support for alot of vid cards for both windows and linux, but their linux drivers generally just havent been that good. 

I run a Dell E1705 with a radeon mobility x1400 on ubuntu 9.04. The only way i could get their old drivers to work was to downgrade parts of Xorg to intrepid ibex 8.10. 

If your ATI card isnt supported under 9.04, this tutorial worked for me. 
[http://ubuntuforums.org/showthread.php?p=7983598](http://ubuntuforums.org/showthread.php?p=7983598)

As for running ubuntu within windows, unless you have a really high end setup, you're just not going to get much performance. Installing Opera within ubuntu will not install opera in windows. To get more of an idea of what ubuntu would run like if you had installed it on your computer, burn the live cd and give that a spin.

---

