---
title: "original unity."
date: 2011-07-08
forum: New to Ubuntu
---

### Post by hookitup on 2011-07-08
so when i installed ubuntu 11.04 i got the error "you dont have sufficient hardware to support unitys 3d like fetures" blah blah blah , so when i logged in and searched additional drivers i got something about my nvidia card supports 3d something or other.... i don't quiet remember ,,, does this mean i can restore the original unity or does this mean nothing in regards to unity and if i can restore it how do  i go about doing this.

Thanks in advance for the help

---

### Post by wojox on 2011-07-08
Yes, just install the "recommended driver" for your nvidia card/chipset from the list. Then reboot.

---

### Post by hookitup on 2011-07-08
well i went ahead and installed the driver and rebooted and never got unity. its still the bumped down version with no unity

---

### Post by TeoBigusGeekus on 2011-07-08
From the log in screen, choose unity at the drop down menu at the bottom of the screen.

---

### Post by hookitup on 2011-07-08
will i be able to see this even if i already installed unity 2d

---

### Post by TeoBigusGeekus on 2011-07-08
Hopefully, yeah.

---

### Post by hookitup on 2011-07-08
this is what i have :(

---

### Post by Frogs Hair on 2011-07-08
To use Unity 3d select Ubuntu .

---

### Post by TeoBigusGeekus on 2011-07-08
> **Frogs Hair said:**
> To use Unity 3d select Ubuntu .

^^^This.

---

### Post by hookitup on 2011-07-08
so i clicked ubuntu instead of the unity 2d and it appears its still in unity 2d ,,, the only way i can tell that it is still 2d and not 3d is cause when i click on the  "workspaces" its all retarded and laggy as it is in the unity 2d and acts nothing like the workspace on my laptop which has the unity 3d.

---

### Post by diesch on 2011-07-08
What does
```
/usr/lib/nux/unity_support_test -p
```
print?

---

### Post by hookitup on 2011-07-08
this is what it says ,```
 OpenGL vendor string:   Nouveau
OpenGL renderer string: Mesa DRI nv17 20091015 x86/MMX/SSE2
OpenGL version string:  1.2 Mesa 7.10.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        no
GL fragment program:      no
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       no

Unity supported:          no

```



so does this mean its still not able to run unity ?

---

### Post by wildmanne39 on 2011-07-08
> **hookitup said:**
> so i clicked ubuntu instead of the unity 2d and it appears its still in unity 2d ,,, the only way i can tell that it is still 2d and not 3d is cause when i click on the  "workspaces" its all retarded and laggy as it is in the unity 2d and acts nothing like the workspace on my laptop which has the unity 3d.Hi, depending on your system specs do what is suggest on this link may help the lagging.
[http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow](http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow)

---

### Post by hookitup on 2011-07-08
it seems he is speaking of unity, im trying to upgrade my unity 2d to the unity 3d or whatever 11.04 comes with

---

### Post by wojox on 2011-07-09
> **hookitup said:**
> it seems he is speaking of unity, im trying to upgrade my unity 2d to the unity 3d or whatever 11.04 comes with

What are you other choices in Additional Drivers for Nvidia?

Your using the open source nouveau.

---

### Post by wildmanne39 on 2011-07-09
> **hookitup said:**
> it seems he is speaking of unity, im trying to upgrade my unity 2d to the unity 3d or whatever 11.04 comes withHi, the lagging is the only issues I am addressing and it applies know matter what you log in as except classic with no effects.

---

### Post by wildmanne39 on 2011-07-09
Hi, also run these commands in a terminal
```
lspci | grep VGA

```
```
sudo lshw
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.
Also in the information you posted it says unity is not supported, but run these commands and we will be able to tell more about your system and have a better idea if we can help you get unity.

---

