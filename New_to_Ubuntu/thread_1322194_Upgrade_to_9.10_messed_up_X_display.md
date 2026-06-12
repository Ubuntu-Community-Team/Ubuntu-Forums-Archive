---
title: "Upgrade to 9.10 messed up X display"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by Mariane on 2009-11-10
After the upgrade the GUI didn't function in 9.10 so I started fiddling with it. I installed displayconfig-gtk and this gave me the option to run in low graphics mode. I chose that and it gives me a very crappy display. The computer is barely usable (for example I have to move the browser window from left to right and back with the mouse to read, if I resize it until it fits the screen the scroll handle disappears). 

I have a display, according to displayconfig-gtk:
Model Plug 'n' Play
Resolution 640 x 480 at 60 Hz
And when I try to put it on something else the screen goes black. I have not tried every options, there are many. 

I read that it could be fixed by
sudo dpkg-reconfigure xserver-xorg

But this started asking me many questions about the keyboard so I killed it, thinking the last thing I needed was to mess up the keyboard settings. 

I looked for utilities and found hwdata which installed but apparently did nothing, and nvidia-xconfig which terminated with a segmentation fault. Installing nvidia-xconfig removed nvidia-glx-new so I reinstalled nvidia-glx-new (and it removed nvidia-xconfig). 

I tried both KDE and GNOME and the problem is the same. Over large font everywhere, huge aliased icons, the only program which seems able to properly display its contents is vlc. 

Going back, 9.04 is also messed up but 8 (I've forgotten 8 dot what) still functions. From this I was able to run nvidia-settings - it didn't run in the messed up versions - and to save to /etc/X11/xorg.conf

But now I don't know what to do, I am afraid of going from bad to worse if I start fiddling with xorg.conf


Mariane

---

### Post by OriginalName on 2009-11-13
Hi, dpkg-reconfigure xserver-xorg is asking about your keyboard because it configures the xserver, not just the graphics elements of it... the input elements too - just go through the process - as long as you've not got some completely weird keyboard attached it'll be fine. 

That should get you to a working desktop... probably no 3d though - you'll then need to set up the nvidia restricted drivers.

---

