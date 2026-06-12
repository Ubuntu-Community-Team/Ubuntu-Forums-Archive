---
title: "Quick question: Xorg? Wacom tablet?"
date: 2011-08-13
forum: New to Ubuntu
---

### Post by Lucypie on 2011-08-13
I was reading articles to get my tablet set up. I used one for 10.10 since I couldn't find one in 11. It tells me if I am having problems making small lines (which I am) to add a line to the xorg file. I cannot find it xD It said it was in etc/x11/xorg.something I forgot xD 

Where is it or is there something else I can do? 

using 11.04 normal install. wacom bamboo tablet. I'm using gimp too, I have it already set up, I just want to make smaller lines xD

---

### Post by Favux on 2011-08-13
Hi Lucypie,

Which tablet do you have?  What line are you planning on adding?

While you can use the xorg.conf in /etc/X11 now days you might not even have one and would have to create it.  The Wacom tablet is configured in the 50-wacom.conf file located in xorg.conf.d i.e. /usr/share/X11/xorg.conf.d/50-wacom.conf.  But since that is a system file managed by Ubuntu technically you should add options by creating a 52-wacom-options.conf in /etc/X11/xorg.conf.d:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xorg.conf.d](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xorg.conf.d)  But as the HOW TO page says you can't configure the parent device (stylus) yet with Natty's X server 1.10.  So actually a coin flip on how you want to do it.

The HOW TO page:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO)

---

### Post by Lucypie on 2011-08-13
This is the exact thing I am trying to do.
[https://help.ubuntu.com/community/Wacom#Modifying%20Stroke%20Pressure]("https://help.ubuntu.com/community/Wacom#Modifying%20Stroke%20Pressure")

This is the line I have to add. 
  Option        "PressCurve"    "50,0,100,50"         # Custom preference

Also, I do not have the specified folder you are talking about. o_o Is that bad?

---

### Post by lykeion on 2011-08-13
/etc/X11/xorg.conf is a configuration file for the GUI in most Linux distributions, including Ubuntu. In this file you can set graphic drivers, screens, input devices, etc.

Newer Ubuntu versions don't have this file as default, since it's not needed. But for special configuration you can generate one with this command:
```
sudo Xorg configure
```

Like Favux says the structure of the X conf files have changed: see here [http://askubuntu.com/questions/37761/xorg-conf-in-ubuntu-natty-11-04](http://askubuntu.com/questions/37761/xorg-conf-in-ubuntu-natty-11-04)

Note that after changing X configuration you need to restart X for changes to take effect. The easiest way to do this is to reboot. You can restart X from command-line also (this is not Windows we're talking about), but for simplicity just reboot.

---

### Post by Lucypie on 2011-08-13
When using that command I got the following error.

```
Unrecognized option: configure
use: X [:<display>] [option]
-a #                   default pointer acceleration (factor)
-ac                    disable access control restrictions
-audit int             set audit trail level
-auth file             select authorization file
-br                    create root window with black background
+bs                    enable any backing store support
-bs                    disable any backing store support
-c                     turns off key-click
c #                    key-click volume (0-100)
-cc int                default color visual class
-nocursor              disable the cursor
-core                  generate core dump on fatal error
-dpi int               screen resolution in dots per inch
-dpms                  disables VESA DPMS monitor control
-deferglyphs [none|all|16] defer loading of [no|all|16-bit] glyphs
-f #                   bell base (0-100)
-fc string             cursor font
-fn string             default font name
-fp string             default font path
-help                  prints message with these options
-I                     ignore all remaining arguments
-ld int                limit data space to N Kb
-lf int                limit number of open files to N
-ls int                limit stack space to N Kb
-nolock                disable the locking mechanism
-nolisten string       don't listen on protocol
-noreset               don't reset after last client exists
-background [none]     create root window with no background
-nr                    (Ubuntu-specific) Synonym for -background none
-reset                 reset after last client exists
-p #                   screen-saver pattern duration (minutes)
-pn                    accept failure to listen on all ports
-nopn                  reject failure to listen on all ports
-r                     turns off auto-repeat
r                      turns on auto-repeat 
-render [default|mono|gray|color] set render color alloc policy
-retro                 start with classic stipple and cursor
-s #                   screen-saver timeout (minutes)
-t #                   default pointer threshold (pixels/t)
-terminate             terminate at server reset
-to #                  connection time out
-tst                   disable testing extensions
ttyxx                  server started from init on /dev/ttyxx
v                      video blanking for screen-saver
-v                     screen-saver without video blanking
-wm                    WhenMapped default backing-store
-wr                    create root window with white background
-maxbigreqsize         set maximal bigrequest size 
+xinerama              Enable XINERAMA extension
-xinerama              Disable XINERAMA extension
-dumbSched             Disable smart scheduling, enable old behavior
-schedInterval int     Set scheduler interval in msec
-sigstop               Enable SIGSTOP based startup
+extension name        Enable extension
-extension name        Disable extension
-query host-name       contact named host for XDMCP
-broadcast             broadcast for XDMCP
-multicast [addr [hops]] IPv6 multicast for XDMCP
-indirect host-name    contact named host for indirect XDMCP
-port port-num         UDP port number to send messages to
-from local-address    specify the local address to connect from
-once                  Terminate server after one session
-class display-class   specify display class to send in manage
-cookie xdm-auth-bits  specify the magic cookie for XDMCP
-displayID display-id  manufacturer display ID for request
[+-]accessx [ timeout [ timeout_mask [ feedback [ options_mask] ] ] ]
                       enable/disable accessx key sequences
-ardelay               set XKB autorepeat delay
-arinterval            set XKB autorepeat interval


Device Dependent Usage
-modulepath paths      specify the module search path
-logfile file          specify a log file name
-configure             probe for devices and write an xorg.conf
-showopts              print available options for all installed drivers
-config file           specify a configuration file, relative to the
                       xorg.conf search path, only root can use absolute
-configdir dir         specify a configuration directory, relative to the
                       xorg.conf.d search path, only root can use absolute
-verbose [n]           verbose startup messages
-logverbose [n]        verbose log messages
-quiet                 minimal startup messages
-pixmap24              use 24bpp pixmaps for depth 24
-pixmap32              use 32bpp pixmaps for depth 24
-fbbpp n               set bpp for the framebuffer. Default: 8
-depth n               set colour depth. Default: 8
-gamma f               set gamma value (0.1 < f < 10.0) Default: 1.0
-rgamma f              set gamma value for red phase
-ggamma f              set gamma value for green phase
-bgamma f              set gamma value for blue phase
-weight nnn            set RGB weighting at 16 bpp.  Default: 565
-layout name           specify the ServerLayout section name
-screen name           specify the Screen section name
-keyboard name         specify the core keyboard InputDevice name
-pointer name          specify the core pointer InputDevice name
-nosilk                disable Silken Mouse
-flipPixels            swap default black/white Pixel values
-disableVidMode        disable mode adjustments with xvidtune
-allowNonLocalXvidtune allow xvidtune to be run as a non-local client
-allowMouseOpenFail    start server even if the mouse can't be initialized
-ignoreABI             make module ABI mismatches non-fatal
-isolateDevice bus_id  restrict device resets to bus_id (PCI only)
-version               show the server version
-showDefaultModulePath show the server default module path
-showDefaultLibPath    show the server default library path
vtXX                   use the specified VT number
-keeptty               don't detach controlling tty (for debugging only)
-novtswitch            don't immediately switch to new VT
-sharevts              share VTs with another X server
-nohwaccess            don't access hardware ports directly


Fatal server error:
Unrecognized option: configure


Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 

 ddxSigGiveUp: Closing log

```

---

### Post by lykeion on 2011-08-13
Sorry forgot the dash. You could see the right usage in your output also :) 

```
sudo Xorg -configure
```

---

### Post by Favux on 2011-08-13
You'd add the line:
```
Option "PressCurve" "50,0,100,50"
```
to the USB snippet, assuming your tablet is usb.  For example:
```
Section "InputClass"
	Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#	MatchProduct "Wacom|WALTOP|WACOM"
	MatchProduct "Wacom|WACOM"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
	Option "PressCurve" "50,0,100,50"
EndSection
```
To edit use:
```
gksudo gedit /usr/share/X11/xorg.conf.d/50-wacom.conf
```
See "III. Configure the Wacom Bamboo P&T tablet" on the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  Although if you create a xorg.conf it becomes a moot point.

Many folks would use a *xsetwacom set* command to do that:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xsetwacom](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xsetwacom)

---

### Post by Lucypie on 2011-08-13
More probs with the configure...

```
Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.


Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 

 ddxSigGiveUp: Closing log

```

I did what favux said... and I think it made slightly smaller lines. Not quite small enough, but I think with a little tweaking I can fix it.

Thanks everyone for the help :)

---

