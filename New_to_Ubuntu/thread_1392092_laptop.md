---
title: "laptop"
date: 2010-01-27
forum: New to Ubuntu
---

### Post by spoc55 on 2010-01-27
[LEFT]just installed ubuntu and when I put my laptop into hibernation or close it up it does not default back to anything when I open it up. I have to reboot again. Is there something I can do to correct this?
[/LEFT]

---

### Post by Kafubie on 2010-01-27
I manually select suspend.
Then close the laptop, then when I want to use it; I just open it again and log in.

---

### Post by MaindotC on 2010-01-27
This type of issue typically has to do with your video driver.  Please post your laptop specifications with a link to a manufacturer website.  Also please post the output of:
```

lspci
lshw -c Video

```

---

### Post by peace.gangsta on 2010-01-27
How exactly did you install Ubuntu?
Did you dual boot or a stand alone Ubuntu ?

---

### Post by MaindotC on 2010-01-27
> **peace.gangsta said:**
> How exactly did you install Ubuntu?
Did you dual boot or a stand alone Ubuntu ?

Can you explain why this question is relevant?

---

### Post by kennewickrockerguy on 2010-01-27
> **spoc55 said:**
> [LEFT]just installed ubuntu and when I put my laptop into hibernation or close it up it does not default back to anything when I open it up. I have to reboot again. Is there something I can do to correct this?
[/LEFT]

Not sure how familiar you are with computer and laptops, but when I put Vista to sleep, the spacebar wakes it up but when it's hibernation, I have to hit the power button and it looks like it's loading but is just resuming. I am new to Ubuntu (day 2 now) and noticed when it hibernates and I push power a screen pops up briefly saying something to the effect of waking up system. I'm not sure how new to Ubuntu you are, but have you tried the power button, maybe open a new note and type something random on it and put it to hibernate just t see if you're actually rebooting or waking up. If you need to change what happens when you close the lid go to:
System > Preferences > Power Management
from here you can chose what happens when you close the lid on AC power and battery. I hope this helps.


Regards,
Ubuntu Noob

---

### Post by docmkk on 2010-02-04
I have the same problem with failure to wake up from suspend or hibernate. Suspend goes into a black hole, and hibernate sort of wakes up, giving me a message "Waking up, this might take a few moments..." which lasts until I force a restart. 

I have a Dell Inspiron 1720. When I run lshw -c Video, I get:
 description: VGA compatible controller
       product: G84 [GeForce 8600M GT]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:fd000000-fdffffff memory:e0000000-efffffff(prefetchable) memory:fa000000-fbffffff ioport:ef00(size=128) memory:fea00000-fea1ffff(prefetchable)

I have added 2GB of swap space, so I don't think that is the problem. Browsing around suggests something wrong with my video driver. I installed Ubuntu 9.10 from a CD image burned from a recent download.

---

### Post by samantha_ on 2010-02-04
Have you looked in System -> Administration -> Hardware Drivers?
(or at least I think thats where it is....)
and installed the drivers from there?
---------------------------------
or download the drivers from the nvidia site.
```

32  -bit : http://www.nvidia.com/object/linux_display_ia32_190.53.html
64 -bit :  http://www.nvidia.com/object/linux_display_amd64_190.53.html

```
Download one of those to your desktop, press alt+ F1, login and type this in...
```

sudo killall gdm
cd ~/Desktop
sudo sh NVIDIA*sh

```
Follow the onscreen instructions, and after you finish the installation,
```

sudo shutdown 0 -r

```
-----------------------------------
or you can also use envyng
```

sudo apt-get install envyng-core envyng-gtk
sudo envyng -g

```

oh, and please dont do all of the options, only do ONE of them....

---

### Post by docmkk on 2010-02-05
I added the hardware driver found in "System/Hardware Drivers". The laptop now wakes up, although I get some error-like messages before it shuts down. I'll research a little more about the driver using your suggestion. Thanks for putting me on the right path.

---

