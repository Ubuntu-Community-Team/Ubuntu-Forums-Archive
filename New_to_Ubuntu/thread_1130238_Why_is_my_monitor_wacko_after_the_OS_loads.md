---
title: "Why is my monitor wacko after the OS loads?"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by durija on 2009-04-19
Finally got Ubuntu (8.04.2) to dual boot with my XP install on my old Dell.
[http://www.uluga.ubuntuforums.org/showthread.php?p=7099796]("http://www.uluga.ubuntuforums.org/showthread.php?p=7099796")
But now, when I boot into Ubuntu, everything looks right at first. I get the black screen with the ubuntu logo and the orange progress bar. (I guess this is where the hand off to the OS happens.) Anyway, after that, the monitor goes to a static blue field with a bunch of garbage and a half inch square white box for a mouse cursor. I can move the cursor, but there is nothing to do with it. The only way out from here is to reach down and hold the power button until it shuts down. Anybody have an idea of how I can proceed?

---

### Post by mgranet on 2009-04-19
When you see the blue screen with garbage, press and hold CTRL-ALT, then press F1. This will take you to the console. Now login, and type in ```
gedit /etc/X11/xorg.conf
``` Post the contents here.

---

### Post by durija on 2009-04-19
> **mgranet said:**
> When you see the blue screen with garbage, press and hold CTRL-ALT, then press F1. This will take you to the console. Now login, and type in ```
gedit /etc/X11/xorg.conf
``` Post the contents here.

Pressed and held CTRL-ALT and then pressed F1 while holding. No response. It is like everything is locked except the square box cursor.

---

### Post by ktrnka on 2009-04-19
Reboot and select recovery mode from GRUB. If asked, select to drop to a root shell and execute: 
```
dpkg-reconfigure xserver-xorg
```

Just answer yes and ok to all the questions. Then type exit and then select resume normal boot. (or reboot your computer as normal).

If that still didn't work, get back into recovery mode and open your xorg.conf:

```
nano /etc/X11/xorg.conf
```

Then move to where it says "Device" and add -     Driver       "vesa"

right below the "Device" section. Make sure it's Driver without quotes and "vesa" with quotes. Then hit ctrl-x then Enter to save your settings & reboot as normal.

---

### Post by starcannon on 2009-04-19
> **mgranet said:**
> When you see the blue screen with garbage, press and hold CTRL-ALT, then press F1. This will take you to the console. Now login, and type in ```
gedit /etc/X11/xorg.conf
``` Post the contents here.

gedit doesn't work so great in a console, nano however is a solid choice.

+1 to [ktrnka]("http://ubuntuforums.org/member.php?u=258521")'s safemode post, if that doesn't do it, then some time troubleshooting in console may be coming.

---

### Post by mgranet on 2009-04-19
> **starcannon said:**
> gedit doesn't work so great in a console, nano however is a solid choice.


I use nano on Kubuntu, but wasn't sure if gedit replaced it in Ubuntu. Good to know though! :)

---

### Post by durija on 2009-04-19
Thanks ktrnka. Very interesting going through those screens, even if I only vaguely understood a tiny part of it. That eventually got me to the normal login screen. So I have to decide whether to reboot now, or download and install updates. I leaning toward the latter. Might even have a fix in there. Or is there something else I should do first?

---

### Post by neu2buntu on 2009-04-19
i have read in other posts that ```
xterm
``` will run no matter what problems there are with graphics....hopefully i wont need to find this out!!!

---

### Post by ktrnka on 2009-04-19
> **durija said:**
> Thanks ktrnka. Very interesting going through those screens, even if I only vaguely understood a tiny part of it. That eventually got me to the normal login screen. So I have to decide whether to reboot now, or download and install updates. I leaning toward the latter. Might even have a fix in there. Or is there something else I should do first?

If you are having problems, I would most definitely make sure that the system has been fully updated.

---

### Post by ktrnka on 2009-04-19
Once you get your system back up, then you can start "toying" around trying to get the correct driver to work. What is your system's graphics card?

---

### Post by durija on 2009-04-19
Update: When I went back to the machine, I was given the choice of whether to enable the proprietary Nvidia video driver. I thought, "of course". I did and restarted without any problems. Then I installed all updates and again no problems, so I guess this one is solved. However, I wish there was a way to avoid this in the first place. (Install my oem video card if I can find it?) Apparently there is a problem with the generic drivers and my (at the time) high end video card. Not looking forward to reinstalling on this box. Two big headaches so far.

At least if I have problems, this is a friendly and helpful crowd. Thanks so much, especially ktrnka. Go Red Wings.  I think I'm ready to Ubuntu!

---

### Post by starcannon on 2009-04-19
> **durija said:**
> Update: When I went back to the machine, I was given the choice of whether to enable the proprietary Nvidia video driver. I thought, "of course". I did and restarted without any problems. Then I installed all updates and again no problems, so I guess this one is solved. However, I wish there was a way to avoid this in the first place. (Install my oem video card if I can find it?) Apparently there is a problem with the generic drivers and my (at the time) high end video card. Not looking forward to reinstalling on this box. Two big headaches so far.

At least if I have problems, this is a friendly and helpful crowd. Thanks so much, especially ktrnka. Go Red Wings.  I think I'm ready to Ubuntu!

Nice job! And yeah, you've stumbled into one of the friendliest forums on the web.

---

### Post by ktrnka on 2009-04-19
Glad to help. Just helping to repay the debt I owe to these forums!  :) Gotta love the Ubuntu crowd!

---

