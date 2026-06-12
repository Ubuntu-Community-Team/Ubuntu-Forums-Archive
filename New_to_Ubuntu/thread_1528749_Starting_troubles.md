---
title: "Starting troubles"
date: 2010-07-11
forum: New to Ubuntu
---

### Post by Merrr on 2010-07-11
Hi,

I've installed Xubuntu on a very old Intel Pentium 3 laptop. Somehow after installing all 160 updates and rebooting, the system sort of stalls after startup showing the mouse arrow and a blue background, sometimes even the background wallpaper. After a while the screen saver will activate, but nothing else is happening. When I press Alt-F4 I get the shutdown window popup, but that is about the only functioning thing.

Can anyone help me out?
Merrr

---

### Post by piperinkpen on 2010-07-11
if you press ctrl-alt-F3 what do you get?

---

### Post by Merrr on 2010-07-11
The shell of course this part works fine

---

### Post by piperinkpen on 2010-07-11
I was just assertaining as to where the problem lies... which is in X... have you tried going itno the shell and restarting the WM?

---

### Post by Merrr on 2010-07-11
Thank you for your fast responses. No I haven't tried it yet, but how can I restart it? (I'm quite new to linux)

---

### Post by piperinkpen on 2010-07-11
first way is from the blue wasteland / wallpaper... type ctrl-alt-backspace
or from a command line:

```
sudo /etc/init.d/xdm restart
```I can't guarantee it will solve your problem... but it's a start :)

---

### Post by Merrr on 2010-07-11
CTRL-ALT-Backspace didn't work, so I used CTRL-ALT-F3 and logged in.
The restart was initiated, screen was blanked with a blinking cursor in the upperleft corner, but all of a sudden the cursor stopped blinking, and my caps lock and num lock leds started to blink. Somehow I didn't expect this result from a window manager restart. System doesn't respond to anything but a hard reset.
Any other suggestions?

---

### Post by piperinkpen on 2010-07-11
Sorry...but my knowledge is rather limited... you could try re-installing

---

### Post by Merrr on 2010-07-11
I was thinking about it as well although it sounds like a  windows solution to me.

---

### Post by Merrr on 2010-07-11
I've tried it by stopping gdm and than starting it again and somehow it did not make my computer freeze (as restart did). I did get a warning however:
gdm-binary[1283]: WARNING: Unable to find users: no seat-id found

---

### Post by Vincentlaborant on 2010-07-11
> **Merrr said:**
> CTRL-ALT-Backspace didn't work, so I used CTRL-ALT-F3 and logged in.
The restart was initiated, screen was blanked with a blinking cursor in the upperleft corner, but all of a sudden the cursor stopped blinking, and my caps lock and num lock leds started to blink. Somehow I didn't expect this result from a window manager restart. System doesn't respond to anything but a hard reset.
Any other suggestions?

You just had a kernel panic. That can occur if something is giving a unexpected response on kernel actions. Which kernel are you using now? The newest kernel that came with the updates, or the original kernel that came with Xubuntu 10.04 LTS?

I would suggest to run a memtest from the grub menu (you should be able to select it) , or via the live cd (it does not matter which way you start it). It could be that you have a memory problem, which can be traced with a memtest.:popcorn: Grab a cup of tea/ glass of beer and wait for the results (let it run for 1-2 hours so it had multiple runs, so you can see if there are problems that occur random).

---

### Post by Merrr on 2010-07-23
I've reinstalled Xubuntu and somehow the problem was gone. One other problem however is still present. It's the fact that, although my wireless network card is working well, I can't connect to my wep encrypted network. I can see al the networks around, but when connecting it says the password is bad. 
I've tried connecting with the default connection manager and with WICD. Both came up with a similar error, although the "password" works fine with my other PC's (OSX, XP and iOS4).

Any suggestions?

Merlijn

---

