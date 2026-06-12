---
title: "new to linux/ubuntu"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by penguinjr86 on 2009-01-11
Hey All,
I'm new to ubuntu and to linux. I thought it would be smart to start out with ubuntu because I've heard that the ubuntu community is one the most helpfull places for beginning users of linux. So here I am now. I've succesfully installed it and I need some help of how to get started in my learning process of getting to know linux graphical interface and commandline. I also have the following problem, every so many minutes my firefox freezes and there's no way to shut firefox down and restart it, I've noticed that it's also usually after I press ctrl+t and then when I select to go to my home page. Under windows I don't have this problem. Does anyone have any idea what the problem could be. I look foward to seeing all of you on the forum. 


penguinjr86

---

### Post by karlmp on 2009-01-11
what version of ubuntu are you using?

what page are you visiting when firefox freezes ?

---

### Post by Titan8990 on 2009-01-11
Go to Applications -> Accessories -> Terminal


Type in it:

firefox


wait for the problem occur again and check the terminal screen for error messages that might be useful. Post them here.

---

### Post by Temposs on 2009-01-11
hello and welcome to Ubuntu!

You came to the right place for getting some help :-)

As for closing a graphical program that freezes and cannot be closed otherwise, there is nifty little applet you have called Force Quit. To add it, right click a blank part of the top panel, click Add To Panel, and find the Force Quit applet. Then you just click on the icon on the panel when a program freezes, and then click on the window that's frozen. You will be able to close anything that way.

As to why it's freezing, I'm not sure. It's certainly not an overwhelmingly common problem for Ubuntu users. My first suspect to check out would be the Flash plugin. Think about which sites you visit when there is a crash, and think about if they use flash at all on those sites. Or figure out some other kind of pattern. Have you noticed a pattern like this at all?

---

### Post by karlmp on 2009-01-11
[QUOTE=Titan8990]Go to Applications -> Accessories -> Terminal


Type in it:

firefox


wait for the problem occur again and check the terminal screen for error messages that might be useful. Post them here.[/QUOTE]





after typing 'firefox' press enter

---

### Post by penguinjr86 on 2009-01-11
I'm using Ubuntu 8.04 Desktop 32bit. It just happened again and doesn't happy on any particular page. like this last time it happened when I clicked on reply on the forum here. the problem is when  it happens, my whole system freezes and I can't even click any where to force the application to quit. I used the DVD version if that matters?

---

### Post by karlmp on 2009-01-11
what are your specs?

---

### Post by penguinjr86 on 2009-01-11
2GB Ram
Gefore 8800 
2x500GB
Sweex 5.1 Soundcard
E8400

I've noticed no patterns.Maybe a reinstall of the whole system will help, if I try just using the cd image?

---

### Post by stevoo on 2009-01-11
I would reccomend to upgrade to ubuntu 8.10. 

This may solve your ff problems. 

To do this, open a command line and type : update-manager -c -d
You will be prompted that a newer version is available. 
Update to that. 

*.04 in Ubuntu world adds a lot of new stuff and with it some instability. 
*.10 will do a lot of maintenance and fixes and do the system a lot more stable. 

So i reccomend upgrading to the newer version a must.

---

### Post by ugm6hr on 2009-01-11
> **penguinjr86 said:**
> I used the DVD version if that matters?

What DVD version?

Amazon sells official Ubuntu DVDs, but Canonical only supplies CD images.

Where did you get Ubuntu from?

---

### Post by minsf on 2009-01-11
before reinstalling the whole system, try reinstalling firefox:
```
sudo apt-get install --reinstall firefox
```
from the command line. 
if this does not help, let us know and we'll help you reinstall the plugins.

have you already tried to find errors by runnung "firfox" from the command line, like the previous posts suggested?

regarding learning the command line, you parobably want to start here:
[www.linuxcommand.org](www.linuxcommand.org)
then you can move to the beginner and advanced bash guides in 
[http://www.tldp.org/guides.html](http://www.tldp.org/guides.html)

---

### Post by penguinjr86 on 2009-01-11
this one:

[http://nl.archive.ubuntu.com/ubuntu-cdimages/hardy/release/](http://nl.archive.ubuntu.com/ubuntu-cdimages/hardy/release/)


when I tried running firefox from the commandline it only opens another firefox window

---

### Post by minsf on 2009-01-11
yes it'll open a new firefox window.
the idea is that this new ff window will output the errors to the terminal from which you opened it, so that you can see the errors and let us know

---

### Post by penguinjr86 on 2009-01-11
Can't do that. my whole system freezes. I'm going to try a system reinstall. installing a 8.10 from scratch.

---

### Post by dragonwolf on 2009-01-11
Well 1st thing I would do if you have not done so already is dump 8.04 and go to 8.10 this will probably fix your issue as was suggested earlier I run 8.10 on everything from a PIII server to my desktop which is a phenom 8650 with no issues both 32 bit and 64 bit.

---

### Post by penguinjr86 on 2009-01-11
I did a fresh reinstall and installed 8.10 and the problem seems to be gone.

---

