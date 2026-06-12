---
title: "Mouse sensitivity problem"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by Geenimetsuri on 2010-05-09
Hi!

I have a basic Logitech mouse (UV96 I think) with 1920x wide screen and moving the mouse around is horribly tedious.

I know I can adjust acceleration under system settings, but is there a function somewhere to adjust mouse sensitivity similar to Windows where acceleration is distinct from sensitivity?

Basically what I'm asking for is movement multiplier adjustment.

I tried searching the forums & apt-cache but couldn't find a solution.

I'd appreciate any help. :)

---

### Post by ankspo71 on 2010-05-09
Hi,
I think that would be "Pointer Threshold" right below the "Pointer Acceleration" option.

---

### Post by narendraD on 2010-05-09
In Lucid I can see both Acceleration and Sensitivity. So try them.

---

### Post by Geenimetsuri on 2010-05-09
> **narendraD said:**
> In Lucid I can see both Acceleration and Sensitivity. So try them.
Oy, that'd be great. 

Gotta upgrade my stick-Kubuntu, which I've mostly used on lower resolutions, then.


Thanks for your replies. :-)

---

### Post by aleko74 on 2010-05-09
> **narendraD said:**
> In Lucid I can see both Acceleration and Sensitivity. So try them.

Where exactly do you see that? I've just upgraded from 9.10 to 10.04 and I don't see these options.

---

### Post by quadproc on 2010-05-09
> **Geenimetsuri said:**
> Hi!

I have a basic Logitech mouse (UV96 I think) with 1920x wide screen and moving the mouse around is horribly tedious.

I know I can adjust acceleration under system settings, but is there a function somewhere to adjust mouse sensitivity similar to Windows where acceleration is distinct from sensitivity?

Basically what I'm asking for is movement multiplier adjustment.

I tried searching the forums & apt-cache but couldn't find a solution.

I'd appreciate any help. :)
You might find that xset m would do what you need.  I typically use xset m 3/2 0.

quadproc

---

### Post by narendraD on 2010-05-10
System --> Preferences -->Mouse

---

### Post by aleko74 on 2010-05-10
> **narendraD said:**
> System --> Preferences -->Mouse

I'm using KDE and there is no such thing there. In the mouse configuration dialog I can see acceleration and double click related settings but nothing about sensitivity.

BTW, 'xset m' doesn't work either because it sets the acceleration. What I need to adjust is the normal (non-accelerated) motion speed.

---

### Post by narendraD on 2010-05-11
I was referring to GNOME. Should be there in KDE as well but i am not familiar with it. So i am sorry.

---

### Post by Geenimetsuri on 2010-10-01
I forgot about this...


In anycase, I've toyed around with various Ubuntu releases (I'm typing this on Flubuntu) and yes...There's mouse sensitivity option.


However it starts from setting of 100, meaning there's no way to make mouse move linearly faster...

...which in turn makes using Ubuntu or its derivatives impossible as I prefer a fast mouse. :(

---

### Post by jtarin on 2010-10-01
I wonder if you read the man pages.....or maybe I'm not understanding your post> mouse
The m option controls the mouse parameters; it may be abbreviated to 'm'. The parameters for the mouse are 'acceleration' and 'threshold'. The acceleration can be specified as an integer, or as a simple fraction. The mouse, or whatever pointer the machine is connected to, will go 'acceleration' times as fast when it travels more than 'threshold' pixels in a short time. This way, the mouse can be used for precise alignment when it is moved slowly, yet it can be set to travel across the screen in a flick of the wrist when desired. One or both parameters for the m option can be omitted, but if only one is given, it will be interpreted as the acceleration. If no parameters or the flag 'default' is used, the system defaults will be set.

---

### Post by Geenimetsuri on 2010-10-02
> **jtarin said:**
> I wonder if you read the man pages.....or maybe I'm not understanding your post

Ah, ok!

So acceleration isn't actually acceleration, merely speed multiplier.


Sorry for the confusion then, I've grown accustomed to sensitivity being the multiplier and acceleration standing for - yes - acceleration of the mouse: Sensitivity controls the ds/dt (=v) and acceleration d^2s/dt^2 (= dv/dt = a) so to speak.


I have to ask though, what does the sensitivity slider do then? Is it just another name for threshold?

---

### Post by jtarin on 2010-10-02
If you play with the sliders you will understand. Put one high and the other low and move the mouse around the desktop. Now set them opposite and move around the desktop. Sensitivity is like drag.

---

