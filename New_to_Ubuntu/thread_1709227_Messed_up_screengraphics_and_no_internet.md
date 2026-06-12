---
title: "Messed up screen/graphics and no internet"
date: 2011-03-17
forum: New to Ubuntu
---

### Post by hh511jas on 2011-03-17
[FONT=Tahoma][SIZE=2]I'm a Windows Vista user but I  decided to try Ubuntu 10.10 for the first time, I installed it using  Wubi (duel boot), finished installing and rebooted. Once Ubuntu started,  the screen/graphics were messed up. I notice it was too big, a lot  of lines a lot of distortion half of the screen is missing, etc. Once it finished installing, it  rebooted and went to the Ubuntu log on [/SIZE][/FONT][FONT=Tahoma][SIZE=2]screen  and it was severely distorted too. Maybe it has to do with my system  not meeting the requirements, the following are my system specs:

**32-bit HP Pavilion dv6500 Notebook**[B]

Processor:     AMD Anthlon(tm) 64 X2 Mobile TK55

Graphic Card:  NVIDIA GeForce 7150/ nForce630M

X86 Based PC

1.80GHz

1GB RAM

140 GB of in my C Drive
117GB of free space

Monitor Resolution 1200 by 800 pixels[/B][/SIZE][/FONT]        [FONT=Tahoma][SIZE=2]

I'm pretty sure it meets the requirements but just in case I'll put it there. Anyways I went to* _System -> Administration -> Additional Drivers_* and tried to enable Nvidia drivers but it gave me this: [/SIZE][/FONT][FONT=Tahoma][SIZE=2]"_*Downloading*_[/SIZE][/FONT][FONT=Tahoma][SIZE=2]*_ package indexes failed, please check your network status. Most drivers will not be available_*_._" I have no internet as well and I use wireless. I also tried, since its duel boot, the recovery option and tried to start it with the option that says reconfigure graphics or something like that (sorry can't remember) but after it won't let me pass from there. NOW, I just want you guys to notice that I'm not able to see the entire screen, because half of it is hidden because of the graphics. [/SIZE][/FONT][FONT=Tahoma][SIZE=2]Can somebody please give me a solution because I'm unable to do anything in Ubuntu with the messed of graphics and no internet wireless. Thank you...
[/SIZE][/FONT]

---

### Post by hh511jas on 2011-03-17
[SIZE=2][FONT=Tahoma]In advance I appreciate the advice thank you...
[/FONT][/SIZE]

---

### Post by varunendra on 2011-03-18
Booting with the same 'recovery' option, select 'failsafeX' then again select the default option ('run in low grphx mode for just one session').

Hopefully this should lead you into a decent graphics mode.

If the distortion disappears, but the resolution is still out of screen, you may try '**ctrl**+**alt**+**(+)**' (that is 'plus' sign with 'ctrl' and 'alt' keys) to adjust the resolution to fit your screen.

Once the resolution is good enough to work with, post your question regarding networking issue in "wireless and networking" section, and post here a link to that post/thread so that anyone interested (including me) could follow it.

---

### Post by hh511jas on 2011-03-20
[FONT="Tahoma"][SIZE="2"]I did try it but the graphics stayed the same, it didn't work I'm going to try the **'ctrl+alt+(+)'**. Sorry for the late respond by the way, I wasn't notified by my hotmail.[/SIZE][/FONT]

---

### Post by hh511jas on 2011-03-21
[LEFT][SIZE=2][FONT=Tahoma]Hello again, I followed instructions but nothing... same results. I'm researching but I got nothing...[/FONT][/SIZE]
[/LEFT]

---

### Post by varunendra on 2011-03-21
See if this could help (old one, but maybe useful): [http://ubuntuforums.org/showthread.php?t=987162](http://ubuntuforums.org/showthread.php?t=987162)

Can you temporarily use some wired internet connection?

Here's another suggestion for graphics problem, but requires internet connection :( :
[http://ubuntuforums.org/showthread.php?t=1130587](http://ubuntuforums.org/showthread.php?t=1130587)


Also, as I already suggested before, put your wifi problem in a new post in a new or existing thread under "Wireless & Networking" section of this forum, and post here a link to that post. Maybe connecting to internet could make things easier.

(You may also wish to put a link to this thread there so as to increase chances of getting attention of some experienced guy)

---

### Post by hh511jas on 2011-03-22
[FONT="Tahoma"][SIZE="2"]Yes it's fixed. First I connected the internet (wired connection), then I went to terminal and put ```
aptitude show nvidia-glx-180
``` It showed me that I have two options which I can install (don't remember it), I chose one and put the install code that it gave me, installed, then I went to additional drivers and there was nvidia and my wireless broadcom. Updated then restarted and I got my graphics and wireless. Thank you for the link and the advice. :popcorn:[/SIZE][/FONT]

---

