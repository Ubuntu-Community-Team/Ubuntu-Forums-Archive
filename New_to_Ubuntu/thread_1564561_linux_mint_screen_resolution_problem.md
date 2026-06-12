---
title: "linux mint screen resolution problem"
date: 2010-08-30
forum: New to Ubuntu
---

### Post by lolzywut on 2010-08-30
I installed linux mint yesterday but I have a small problem. Some of it  is not taking up all of my screen. It's not really noticable on Gnome  but when I installed fluxbox half of the screen was black. And on grub a  small part of each side of the screen is cut off. Here's a screenshot on fluxbox:

[http://i34.tinypic.com/2utia93.png](http://i34.tinypic.com/2utia93.png)

what do I do about this? How do I fix my resolution?

---

### Post by scorp123 on 2010-08-30
Why don't you ask this on the Linux Mint forums?? :confused:

[http://forums.linuxmint.com/](http://forums.linuxmint.com/)

---

### Post by lolzywut on 2010-08-30
I asked there also. But since mint is based on ubuntu, and this is a much bigger forum I figured I might also get a response here.

---

### Post by XtrmJosh on 2010-08-30
If you don't get this problem from Ubuntu, it's obviously a flaw in Linux Mint. Tried / considered that thought?

Good luck either way.

---

### Post by scorp123 on 2010-08-30
> **XtrmJosh said:**
> If you don't get this problem from Ubuntu, it's obviously a flaw in Linux Mint.  That's what I thought. "Clem" (the creator of Mint) added a bunch of stuff that makes Mint quite a bit different from Ubuntu ... Saying *"Mint is based on Ubuntu"* is like saying "*Ubuntu is based on Debian"* ... Yes, but then again there is a truckload of differences between all of them, despite all the similarities on the surface.

---

### Post by wojox on 2010-08-30
> **lolzywut said:**
> I installed linux mint yesterday but I have a small problem. Some of it  is not taking up all of my screen. It's not really noticable on Gnome  but when I installed fluxbox half of the screen was black. And on grub a  small part of each side of the screen is cut off. Here's a screenshot on fluxbox:

[http://i34.tinypic.com/2utia93.png](http://i34.tinypic.com/2utia93.png)

what do I do about this? How do I fix my resolution?

Is this a desktop monitor or a laptop screen?

---

### Post by lolzywut on 2010-08-30
> If you don't get this problem from Ubuntu, it's obviously a flaw in Linux Mint. Tried / considered that thought?

Good luck either way. 	

No I haven't because I haven't tried the newest ubuntu


> Is this a desktop monitor or a laptop screen? 	

laptop.

---

### Post by wojox on 2010-08-30
> **scorp123 said:**
> That's what I thought. "Clem" (the creator of Mint) added a bunch of stuff that makes Mint quite a bit different from Ubuntu ... Saying *"Mint is based on Ubuntu"* is like saying "*Ubuntu is based on Debian"* ... Yes, but then again there is a truckload of differences between all of them, despite all the similarities on the surface.

I thought I remembered reading that Mint was switching over to Debian like Crunchbang did.

@OP I've had a similar problem with Ubuntu before, but on a desktop monitor and had to adjust the menu settings on the side of the monitor to reset it.

I'm not to familiar with Fluxbox. Is there a .fluxbox folder (Ctrl+H) in your Home Folder with a configuration file you can adjust?

---

### Post by lolzywut on 2010-08-30
There are quite a bit of configuration files. It's not a fluxbox problem though because when I'm booting up I notice some of the screen is black on the sides. It's just some kind of resolution thing, for some reason it's extreme with fluxbox though. Is there a way to change the monitor settings through some program?

---

### Post by wojox on 2010-08-30
What are you using for Graphics card/chip? In the terminal run:

```
lspci | grep VGA
```

---

### Post by lolzywut on 2010-08-31
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
```

---

### Post by wojox on 2010-08-31
That's what I got as well

```

wojox@wojox-laptop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

```

You using a Dell Studio by chance. You using 1440 x 900?

---

### Post by lolzywut on 2010-08-31
No I'm using HP. And I have 1366 x 768 16:9

---

### Post by lolzywut on 2010-08-31
I installed xfce and the same thing is happening but this time the bottom of the desktop is messed up. So it's obviously  not fluxbox

---

### Post by wojox on 2010-08-31
> **lolzywut said:**
> I installed xfce and the same thing is happening but this time the bottom of the desktop is messed up. So it's obviously  not fluxbox

I've used Mint and Xfce on my laptop and not had a problem. What if you do mess with the resolution settings? May be your laptop. is it old?

---

### Post by lolzywut on 2010-08-31
I've tried messing with compiz and changing my resolution settings but they don't really do much. I don't even know what I'm trying to do though, I don't just wanna go pressing things hoping something works. I'm looking for more of a solution. And my laptop is very new I bought it like a year ago

---

### Post by lolzywut on 2010-08-31
bump

---

### Post by lolzywut on 2010-08-31
bump

---

### Post by scorp123 on 2010-09-02
Did you ask on the Mint forum?

---

