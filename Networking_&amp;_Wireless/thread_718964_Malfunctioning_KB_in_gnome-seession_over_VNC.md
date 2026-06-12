---
title: "Malfunctioning KB in gnome-seession over VNC"
date: 2008-03-08
forum: Networking &amp; Wireless
---

### Post by itsu207 on 2008-03-08
Hi Ubuntuans, hope I am not the only one who is having this issue. So I have a beater PC that I use exclusively as a small webserver/home NAS machine. It seats in one of the dingy corner of my leaving room, doing its job. I usually maintain teh machine over ssh/webmin/VNC from a XP machine and that works fairly well. Upon connection to the machine via VNC I ended up in a xterm and I can use that terminal for almost all my work, such as firefox/synaptic/etc. The only time I am having hard time is when I use gnome-session command from the terminal, via VNC. Upon issuing the gnome-session command, I get to see my actual desktop from my XP machine (connecting thru UltraVNC client) and use the mouse to do whatever I want, but my keyboard just does not work. Even ctrl-alt-del does not work, let alone enter/del/backspace. Is there anything I could do to resolve this weired issue?
System Info:-
P3 500MHz, 384MB RAM
Ubuntu 7.10
Installed vncserver- tightvncserver-1.2.9-21
I have the output log of what is going on, as shown below.

**Output from vnc log:-**
-------------------------------------------------------------------------------------------------------------------------------------------
02/03/08 18:15:58 Xvnc version 3.3.tight1.2.9
02/03/08 18:15:58 Copyright (C) 1999 AT&T Laboratories Cambridge.
02/03/08 18:15:58 Copyright (C) 2000-2002 Constantin Kaplinsky.
02/03/08 18:15:58 All Rights Reserved.
02/03/08 18:15:58 See [http://www.uk.research.att.com/vnc](http://www.uk.research.att.com/vnc) for information on VNC
02/03/08 18:15:58 See [http://www.tightvnc.com](http://www.tightvnc.com) for TightVNC-specific information
02/03/08 18:15:58 Desktop name 'X' (xubuntu:1)
02/03/08 18:15:58 Protocol version supported 3.3
02/03/08 18:15:58 Listening for VNC connections on TCP port 5901
02/03/08 18:15:58 Listening for HTTP connections on TCP port 5801
02/03/08 18:15:58   URL [http://xubuntu:5801](http://xubuntu:5801)
Font directory '/usr/X11R6/lib/X11/fonts/Type1/' not found - ignoring
Font directory '/usr/X11R6/lib/X11/fonts/Speedo/' not found - ignoring
Font directory '/usr/X11R6/lib/X11/fonts/misc/' not found - ignoring
Font directory '/usr/X11R6/lib/X11/fonts/75dpi/' not found - ignoring
Font directory '/usr/X11R6/lib/X11/fonts/100dpi/' not found - ignoring
xrdb: No such file or directory
xrdb: can't open file '/root/.Xresources'
Option --login is no longer supported in this version of gnome-terminal; you might want to create a profile with the desired setting, and use the new --window-with-profile option
Window manager warning: Log level 32: could not find XKB extension.



08/03/08 17:14:43 Got connection from client 192.168.1.110
08/03/08 17:14:43 Protocol version 3.4
08/03/08 17:14:43 Ignoring minor version mismatch
08/03/08 17:14:49 Full-control authentication passed by 192.168.1.110
08/03/08 17:14:49 Pixel format for client 192.168.1.110:
08/03/08 17:14:49   32 bpp, depth 24, little endian
08/03/08 17:14:49   true colour: max r 255 g 255 b 255, shift r 16 g 8 b 0
08/03/08 17:14:49   no translation needed
08/03/08 17:14:49 rfbProcessClientNormalMessage: ignoring unknown encoding 16
08/03/08 17:14:49 rfbProcessClientNormalMessage: ignoring unknown encoding 9
08/03/08 17:14:49 rfbProcessClientNormalMessage: ignoring unknown encoding 8
08/03/08 17:14:49 Using tight encoding for client 192.168.1.110
08/03/08 17:14:49 Using compression level 6 for client 192.168.1.110
08/03/08 17:14:49 Enabling X-style cursor updates for client 192.168.1.110
08/03/08 17:14:49 Enabling cursor position updates for client 192.168.1.110
08/03/08 17:14:49 Using image quality level 6 for client 192.168.1.110
08/03/08 17:14:49 rfbProcessClientNormalMessage: ignoring unknown encoding -65530
08/03/08 17:14:49 Enabling LastRect protocol extension for client 192.168.1.110
08/03/08 17:14:49 rfbProcessClientNormalMessage: ignoring unknown encoding -223
08/03/08 17:14:49 rfbProcessClientNormalMessage: ignoring unknown encoding -65535
08/03/08 17:14:49 Pixel format for client 192.168.1.110:
08/03/08 17:14:49   32 bpp, depth 24, little endian
08/03/08 17:14:49   true colour: max r 255 g 255 b 255, shift r 16 g 8 b 0
08/03/08 17:14:49   no translation needed
08/03/08 17:14:49 Using hextile encoding for client 192.168.1.110
08/03/08 17:14:49 rfbProcessClientNormalMessage: ignoring unknown encoding 16
08/03/08 17:14:49 rfbProcessClientNormalMessage: ignoring unknown encoding 9
08/03/08 17:14:49 rfbProcessClientNormalMessage: ignoring unknown encoding 8
08/03/08 17:14:49 Using compression level 6 for client 192.168.1.110
08/03/08 17:14:49 Enabling X-style cursor updates for client 192.168.1.110
08/03/08 17:14:49 Enabling cursor position updates for client 192.168.1.110
08/03/08 17:14:49 Using image quality level 6 for client 192.168.1.110
08/03/08 17:14:49 rfbProcessClientNormalMessage: ignoring unknown encoding -65530
08/03/08 17:14:49 Enabling LastRect protocol extension for client 192.168.1.110
08/03/08 17:14:49 rfbProcessClientNormalMessage: ignoring unknown encoding -223
08/03/08 17:15:21 KbdAddEvent: unknown KeySym 0xff61 - allocating KeyCode 90
08/03/08 17:32:58 KbdAddEvent: unknown KeySym 0xff8d - allocating KeyCode 91
Window manager warning: from event callback
Window manager warning: from event callback
Window manager warning: from event callback
Window manager warning: from event callback
Window manager warning: from event callback
Window manager warning: from event callback
Window manager warning: from event callback
08/03/08 17:34:30 KbdAddEvent: unknown KeySym 0xff61 - allocating KeyCode 92
08/03/08 17:38:08 Client 192.168.1.110 gone
08/03/08 17:38:08 Statistics:
08/03/08 17:38:08   key events received 433, pointer events 9742
08/03/08 17:38:08   framebuffer updates 3148, rectangles 6296, bytes 21190574
08/03/08 17:38:08     LastRect markers 1, bytes 12
08/03/08 17:38:08     cursor shape updates 228, bytes 24446
08/03/08 17:38:08     cursor position updates 2, bytes 24
08/03/08 17:38:08     copyRect rectangles 266, bytes 4256
08/03/08 17:38:08     hextile rectangles 5736, bytes 21103036
08/03/08 17:38:08     tight rectangles 63, bytes 58800
08/03/08 17:38:08   raw bytes equivalent 350331216, compression ratio 16.554859
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Output from gnome-session**
Log of gnome-session 
Sat Mar  8 17:34:13 2008

SESSION_MANAGER=local/xubuntu:/tmp/.ICE-unix/25103
Checking for Xgl: Xlib:  extension "XVideo" missing on display ":1.0".
xvinfo: No X-Video Extension on :1.0
not present. 
AIEEEEH, no Log file found 
Keyboard Control:
  auto repeat:  on    key click percent:  0    LED mask:  00000000
  auto repeating keys:  0000000000000000
                        0000000000000000
                        0000000000000000
                        0000000000000000
  bell percent:  50    bell pitch:  400    bell duration:  100
Pointer Control:
  acceleration:  2/1    threshold:  4
Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  600    cycle:  600
Colors:
  default colormap:  0x21    BlackPixel:  0    WhitePixel:  16777215
Font Path:
  /root/.gnome2/share/cursor-fonts,/usr/X11R6/lib/X11/fonts/Type1/,/usr/X11R6/lib/X11/fonts/Speedo/,/usr/X11R6/lib/X11/fonts/misc/,/usr/X11R6/lib/X11/fonts/75dpi/,/usr/X11R6/lib/X11/fonts/100dpi/,/usr/share/fonts/X11/misc/,/usr/share/fonts/X11/Type1/,/usr/share/fonts/X11/75dpi/,/usr/share/fonts/X11/100dpi/,/root/.gnome2/share/fonts
Bug Mode: compatibility mode is disabled
DPMS (Energy Star):
  Server does not have the DPMS Extension 
Detected PCI ID for VGA: 00:10.0 0300: 1002:5044 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 
Window manager warning: Failed to read saved session file /root/.metacity/sessions/default0.ms: Failed to open file '/root/.metacity/sessions/default0.ms': No such file or directory
Window manager warning: Log level 32: could not find XKB extension.


Tracker version 0.6.3 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at [http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)

Initialising tracker...
** Message: Not starting remote desktop server

** (update-notifier:25229): WARNING **: not starting because user is not in admin group

Throttle level is 0
Initializing gnome-mount extension
** Message: Not starting remote desktop server

---

### Post by itsu207 on 2008-03-09
Anyone wants to help? Please.

---

### Post by lukemack on 2008-07-04
did you resolve this? I'm also getting 'Window manager warning: Log level 32: could not find XKB extension.'

---

