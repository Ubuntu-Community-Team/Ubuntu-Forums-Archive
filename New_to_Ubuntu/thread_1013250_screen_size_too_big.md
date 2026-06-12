---
title: "screen size too big"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by puglover on 2008-12-16
I just finished installing Ubuntu 8.10 on my laptop and when I booted up first it thinks my screen is larger than it actually is so a chunk of the right side and the bottom is cut off. Also I couldnt connect to the internet. I use a wireless hook up. Any assistance would be greatly appreciated.

---

### Post by starcannon on 2008-12-16
what video/graphics chipset is in your laptop?
If your unsure then please post the contents of
```
sudo lshw -C video
```

If your having trouble getting to a terminal because of screen resolution:
CTRL+ALT+F1 will take you to a terminal
CTRL+ALT+F7 will take you back to a GUI/Desktop

---

### Post by puglover on 2008-12-16
that command returned:

*-display UNCLAIMED
description: VGA compatible controller
product: CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro]
vendor: VIA Technologies, Inc.
physical id: 0
bus info: pci@0000:01:00.0
version: 01
width 32 bits
clock: 66MHz
capabilities: pm agp agp-3.0 bus_master cap_list
configureation: latency=64 mingnt=2

---

### Post by starcannon on 2008-12-16
Okay you have a:
> 
product: CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro]
vendor: VIA Technologies, Inc.

video card.
This card is a bit of a problem child, but can be made to work on some systems.
The drivers for the card are available here:
[http://linux.via.com.tw/](http://linux.via.com.tw/)
Link to yours in particular is:
[http://linux.via.com.tw/support/beginDownload.action?eleid=222&fid=483](http://linux.via.com.tw/support/beginDownload.action?eleid=222&fid=483)

You may get lucky and it just works, be sure to read any README files in the package, and if you run into problems post back here; I have some experience with these cards and will do what I can to help.

---

### Post by puglover on 2008-12-16
i have another problem...it wont connect to my wireless network...how would i do that??

---

### Post by starcannon on 2008-12-16
will it connect using a cable? if so lets solve the via graphics problem first, then we'll move on to the wifi problem next.
Please post the brand and model of the laptop were working on as well.

---

### Post by puglover on 2008-12-16
it can not connect thru a wire..the slot thingy is broken...my laptop is a gateway

---

### Post by puglover on 2008-12-16
how do i find out what kind of wi-fi card i have?...btw thanks for all your help

---

### Post by starcannon on 2008-12-16
is your wifi device usb, or a pc card that slides into the side of the computer, or is it onboard (came with the cumputer)?

---

### Post by puglover on 2008-12-16
came with the computer

---

### Post by starcannon on 2008-12-16
Okay, excellent, please post output of:
```
sudo lshw -C network
```

---

### Post by puglover on 2008-12-16
oh geez theres alot...and i dont have the pleasure of copy/paste...is there any line in particular your looking for??? or shud i just post the output  for network 0...which is the wireless interface

---

### Post by starcannon on 2008-12-16
yeah just the one thats your wifi card

---

### Post by theozzlives on 2008-12-16
Do lspci

---

### Post by puglover on 2008-12-16
description: wireless interface
product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
vendor: Realtek Semiconductor Co., Ltd.
physical id: e
bus info: pci@0000:00:0e.0
logical name: wmaster0
version: 20
serial: 00:c0:a8:b8:4c:20
width: 32 bits
clock: 33MHZ
capabilities: broadcast=yes driver=rtl8180 latecy=64 maxlatency=64 mingnt=32 module=rtl8180 multicast=yes wireless=IEEEE 802.11bg

---

### Post by starcannon on 2008-12-16
alright, sorry, i usually use gui for this, so had to do a bit of googling around:

post output of:
```
iwconfig
```
I am guessing that the wifi card will show up as wlan0 but lets make sure.

---

### Post by puglover on 2008-12-16
lo  no wireless extensions.
eth0 no wireless extenstions.
wmaster0 no wireless extentions.
wlan0  IEEE 802.11bg  ESSID:""
       Mode: Managed Frequency:2.412 GHz   Access Point: Not-Associated
       Tx-Power=27dBm
       Retry min limit:7   RTS thr:off   fragment thr=2352 B
       Power Management: Off
       Link Quality:0   Signal Level:0    Noise Level:0
       Rx invalid nwid:0   Rx invalid crypt:0 Rx invalid frag:0
       Tx excessive retries: 0   Invalid misc:0   Missed beacon:0

pan0  no wireless extensions.

---

### Post by starcannon on 2008-12-16
For WPA this guide should get you connected using terminal:
[http://www.newlinuxuser.com/howto-use-iwconfig/](http://www.newlinuxuser.com/howto-use-iwconfig/)

For WEP this one should do it:
[http://wirelessdefence.org/Contents/LinuxWirelessCommands.htm](http://wirelessdefence.org/Contents/LinuxWirelessCommands.htm)

once your connected we can work on the vid driver issue which should allow you to use entire GUI.

---

### Post by puglover on 2008-12-16
it didnt work...i did 
iwconfig [interface] mode managed key [WEP key]
it says SET failed on device wlan0: operation not permitted.

---

### Post by starcannon on 2008-12-16
[LIST=1]
[*]**iwconfig [interface]  mode managed key [WEP key] **(128 bit WEP use 26 hex characters, 64 bit WEP  uses 10)
[*]**iwconfig essid  "[ESSID]" **(Specify ESSID for the WLAN)
[*]**dhclient [interface] **(to receive an IP address, netmask, DNS server and default gateway from the Access  Point)
[*]**ping [www.bbc.co.uk](www.bbc.co.uk)  **(if you receive a reply you have access)
[/LIST]


So that would be:

[LIST=1]
[*]iwconfig wlan0 mode managed key yourkeyhere
[*]iwconfig essid "yourRouterNameHere"
[*]dhclient wlan0
[*]ping -c 4 [www.google.com](www.google.com) (if you receive a reply you have access)
[/LIST]

---

### Post by puglover on 2008-12-16
the error comes right after the first line...i do press enter at each line correct?? or is this all one command??

---

### Post by starcannon on 2008-12-16
enter after each line

---

### Post by puglover on 2008-12-16
ok well it says the key should be 26 or 10 characters long...mine is 16...so is it me doing something wrong right now??

---

### Post by starcannon on 2008-12-16
oh my bad sorry, run them as sudo

So that would be:

[LIST=1]
[*]sudo iwconfig wlan0 mode managed key yourkeyhere
[*]sudo iwconfig essid "yourRouterNameHere"
[*]sudo dhclient wlan0
[*]ping -c 4 [www.google.com]("http://www.google.com/") (if you receive a reply you have access)
[/LIST]

---

### Post by puglover on 2008-12-16
it said
error for wireless request "Set Encode" (8B2A):
invalid argument "mykey"

---

### Post by starcannon on 2008-12-16
Do you have any screen resolution options in:

System>Preferences>Screen Resolution

If so lets see if we can get you into the nm-applet gui and not have to worry about iwconfig

---

### Post by puglover on 2008-12-16
yes what should i change it to??...i feel like such a dork for not finding this earlier...i thought i looked everywhere!!

---

### Post by starcannon on 2008-12-16
If no options available in screen resolution, lets try a trick:


[LIST=1]
[*]R-click on the top panel or top menu bar, in a gray area
[*]Click on Properties
[*]Uncheck the Expand box
[/LIST]
Can you now see both ends of the bar?

If so

[LIST=1]
[*]Click on the nm-applet icon (looks like 2 little computers, generally next to the volume icon)
[*]Choose your wireless network from the menu
[*]Choose WEP or WPA whichever your network uses
[*]Fill in Password when asked
[/LIST]

---

### Post by starcannon on 2008-12-16
> **puglover said:**
> yes what should i change it to??...i feel like such a dork for not finding this earlier...i thought i looked everywhere!!

What are the choices?

P.S. I feel like a dork for assuming you'd have known about that :biggrin: lol /sigh, sometimes i miss the forest for the trees and assume the simplist solution has already been tried. anyway sorry for overcomplicating things a bit hehe

---

### Post by puglover on 2008-12-16
crap i clicked something a really messsed it up...im such a moron!! its huge and now i cant get back to it!!!

---

### Post by starcannon on 2008-12-16
hang on this is fixable

Please Press CTRL-ALT-F1

log in when it asks you to

Then enter the following commands:

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo dpkg-reconfigure -phigh xserver-xorg
sudo /etc/init.d/gdm restart

```

That should have you back where we started ;)

---

### Post by puglover on 2008-12-16
well i just did it the hard way and re-installed...hehe...ok now which resolution should i choose?? 
default is 1600 X 1200 (4:3)
other options are:
1400 X 1050 (4:3)
1280 X 1024 (5:4)
1280 X 800 (16:10)
1024 X 768 (4:3)
800 X 600 (4:3)
720 X 576 (5:4)
720 X 540 (4:3)
720 X 480 (3:2)
640 X 480 (4:3)

i believe my moniter is like 15 inches or something like that

---

### Post by starcannon on 2008-12-16
what model of gateway is that, I'll see if i can find out your monitors native resolution, though I will say generally the highest is the one you want. 

Also worth noting, reinstalling is not a necessary evil when all your doing is resetting the xserver to its defaults, those commands would have done that in about 1 minute ;) 

Anyway, post back the exact brand AND model of your laptop.

P.S. Brand and Model should be on a sticker on the bottom of the laptop

---

### Post by puglover on 2008-12-16
its a gateway mx3230

---

### Post by starcannon on 2008-12-16
I believe  1280 X 800 (16:10) should do it for you.

Info gleaned from 
[http://support.gateway.com/s/Mobile/Q106/MagicLC/2522998/2522998sp2.shtml](http://support.gateway.com/s/Mobile/Q106/MagicLC/2522998/2522998sp2.shtml)
[http://www.screentekinc.com/Gateway_MX3230--14-inch--1280x768-wxga-laptop-lcd-screen.shtml](http://www.screentekinc.com/Gateway_MX3230--14-inch--1280x768-wxga-laptop-lcd-screen.shtml)

More info about your laptop here:
[http://support.gateway.com/s/Mobile/Q106/MagicLC/1009037sp2.shtml](http://support.gateway.com/s/Mobile/Q106/MagicLC/1009037sp2.shtml)
and here:
[http://support.gateway.com/s/Mobile/Q106/MagicLC/1009037nv.shtml](http://support.gateway.com/s/Mobile/Q106/MagicLC/1009037nv.shtml)

---

### Post by puglover on 2008-12-16
thank you so much for all your help!

---

### Post by starcannon on 2008-12-16
Did that get your screen resolution managed? If so, are we ready to tackle the wifi?

---

### Post by puglover on 2008-12-16
the problem with the wi-fi was the screen size...i couldnt get to the icon to connect...i cant fix the screen resolution and the code you gave me doesnt work to put it back so i had to re-install it like 4 times already so i have given up...ill deal with the loss of space...but isnt there a recycle bin in the bottom right corner?? if so how do i get to that??

---

### Post by starcannon on 2008-12-16
the file manager address for the trash can is:
trash:///
thats right 3 slashes

to get there by cli
```

cd ./.local/share/Trash

```

I am curious though, does the display issue occur while running the live cd?

---

### Post by puglover on 2008-12-16
well when i ran the live cd the only icons on the desktop were install and one other one on top of install...but the top menu bar was normal...like i could see it from end to end

---

### Post by starcannon on 2008-12-16
please post output of:
```

cat /etc/X11/xorg.conf | grep Driver

```
I want to see what driver your xorg.conf is loading, if its trying to load the via driver, we may be able to get a working resolution by loading the vesa driver instead.

---

### Post by puglover on 2008-12-16
nothing happened when i piped it through grep so i deleted that and this is what came up

cat /etc/X11/xorg.conf 
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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

---

### Post by starcannon on 2008-12-17
okay cool, you have default xorg.conf there.

Lets see what module your using for your gpu, we'll take a couple guesses here.
First lets try:
```
glxinfo | grep server
```
if that gives up nothing then:
```
lsmod | grep vesa
```
and if nothing
```
lsmod | grep via
```

---

### Post by puglover on 2008-12-17
first one
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:

the others produce no results

---

### Post by starcannon on 2008-12-17
Hmmm, lets look at one more thing before we force a vesa driver
```
glxinfo | grep direct
```
then we'll force vesa.

---

### Post by puglover on 2008-12-17
direct rendering: Yes

---

### Post by starcannon on 2008-12-17
oh thats a bit unexpected.
Okay well lets do a little recapping here.

Is there anyway you can put skype on the computer your using for the forums here? If we could voice chat I think we could nail this thing down pretty quickly.

[http://www.skype.com](http://www.skype.com)

If not then proceeding as we have, I am hesitant to go vesa when you really just need to get the screen resolution right, you already have direct rendering, so we would have little left to do once we get resolution set.

So lets try this
```
gksu gedit /etc/X11/xorg.conf
```
Then:
```


# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
Modeline "1280x720@60"      73.78  1280 1312 1592 1624    720  735  742  757
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
    Subsection "Display"
        Depth "24"
        Modes "1280x720@60"
        Virtual 1280 720
    EndSubsection
EndSection 	

```
modify your file to look like that, if gedit is a pain in the asterik, then use nano instead. 
To save when using nano press CTRL+X then press Y, then press Enter.
Now reboot.
DO NOT REINSTALL if things don't work as expected, we can simply remove our changes using nano and try vesa as a last ditch effort.

---

### Post by puglover on 2008-12-17
how would i modify the file???

---

### Post by puglover on 2008-12-17
i think i did it...how do i kno if it took

---

### Post by starcannon on 2008-12-17
> **puglover said:**
> how would i modify the file???

oh sorry right I forgot to mention that bit:
```
sudo nano /etc/X11/xorg.conf
```make the changes, then:

[LIST=1]
[*]CTRL+X
[*]Press Y
[*]Press Enter
[/LIST]
Then reboot.
again, DO NOT reinstall, we can edit out our changes and go the vesa route as a last resort without need of rebooting.

---

### Post by starcannon on 2008-12-17
> **puglover said:**
> i think i did it...how do i kno if it took
reboot or CTRL+ALT+Backspace

addendum you can always just 
```
cat /etc/X11/xorg.conf
``` 
and see if your changes are there.

---

### Post by puglover on 2008-12-17
yea that totally didnt work it booted up with low graphics but wouldnt let me so i had to reboot again in recovery mode...and i think that put it back to normal

---

### Post by starcannon on 2008-12-17
Okay well vesa it is for now, lol, told ya via could be a pita ;)

so edit out the changes I had you make and instead make this change:
```
sudo nano /etc/X11/xorg.conf
```
Make your file look like this(were just adding the vesa driver to the Device section of the original xorg.conf file):
```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
Driver     "vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

[LIST=1]
[*]Press Ctrl+X
[*]Press Y
[*]Press Enter
[*]Press CTRL+ALT+Backspace
[/LIST]
If all went well its going to come back in a useable mode, albeit a bit spartan.

---

### Post by puglover on 2008-12-17
ok that didnt work either...it gave me a black screen with some red lines at the top...so again i rebooted into recovery mode and got back to where i was...i think im just gonna give up...everything i try seems to make it worse...at least i got past the part of re-installing everytime...hehe

---

### Post by starcannon on 2008-12-17
Puglover, I'll hang with you for as long as your willing, again skype would have shaved hours off of our troubleshooting, perhaps even gotten us there by now.
That said, if you like, just take a break, we can give it a shot again tomorrow; though I will say you have particularly challenging hardware. Intel(just works), Nvidia(easily made perfect), and ATi(moderately easy) are the easiest cards to deal with. VIA is a pain in the asteriks, and SiS is just horrid.

---

### Post by puglover on 2008-12-17
i dont have skype...isnt that a cam chat?? i dont have a cam...maybe tomorrow i'll give it another shot

---

### Post by starcannon on 2008-12-17
> **puglover said:**
> i dont have skype...isnt that a cam chat?? i dont have a cam...maybe tomorrow i'll give it another shot
Its text, voice, and cam. cam is optional, voice is optional.
Voice is all we'd use.
Gimme a holler tomorrow, I'll hang in there till we solve you. If you can lay your hands on a usb adapter to get your cat5 cable plugged in, I'd be willing to remote in and help out that way as well; I like a good challenge, and I think your's will turn out in working order, just a matter of getting it right.

Send me a PM when your on tomorrow, I'll check in on and off for you.

---

