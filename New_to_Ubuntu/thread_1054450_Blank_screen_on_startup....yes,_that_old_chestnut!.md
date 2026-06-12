---
title: "Blank screen on startup....yes, that old chestnut!"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by EGLF24 on 2009-01-29
As a Windows user of some 10 years or so I have finally taken the plunge into the world of Linux - Ubuntu specifically. It installed eventually (via the alternate install method)  but when it boots I am just getting a blank screen after the Ubuntu splashscreen. I realise this a common problem and has been answered many times all over the web but I have not had any luck sorting this.

I get a text prompt if I press Ctrl-Alt-F1 so I know it hasn't locked up but, I can get no further. I'm assuming it's a graphics display problem and many folks out there suggest booting in recovery mode, typing the following and installing the Vesa driver: 

sudo dpkg-reconfigure xserver-xorg

However, when I type this and go to the xserver-xorg config pages, the only options I get are for the keyboard. There is nothing there for video!!

Can anyone help please? I have so far spent two evenings trying sort this and am reaching the point where I'm going to throw in the towel and stick with Mr Gate's offerings. :(

Thanks in advance.

---

### Post by tuxxy on 2009-01-29
Enter the command in the terminal

```
sudo dpkg-reconfigure xserver-xorg
```

Follow the questions through to the end and reboot.

---

### Post by avtolle on 2009-01-29
That particular command does not work any longer with the new X implementation. My suggestion: at the boot menu, select "safe graphics mode" and boot; this will (hopefully) get you into some type of desktop, from which you can then proceed to install the appropriate driver. If this doesn't work, post back, please.

---

### Post by EGLF24 on 2009-01-29
Thanks for the reply, but as I mentioned, I have already tried this and the only options I get are for the keyboard - nothing else!

---

### Post by EGLF24 on 2009-01-29
Sorry avtolle - I was replying to tuxxy! Excuse the dumb question, but I'm completely new to this - how do I get to the boot menu?!

---

### Post by avtolle on 2009-01-29
My bad; I think I confused your situation with a similar problem I've been working on involving booting from the Live CD. 

When booting from the recovery mode, at the prompt type "startx" (without the quotes) and see if that loads anything.

---

### Post by EGLF24 on 2009-01-29
I just tried typing startx. A load of text started scrolling up the screen (far too quickly to read!) and then a split second later the screen went blank. The hard drive continued rattling for 20 seconds or so, but now nothing is happening!....

---

### Post by EGLF24 on 2009-01-30
Blimey, it doesn't take long for a post to get buried on here! I have tried both suggestions above but still get the blank screen. Anymore ideas? Thanks.

---

### Post by AnimalMagic on 2009-01-30
I was getting this intermittently on my 8.04 systems. I found that rebooting, sometimes several times, would get me into the GUI.

In an attempt to debug, I downloaded 'startup manager' and switched off 'show boot splash' and switched on 'show text during boot' and the problem went away. So I now do this on all systems...

---

### Post by EGLF24 on 2009-01-30
Unfortunately I've rebooted countless times and it does the same thing every time. I have also tried disabling the splash screen but all that happened was lots of text scrolled up the screen, then it went blank! (much like when running startx as described above!).

---

### Post by 3rdalbum on 2009-01-30
What graphics card do you have?

When you go to the text terminal, log into it, and then type the following:

```
sudo nano /etc/X11/xorg.conf
```

(that first X is a capital X)

This opens up a text editor. In the Section Device part, just under the line that begins "Identifier", type:

```
     Driver          "vesa"
```

Use tabs so that the new part lines up with the old part.

Save your changes by pressing Control-O and pressing Enter, and then quit by pressing Control-X. Reboot:

```
sudo reboot
```

And you should hopefully have basic unaccelerated graphics and be able to get into the GUI. From there you can try installing proprietary graphics card drivers, if you wish.

---

### Post by EGLF24 on 2009-01-30
That's sorted out! Thanks very much for your help. :D

---

