---
title: "Newest kernel module update broke VNC?"
date: 2008-02-14
forum: Networking &amp; Wireless
---

### Post by SadaraX on 2008-02-14
I was using TightVNC on a remote computer running MythBuntu today. Then I saw there were updates, so I grabbed those. A while later I rebooted the computer, but now I cannot get VNC to connect. I am using KDE's remote desktop client (krdc) to connect through an SSH tunnel (which has worked just fine in the past). I think the problem is the video on the remote machine.

Here is the log from desktop 9 (which is the one I usually use) from my ~/.vnc:

> 
14/02/08 05:53:28 Xvnc version 3.3.tight1.2.9
14/02/08 05:53:28 Copyright (C) 1999 AT&T Laboratories Cambridge.
14/02/08 05:53:28 Copyright (C) 2000-2002 Constantin Kaplinsky.
14/02/08 05:53:28 All Rights Reserved.
14/02/08 05:53:28 See [http://www.uk.research.att.com/vnc](http://www.uk.research.att.com/vnc) for information on VNC
14/02/08 05:53:28 See [http://www.tightvnc.com](http://www.tightvnc.com) for TightVNC-specific information
14/02/08 05:53:28 Desktop name 'X' (Ruby:9)
14/02/08 05:53:28 Protocol version supported 3.3
14/02/08 05:53:28 Listening for VNC connections on TCP port 5909
Font directory '/usr/X11R6/lib/X11/fonts/Type1/' not found - ignoring
Font directory '/usr/X11R6/lib/X11/fonts/Speedo/' not found - ignoring
Font directory '/usr/X11R6/lib/X11/fonts/misc/' not found - ignoring
Font directory '/usr/X11R6/lib/X11/fonts/75dpi/' not found - ignoring
Font directory '/usr/X11R6/lib/X11/fonts/100dpi/' not found - ignoring
xrdb: No such file or directory
xrdb: can't open file '/home/clifton/.Xresources'

** (x-window-manager:6116): WARNING **: The display does not support the XRender extension.

** (x-window-manager:6116): WARNING **: The display does not support the XRandr extension.

** (x-window-manager:6116): WARNING **: The display does not support the XComposite extension.

** (x-window-manager:6116): WARNING **: The display does not support the XDamage extension.

** (x-window-manager:6116): WARNING **: The display does not support the XFixes extension.

** (x-window-manager:6116): WARNING **: Compositing manager disabled.
** Message: Querying Xkb extension
** Message: Your X server does not support Xkb extension
Xlib:  extension "RANDR" missing on display ":9.0".
Xlib:  extension "XFree86-VidModeExtension" missing on display ":9.0".
alsa: error: master control not found. I even tried to guess wildly, but to no avail.
alsa: info: developer information follows: (send E-Mail to Developer with that)
alsa: * Headphone,0
alsa: * Front,0  <--- hint hint
alsa: * Front Mic,0  <--- hint hint
alsa: * Surround,0  <--- hint hint
alsa: * Center,0  <--- hint hint
alsa: * LFE,0  <--- hint hint
alsa: * Side,0  <--- hint hint
alsa: * Line,0  <--- hint hint
alsa: * Mic,0  <--- hint hint
alsa: * Capture,0
alsa: * Capture,1
alsa: * Input Source,0
alsa: * Input Source,1
alsa: info: end of developer information
** Message: This build doesn't include support for XF86Misc extension
** Message: Querying Xkb extension
** Message: Your X server does not support Xkb extension


And after I kill the VNC session, there is this added to the log file:

> 
The application 'x-window-manager' lost its connection to the display :9.0;
most likely the X server was shut down or you killed/destroyed
the application.
The application 'xfce-mcs-manager' lost its connection to the display :9.0;
most likely the X server was shut down or you killed/destroyed
the application.

(xfce4-terminal:6115): Gdk-WARNING **: GdkWindow 0x1800046 unexpectedly destroyed

(xfce4-terminal:6115): Gdk-WARNING **: GdkWindow 0x1800038 unexpectedly destroyed

(xfce4-terminal:6115): Gdk-WARNING **: GdkWindow 0x1800045 unexpectedly destroyed

(xfce4-terminal:6115): Gdk-WARNING **: GdkWindow 0x1800044 unexpectedly destroyed

(xfce4-terminal:6115): Gdk-WARNING **: GdkWindow 0x1800043 unexpectedly destroyed

(xfce4-terminal:6115): Gdk-WARNING **: GdkWindow 0x1800042 unexpectedly destroyed

(xfce4-terminal:6115): Gdk-WARNING **: GdkWindow 0x1800041 unexpectedly destroyed

(xfce4-terminal:6115): Gdk-WARNING **: GdkWindow 0x180003d unexpectedly destroyed

(xfce4-terminal:6115): Gdk-WARNING **: GdkWindow 0x180003c unexpectedly destroyed

(xfce4-terminal:6115): Gdk-WARNING **: GdkWindow 0x1800033 unexpectedly destroyed

(xfce4-terminal:6115): Gdk-WARNING **: GdkWindow 0x180000e unexpectedly destroyed
The application 'xfce4-terminal' lost its connection to the display :9.0;
most likely the X server was shut down or you killed/destroyed
the application.


---

