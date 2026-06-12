---
title: "Integrated Graphics in 11.04 Fixed?"
date: 2011-09-05
forum: New to Ubuntu
---

### Post by DGINSD on 2011-09-05
I just upgraded to 11.04 for the second time, after the first there were too many issues and I went back to 10.10.

The main issue is still the same though and after a bit of searching I haven't found a solution. In 10.10 my system used the intel i915 integrated graphics driver with no issues but when I try to activate it in 11.04 I get nothing useable. I've  found plenty of issues reported but no solutions, is there something I'm missing or has this issue still not been resolved?  

I'd imagine it has been and I'm just not doing the right search.

---

### Post by DGINSD on 2011-09-05
For clairitys sake and in the interest of making sure I'm doing this correctly, to activate the intel integrated graphics driver I used the instructions here [[COLOR="Blue"]//wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus[/COLOR]]("//wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus") which state to

> To enable the Intel driver you need to create a file called /etc/X11/xorg.conf containing the following:

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "intel"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection


This page is for Maverick not for Natty so I'm wondering if there is another way your supposed activate in Natty?

I also found this thread which has a lot of various options to try and resolve the issue but they aren't explained very well or I don't have the know how to interpret them here's a link [[COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=1743535&highlight=natty+intel+integrated+graphics[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1743535&highlight=natty+intel+integrated+graphics")

I also don't think I was clear in my original post, I get video with the originally installed video driver, but when I try to enable the intel driver and reboot to get 3D graphics acceleration, I get video but it blinks in and out, clicking and moving the mouse will erase parts if the screen, drop menus erase parts of the screen and are blank.

I've also found some bugs reported by those using the same driver but only when using a secondary monitor. I'm not using a second monitor.

Is it common for the developers to change a driver it just seems strange that it worked fine in Maverick but is actin so screwy in Natty.

One last thing I'm having trouble finding the right bug to join,  how best to search the bug reports to find ones with the same issue, or is it best to report a new one and let it be merged? If someone knows of a "how to" on how to file bug reports?

---

### Post by realzippy on 2011-09-05
please show
```
lshw -c video
```
and 
```
uname -a
```

---

### Post by DGINSD on 2011-09-05
Here you are, thanks for the reply.

```
david@david-Inspiron-1150:~$ sudo lshw -c video
  *-display:0             
       description: VGA compatible controller
       product: 82852/855GM Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:11 memory:e8000000-efffffff memory:f6f80000-f6ffffff ioport:c000(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: 82852/855GM Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:e0000000-e7ffffff memory:f6f00000-f6f7ffff

david@david-Inspiron-1150:~$ uname -a
Linux david-Inspiron-1150 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:05:14 UTC 2011 i686 i686 i386 GNU/Linux


```

---

### Post by realzippy on 2011-09-05
> **DGINSD said:**
> 
```
david@david-Inspiron-1150:~$ sudo lshw -c video
  *-display:0             
       description: VGA compatible controller
       product: 82852/855GM Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list rom
       configuration: [COLOR="Lime"]driver=i915[/COLOR] latency=0

```
hm,intel driver seems to be in use.

---

### Post by DGINSD on 2011-09-05
> **realzippy said:**
> hm,intel driver seems to be in use.

Now I'm confused, so I don't need to make the xorg.conf file to activate it?
 
Ubuntu says I have to use the Ubuntu Classic, I assume because I don't have enough RAM (less than one G like 756M or something) which is fine but my compiz bells an whistles don't seem to work (cube switcher, window shadows, etc) and all worked great in Maverick.

So it appears I'm a moron and my issue lies elsewhere, what to do now?

---

### Post by DGINSD on 2011-09-05
I read somewhere that it won't work properly if the built in framebuffer wasn't used, I can't remember where I read it, and it makes little sense to me but....

Also the monitor shows up as unknown in the monitor preferences gui and nothing can be changed (resolution(though correct), refresh, rotation)

---

### Post by realzippy on 2011-09-05
You could try:

1.Removing/Renaming current xorg.conf
**and**
2.Try glasen`s intel driver versions.
[http://www.ubuntugeek.com/how-to-install-intel-82852855gm-drivers-in-ubuntu-using-ppa.html](http://www.ubuntugeek.com/how-to-install-intel-82852855gm-drivers-in-ubuntu-using-ppa.html)
[https://launchpad.net/~glasen/+archive/intel-driver](https://launchpad.net/~glasen/+archive/intel-driver)

---

### Post by DGINSD on 2011-09-05
There's actually no xorg.conf I removed it when the problems arose.

I'll give the other drivers a try though.

---

### Post by realzippy on 2011-09-05
> **DGINSD said:**
> 
I'll give the other drivers a try though.
means:

```
sudo add-apt-repository ppa:glasen/intel-driver
sudo apt-get update
sudo apt-get upgrade
sudo update-initramfs -u -k all

```
reboot
If then still no unity:
```
/usr/lib/nux/unity_support_test -p
```

---

### Post by DGINSD on 2011-09-05
Did as instructed but no unity, here's the output of the last command given.
```
david@david-Inspiron-1150:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string:  2.1 Mesa 7.10.2

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  no
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          no

```

So strange, graphics worked great in 10.10, I'd be fine just using Gnome if I could get my compiz stuff to work.

---

### Post by realzippy on 2011-09-05
Just read that intel 855GM only runs OpenGL 1.2...
which indeed would mean:
no compiz (new version needs 1.3) 
=
no unity 3D

Sorry,I did not know that,I would have saved you the work.

---

### Post by gandaran on 2011-09-05
>  Integrated Graphics in 11.04 Fixed?
most Intel video cards/drivers work very well like mine but there are some that don't work on 11.04 and it wont be fixed, maybe it will be fixed on the 11.10 release.

---

### Post by DGINSD on 2011-09-05
Could the new version be removed and the old installed?

---

### Post by DGINSD on 2011-09-05
> **gandaran said:**
> most Intel video cards/drivers work very well like mine but there are some that don't work on 11.04 and it wont be fixed, maybe it will be fixed on the 11.10 release.

Do u happen to know what was changed to cause this, as I said worked great in 10.10. Is this a side effect of going to the Unity desktop?

---

### Post by realzippy on 2011-09-05
The new compiz version.... (?)

---

### Post by DGINSD on 2011-09-05
> **realzippy said:**
> The new compiz version.... (?)

Sorry mis-read your post open-gl is what has changed?

---

### Post by realzippy on 2011-09-05
[clasen`s blog]("http://www.glasen-hardt.de/?p=1204") says (translated):
"No desktop effects in 11,04 for i855m because all new compiz versions need at least OpenGL 1.3 which the chip can't do. (1.2)"

---

### Post by DGINSD on 2011-09-05
Bummer, time to get a new computer, looks like this one is about to out live it's usefulness.

---

### Post by DGINSD on 2011-09-05
needless to say this is likely not something that will be "fixed" in later releases?

---

### Post by kaldor on 2011-09-05
> **DGINSD said:**
> needless to say this is likely not something that will be "fixed" in later releases?

Nope. It's a new specification and the current graphics card won't work nicely with it. I wouldn't get a new computer over this, though. Unity is still quite buggy and you probably won't like it until later on anyway.

If you want a longterm OS, stick to Ubuntu 10.04. 

Good luck with whatever path you choose :)

Edit: Oh wow, just noticed the PC you're using. Yeah, a new PC would definitely be a good idea. I recommend anything from HP and anything with Intel graphics. Should be able to get a decently spec'd system for 300-500 in the US or Canada.

---

### Post by BlinkinCat on 2011-09-05
Or you could try Xubuntu, Kubuntu or Lubuntu LTS ? - :p

---

### Post by DGINSD on 2011-09-05
> **kaldor said:**
> Nope. It's a new specification and the current graphics card won't work nicely with it. I wouldn't get a new computer over this, though. Unity is still quite buggy and you probably won't like it until later on anyway.

If you want a longterm OS, stick to Ubuntu 10.04. 

Good luck with whatever path you choose :)

Edit: Oh wow, just noticed the PC you're using. Yeah, a new PC would definitely be a good idea. I recommend anything from HP and anything with Intel graphics. Should be able to get a decently spec'd system for 300-500 in the US or Canada.

I've defiantly been looking at new ones, and even the cheapest of the cheap would be a significant upgrade.

Would switching to Kubuntu make any difference or does it work much in the same way? Incidentally, I have some power manager issues that carried over from 10.10, so fixing those would be another reason to switch (I do like Gnome though).

---

### Post by DGINSD on 2011-09-06
Just a few other thoughts or possibilitys, removing Compiz and installing the version from the maverick repo? or maybe another window manager, recommendations?

---

