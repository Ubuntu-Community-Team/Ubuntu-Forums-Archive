---
title: "Ubuntu 9.1 screen resolution stuck at 800x600..:|"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by keinad on 2009-11-03
Need help with this too..I have no experience with ubuntu, and got stuck with this problem too, just like joe2005.
I installed this on a Toshiba Tecra 8200, Pentium III, 20 GB.
lspci
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 11)
00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 11)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801BAM ISA Bridge (LPC) (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801BAM IDE U100 Controller (rev 03)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 03)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 03)
00:1f.6 Modem: Intel Corporation 82801BA/BAM AC'97 Modem Controller (rev 03)
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade/XP (rev 63)
02:07.0 Multimedia audio controller: Yamaha Corporation YMF-754 [DS-1E Audio Controller]
02:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)
02:0d.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 31)
02:0d.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 31)

was able to create a xorg.conf.new file under /home..
tried making a copy to /etc/X11 (but can't do it properly..how should it be moved?)
am lost at configuring it..

/home/     /xorg.conf.new
> Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "dri"
	Load  "extmod"
	Load  "glx"
	Load  "record"
	Load  "dbe"
	Load  "dri2"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "AccelMethod"        	# [<str>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "PciRetry"           	# [<bool>]
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SetMClk"            	# <freq>
        #Option     "MUXThreshold"       	# <i>
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "Rotate"             	# [<str>]
        #Option     "VideoKey"           	# <i>
        #Option     "NoMMIO"             	# [<bool>]
        #Option     "NoPciBurst"         	# [<bool>]
        #Option     "MMIOonly"           	# [<bool>]
        #Option     "CyberShadow"        	# [<bool>]
        #Option     "CyberStretch"       	# [<bool>]
        #Option     "XvHsync"            	# <i>
        #Option     "XvVsync"            	# <i>
        #Option     "XvBskew"            	# <i>
        #Option     "XvRskew"            	# <i>
        #Option     "FpDelay"            	# <i>
        #Option     "Display1400"        	# [<bool>]
        #Option     "Display"            	# [<str>]
        #Option     "GammaBrightness"    	# [<str>]
        #Option     "TVChipset"          	# [<str>]
        #Option     "TVSignal"           	# <i>
	Identifier  "Card0"
	Driver      "trident"
	VendorName  "Trident Microsystems"
	BoardName   "CyberBlade/XP"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection


spent many sleepless nights following different threads...and I can't seem to get it right.:| step by step help would be really appreciated.

---

### Post by halitech on 2009-11-03
try this.

```
gksudo gedit /etc/X11/xorg.conf
```
this should open a new blank file. Then copy and paste the info from this post into it

[http://ubuntuforums.org/showpost.php?p=5039883&postcount=12](http://ubuntuforums.org/showpost.php?p=5039883&postcount=12)

Save the file and reboot. you *should* now have 1024x768 resolution.

---

### Post by keinad on 2009-11-03
thanks for the response..
it worked.:)
thanks..hope there are no more problems.

---

### Post by halitech on 2009-11-03
glad to hear it worked for you :)

---

### Post by mattbraafhart on 2009-11-06
I'm having same issue, I just installed Xubuntu 9.1 on VirtualBox adn the resolution is stuck at 800x600, and I can't go higher.

I tried running sudo Xorg -configure, I can't get that to run because I can't get X server to stop because of gdm

i tried reconfiguring, doesn't work

I tried to change xorg.conf, the file doesn't exist

Is there GUI tool to configure X that can be installed?

If this can't be fixed it makes my VM useless since I won't be able to move it toother machines with different resolutions.

---

### Post by halitech on 2009-11-06
did you install the VirtualBox addons?

---

### Post by trix33 on 2009-11-06
Halitech wat's man
am a complete newbie and i need help on my sis672 mirage card it's stuck at 800x600 resolution and am using ubuntu 9.10 please help.thanks

---

### Post by mattbraafhart on 2009-11-06
Do you mean add ons for the guest or add ons for the host, my host is Windows XP?

---

### Post by unknownjason on 2009-11-06
I just did what was suggested, and on the reboot, it wont. At all. It just rapid flashes on a black screen for my login name, but i cannot type anything. 
Did I break everything?
I'm scared.

---

### Post by halitech on 2009-11-08
> **mattbraafhart said:**
> Do you mean add ons for the guest or add ons for the host, my host is Windows XP?

once you boot into the virtual machine, there is an option to install guest addons. You need to install them to get better resolutions.

---

### Post by halitech on 2009-11-08
> **trix33 said:**
> Halitech wat's man
am a complete newbie and i need help on my sis672 mirage card it's stuck at 800x600 resolution and am using ubuntu 9.10 please help.thanks

with 9.10 there is no /etc/X11/xorg.conf file so you will need to create it in order to use the same fix that keinad used. I don't know if it will work with an SiS card as they aren't all that linux friendly but you can try. You should probably open a new thread if it doesn't work.

---

### Post by halitech on 2009-11-08
> **unknownjason said:**
> I just did what was suggested, and on the reboot, it wont. At all. It just rapid flashes on a black screen for my login name, but i cannot type anything. 
Did I break everything?
I'm scared.

what kind of video card do you have?

you can try booting into single user mode from the GRUB menu and try to fix the xserver from there.

---

### Post by unknownjason on 2009-11-08
> **halitech said:**
> what kind of video card do you have?

you can try booting into single user mode from the GRUB menu and try to fix the xserver from there.

I started a new thread and got it fixed, but I am still trying to fix the resolution. Help? The thread is here, and my video card specs are there:
[http://ubuntuforums.org/showthread.php?p=8274145#post8274145](http://ubuntuforums.org/showthread.php?p=8274145#post8274145)

---

### Post by seedsetter on 2009-11-20
i am having the same problem with my resolution I only have the option to change between 640X480 and 800X600 I already changed the xorg.conf and restarted the computer now it shows 1024X768 but still dont give me the option to change to it.

I am running 9.10 on a 500mhz ppc 1.2 gig ram 
I am brand new to ubuntu and would appreciate any help. Thanks in advance.
Here is what is displayed

Section "Device"
    Identifier    "Configured Video Device"
    BusID        "PCI:0:16:0"
    Option        "UseFBDev"        "true"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
Section "Device"
  Identifier "Trident Microsystems CyberBlade XPAi1"
  Driver "trident"
  BusID "PCI:1:0:0"
EndSection

Section "Monitor"
  Identifier "Generic Monitor"
  Option "DPMS"
  HorizSync 28-51
  VertRefresh 43-60
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Generic Monitor"
    Device        "Trident Microsystems CyberBlade XPAi1"
    SubSection "Display"
           Depth 8
           Modes "1024x768"
    EndSubSection
    SubSection "Display"
           Depth 16
           Modes "1024x768"
    EndSubSection
    SubSection "Display"
           Depth 24
           Modes "1024x768"
    EndSubSection
    SubSection "Display"
           Depth 32
           Modes "1024x768"
    EndSubSection
EndSection

---

### Post by sailor2001 on 2009-11-20
will a start-up manager (synaptics) help you out?

---

### Post by seedsetter on 2009-11-20
> **sailor2001 said:**
> will a start-up manager (synaptics) help you out?

I realy dont know i am very new under a week I would need a step by step. I did look at it under system/admin but it just looks like Chinese to me. I dont know what i am looking for.

---

### Post by seedsetter on 2009-11-21
This is my video card

frank@frank-desktop:~$ lspci | grep VGA
0000:00:10.0 VGA compatible controller: ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS

---

### Post by extreme-moja on 2009-11-23
> **halitech said:**
> try this.

```
gksudo gedit /etc/X11/xorg.conf
```this should open a new blank file. Then copy and paste the info from this post into it

[http://ubuntuforums.org/showpost.php?p=5039883&postcount=12](http://ubuntuforums.org/showpost.php?p=5039883&postcount=12)

Save the file and reboot. you *should* now have 1024x768 resolution.

Thanks A LOT for this halitech!!! I've been searching EVERYWHERE for this answer! How come Ubuntu haven't mentioned that something like this could happen? I guess it's because I installed 9.10 on an old laptop..... 

Anyway, my screen resolution is working properly now! Thanks!!!

---

### Post by halitech on 2009-11-24
> **extreme-moja said:**
> Thanks A LOT for this halitech!!! I've been searching EVERYWHERE for this answer! How come Ubuntu haven't mentioned that something like this could happen? I guess it's because I installed 9.10 on an old laptop..... 

Anyway, my screen resolution is working properly now! Thanks!!!

Glad to hear you have things working properly now :)

I guess everyone assumes most people are using fairly new machines to run Ubuntu on so answers to issues on older machines are harder to find.

---

### Post by czar2tsar on 2010-02-01
Like many, after installing 9.10 as a fresh install I rebooted to 800x600. Well, the next step was to plug in my nVidia FX 5600 AGP video card w/ 256mb 

Result: 640x480 in 24bit color.  I've tried every suggestion I can find on the forums.  nada, nothing... edited xorg.conf til I'm blue in the fingers, nada. xrandr, nothing

So, setup is I've a IBM P200 and the nVidia FX 5600 AGP 8x w/ 256

Eventually I want it hooked to my HDTV via DVI, but 1 thing @ a time.  

I'm stumped totally.

---

### Post by fishnuke on 2010-02-19
After much searching around and many failures, I have added new resolutions to the System->Preferences->Display GUI in Ubuntu 9.1.  It now defaults to 1024x768 60Hz.  I have an old computer with an integrated Intel 3D "Extreme" Graphics chip, and the 800x600 was maddening!

Preface:  there is no xorg.conf anymore, and adding one doesn't do the trick for these crappy integrated chips.  There is no obvious way to add new graphics modes to the GUI, and using xrandr on the command line is not persistent after a reboot.

Solution:

1) Edit gdm Default file (likely back it up if you're scared).
sudo nano /etc/gdm/Init/Default 

2) insert these lines, or something similar
xrandr --newmode "1024x768 60Hz" 60 1024 1072 1176 1328 768 771 775 798 -hsync +vsync
xrandr --addmode VGA1 "1024x768 60Hz"
xrandr --mode "1024x768 60Hz"

(put them before this line)
initctl -q emit login-session-start DISPLAY_MANAGER=gdm

3) Since this seemed to have lost res after logging in, I repeated the last line one more time, right before the end.

xrandr --mode "1024x768 60Hz"

(put this before this line)
exit 0

The refresh rate min and max used above were from someone using 75Hz, with my display, it comes out as 57Hz in the GUI.  Close enough for me to use this computer for work instead of dealing with 800x600.  man xrandr has more information, but I have other things to do than this!

This isn't elegant, but it works and is concise.  Please ubuntu, put 1024x768 as a default, instead of just 800x600 and 640x480!

Thanks to a combination of these posts:
[http://ubuntuforums.org/showthread.php?t=1319491&page=2](http://ubuntuforums.org/showthread.php?t=1319491&page=2)
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)
[http://heatware.net/linux-unix/how-to-change-screendisplay-resolution-in-ubuntu-9-10/](http://heatware.net/linux-unix/how-to-change-screendisplay-resolution-in-ubuntu-9-10/)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1221226](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1221226)
[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2)
[http://ubuntuforums.org/showthread.php?t=1388543](http://ubuntuforums.org/showthread.php?t=1388543)
and of course, this one!

---

### Post by hnaqvi46 on 2010-04-25
Please help me :( I'm a complete ubuntu noob. I was wondering if you could do an IM chat with me to walk me through the steps. I have the same problem. My monitor isn't detected by ubuntu, so I'm also stuck with 800x600 resolution and it's really annoying.

I know it might be some trouble for you, but I'm completely new to linux so I have a hard time following written instructions in a forum..it would really help me if I could talk to you in real time in IM. I really want to try ubuntu and give linux a fair chance, but I need help from intermediate-advanced users like you.

Please email me at [email]hnaqvi46@gmail.com[/email]
I'd really appreciate it.


> **fishnuke said:**
> After much searching around and many failures, I have added new resolutions to the System->Preferences->Display GUI in Ubuntu 9.1.  It now defaults to 1024x768 60Hz.  I have an old computer with an integrated Intel 3D "Extreme" Graphics chip, and the 800x600 was maddening!

Preface:  there is no xorg.conf anymore, and adding one doesn't do the trick for these crappy integrated chips.  There is no obvious way to add new graphics modes to the GUI, and using xrandr on the command line is not persistent after a reboot.

Solution:

1) Edit gdm Default file (likely back it up if you're scared).
sudo nano /etc/gdm/Init/Default 

2) insert these lines, or something similar
xrandr --newmode "1024x768 60Hz" 60 1024 1072 1176 1328 768 771 775 798 -hsync +vsync
xrandr --addmode VGA1 "1024x768 60Hz"
xrandr --mode "1024x768 60Hz"

(put them before this line)
initctl -q emit login-session-start DISPLAY_MANAGER=gdm

3) Since this seemed to have lost res after logging in, I repeated the last line one more time, right before the end.

xrandr --mode "1024x768 60Hz"

(put this before this line)
exit 0

The refresh rate min and max used above were from someone using 75Hz, with my display, it comes out as 57Hz in the GUI.  Close enough for me to use this computer for work instead of dealing with 800x600.  man xrandr has more information, but I have other things to do than this!

This isn't elegant, but it works and is concise.  Please ubuntu, put 1024x768 as a default, instead of just 800x600 and 640x480!

Thanks to a combination of these posts:
[http://ubuntuforums.org/showthread.php?t=1319491&page=2](http://ubuntuforums.org/showthread.php?t=1319491&page=2)
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)
[http://heatware.net/linux-unix/how-to-change-screendisplay-resolution-in-ubuntu-9-10/](http://heatware.net/linux-unix/how-to-change-screendisplay-resolution-in-ubuntu-9-10/)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1221226](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1221226)
[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2)
[http://ubuntuforums.org/showthread.php?t=1388543](http://ubuntuforums.org/showthread.php?t=1388543)
and of course, this one!

---

