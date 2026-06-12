---
title: "To big resolution"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by snekkis on 2009-01-16
Just starting with linux and choosing Ubuntu 8.10. Have installed on a Fujitsu-Siemens Amilo Pro v2055, but the resolution is set to 1600 x 1200 default after install. It extends beyond the physical screen and I'm missing out on lower part and right side of the screen. If I set it to 1200 X 800 (default), it goes all distorted and I can not set it back.

No refresh rates is provided from manufacturer. Only this, Display diagonal: 15.4 inch WXGA, TFT
Max. resolution: 1280 x 800 / 16 mio. colours
Screen controller
Chip: VN 800 / Uni Chrome Pro 3D/2D
Video memory (VRAM): shared memory

I have seen some posts about doing something in the terminal, but I don't know it it applies to the latest 8.10 distribution. I'm not that terminally either.

 I get all confused when I even try connect the wireless. In help it says: (system > administration > network) to find the Network Manager, but I can not find the Network Manager. As I understand it should scan for available networks and find my router.

I've found Network configuration in Preferences though, and its called Network Configuration when the dialog window opens???

Want to fix this and use Ubuntu. It looks very nice.

Snekkis

---

### Post by mrjohnston on 2009-01-17
Ok, first the wireless.  Network-manager should be a little computer monitors icon in the upper right hand corner of the screen.  Right click on the monitors and it will display your network cards you can use to connect as well as any routers available wirelessly and their signal strength.

Now the screen resolution.  Usually that is autodetected, but under preferences you can go to screen resolution and change it and the monitor frequency to find one that works better.  I would also ask you you are using any kind of adapter to connect your monitor (like dvi to vga or a KVM switch) as those can mess with the ability to autodetect the monitor.

You also seem to be using a chrome video card, which I believe is fairly old and troublesome.  I know there is an openchrome driver you can use, but not sure about the details of it as I've never owned one.

---

### Post by snekkis on 2009-01-17
That icon I can not see. It is beyond the screen. I have notebook and there is no external things connected. But I'll look for that driver and see.

Thanks for replying!

---

### Post by sailor2001 on 2009-01-17
alt/f2  type in /usr/share/applications/screens and graphics  try setting refresh at 60 and go from there

---

### Post by northern lights on 2009-01-17
mkey.

As for the resolution, there's two issues that might both need tweaking.

It's possible you're not using the most suiting graphics driver; although, if you were on no driver but VESA at all, these high resolution would not be possible. Check under "System > Administration > Hardware Drivers", whether a proprietary driver is offered and whether the recommended driver is in use.

Since your on too large a resolution and your monitor's native resolution is screwed up, it is very likely you don't have the correct monitor selected. What graphics device does your laptop use?
The following goes for nvidia devices:
If the proprietary nvidia driver is in use, there should be a "NVIDIA X Server Settings" entry under "System > Administration". Open it, find the "GPU 0" entry in the menu and further find its subsection "CRT 0". Highlight "CRT 0" and click on the "Acquire EDID..." button. Native resolutions should now be supported. You will have to restart X (logout/reboot).

As for the wireless, can you please open a Terminal (Applications > Accessories > Terminal) and post the outputs of ```
sudo lshw -C network
``````
ifconfig
```and```
iwconfig
```

Further, if you're unsure about your graphics device, also post the output of```
sudo lshw -C display
```

---

### Post by benit on 2009-02-26
I have the same laptop as snekkis and the same issues (new to Ubuntu, not very terminally etc, and obviously the same problem with the screen resol.)

I been trying to find out how to work in Ubuntu and the first thing that more or less gave me a better idea was by finding a list of basic commands in Ubuntu. 

The problem with the screen resolution when installing Ubuntu 8.10 in the Amilo V2055 is that it doesn't install the correct driver for the Chipset Via VN800 (So it seems by what I have read), so it starts running with a General Driver, this is what I get if I access the xorg file in the terminal I entered:

 sudo gedit /etc/X11/xorg.conf

--------------------------------------------
This is what it comes up:
--------------------------------------------
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
		
EndSection

---------------------------------------------------
And that's it, I was reading some other solutions given to similar screen resolution problems, and some say to modify this file, as I am totally new to Ubuntu I didn't want to make almost any changes.

 The simplest suggestion that I found was to add a couple of lines to the xorg file, 

I again entered in terminal:

sudo gedit /etc/X11/xorg.conf 


and did this:
----------------------------------------------------

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	   SubSection "Display"
		
Modes		"800x600@60"	"1024x768@60"	"800x600@56"	"1280x800@60"
	EndSubSection
EndSection

----------------------------------------------
I saved the xorg with the new lines and then rebooted, I clicked on System>Preferences>Screen Resolution.  Hoping to see the new options with their respective refresh rates but nothing seem to have changed, (in the choices "1600x1200" "1400x1050" "1280x1024" "1280x800" etc...  all have still O Hz refresh rate the only option that has a value different to zero rate is "640x480" at 60 Hz )

If I select the "1280x800" (which is the correct resolution for Amilo V2055) there is no refresh rate so I just lines all over the screen as I move the cursor across it.

I try finding too the correct driver for this laptop as suggested the only one I could find was the one refered to in [http://ubuntuforums.org/showthread.php?t=485646](http://ubuntuforums.org/showthread.php?t=485646)

But I don't know how to follow this instructions or even how to install the File Type: openchrome-stable.sh 

I hope the problem is clear (totally new clueless user  :-)  please help in step by step if possible.  Thank you all for your time!!

---

### Post by northern lights on 2009-02-26
One ahead of the specific issues: Irrespective of the task / problem at hand, if you need to run graphical applications as root, please do so with *gksu* (*kdesu* under KDE/Kubuntu) rather than *sudo*. Use that for shell processes only.

As far as your graphical problem is concerned, please (as requested above) open a terminal and post the output of ```
sudo lshw -C display
```That will display information on your graphics device and the currently assigned driver. We'll take it from there.

---

### Post by kansasnoob on 2009-02-26
Editing "/etc/X11/xorg.conf" on 8.10 (Intrepid) doesn't work. In 8.04.2 that would be the thing to do, though you didn't do it just right, but unless you decide to install 8.04.2 that doesn't matter.

What I'd suggest now is either getting to terminal which sounds like it may not be an option for you or just restarting and accessing GRUB by waiting until the system prompt passes and pressing Esc. Then you'll see a list of boot options, basically the newest kernel first followed by a recovery mode and the same for each older kernel and finally an option for "memtest".

Once you access the GRUB screen you want to select "recovery mode" for the newest kernel and when that's done running you'll be presented with a few options. You want to choose to "recover Xorg/Xserver" or something like that, sorry I can't remember the exact words they use, but it's fairly recognizable.

That should get you back to square one. Optionally if you can get to "terminal" (one way might be pressing Alt > F2 at the same time) you could run in terminal:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Which will just restore xorg to it's original state.

Then to try and fix things I'd install either "grandr" or "lxrandr" (you could install both - they don't interfere with each other) either from Synaptic Package Manager or using the terminal:

```
sudo apt-get install grandr
```

```
sudo apt-get install lxrandr
```

or for both:

```
sudo apt-get install grander lxrandr
```

Then either can be launched (they don't show up in the menu) by pushing "Alt > F2" as I said before and then typing either grander or lxrandr. They both have gui's so they're easy to understand.

BTW, the driver you need to be using is "openchrome" but I have no idea how to manually install it with Intrepid - it was easy in Hardy.

---

### Post by kansasnoob on 2009-02-26
I was doing some testing on Jaunty when I posted that message and couldn't post screenshots for the "randr" gui's but here they are:

[ATTACH]104742[/ATTACH]

[ATTACH]104743[/ATTACH]

---

### Post by kestrel1 on 2009-02-26
> kansasnoob: Editing "/etc/X11/xorg.conf" on 8.10 (Intrepid) doesn't work. In 8.04.2 that would be the thing to do, though you didn't do it just right, but unless you decide to install 8.04.2 that doesn't matter.

This is not true. You can edit the xorg.conf file in Ubuntu 8.10.
This was the only way that I could get my system working correctly, when I installed 8.10 nearly six months ago.

---

### Post by kansasnoob on 2009-02-26
> **kestrel1 said:**
> This is not true. You can edit the xorg.conf file in Ubuntu 8.10.
This was the only way that I could get my system working correctly, when I installed 8.10 nearly six months ago.

Well, I can absolutely guarantee you that I've tried adding "Openchrome" like this:

> Section "Device"
    Identifier    "Configured Video Device"
    Driver        "openchrome"
EndSection

In 8.10 and it causes the whole box to freeze at start up.

Always worked perfectly in 8.04.

I can only refer to my own experiences, and make suggestions based on those.

---

### Post by kansasnoob on 2009-02-26
Quite a bit about the Openchrome driver here:

[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

---

### Post by benit on 2009-02-26
Hi Guys, thank you for the quick response here is what I got:

++kansasnoob

I follow the instructions I installed both grandr and lxrandr, I tried lxrandr first, a small screen appeared and I selected the 11280x800 option from the drop menu. The refresh rate only had to choices (zero and Automatic), I selected auto. and then the screen got full of lines, I couldn't see much, luckly after rebooting everything went back to normal. 

Then I try grandr and from the drop menu only two options had refresh rate 60 Hz (800x600 and 648x480)  all the rest zero. This time I did not take the chance, I was worried I might not be able to know how to undo it if anything went wrong. 

I am reading the extra info in the link you posted on Openchrome. Thanks for the images too. Any Ideas?


++nothernlights

From the code: 

sudo lshw -C network 
------------------------------------------------------
 *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@0000:00:06.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 78
       serial: 00:14:0b:02:ea:3a
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=86.8.252.192 latency=64 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:c2:90:84
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 4a:2e:dd:72:e9:4b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
__________________________________________________

From the code 

ifconfig

-----------------------------------------
eth0      Link encap:Ethernet  HWaddr 00:14:0b:02:ea:3a  
          inet addr:86.8.252.192  Bcast:86.8.255.255  Mask:255.255.252.0
          inet6 addr: fe80::214:bff:fe02:ea3a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4186 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3634 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3681964 (3.6 MB)  TX bytes:639247 (639.2 KB)
          Interrupt:23 Base address:0xe400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)
_____________________________________________________

From code:

iwconfig
----------------------------------
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
________________________________________________________

and finally from code:

sudo lshw -C display
---------------------------------------------------
 *-display UNCLAIMED     
       description: VGA compatible controller
       product: CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro]
       vendor: VIA Technologies, Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-2.0 bus_master cap_list
       configuration: latency=64 mingnt=2

_______________________________________________________

Quite a lot of info I hope this helps, thanks.

---

### Post by kansasnoob on 2009-02-26
I wish I had a better answer for you! I built 23 desktop computers with similar graphic cards and I've chosen to keep most of them on 8.04 (Hardy) just because of this!

Now, that's not a big deal because Hardy is LTS so it will be supported until April 2011.

---

### Post by northern lights on 2009-02-26
mkey.

I only have a few minutes before running to class:

First off, the *lshw* resilt with the *-display* flag would have suffices, but anyhow, Thanks.

Is the openchrome package installed in the first place? Run```
sudo apt-get install xserver-xorg-video-openchrome
```and subsequently```
sudo dpkg-reconfigure -phigh xserver-xorg
```

S3 UniChrome chipsets under Intrepid are a pain though. Report back.

---

### Post by benit on 2009-02-27
++nothernlights

Hi, I tried both codes as you said, first the code:

```
sudo apt-get install xserver-xorg-video-openchrom
```

and this is what came up:
  
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-openchrome is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.



Then tried the code:
```
sudo dpkg-reconfigure -phigh xserver-org
```
And it came up this:
> xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20090227102935


Nothing changed :(  what should I do next??. 


++kansasnoob

I tried before Ubuntu 8.04 as sugested but when I tried to installed it did't install right I tried like 4 times and got it  burn twice from different sources just in case that mighg have been the problem but still did't install correctly, I got stock there, then I installed Ubuntu 8.10 and everything went well (so far.. except for the screen resolution ofcourse and not knowing how to do anything in Ubuntu) but besides that no problems.

---

### Post by benit on 2009-02-27
I think I would like to try to modify the xorg.conf again. Could some one please tell me how to do this correctly???

 At the moment this is what I have in xorg.conf:


> Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection



---

### Post by kestrel1 on 2009-03-02
What video card & monitor do you have?

---

### Post by kansasnoob on 2009-03-02
Well, I've been looking and found this:

[http://wiki.openchrome.org/tikiwiki/tiki-view_forum_thread.php?comments_parentId=5776&topics_threshold=0&topics_offset=4&topics_sort_mode=type_desc&topics_find=&forumId=1](http://wiki.openchrome.org/tikiwiki/tiki-view_forum_thread.php?comments_parentId=5776&topics_threshold=0&topics_offset=4&topics_sort_mode=type_desc&topics_find=&forumId=1)

> I am currently running 1280x800 on Ubuntu Intrepid, using native
Openchrome driver on a VN800 chipset (Gateway MX3215 Laptop). I have
attached my xorg.conf if it can be of any help at all. It took me days
to get these setting just right (and 3D works perfectly with it).

-Jim Raredon


attachment xorg.conf.gz (981 b) 

I unzipped the .gz:

> # xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"Emulate3Buttons"	"true"
EndSection


Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection
Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"openchrome"
	Screen	0
	Option "SWcursor" "true"
	Option "EnableAGPDMA"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1280x800"
	Horizsync	31.5-50.0
	Vertrefresh	56.0 - 65.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes		"1280x768@60"	"1280x720@60"	"800x600@60"	"1280x800@60"	"800x600@56"
	Virtual	1280 768
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"dri"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"openchrome"
	Screen	1
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

Now, mind you, I have no way of knowing whether or not this will work!

So proceed at your own risk!

---

### Post by benit on 2009-03-03
++Kansasnoob

This script that you found in 

[http://wiki.openchrome.org/tikiwiki/...ind=&forumId=1](http://wiki.openchrome.org/tikiwiki/...ind=&forumId=1)

worked perfectly!!!! :) :) :) 

problem solved!!!!!!!!

 I only made a tiny change in the Section "Screen"
in the part of Virtual, I changed the value 1280 768 to 1280 800, then rebooted the computer and now is Perfect!!!!!

Thank you very much!!! :-D :-D :-D

---

### Post by tebay on 2009-03-04
hello,
      I have tried a lot of code in my notebook i have a fujitsu siemens amilo pro v2030 with ubuntu 8.10 the resolution was to big so i changed it and it all fuzzy now tried on diffrent resoultions none work. i'm on recovery settings at the min almost giving up.
please help if possible. cheers

---

### Post by JetarR on 2009-11-05
I know this is an old topic, but i spent the better part of two days getting Ubuntu 9.10 working on a Fujitsu-Siemens Amilo Pro v2030.

I got the same error as the other guy namely that the display operated at a virtual resolution of 1600x1200 even though being capable of a much smaller resolution.

I read this thread and made my own modded version of the xorg.conf (yes, Ubuntu 9.10 will use it if it is there) which is attached to this post

The problem with the xorg.conf from this thread is that it's written for a 1280*800 display, and the Amilo v2030 only has 1024*768.

Save the attached file (xorg.txt) on the desktop and rename the file (xorg.txt) to xorg.conf

Move the xorg.conf to /etc/X11/ and restart the machine.

The xorg.conf looks like this by the way:
--------------------------------------------------------
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
# sudo dpkg-reconfigure -phigh xserver-xorg
Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
Option "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "Emulate3Buttons" "true"
EndSection


Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizEdgeScroll" "0"
EndSection
Section "Device"
Identifier "Configured Video Device"
Boardname "vesa"
Busid "PCI:1:0:0"
Driver "openchrome"
Screen 0
Option "SWcursor" "true"
Option "EnableAGPDMA" "True"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
Vendorname "Generic LCD Display"
Modelname "LCD Panel 1024x800"
Horizsync 31.5-50.0
Vertrefresh 56.0 - 65.0
modeline "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
modeline "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
modeline "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
modeline "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
Gamma 1.0
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Configured Video Device"
Monitor "Configured Monitor"
Defaultdepth 24
SubSection "Display"
Depth 24
Modes "1024x768@60" "1280x768@60" "1280x720@60" "800x600@60" "1280x800@60" "800x600@56"
Virtual 1024 768
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
screen 0 "Default Screen" 0 0
Inputdevice "Synaptics Touchpad"
EndSection
Section "Module"
Load "glx"
Load "GLcore"
Load "dri"
Load "v4l"
EndSection
Section "device" #
Identifier "device1"
Boardname "vesa"
Busid "PCI:1:0:0"
Driver "openchrome"
Screen 1
EndSection
Section "screen" #
Identifier "screen1"
Device "device1"
Defaultdepth 24
Monitor "monitor1"
EndSection
Section "monitor" #
Identifier "monitor1"
Gamma 1.0
EndSection
Section "ServerFlags"
EndSection
--------------------------------------------------------
To make this post Google friendly:

Ubuntu UniChrome 1600x1200 Amilo Pro V2030
 :D

---

### Post by cova on 2010-01-09
Thanks for this JetarR. Was just installing Ubuntu on my Amilo and was going to have a play with the xorg.conf when I got home from work. Hopefully this should do the trick. Will let you know.

EDIT: Yeah, works great thanks. One small thing, I know my monitor can also support 1280x800. Any idea what value string i should add to the xorg for that with relation to the vsync and hsync? Much appreciated.

EDIT 2: Ended up just inserting the basic config and works fine with 1280x800 now.

---

