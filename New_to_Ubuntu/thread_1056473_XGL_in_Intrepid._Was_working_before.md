---
title: "XGL in Intrepid. Was working before"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by marko_4454 on 2009-01-31
So, my computer turned off due to power failure. I turned it back on and compiz/XGL was gone. I uninstalled all the Drivers for my ATI X600 card as well as all compiz related packages. After that, I get the following semi-successful commands: 

```

marco@marco-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X600 Series
OpenGL version string: 2.1.8087 Release

```

```
marco@marco-desktop:~$ glxinfo | grep direct
direct rendering: Yes

```

```
marco@marco-desktop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 

```


So, XGL seems to be the problem when I run compiz. My X.org file is the following: 
```

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
	Driver	"fglrx"
EndSection

```

I am pretty close, however, compiz doesnt seem to open up correctly. Any help? 
Thanks

---

### Post by mjheagle8 on 2009-01-31
did you try starting xgl in the terminal?

---

### Post by marko_4454 on 2009-01-31
> **mjheagle8 said:**
> did you try starting xgl in the terminal?

The thing is that the package xserver-xgl has been retired, so you cant really install it anymore. So I dont know what to do.
If I run xgl it just cant find the xgl:
```
marco@marco-desktop:~$ xgl
bash: xgl: command not found

```

---

### Post by marko_4454 on 2009-02-03
Anyone else that can help?

---

### Post by markbuntu on 2009-02-03
First of all, xserver-xgl will break the fglrx driver so forget about that, it has not worked since Hardy came out. Compiz does not need it with Intrepid anyway.


You should be having no problems with compiz and fglrx. 
Which ati driver are you using?
Where did you get it from?
Did you edit your xorg.conf?

You should try the new 9.1 driver from ati, it fixes pretty much all the compiz issues from previous drivers.

---

### Post by marko_4454 on 2009-02-03
Thanks mark. So after you said that, I went ahead and removed all the compiz packages (pretty much everything, even decorator). I installed it again, using a website for instructions to avoid missing any package and now it works. 
I think I was just missing a package or something like that. I am just happy it works. 
Thanks a lot!

---

