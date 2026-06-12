---
title: "How to  set xrdp on Lubuntu 19.10"
date: 2019-11-16
forum: Networking &amp; Wireless
---

### Post by mariofanboy-21 on 2019-11-16
Hello all, can someone help me out in regards to setting up xrdp for Lubuntu 19.10

---

### Post by mariofanboy-21 on 2019-11-19
Hello everyone, shortly after I installed Lubuntu on an old Dell Latitude D430. At this moment, I am struggling  to  get Xrdp and Vnc to properly display the desktop. How can I be able to fix this issue?

---

### Post by uRock on 2019-11-19
Duplicate threads merged. If you find a post is missing information, you can either edit the post or add a second post to clarify intent or specifications.

---

### Post by mariofanboy-21 on 2019-11-19
Thank you very much. However are you able to help me with my issue?

---

### Post by mörgæs on 2019-11-19
If you post a detailed description of what you have tried, preferably with commands and their results, there is a better chance for getting help.

---

### Post by mariofanboy-21 on 2019-11-20
Okay then, here are some of the commands I've used
```
 sudo apt-get install xrdp
          sudo apt-get install xorgxrdp
          sudo apt-get install lxde
          echo "lxsession -s Lubuntu -e LXDE" > ~/.xsession

```

---

### Post by mariofanboy-21 on 2019-11-22
I just posted some of the commands I used to try to get xrdp onto the laptop

---

### Post by mörgæs on 2019-11-22
Yes, I see that but their result is more interesting. Please post the output of 

```
apt-cache policy xrdp xorgxrdp lxde
```

By the way, I don't know xrdp so I am not able to help. I'm asking for these output because they might give someone else an idea.

Which guide are you following?

---

### Post by mariofanboy-21 on 2019-11-22
```
xrdp:  Installed: 0.9.9-1
  Candidate: 0.9.9-1
  Version table:
 *** 0.9.9-1 500
        500 http://archive.ubuntu.com/ubuntu eoan/universe amd64 Packages
        100 /var/lib/dpkg/status
xorgxrdp:
  Installed: 1:0.2.9-1
  Candidate: 1:0.2.9-1
  Version table:
 *** 1:0.2.9-1 500
        500 http://archive.ubuntu.com/ubuntu eoan/universe amd64 Packages
        100 /var/lib/dpkg/status
lxde:
  Installed: 10
  Candidate: 10
  Version table:
 *** 10 500
        500 http://archive.ubuntu.com/ubuntu eoan/universe amd64 Packages
        100 /var/lib/dpkg/status

```
I am also following this guide. 
[http://c-nergy.be/blog/?p=11336](http://c-nergy.be/blog/?p=11336)

---

### Post by 0x656b694d on 2019-11-23
Hello,

I installed xrdp on one of my machines (19.10) from the repo and it worked fine after I updated /etc/xrdp/sesman.ini with:

```

[Xorg] 
...
param=/usr/lib/xorg/Xorg
```

I didn't have sound forwarded so I removed everything and installed from sources, including the xrdp pulseaudio modules. Now everything works with this machine.

With the other remote machine (also 19.10) and with the default fresh xrdp installation from the repo I don't manage to launch the session: the window manager crashes right after I enter credentials.

So I'm still investigating what's wrong with the second installation.

---

### Post by guiverc on 2019-11-24
I don't see an '-e' option in `lxsession` ([http://manpages.ubuntu.com/manpages/eoan/man1/lxsession.1.html](http://manpages.ubuntu.com/manpages/eoan/man1/lxsession.1.html)) so I don't know what it does, but in your `echo` command I would not have called it Lubuntu; as Lubuntu now refers to LXQt (18.10 up), thus I'm unsure if you'll have clashes as you're trying **not** to use the Lubuntu (LXQt) desktop - but use LXDE. 

 ie. I would have adjusted your commands to match you're using a LXQt based Lubuntu instead of Ubuntu server/gnome 17.10 the instructions were geared for.  It's possible the Lubuntu in your 'echo' is only a text label which does nothing, but I can't advise sorry.

---

### Post by 0x656b694d on 2019-11-24
On the client side, the Windows tool worked straight away, but in Remmina I had to enable two options in the advanced settings: Relax Order Checks and Glyph Cache.

---

### Post by mariofanboy-21 on 2019-11-27
Took me a while to figure out what to do in 18.04

---

### Post by mariofanboy-21 on 2019-11-27
Who can I contact to help me with this?

---

### Post by #&amp;thj^% on 2019-11-27
> **mariofanboy-21 said:**
> Who can I contact to help me with this?

If it worked on 18.04 then it will work just as it did on 19.10.

First open a terminal and enter:
 ```
sudo apt-get install xrdp
```
 When that is installed enter:
```
sudoedit  /etc/xrdp/startwm.sh
``` 
in the terminal.** Make sure the last line looks like this:**
```

. /etc/X11/Xsession
```

Then go to your home folder, rightclick and select Show hidden. If there is no file named .xsession, create it. If there is a filed named like that, open it and make sure that it looks like this when your done: 
```
lxsession -e LXDE -s Lubuntu
```

Now enter
```
sudo service xrdp restart
```
in the terminal to restart xrdp. Now it should work :)

---

### Post by mariofanboy-21 on 2019-11-29
Tried that,  got a blak screen with an x for a cursor

---

### Post by #&amp;thj^% on 2019-12-03
I would check a few things then:
```
sudoedit  /etc/xrdp/startwm.sh

```
If all is not right here, it will fail.
Also did you upgrade to 19.10, or is this a clean install?
Some have had better luck with buliding from the source's, shown by user 0x656b694d post#12
Also be sure this looks ok:
```
sudo nano /etc/xrdp/xrdp.ini
```

Add the following line at the end of the file:/etc/xrdp/xrdp.ini

```

exec startxfce4
``` 
Add your session in place of xfce4.

Save the file and restart the Xrdp service:
```

sudo systemctl restart xrdp
```
Please paste back any errors, so we can have a look.

Mine:
```
systemctl status xrdp
&#9679; xrdp.service - xrdp daemon
   Loaded: loaded (/usr/lib/systemd/system/xrdp.service; disabled; vendor prese>
   Active: active (running) since Tue 2019-12-03 11:53:33 MST; 6s ago
     Docs: man:xrdp(8)
           man:xrdp.ini(5)
  Process: 189823 ExecStart=/usr/bin/xrdp (code=exited, status=0/SUCCESS)
 Main PID: 189824 (xrdp)
    Tasks: 1 (limit: 13974)
   Memory: 2.0M
   CGroup: /system.slice/xrdp.service
           &#9492;&#9472;189824 /usr/bin/xrdp

Dec 03 11:53:32 arch systemd[1]: Starting xrdp daemon...
Dec 03 11:53:32 arch xrdp[189823]: (189823)(109763011483840)[DEBUG] Testing if >
Dec 03 11:53:32 arch xrdp[189823]: (189823)(109763011483840)[DEBUG] Closed sock>
Dec 03 11:53:32 arch systemd[1]: xrdp.service: Can't open PID file /run/xrdp.pi>
Dec 03 11:53:33 arch systemd[1]: Started xrdp daemon.
Dec 03 11:53:34 arch xrdp[189824]: (189824)(109763011483840)[INFO ] starting xr>
Dec 03 11:53:34 arch xrdp[189824]: (189824)(109763011483840)[INFO ] listening t>


```
Also:
```
Xvnc :1

Xvnc TigerVNC 1.9.0 - built Jun 30 2019 10:05:48
Copyright (C) 1999-2018 TigerVNC Team and many others (see README.rst)
See http://www.tigervnc.org for information on TigerVNC.
Underlying X server release 12005000, The X.Org Foundation


Tue Dec  3 11:47:56 2019
 vncext:      VNC extension running!
 vncext:      Listening for VNC connections on all interface(s), port 5901
 vncext:      created VNC server for screen 0

```

---

### Post by mariofanboy-21 on 2019-12-03
Here is the code I'm using```
#!/bin/sh# xrdp X session start script (c) 2015, 2017 mirabilos
# published under The MirOS Licence


if test -r /etc/profile; then
	. /etc/profile
fi


if test -r /etc/default/locale; then
	. /etc/default/locale
	test -z "${LANG+x}" || export LANG
	test -z "${LANGUAGE+x}" || export LANGUAGE
	test -z "${LC_ADDRESS+x}" || export LC_ADDRESS
	test -z "${LC_ALL+x}" || export LC_ALL
	test -z "${LC_COLLATE+x}" || export LC_COLLATE
	test -z "${LC_CTYPE+x}" || export LC_CTYPE
	test -z "${LC_IDENTIFICATION+x}" || export LC_IDENTIFICATION
	test -z "${LC_MEASUREMENT+x}" || export LC_MEASUREMENT
	test -z "${LC_MESSAGES+x}" || export LC_MESSAGES
	test -z "${LC_MONETARY+x}" || export LC_MONETARY
	test -z "${LC_NAME+x}" || export LC_NAME
	test -z "${LC_NUMERIC+x}" || export LC_NUMERIC
	test -z "${LC_PAPER+x}" || export LC_PAPER
	test -z "${LC_TELEPHONE+x}" || export LC_TELEPHONE
	test -z "${LC_TIME+x}" || export LC_TIME
	test -z "${LOCPATH+x}" || export LOCPATH
fi


if test -r /etc/profile; then
	. /etc/profile
fi


test -x /etc/X11/Xsession && exec /etc/X11/Xsession
exec /bin/sh /etc/X11/Xsession


. /etc/X11/Xsession



```


Since I use LXDE for remote desktop I wiull use the code  ```
[[COLOR=#000000][FONT=&quot]exec LXDE[/FONT][/COLOR]/CODE]

For xordxrdp codg

[CODE][ 13578.793] X.Org X Server 1.20.5
X Protocol Version 11, Revision 0
[ 13578.793] Build Operating System: Linux 4.4.0-165-generic x86_64 Ubuntu
[ 13578.793] Current Operating System: Linux cardinlatitude-pc 5.3.0-23-generic #25-Ubuntu SMP Tue Nov 12 09:22:33 UTC 2019 x86_64
[ 13578.793] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-5.3.0-23-generic root=UUID=8e7de9b6-35f2-4234-8cb1-2078a2ee465e ro quiet splash resume=UUID=0d48751d-95ad-4183-a2fc-dc7994016e03 vt.handoff=7
[ 13578.793] Build Date: 08 October 2019  09:43:30AM
[ 13578.793] xorg-server 2:1.20.5+git20191008-0ubuntu1 (For technical support please see http://www.ubuntu.com/support) 
[ 13578.793] Current version of pixman: 0.38.4
[ 13578.793] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[ 13578.793] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[ 13578.793] (++) Log file: ".xorgxrdp.10.log", Time: Tue Dec  3 22:41:02 2019
[ 13579.097] (++) Using config file: "/etc/X11/xrdp/xorg.conf"
[ 13579.097] (==) Using config directory: "/etc/X11/xorg.conf.d"
[ 13579.097] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[ 13579.361] (==) ServerLayout "X11 Server"
[ 13579.361] (**) |-->Screen "Screen (xrdpdev)" (0)
[ 13579.361] (**) |   |-->Monitor "Monitor"
[ 13579.362] (**) |   |-->Device "Video Card (xrdpdev)"
[ 13579.363] (**) |-->Input Device "xrdpMouse"
[ 13579.363] (**) |-->Input Device "xrdpKeyboard"
[ 13579.363] (**) Option "DontVTSwitch" "on"
[ 13579.363] (**) Option "AutoAddDevices" "off"
[ 13579.363] (**) Not automatically adding devices
[ 13579.363] (==) Automatically enabling devices
[ 13579.363] (==) Automatically adding GPU devices
[ 13579.363] (==) Automatically binding GPU devices
[ 13579.363] (==) Max clients allowed: 256, resource mask: 0x1fffff
[ 13579.453] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[ 13579.453] 	Entry deleted from font path.
[ 13579.453] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[ 13579.453] 	Entry deleted from font path.
[ 13579.453] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[ 13579.453] 	Entry deleted from font path.
[ 13579.453] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[ 13579.455] 	Entry deleted from font path.
[ 13579.455] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[ 13579.455] 	Entry deleted from font path.
[ 13579.455] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[ 13579.456] (==) ModulePath set to "/usr/lib/xorg/modules"
[ 13579.456] (II) Loader magic: 0x5567ad5b7020
[ 13579.456] (II) Module ABI versions:
[ 13579.456] 	X.Org ANSI C Emulation: 0.4
[ 13579.456] 	X.Org Video Driver: 24.0
[ 13579.456] 	X.Org XInput driver : 24.1
[ 13579.456] 	X.Org Server Extension : 10.0
[ 13579.469] (II) systemd-logind: took control of session /org/freedesktop/login1/session/c3
[ 13579.742] (II) xfree86: Adding drm device (/dev/dri/card0)
[ 13579.757] (EE) systemd-logind: failed to take device /dev/dri/card0: Operation not permitted
[ 13579.758] (EE) /dev/dri/card0: failed to set DRM interface version 1.4: Permission denied
[ 13579.769] (--) PCI:*(0@0:2:0) 8086:27a2:1028:0201 rev 3, Mem @ 0xeff00000/524288, 0xd0000000/268435456, 0xefec0000/262144, I/O @ 0x0000eff8/8, BIOS @ 0x????????/131072
[ 13579.770] (--) PCI: (0@0:2:1) 8086:27a6:1028:0201 rev 3, Mem @ 0xeff80000/524288
[ 13579.770] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[ 13579.770] (II) LoadModule: "dbe"
[ 13579.770] (II) Module "dbe" already built-in
[ 13579.770] (II) LoadModule: "ddc"
[ 13579.770] (II) Module "ddc" already built-in
[ 13579.770] (II) LoadModule: "extmod"
[ 13579.770] (II) Module "extmod" already built-in
[ 13579.770] (II) LoadModule: "glx"
[ 13579.905] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[ 13579.953] (II) Module glx: vendor="X.Org Foundation"
[ 13579.954] 	compiled for 1.20.5, module version = 1.0.0
[ 13579.954] 	ABI class: X.Org Server Extension, version 10.0
[ 13579.954] (II) LoadModule: "int10"
[ 13579.954] (II) Loading /usr/lib/xorg/modules/libint10.so
[ 13580.052] (II) Module int10: vendor="X.Org Foundation"
[ 13580.052] 	compiled for 1.20.5, module version = 1.0.0
[ 13580.052] 	ABI class: X.Org Video Driver, version 24.0
[ 13580.052] (II) LoadModule: "record"
[ 13580.052] (II) Module "record" already built-in
[ 13580.052] (II) LoadModule: "vbe"
[ 13580.052] (II) Loading /usr/lib/xorg/modules/libvbe.so
[ 13580.082] (II) Module vbe: vendor="X.Org Foundation"
[ 13580.082] 	compiled for 1.20.5, module version = 1.1.0
[ 13580.082] 	ABI class: X.Org Video Driver, version 24.0
[ 13580.082] (II) LoadModule: "xorgxrdp"
[ 13580.082] (II) Loading /usr/lib/xorg/modules/libxorgxrdp.so
[ 13580.177] (II) Module XORGXRDP: vendor="X.Org Foundation"
[ 13580.178] 	compiled for 1.20.3, module version = 0.2.9
[ 13580.178] 	ABI class: X.Org Video Driver, version 24.0
[ 13580.178] xorgxrdpSetup:
[ 13580.178] (II) LoadModule: "fb"
[ 13580.178] (II) Loading /usr/lib/xorg/modules/libfb.so
[ 13580.275] (II) Module fb: vendor="X.Org Foundation"
[ 13580.275] 	compiled for 1.20.5, module version = 1.0.0
[ 13580.275] 	ABI class: X.Org ANSI C Emulation, version 0.4
[ 13580.275] (II) LoadModule: "xrdpdev"
[ 13580.276] (II) Loading /usr/lib/xorg/modules/drivers/xrdpdev_drv.so
[ 13580.304] (II) Module XRDPDEV: vendor="X.Org Foundation"
[ 13580.304] 	compiled for 1.20.3, module version = 0.2.9
[ 13580.304] 	ABI class: X.Org Video Driver, version 24.0
[ 13580.304] xrdpdevSetup:
[ 13580.305] (II) LoadModule: "xrdpmouse"
[ 13580.306] (II) Loading /usr/lib/xorg/modules/input/xrdpmouse_drv.so
[ 13580.307] (II) Module XRDPMOUSE: vendor="X.Org Foundation"
[ 13580.307] 	compiled for 1.20.3, module version = 0.2.9
[ 13580.307] 	Module class: X.Org XInput Driver
[ 13580.307] 	ABI class: X.Org XInput driver, version 24.1
[ 13580.307] rdpmousePlug:
[ 13580.307] (II) LoadModule: "xrdpkeyb"
[ 13580.308] (II) Loading /usr/lib/xorg/modules/input/xrdpkeyb_drv.so
[ 13580.309] (II) Module XRDPKEYB: vendor="X.Org Foundation"
[ 13580.309] 	compiled for 1.20.3, module version = 0.2.9
[ 13580.309] 	Module class: X.Org XInput Driver
[ 13580.309] 	ABI class: X.Org XInput driver, version 24.1
[ 13580.309] rdpkeybPlug:
[ 13580.309] rdpIdentify:
[ 13580.309] (II) XRDPDEV: driver for xrdp: XRDPDEV
[ 13580.309] rdpDriverFunc: op 10
[ 13580.309] (WW) Falling back to old probe method for XRDPDEV
[ 13580.309] rdpProbe:
[ 13580.310] (II) Loading sub module "fb"
[ 13580.310] (II) LoadModule: "fb"
[ 13580.310] (II) Loading /usr/lib/xorg/modules/libfb.so
[ 13580.310] (II) Module fb: vendor="X.Org Foundation"
[ 13580.310] 	compiled for 1.20.5, module version = 1.0.0
[ 13580.310] 	ABI class: X.Org ANSI C Emulation, version 0.4
[ 13580.310] (II) XRDPDEV(0): using default device
[ 13580.310] (WW) VGA arbiter: cannot open kernel arbiter, no multi-card support
[ 13580.310] rdpPreInit:
[ 13580.310] (**) XRDPDEV(0): Depth 24, (--) framebuffer bpp 32
[ 13580.310] (==) XRDPDEV(0): RGB weight 888
[ 13580.310] (==) XRDPDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[ 13580.311] (==) XRDPDEV(0): Default visual is TrueColor
[ 13580.311] (==) XRDPDEV(0): DPI set to (96, 96)
[ 13580.311] (II) XRDPDEV(0): 	mode "640x480" ok
[ 13580.311] (II) XRDPDEV(0): 	mode "800x600" ok
[ 13580.311] (II) XRDPDEV(0): Virtual size is 800x600 (pitch 800)
[ 13580.311] (**) XRDPDEV(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.2 Hz
[ 13580.311] (II) XRDPDEV(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz d)
[ 13580.311] rdpScreenInit: virtualX 800 virtualY 600 rgbBits 8 depth 24
[ 13580.311] rdpScreenInit: pfbMemory bytes 1920000
[ 13580.311] rdpScreenInit: pfbMemory 0x7f950f416010
[ 13580.311] rdpSimdInit: assigning yuv functions
[ 13580.311] rdpSimdInit: cpuid ax 1 cx 0 return ax 0x000006f2 bx 0x00020800 cx 0x0000e3bd dx 0xbfebfbff
[ 13580.311] rdpSimdInit: sse2 amd64 yuv functions assigned
[ 13580.311] rdpXvInit: depth 24
[ 13580.311] (==) XRDPDEV(0): Backing store enabled
[ 13580.312] rdpClientConInit: disconnect idle session after [0] sec
[ 13580.312] rdpClientConInit: kill disconnected [0] timeout [0] sec
[ 13580.312] rdpScreenInit: out
[ 13580.312] (II) Initializing extension Generic Event Extension
[ 13580.313] (II) Initializing extension SHAPE
[ 13580.313] (II) Initializing extension MIT-SHM
[ 13580.314] (II) Initializing extension XInputExtension
[ 13580.314] (II) Initializing extension XTEST
[ 13580.315] (II) Initializing extension BIG-REQUESTS
[ 13580.315] (II) Initializing extension SYNC
[ 13580.316] (II) Initializing extension XKEYBOARD
[ 13580.316] (II) Initializing extension XC-MISC
[ 13580.317] (II) Initializing extension SECURITY
[ 13580.317] (II) Initializing extension XFIXES
[ 13580.318] (II) Initializing extension RENDER
[ 13580.318] (II) Initializing extension RANDR
[ 13580.319] (II) Initializing extension COMPOSITE
[ 13580.319] (II) Initializing extension DAMAGE
[ 13580.320] (II) Initializing extension MIT-SCREEN-SAVER
[ 13580.339] (II) Initializing extension DOUBLE-BUFFER
[ 13580.340] (II) Initializing extension RECORD
[ 13580.340] (II) Initializing extension DPMS
[ 13580.340] (II) Initializing extension Present
[ 13580.341] (II) Initializing extension DRI3
[ 13580.341] (II) Initializing extension X-Resource
[ 13580.341] (II) Initializing extension XVideo
[ 13580.342] (II) Initializing extension XVideo-MotionCompensation
[ 13580.342] (II) Initializing extension SELinux
[ 13580.342] (II) SELinux: Disabled on system
[ 13580.342] (II) Initializing extension GLX
[ 13580.343] (II) AIGLX: Screen 0 is not DRI2 capable
[ 13583.941] (II) IGLX: Loaded and initialized swrast
[ 13583.942] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[ 13583.942] (II) Initializing extension XFree86-VidModeExtension
[ 13583.943] (II) Initializing extension XFree86-DGA
[ 13583.944] (II) Initializing extension XFree86-DRI
[ 13583.944] (II) Initializing extension DRI2
[ 13584.541] (II) Using input driver 'XRDPMOUSE' for 'xrdpMouse'
[ 13584.542] (**) Option "CorePointer"
[ 13584.542] (**) xrdpMouse: always reports core events
[ 13584.542] rdpmousePreInit: drv 0x5567aedc1260 info 0x5567af081210, flags 0x0
[ 13584.542] (II) XINPUT: Adding extended input device "xrdpMouse" (type: Mouse, id 6)
[ 13584.542] rdpmouseControl: what 0
[ 13584.542] rdpmouseDeviceInit:
[ 13584.557] rdpmouseCtrl:
[ 13584.557] rdpRegisterInputCallback: type 1 proc 0x7f951079e370
[ 13584.557] (**) xrdpMouse: (accel) keeping acceleration scheme 1
[ 13584.557] (**) xrdpMouse: (accel) acceleration profile 0
[ 13584.558] (**) xrdpMouse: (accel) acceleration factor: 2.000
[ 13584.558] (**) xrdpMouse: (accel) acceleration threshold: 4
[ 13584.558] rdpmouseControl: what 1
[ 13584.558] rdpmouseDeviceOn:
[ 13584.559] (II) Using input driver 'XRDPKEYB' for 'xrdpKeyboard'
[ 13584.559] (**) Option "CoreKeyboard"
[ 13584.559] (**) xrdpKeyboard: always reports core events
[ 13584.559] rdpkeybPreInit: drv 0x5567aedc0a90 info 0x5567af083d40, flags 0x0
[ 13584.559] (II) XINPUT: Adding extended input device "xrdpKeyboard" (type: Keyboard, id 7)
[ 13584.559] rdpkeybControl: what 0
[ 13584.559] rdpkeybDeviceInit:
[ 13584.610] rdpkeybChangeKeyboardControl:
[ 13584.610] rdpkeybChangeKeyboardControl: autoRepeat on
[ 13584.610] rdpRegisterInputCallback: type 0 proc 0x7f950f945a50
[ 13584.610] rdpkeybControl: what 1
[ 13584.610] rdpkeybDeviceOn:
[ 13584.949] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[ 13584.950] (II) AutoAddDevices is off - not adding device.
[ 13584.951] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[ 13584.952] (II) AutoAddDevices is off - not adding device.
[ 13584.953] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[ 13584.953] (II) AutoAddDevices is off - not adding device.
[ 13584.955] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[ 13584.955] (II) AutoAddDevices is off - not adding device.
[ 13584.955] (II) config/udev: Adding drm device (/dev/dri/card0)
[ 13584.955] (II) xfree86: Adding drm device (/dev/dri/card0)
[ 13584.957] (EE) systemd-logind: failed to take device /dev/dri/card0: Operation not permitted
[ 13584.957] (EE) /dev/dri/card0: failed to set DRM interface version 1.4: Permission denied
[ 13584.960] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event9)
[ 13584.960] (II) AutoAddDevices is off - not adding device.
[ 13584.962] (II) config/udev: Adding input device HDA Intel Mic (/dev/input/event8)
[ 13584.962] (II) AutoAddDevices is off - not adding device.
[ 13584.964] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event7)
[ 13584.964] (II) AutoAddDevices is off - not adding device.
[ 13584.966] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[ 13584.967] (II) AutoAddDevices is off - not adding device.
[ 13584.968] (II) config/udev: Adding input device AlpsPS/2 ALPS DualPoint TouchPad (/dev/input/event6)
[ 13584.969] (II) AutoAddDevices is off - not adding device.
[ 13584.970] (II) config/udev: Adding input device AlpsPS/2 ALPS DualPoint TouchPad (/dev/input/mouse1)
[ 13584.970] (II) AutoAddDevices is off - not adding device.
[ 13584.972] (II) config/udev: Adding input device AlpsPS/2 ALPS DualPoint Stick (/dev/input/event5)
[ 13584.972] (II) AutoAddDevices is off - not adding device.
[ 13584.973] (II) config/udev: Adding input device AlpsPS/2 ALPS DualPoint Stick (/dev/input/mouse0)
[ 13584.974] (II) AutoAddDevices is off - not adding device.
[ 13584.997] rdpSaveScreen:
[ 13584.998] rdpDeferredRandR:
[ 13584.998] rdpResizeSession: width 1024 height 768
[ 13584.998]   calling RRScreenSizeSet
[ 13584.998] rdpRRScreenSetSize: width 1024 height 768 mmWidth 271 mmHeight 203
[ 13584.998] rdpRRGetInfo:
[ 13584.998]   screen resized to 1024x768
[ 13585.004]   RRScreenSizeSet ok 1
[ 13585.005] rdpResizeSession: width 1364 height 768
[ 13585.005]   calling RRScreenSizeSet
[ 13585.005] rdpRRScreenSetSize: width 1364 height 768 mmWidth 361 mmHeight 203
[ 13585.005] rdpRRGetInfo:
[ 13585.006]   screen resized to 1364x768
[ 13585.013]   RRScreenSizeSet ok 1
[ 13585.013] rdpInDeferredRepeatCallback:
[ 13585.013] rdpkeybChangeKeyboardControl:
[ 13585.013] rdpkeybChangeKeyboardControl: autoRepeat off
[ 13585.013] rdpClientConGotConnection:
[ 13585.014] rdpClientConGotConnection: g_sck_accept ok new_sck 7
[ 13585.014] rdpClientConGetConnection: idle_disconnect_timeout set to non-positive value, idle timer turned off
[ 13585.014] rdpAddClientConToDev: adding first clientCon 0x5567af0d8b50
[ 13585.014] rdpClientConProcessMsgVersion: version 0 0 0 1
[ 13585.017] rdpClientConProcessScreenSizeMsg: set width 1364 height 768 bpp 32
[ 13585.017] rdpClientConProcessScreenSizeMsg: shmemid 57 shmemptr 0x7f94fb801000
[ 13585.017] rdpClientConProcessMsgClientInput: invalidate x 0 y 0 cx 1364 cy 768
[ 13585.017] rdpClientConProcessMsgClientInfo:
[ 13585.017]   got client info bytes 5744
[ 13585.017]   jpeg support 0
[ 13585.017]   offscreen support 1
[ 13585.017]   offscreen size 10485760
[ 13585.017]   offscreen entries 100
[ 13585.017]   client can not do offscreen to offscreen blits
[ 13585.017]   client can do new(color) cursor
[ 13585.017]   client can not do multimon
[ 13585.017] rdpRRSetRdpOutputs: numCrtcs 0 monitorCount 0
[ 13585.018] rdpRRSetRdpOutputs: add output 0 left 0 top 0 width 1364 height 768
[ 13585.018] rdpLoadLayout: keylayout 0x00000409 variant  display 10
[ 13585.018] rdpkeybChangeKeyboardControl:
[ 13585.018] rdpkeybChangeKeyboardControl: autoRepeat on
[ 13585.019] rdpkeybChangeKeyboardControl:
[ 13585.019] rdpkeybChangeKeyboardControl: autoRepeat on
[ 13585.118] rdpInDeferredRepeatCallback:
[ 13585.119] rdpkeybChangeKeyboardControl:
[ 13585.119] rdpkeybChangeKeyboardControl: autoRepeat off
[ 13585.119] rdpInDeferredRepeatCallback:
[ 13585.119] rdpkeybChangeKeyboardControl:
[ 13585.119] rdpkeybChangeKeyboardControl: autoRepeat off
[ 13588.030] rdpkeybChangeKeyboardControl:
[ 13588.031] rdpkeybChangeKeyboardControl: autoRepeat off
[ 13588.031] rdpkeybChangeKeyboardControl:
[ 13588.031] rdpkeybChangeKeyboardControl: autoRepeat off
[ 13589.786] rdpRRCrtcGetGamma: 0x5567af0bb540 0x5567af0c2d40 0x5567af0c3140 0x5567af0c2f40
[ 13589.787] rdpRRCrtcGetGamma: 0x5567af0bb540 0x5567af0c2d40 0x5567af0c3140 0x5567af0c2f40
[ 13692.099] rdpClientConRecv: g_sck_recv failed(returned 0)
[ 13692.099] rdpClientConRecvMsg: error
[ 13692.099] rdpClientConCheck: rdpClientConGotData failed
[ 13692.099] rdpClientConDisconnect:
[ 13692.099] rdpRemoveClientConFromDev: removing clientCon 0x5567af0d8b50



```

---

### Post by #&amp;thj^% on 2019-12-04
My code is different as shown:
```
#!/usr/bin/env bash
#
# This script is an example. You might need to edit this script
# depending on your distro if it doesn't work for you.
#
# Uncomment the following line for debug:
# exec xterm


# Execution sequence for interactive login shell - pseudocode
#
# IF /etc/profile is readable THEN
#     execute ~/.bash_profile
# END IF
# IF ~/.bash_profile is readable THEN
#     execute ~/.bash_profile
# ELSE
#     IF ~/.bash_login is readable THEN
#         execute ~/.bash_login
#     ELSE
#         IF ~/.profile is readable THEN
#             execute ~/.profile
#         END IF
#     END IF
# END IF
pre_start()
{
  if [ -r /etc/profile ]; then
    . /etc/profile
  fi
  if [ -r ~/.bash_profile ]; then
    . ~/.bash_profile
  else
    if [ -r ~/.bash_login ]; then
      . ~/.bash_login
    else
      if [ -r ~/.profile ]; then
        . ~/.profile
      fi
    fi
  fi
  return 0
}

# When loging out from the interactive shell, the execution sequence is:
#
# IF ~/.bash_logout exists THEN
#     execute ~/.bash_logout
# END IF
post_start()
{
  if [ -r ~/.bash_logout ]; then
    . ~/.bash_logout
  fi
  return 0
}

#start the window manager
wm_start()
{
  if [ -r /etc/locale.conf ]; then
    . /etc/locale.conf
    export LANG LANGUAGE
  fi

  # arch user
  if [ -r ~/.xinitrc ]; then
    . ~/.xinitrc
    exit 0
  fi
  # arch
  if [ -r /etc/X11/xinit/xinitrc ]; then
    . /etc/X11/xinit/xinitrc
    exit 0
  fi

  # debian
  if [ -r /etc/X11/Xsession ]; then
    pre_start
    . /etc/X11/Xsession
    post_start
    exit 0
  fi

  # el
  if [ -r /etc/X11/xinit/Xsession ]; then
    pre_start
    . /etc/X11/xinit/Xsession
    post_start
    exit 0
  fi

  # suse
  if [ -r /etc/X11/xdm/Xsession ]; then
    # since the following script run a user login shell,
    # do not execute the pseudo login shell scripts
    . /etc/X11/xdm/Xsession
    exit 0
  fi

  pre_start
  xterm
  post_start
}

#. /etc/environment
#export PATH=$PATH
#export LANG=$LANG

# change PATH to be what your environment needs usually what is in
# /etc/environment
#PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
#export PATH=$PATH

# for PATH and LANG from /etc/environment
# pam will auto process the environment file if /etc/pam.d/xrdp-sesman
# includes
# auth       required     pam_env.so readenv=1

wm_start

. /etc/X11/Xsession
#!/bin/sh

if [ -r /etc/default/locale ]; then
  . /etc/default/locale
  export LANG LANGUAGE
fi

startmate-session

exit 1
```
And you did not give me the output from:
```
sudo systemctl restart xrdp
```
It might shed some light to go on.

---

### Post by mariofanboy-21 on 2019-12-14
This is the code of ```
[COLOR=#000000][FONT=&amp]sudo systemctl restart xrdp[/FONT][/COLOR]
```

[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]```
&#9679; xrdp.service - xrdp daemon   Loaded: loaded (/lib/systemd/system/xrdp.service; enabled; vendor preset: enabled)
   Active: active (running) since Sat 2019-12-14 07:25:29 AST; 1h 20min ago
     Docs: man:xrdp(8)
           man:xrdp.ini(5)
  Process: 17706 ExecStartPre=/bin/sh /usr/share/xrdp/socksetup (code=exited, status=0/SUCCESS)
  Process: 17714 ExecStart=/usr/sbin/xrdp $XRDP_OPTIONS (code=exited, status=0/SUCCESS)
 Main PID: 17715 (xrdp)
    Tasks: 1 (limit: 1663)
   Memory: 1.3M
   CGroup: /system.slice/xrdp.service
           &#9492;&#9472;17715 /usr/sbin/xrdp


Dec 14 07:25:27 cardinlatitude-pc systemd[1]: Starting xrdp daemon...
Dec 14 07:25:28 cardinlatitude-pc xrdp[17714]: (17714)(140652451698496)[DEBUG] Testing if xrdp can l
Dec 14 07:25:28 cardinlatitude-pc xrdp[17714]: (17714)(140652451698496)[DEBUG] Closed socket 7 (AF_I
Dec 14 07:25:28 cardinlatitude-pc systemd[1]: xrdp.service: Can't open PID file /run/xrdp/xrdp.pid (
Dec 14 07:25:29 cardinlatitude-pc systemd[1]: Started xrdp daemon.
Dec 14 07:25:30 cardinlatitude-pc xrdp[17715]: (17715)(140652451698496)[INFO ] starting xrdp with pi
Dec 14 07:25:30 cardinlatitude-pc xrdp[17715]: (17715)(140652451698496)[INFO ] listening to port 338
lines 1-20/20 (END)...skipping...
&#9679; xrdp.service - xrdp daemon
   Loaded: loaded (/lib/systemd/system/xrdp.service; enabled; vendor preset: enabled)
   Active: active (running) since Sat 2019-12-14 07:25:29 AST; 1h 20min ago
     Docs: man:xrdp(8)
           man:xrdp.ini(5)
  Process: 17706 ExecStartPre=/bin/sh /usr/share/xrdp/socksetup (code=exited, status=0/SUCCESS)
  Process: 17714 ExecStart=/usr/sbin/xrdp $XRDP_OPTIONS (code=exited, status=0/SUCCESS)
 Main PID: 17715 (xrdp)
    Tasks: 1 (limit: 1663)
   Memory: 1.3M
   CGroup: /system.slice/xrdp.service
           &#9492;&#9472;17715 /usr/sbin/xrdp


Dec 14 07:25:27 cardinlatitude-pc systemd[1]: Starting xrdp daemon...
Dec 14 07:25:28 cardinlatitude-pc xrdp[17714]: (17714)(140652451698496)[DEBUG] Testing if xrdp can listen on 0.0.0.0 port 3389.
Dec 14 07:25:28 cardinlatitude-pc xrdp[17714]: (17714)(140652451698496)[DEBUG] Closed socket 7 (AF_INET6 :: port 3389)
Dec 14 07:25:28 cardinlatitude-pc systemd[1]: xrdp.service: Can't open PID file /run/xrdp/xrdp.pid (yet?) after start: No such file or directory
Dec 14 07:25:29 cardinlatitude-pc systemd[1]: Started xrdp daemon.
Dec 14 07:25:30 cardinlatitude-pc xrdp[17715]: (17715)(140652451698496)[INFO ] starting xrdp with pid 17715
Dec 14 07:25:30 cardinlatitude-pc xrdp[17715]: (17715)(140652451698496)[INFO ] listening to port 3389 on 0.0.0.0

~
```[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]

---

