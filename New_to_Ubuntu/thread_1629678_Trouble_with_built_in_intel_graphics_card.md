---
title: "Trouble with built in intel graphics card"
date: 2010-11-24
forum: New to Ubuntu
---

### Post by igotsanevo4g on 2010-11-24
This started when trying to get a working, visually appealing, dockbar working and i couldnt without going to desktop effects and enabling them. When i try to enable desktop effects from none to Normal, it searches for some drivers, tells me it couldnt find them, and then doesnt let me enable desktop effects.

I've read somewhere that my built in intel graphics card in my compaq presario is not compatible or hard to get working with ubuntu?

I'm just looking to solve these by any means possible, this has also hampered most of my media/video/and audio entertainment too.

Thoughts?

Here are my exact specs

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00047765&lc=en&dlc=en&cc=us&product=364077&lang=en](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00047765&lc=en&dlc=en&cc=us&product=364077&lang=en)

82845G with i915 drivers

---

### Post by mikewhatever on 2010-11-24
The thing is, some graphics cards can't run desktop effects. I guess older Intel cards are among those.

---

### Post by igotsanevo4g on 2010-11-24
> **mikewhatever said:**
> The thing is, some graphics cards can't run desktop effects. I guess older Intel cards are among those.

Its not just desktop effects. It's anything that has to do with hardware acceleration, just sucks and/or will not work.

There's gotta be some way around it. I would hope? No?

---

### Post by mastablasta on 2010-11-24
It says:
Video graphics
Integrated Intel Extreme graphics with up to 64 MB shared video memory
 
 
So which chip it is?
 
type this in terminal, to see:
```
lspci | grep VGA
```
 
also you might not be able to use the special effects. or even if you do they might not be much good as your card only has 64MB ram. then again who knows... i only tried with 32 MB ram and could run it perfectly as long as i didn't use the effects.
 
oh and intel graphics (epsecially old ones have poor linux support and are also bad cards. so you mightnot be able to do much with them in windows as well.
 
an option could be this:
[http://ubuntuforums.org/showpost.php?p=9217816&postcount=10](http://ubuntuforums.org/showpost.php?p=9217816&postcount=10)
 
but it can ruin the system. or not...

---

### Post by igotsanevo4g on 2010-11-24
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)

Thats what it spits back at me, no idea what it means honestly...

Well, i have my XP to fall back on if i break 10.10 here. But i'll save switching kernels and other crazy stuff (crazy for me right now at least lol) for later.

What should i do now..?

---

### Post by mikewhatever on 2010-11-24
While Intel 82845 graphics is not a speed daemon, it used to be able to run Beryl (desktop effects of a few years back). However, ever since the second part of 2008, Intel graphics driver support has been going from bad to worse, and it seems that the older 8xx controllers are simply left unmaintained. It got so bad with 10.04 (freezes and xserver crashing), that I think for 10.10, the devs decided to use Vesa instead of the native Intel driver.

Run the command below to find out what driver is used in your case.
```
sudo lshw -C display | grep driver
```

---

### Post by igotsanevo4g on 2010-11-24
> **mikewhatever said:**
> While Intel 82845 graphics is not a speed daemon, it used to be able to run Beryl (desktop effects of a few years back). However, ever since the second part of 2008, Intel graphics driver support has been going from bad to worth, and it seems that the older 8xx controllers are simply left unmaintained. It got so bad with 10.04 (freezes and xserver crashing), that I think for 10.10, the devs decided to use Vesa instead of the native Intel driver.

Run the command below to find out what driver is used in your case.
```
sudo lshw -C display | grep driver
```

This is my driver

configuration: driver=i915 latency=0

Ive learned its no speed demon, but i figure it can do basic stuff lol. It seems like its not doing anything whenever hardware acceleration is enable.

There has to be a fix?

---

### Post by mikewhatever on 2010-11-24
OK, it's not Vesa as I thought. What about the output of the following:
glxinfo | grep rendering

---

### Post by igotsanevo4g on 2010-11-24
> **mikewhatever said:**
> OK, it's not Vesa as I thought. What about the output of the following:
glxinfo | grep rendering

First i get this


The program 'glxinfo' is currently not installed.  You can install it by typing:
sudo apt-get install mesa-utils

Then i installed it and get this


direct rendering: Yes

---

### Post by igotsanevo4g on 2010-11-24
bump

---

### Post by owners4life5 on 2010-11-25
bump. having THE EXACT SAME problem.

---

### Post by mikewhatever on 2010-11-25
Let's try another test, since it's not Vesa and the direct rendering is enabled.

```
glxgears -fullscreen
```

If it runs, you'll see an animation of the spinning gears. Let it run for about 30 seconds, then kill it with the **Esc** key, and post the Terminal output.

---

### Post by igotsanevo4g on 2010-11-25
> **mikewhatever said:**
> Let's try another test, since it's not Vesa and the direct rendering is enabled.

```
glxgears -fullscreen
```

If it runs, you'll see an animation of the spinning gears. Let it run for about 30 seconds, then kill it with the **Esc** key, and post the Terminal output.

Will run that when I get home

---

### Post by tajiknomi on 2010-11-25
[QUOTE=What about the output of the following:
glxinfo | grep rendering[/QUOTE]

[SIZE=2]Sorry for interfering, But can i know ,what this COMMAND is used for....?[/SIZE]

---

### Post by mikewhatever on 2010-11-25
> **tajiknomi said:**
> [SIZE=2]Sorry for interfering, But can i know ,what this COMMAND is used for....?[/SIZE]

Basically, checking if the direct rendering is enabled. You get a simple Yes/No answer which is very convenient.

---

### Post by owners4life5 on 2010-11-25
> **mikewhatever said:**
> Let's try another test, since it's not Vesa and the direct rendering is enabled.

```
glxgears -fullscreen
```If it runs, you'll see an animation of the spinning gears. Let it run for about 30 seconds, then kill it with the **Esc** key, and post the Terminal output.

here is mine:

```
brian@brian-Dimension-2400:~$ glxgears -fullscreen
76 frames in 5.0 seconds = 15.087 FPS
74 frames in 5.0 seconds = 14.783 FPS
77 frames in 5.0 seconds = 15.264 FPS
76 frames in 5.0 seconds = 15.158 FPS
77 frames in 5.1 seconds = 15.205 FPS
77 frames in 5.1 seconds = 15.208 FPS
brian@brian-Dimension-2400:~$ 

```

---

### Post by mikewhatever on 2010-11-25
Not bad. I should have probably mentioned that the frame rate depends on the screen resolution and cpu intensive programs running in the background. Just to give a relative value to these numbers, here is my output on the Dell mini 10 netbook, gma500 graphics, 1024x576 screen.

```
524 frames in 5.0 seconds
473 frames in 5.0 seconds
537 frames in 5.0 seconds
513 frames in 5.0 seconds
542 frames in 5.0 seconds
497 frames in 5.0 seconds
531 frames in 5.0 seconds
483 frames in 5.0 seconds
537 frames in 5.0 seconds
466 frames in 5.0 seconds

```

Long story short, it might be enough to run compiz and it might not. It looks like the reason you can't enable desktop effects is because Intel 8xx has been intentionally blacklisted.
[http://wiki.compiz.org/Hardware/Blacklist](http://wiki.compiz.org/Hardware/Blacklist)

I think the state of affairs with Intel 8xx graphics is summarized well in the following paragraph:

[https://wiki.ubuntu.com/X/Drivers#Video%20Drivers](https://wiki.ubuntu.com/X/Drivers#Video%20Drivers)
> For the older 8xx cards, upstream support has been spotty, and there have been numerous bugs reported. Our primary objective is to give users a stable out-of-the-box experience, so this means turning off features (including KMS and 3D) to minimize the frequency of the problems. Part of the problem (both in Ubuntu and upstream) has been lack of hardware for testing. We're a bit worried that some hardware is so obscure that no one is testing it, and issues will only become visible post-release. 

---

