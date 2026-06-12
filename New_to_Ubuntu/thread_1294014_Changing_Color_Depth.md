---
title: "Changing Color Depth"
date: 2009-10-17
forum: New to Ubuntu
---

### Post by keyboardbandit on 2009-10-17
[FONT=monospace]I am trying to change my color depth to 24 in Ubuntu 9.04.

I have read around and some people have said that I need to change the color depth value to 24 after entering the following command in the terminal:[/FONT]sudo gedit /etc/xorg.conf

However, after following the command, the file comes up blank with no values to edit...

Anyone know what I should do?  (And is there any GUI way to change the color depth?)

---

### Post by fooman on 2009-10-17
not sure what values your trying to change there,  but the command should be:

```
 gksudo gedit /etc/X11/xorg.conf
```

---

### Post by mbeichorn on 2009-10-17
Sorry, but sudo gedit will work just fine.

The problem is that in ubuntu >= 9.04 xorg.conf is being left blank as using it is being depreciated. (In fact it doesnt exist in karmic at all).

Unfortunately I cannot recall a GUI way to change colors save with the proprietary Nvdia driver and that only works if your graphics are Nvidia.

However, I wonder how you got your graphics to something other than 24 bit, as I believe 24 is the default.

Cheers!

---

### Post by falconindy on 2009-10-17
> **mbeichorn said:**
> Sorry, but sudo gedit will work just fine.

The problem is that in ubuntu >= 9.04 xorg.conf is being left blank as using it is being depreciated. (In fact it doesnt exist in karmic at all).

Unfortunately I cannot recall a GUI way to change colors save with the proprietary Nvdia driver and that only works if your graphics are Nvidia.

However, I wonder how you got your graphics to something other than 24 bit, as I believe 24 is the default.

Cheers!
sudo and gksudo (or gksu) are functionally different. You should **always** use gksu when wanting to launch graphical apps with elevated permissions. Using sudo in place can lead to undesired effects.

Go ahead and try to boot with a blank xorg.conf. Let us know how that works out when you can't use anything but the VESA drivers. fooman is correct that the OP is looking for the config file in the wrong path.

'System -> Preferences -> Display' will provide a graphical interface that should let you change your resolution and color depth. There's no need to go rooting around in xorg.conf.

Oh hey, check this out. It's my xorg.conf from my Karmic install:

```
Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection
```
Getting smaller, but its still there. Please stop spreading misinformation.

---

### Post by fooman on 2009-10-18
> **mbeichorn said:**
> Sorry, but sudo gedit will work just fine.

The problem is that in ubuntu >= 9.04 xorg.conf is being left blank as using it is being depreciated. (In fact it doesnt exist in karmic at all).


well,  sudo gedit *may* work just fine....but then again, * it may not!*  as falconindy has already pointed out....you should play it safe and use gksudo when using a gui text editor such as gedit.  save sudo for using a command line editor such a nano or vi.

here is a link that will explain it better then i can:

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

like i said,  not sure what the op plans on editing there...just wanted to point out the correct path and that gksudo should be used instead of sudo.

and sorry,  i should have said all that in my first post.  :oops:

---

