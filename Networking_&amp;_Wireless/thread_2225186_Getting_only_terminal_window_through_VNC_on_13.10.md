---
title: "Getting only terminal window through VNC on 13.10"
date: 2014-05-20
forum: Networking &amp; Wireless
---

### Post by roeeco on 2014-05-20
Greeting all , been struggling with this one.
Able to vnc from outside but getting only a grey screen with a terminal window, starting /usr/bin/gnome-session from that window also fails.
Router and Firewall ports are open obviously since I can log in, should I open tcp connection for the X-server ?
[U][B]My  ~/.vnc/xstartup
[/B][/U]
```

#!/bin/sh


# Uncomment the following two lines for normal desktop:
unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc


export XKL_XMODMAP_DISABLE=1


[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#x-window-manager &
gnome-session –session=ubuntu-2d &
#gnome-session &



```


[U][B]My VNC log file
[/B][/U]
20/05/14 14:43:12 Xvnc version TightVNC-1.3.9
20/05/14 14:43:12 Copyright (C) 2000-2007 TightVNC Group
20/05/14 14:43:12 Copyright (C) 1999 AT&T Laboratories Cambridge
20/05/14 14:43:12 All Rights Reserved.
20/05/14 14:43:12 See [http://www.tightvnc.com/](http://www.tightvnc.com/) for information on TightVNC
20/05/14 14:43:12 Desktop name 'X' (SkyNet:1)
20/05/14 14:43:12 Protocol versions supported: 3.3, 3.7, 3.8, 3.7t, 3.8t
20/05/14 14:43:12 Listening for VNC connections on TCP port 5901
Font directory '/usr/share/fonts/X11/75dpi/' not found - ignoring
Font directory '/usr/share/fonts/X11/100dpi/' not found - ignoring
No VNC extension on display :1
Option "--login" is no longer supported in this version of gnome-terminal; you might want to create a profile with the desired setting, and use the new '--profile' option
gnome-session-is-accelerated: No composite extension.
gnome-session-check-accelerated: Helper exited with code 256
gnome-session-is-accelerated: No composite extension.
gnome-session-check-accelerated: Helper exited with code 256


** (process:1065): WARNING **: software acceleration check failed: Child process exited with code 1


** (gnome-session:1065): CRITICAL **: We failed, but the fail whale is dead. Sorry....


20/05/14 14:43:18 Got connection from client 212.29.197.186
20/05/14 14:43:18 Using protocol version 3.8
20/05/14 14:43:30 Full-control authentication passed by 212.29.197.186
20/05/14 14:43:30 rfbProcessClientNormalMessage: ignoring unknown encoding 16
20/05/14 14:43:30 rfbProcessClientNormalMessage: ignoring unknown encoding 22
20/05/14 14:43:30 rfbProcessClientNormalMessage: ignoring unknown encoding 21
20/05/14 14:43:30 rfbProcessClientNormalMessage: ignoring unknown encoding 15
20/05/14 14:43:30 Using zlib encoding for client 212.29.197.186
20/05/14 14:43:30 rfbProcessClientNormalMessage: ignoring unknown encoding -311
20/05/14 14:43:30 Enabling full-color cursor updates for client 212.29.197.186
20/05/14 14:43:30 rfbProcessClientNormalMessage: ignoring unknown encoding -223
20/05/14 14:43:30 Pixel format for client 212.29.197.186:
20/05/14 14:43:30   8 bpp, depth 8
20/05/14 14:43:30   uses a colour map (not true colour).
20/05/14 14:43:30 Using raw encoding for client 212.29.197.186
20/05/14 14:43:30 rfbProcessClientNormalMessage: ignoring unknown encoding 22
20/05/14 14:43:30 rfbProcessClientNormalMessage: ignoring unknown encoding 21
20/05/14 14:43:30 rfbProcessClientNormalMessage: ignoring unknown encoding 16
20/05/14 14:43:30 rfbProcessClientNormalMessage: ignoring unknown encoding 15
20/05/14 14:43:30 rfbProcessClientNormalMessage: ignoring unknown encoding -311
20/05/14 14:43:30 Enabling full-color cursor updates for client 212.29.197.186
20/05/14 14:43:30 rfbProcessClientNormalMessage: ignoring unknown encoding -223
20/05/14 14:43:30 rfbProcessClientNormalMessage: ignoring unknown encoding 16
20/05/14 14:43:30 rfbProcessClientNormalMessage: ignoring unknown encoding 22
20/05/14 14:43:30 rfbProcessClientNormalMessage: ignoring unknown encoding 21
20/05/14 14:43:30 rfbProcessClientNormalMessage: ignoring unknown encoding 15
20/05/14 14:43:30 Using zlib encoding for client 212.29.197.186
20/05/14 14:43:30 rfbProcessClientNormalMessage: ignoring unknown encoding -311
20/05/14 14:43:30 Enabling full-color cursor updates for client 212.29.197.186
20/05/14 14:43:30 rfbProcessClientNormalMessage: ignoring unknown encoding -223
20/05/14 14:43:37 KbdAddEvent: unknown KeySym 0xff8d - allocating KeyCode 89

I would thank for your help, it is very frustrating.

---

### Post by steeldriver on 2014-05-20
Have a look at what sessions are actually available (in /usr/share/xsessions) - I don't think the ubuntu-2d session exists in 13.10 (replaced by gnome-fallback?) 

Also you are missing a - from your session syntax, it needs to be

```

gnome-session **--**session=*session-name*

```

You might also want to remove

```

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup

```

(exec replaces the current process i.e. it will cause anything below it to be ignored, I think). Possibly there is no global /etc/vnc/xstartup though in which case it's moot.

---

### Post by roeeco on 2014-05-21
Thanks, I've changed that but still getting the same result.
What should be the session-name ? is it the desktop name? or just session-name?
this is the log file:


21/05/14 09:31:55 Xvnc version TightVNC-1.3.9
21/05/14 09:31:55 Copyright (C) 2000-2007 TightVNC Group
21/05/14 09:31:55 Copyright (C) 1999 AT&T Laboratories Cambridge
21/05/14 09:31:55 All Rights Reserved.
21/05/14 09:31:55 See [http://www.tightvnc.com/](http://www.tightvnc.com/) for information on TightVNC
21/05/14 09:31:55 Desktop name 'X' (SkyNet:1)
21/05/14 09:31:55 Protocol versions supported: 3.3, 3.7, 3.8, 3.7t, 3.8t
21/05/14 09:31:55 Listening for VNC connections on TCP port 5901
Font directory '/usr/share/fonts/X11/75dpi/' not found - ignoring
Font directory '/usr/share/fonts/X11/100dpi/' not found - ignoring
No VNC extension on display :1
Option "--login" is no longer supported in this version of gnome-terminal; you might want to create a profile with the desired setting, and use the new '--profile' option
gnome-session-is-accelerated: No composite extension.
gnome-session-check-accelerated: Helper exited with code 256
gnome-session-is-accelerated: No composite extension.
gnome-session-check-accelerated: Helper exited with code 256


** (process:21681): WARNING **: software acceleration check failed: Child process exited with code 1


** (gnome-session:21681): CRITICAL **: We failed, but the fail whale is dead. Sorry....

---

### Post by jon51 on 2014-05-28
roeeco ... did you ever figure out the issue?

I believe their is a second forum working on the same issue: [http://ubuntuforums.org/showthread.php?t=2221982](http://ubuntuforums.org/showthread.php?t=2221982)

I've used both VNC and Tight VNC and get to the same terminal window ...

Would type startx but my s or d does not work in the terminal window .... agh!

---

### Post by jon51 on 2014-05-28
Got past the s and d and typed startx to get the following:

ubuntu@ip-47:~$ sudo -s startx




X.Org X Server 1.15.1
Release Date: 2014-04-13
X Protocol Version 11, Revision 0
Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
Current Operating System: Linux ip- 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 x86_64
Kernel command line: root=LABEL=cloudimg-rootfs ro console=hvc0 
Build Date: 16 April 2014  01:36:29PM
xorg-server 2:1.15.1-0ubuntu2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.30.2
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed May 28 22:02:11 2014
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
Initializing built-in extension Generic Event Extension
Initializing built-in extension SHAPE
Initializing built-in extension MIT-SHM
Initializing built-in extension XInputExtension
Initializing built-in extension XTEST
Initializing built-in extension BIG-REQUESTS
Initializing built-in extension SYNC
Initializing built-in extension XKEYBOARD
Initializing built-in extension XC-MISC
Initializing built-in extension SECURITY
Initializing built-in extension XINERAMA
Initializing built-in extension XFIXES
Initializing built-in extension RENDER
Initializing built-in extension RANDR
Initializing built-in extension COMPOSITE
Initializing built-in extension DAMAGE
Initializing built-in extension MIT-SCREEN-SAVER
Initializing built-in extension DOUBLE-BUFFER
Initializing built-in extension RECORD
Initializing built-in extension DPMS
Initializing built-in extension Present
Initializing built-in extension DRI3
Initializing built-in extension X-Resource
Initializing built-in extension XVideo
Initializing built-in extension XVideo-MotionCompensation
Initializing built-in extension SELinux
Initializing built-in extension XFree86-VidModeExtension
Initializing built-in extension XFree86-DGA
Initializing built-in extension XFree86-DRI
Initializing built-in extension DRI2
Loading extension GLX
(EE) 
Fatal server error:
(EE) no screens found(EE) 
(EE) 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
(EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
(EE) 
(EE) Server terminated with error (1). Closing log file.
xinit: giving up
xinit: unable to connect to X server: Connection refused
xinit: server error

---

### Post by jon51 on 2014-05-29
Tried these fixes for starting X without any accomplishment ...

[http://ubuntuforums.org/archive/index.php/t-1586633.html](http://ubuntuforums.org/archive/index.php/t-1586633.html)

Any Suggestions?

---

### Post by steeldriver on 2014-05-29
I'm confused - you've posted in a thread about only getting the default xterm/gray root in a VNC session - but you appear to be trying to start a **local** X session (with startx). Can you clarify exactly what you are trying to do?

Is your setup headless (no physical display attached)?

BTW using sudo to startx is a recipe for later problems

---

### Post by jon51 on 2014-05-29
I am trying to get a server GUI through VNC 

Correct the setup is headless ... cloud server

Thanks for the info on sudo startx that must be the reason for the .Xauthority issues ...

---

