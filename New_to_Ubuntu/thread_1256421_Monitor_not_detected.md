---
title: "Monitor not detected"
date: 2009-09-02
forum: New to Ubuntu
---

### Post by burtzacarach on 2009-09-02
In
System > Preferences > Display
My monitor isn't detected as "Unknown"
and the resolution defaults to
1600 x 1200 (4:3)

The desktop displays as shown:
[IMG]http://farm3.static.flickr.com/2590/3882415282_face7c2c50_b.jpg[/IMG]

and the red highlight is the viewable screen on my laptop, which is 1280 x 768
but when I switch my resolution to 1280 x 768, my screen basically looks shredded up and it's a pain to return it to something visible.
What other information can I provide for anyone to help?
What can I do to make my entire desktop visible?
I'm trying to permanently move to Linux, but all these fundamental things aren't working and I'd love to know how to fix them!
Thanks everyone!

---

### Post by NinjaNumberNine on 2009-09-02
System>Administration>Hardware Drivers
And if there are any proprietary drivers listed there install them!
Hope it helps, I've had lots of graphics problems with various "buntus". :D

---

### Post by burtzacarach on 2009-09-02
This is what I get:
[IMG]http://farm4.static.flickr.com/3482/3881664681_72bc3ccc69.jpg[/IMG]

The laptop which has JJ installed isn't connected to the internet yet, I'm using a portable hard drive to move files across two systems.

---

### Post by NinjaNumberNine on 2009-09-02
Okay, sorry, that means drivers aren't the issue. I'm looking it up right now...

---

### Post by NinjaNumberNine on 2009-09-02
Hey just a sec . Why is the refresh rate on 0 hz? Never seen that one before! Usually it is something like 60hz but maybe thats just for desktops, not laptops.

---

### Post by NinjaNumberNine on 2009-09-02
BTW is this your problem? [http://ubuntuforums.org/showthread.php?t=1234822&highlight=monitor+resolution+laptop](http://ubuntuforums.org/showthread.php?t=1234822&highlight=monitor+resolution+laptop) :confused:

---

### Post by Omegaham on 2009-09-02
Absolute beginner here.

I downloaded Ubuntu yesterday, made the switch today, and got the exact same problem, except I have a 1920x1080 screen and the resolution was 800x600. It also wasn't detecting the monitor.

However, I randomly got 220-something updates, restarted, and tried again... and this time it detected the drivers. Now it's working perfectly fine.

Right now, Ubuntu is a big black box to me, so I have no idea why it did it, but it did.

---

### Post by burtzacarach on 2009-09-02
It doesn't give me an option to change the refresh rate:
[IMG]http://farm3.static.flickr.com/2641/3882506762_da9e23a1aa.jpg[/IMG]

The topic at [http://ubuntuforums.org/showthread.php?t=1234822&highlight=monitor+resolution+laptop]("http://ubuntuforums.org/showthread.php?t=1234822&highlight=monitor+resolution+laptop")
could be my problem... but I don't know where to find xorg.conf!
where in the filesystem is xorg.conf and I will apply the changes and take screens of the results.

---

### Post by modmadmike on 2009-09-02
> **burtzacarach said:**
> It doesn't give me an option to change the refresh rate:
[IMG]http://farm3.static.flickr.com/2641/3882506762_da9e23a1aa.jpg[/IMG]

The topic at [http://ubuntuforums.org/showthread.php?t=1234822&highlight=monitor+resolution+laptop]("http://ubuntuforums.org/showthread.php?t=1234822&highlight=monitor+resolution+laptop")
could be my problem... but I don't know where to find xorg.conf!
where in the filesystem is xorg.conf and I will apply the changes and take screens of the results.
/etc/X11/xorg.conf is the location of xorg.conf (to find things like that you can usualy run ```
locate <name of file>
```

---

### Post by Znupi on 2009-09-02
**/etc/X11/xorg.conf**

Just one question: is the laptop with this problem connected to the internet? It must be connected in order to search for hardware drivers.

---

### Post by NinjaNumberNine on 2009-09-02
sudo nano etc/x11/xorg.conf

---

### Post by NinjaNumberNine on 2009-09-02
> Just one question: is the laptop with this problem connected to the internet? It must be connected in order to search for hardware drivers. That makes sense... :D

---

### Post by modmadmike on 2009-09-02
> **modmadmike said:**
> /etc/X11/xorg.conf is the location of xorg.conf (to find things like that you can usualy run ```
locate <name of file>
```

```
modmadmike@modmadmike-server:~/Desktop$ locate xorg.conf
/xorg.conf.new
/etc/X11/xorg.conf
/etc/X11/xorg.conf-backup-090716225347
/etc/X11/xorg.conf.20090719023211
/etc/X11/xorg.conf.20090724202158
/etc/X11/xorg.conf.20090725171538
/etc/X11/xorg.conf.20090726160909
/etc/X11/xorg.conf.20090726161013
/etc/X11/xorg.conf.backup
/etc/X11/xorg.conf.dist-upgrade-200907290238
/etc/X11/xorg.conf.failsafe
/etc/X11/xorg.conf~
/home/modmadmike/Documents/xorg.conf
/home/modmadmike/linuxwacom-0.8.0-2/wacom/xorg.conf
/home/modmadmike/wacom/xorg.conf
/home/modmadmike/wacom_new/xorg.conf
/usr/share/man/man5/xorg.conf.5.gz
``` This is what happens when you install the NVIDIA drivers too many times lol

---

### Post by burtzacarach on 2009-09-02
> **Znupi said:**
> **/etc/X11/xorg.conf**

Just one question: is the laptop with this problem connected to the internet? It must be connected in order to search for hardware drivers.

Yes, the laptop is having trouble. I don't believe i have any way to share my desktop's connection with my laptop, as I'm connected on the desktop with a USB EVDO modem, and in Windows it registers as a dial-up connection, so I can't bridge it to the desktop's ethernet port. If I could, that would be amazing.

---

### Post by modmadmike on 2009-09-02
> **burtzacarach said:**
> Yes, the laptop is having trouble. I don't believe i have any way to share my desktop's connection with my laptop, as I'm connected on the desktop with a USB EVDO modem, and in Windows it registers as a dial-up connection, so I can't bridge it to the desktop's ethernet port. If I could, that would be amazing.

just plug the EVDO card into the laptop and then set the connection to "USB CMDA modem"

EDIT: Click on Network Manager to get this option but if your not using Juanty this won't work though.

---

### Post by NinjaNumberNine on 2009-09-02
Uh huh, modems are kind of outdated.
But you can plug it in the linux laptop if it has a modem too and linux will recognize it and you can set it up temporarily to update drivers. But for that matter, ubuntu is practically nothing without internet.

---

### Post by Znupi on 2009-09-02
> **modmadmike said:**
> just plug the EVDO card into the laptop and then set the connection to "USB CMDA modem"
Or run around the block searching for a WiFi connection :D

On another note: if you get internet access, make sure to fully update your system first, before attempting to install any drivers.

---

### Post by modmadmike on 2009-09-02
> **Znupi said:**
> Or run around the block searching for a WiFi connection :D

or that lol

---

### Post by modmadmike on 2009-09-02
> **NinjaNumberNine said:**
> Uh huh, modems are kind of outdated.
But you can plug it in the linux laptop if it has a modem too and linux will recognize it and you can set it up temporarily to update drivers. But for that matter, ubuntu is practically nothing without internet.

Not realy EVDO/CMDA modems are new (Like Verizons USB 727)

I have one it looks like this:
[IMG]http://t3.gstatic.com/images?q=tbn:ThrrX0Pz3Dw7iM:http://friendlycomm.com/images/products/detail/Equipment_USB727_Left_LRG.gif[/IMG]

---

### Post by burtzacarach on 2009-09-02
> **modmadmike said:**
> Not realy EVDO/CMDA modems are new (Like Verizons USB 727)

I have one it looks like this:
[IMG]http://t3.gstatic.com/images?q=tbn:ThrrX0Pz3Dw7iM:http://friendlycomm.com/images/products/detail/Equipment_USB727_Left_LRG.gif[/IMG]

This is the exact one I use.

---

### Post by modmadmike on 2009-09-02
> **burtzacarach said:**
> This is the exact one I use.

Cool cause I use it with ubuntu so I know it works lol

---

### Post by NinjaNumberNine on 2009-09-02
>  
Or run around the block searching for a WiFi connection :grin:

 yeah, go to mcdonalds they have free WIFI at ours!
>  
Not realy EVDO/CMDA modems are new (Like Verizons USB 727)
 I meant the old PCI kind and I guess the word would be slower, not older.

---

### Post by burtzacarach on 2009-09-02
I don't know where Network Manager is, and when I plug in my modem and try to set up a Mobile Broadband connection in Network Connections, it doesn't really seem to do anything.
Based on this I believe I'm going to have to set up my monitor manually.
Here's my xorg.conf, I haven't done anything to it yet in fear of messing something up and having to re-install:
[IMG]http://farm4.static.flickr.com/3420/3882610524_a2c6a5df62_b.jpg[/IMG]

---

### Post by modmadmike on 2009-09-02
> **burtzacarach said:**
> I don't know where Network Manager is, and when I plug in my modem and try to set up a Mobile Broadband connection in Network Connections, it doesn't really seem to do anything.
Based on this I believe I'm going to have to set up my monitor manually.
Here's my xorg.conf, I haven't done anything to it yet in fear of messing something up and having to re-install:
[IMG]http://farm4.static.flickr.com/3420/3882610524_a2c6a5df62_b.jpg[/IMG]

Network manager is the icon with the bars next to the clock between the battery, display with ruler and volume control.

---

### Post by modmadmike on 2009-09-02
> **modmadmike said:**
> Network manager is the icon with the bars next to the clock between the battery, display with ruler and volume control.

example: 
[IMG]http://tigger.uic.edu/~gadget/UIC-Wireless/NetworkManager.550x310.jpg[/IMG]
[IMG]http://tigger.uic.edu/~gadget/UIC-Wireless/NetworkManager.connected.3of3.550x385.jpg[/IMG]

---

### Post by modmadmike on 2009-09-02
try runing ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by burtzacarach on 2009-09-02
> **modmadmike said:**
> example: 
[IMG]http://tigger.uic.edu/~gadget/UIC-Wireless/NetworkManager.550x310.jpg[/IMG]

Okay. My monitor resolution problem was cutting that off so i couldn't use it, but I set my main panel to net expand so i can see it now.
Now i'm using my laptop! very cool.
So now that i'm connected to the interwebz,
what can I do to get my monitor back?

[IMG]http://farm3.static.flickr.com/2648/3882657656_ab3e0d242a_b.jpg[/IMG]

---

### Post by modmadmike on 2009-09-02
> **burtzacarach said:**
> Okay. My monitor resolution problem was cutting that off so i couldn't use it, but I set my main panel to net expand so i can see it now.
Now i'm using my laptop! very cool.
So now that i'm connected to the interwebz,
what can I do to get my monitor back?

[IMG]http://farm3.static.flickr.com/2648/3882657656_ab3e0d242a_b.jpg[/IMG]

go into hardware drivers and see if anything appears.

EDIT: Try runing ```
jockey-gtk -c
``` and ```
jockey-gtk -m any
```

---

### Post by NinjaNumberNine on 2009-09-02
Search for drivers now or reboot computer.

---

### Post by Znupi on 2009-09-02
> **burtzacarach said:**
> 
So now that i'm connected to the interwebz,
what can I do to get my monitor back?


**System &#8594; Administration &#8594; Update Manager** and install all updates. After that, reboot. If it still doesn't work, **System &#8594; Administration &#8594; Hardware Drivers** and see if you get anything. If it still doesn't work, post.

Others seem to keep forgetting this (no offense, I just don't want the new user to screw his Ubuntu installation), although it is very important, so I will write it here in big letters:
[size=7][color="red"]**Install all updates first!**[/color][/size]

---

### Post by NinjaNumberNine on 2009-09-02
> System &#8594; Administration &#8594; Update Manager and install all updates. After that, reboot. If it still doesn't work, System &#8594; Administration &#8594; Hardware Drivers and see if you get anything. If it still doesn't work, post.

That'll take a couple hours, though. :D

---

### Post by modmadmike on 2009-09-02
> **modmadmike said:**
> go into hardware drivers and see if anything appears.

EDIT: Try runing ```
jockey-gtk -c
``` and ```
jockey-gtk -m any
```

I stand by these commands when it detects nothing.

---

### Post by Znupi on 2009-09-02
> **NinjaNumberNine said:**
> That'll take a couple hours, though. :D
Because of the modem? On a fresh install it installs all updates (I think around 200) in less than 10 minutes for me.

---

### Post by modmadmike on 2009-09-02
If all else fails try Karmic....... JK! I would not recommend karmic koala yet because its still in alpha and i hate the volume control lol.

---

### Post by Znupi on 2009-09-02
> **modmadmike said:**
> i hate the volume control lol.
Is it **WORSE** than the one in Jaunty!?

---

### Post by modmadmike on 2009-09-02
> **Znupi said:**
> Because of the modem? On a fresh install it installs all updates (I think around 200) in less than 10 minutes for me.

seems all the servers far away from me (like Switzerland) are faster than the ones near me (US) roflmao :P

---

### Post by modmadmike on 2009-09-02
> **znupi said:**
> is it **worse** than the one in jaunty!?

yup its the biggest p.o.s since vista!!!!!!!!!!!!!!

---

### Post by Znupi on 2009-09-02
> **modmadmike said:**
> seems all the servers far away from me (like Switzerland) are faster than the ones near me (US) roflmao :P
Heh, Romanian servers FTW

---

### Post by modmadmike on 2009-09-02
> **modmadmike said:**
> yup its the biggest p.o.s since vista!!!!!!!!!!!!!!

[Juanty]
[IMG]http://fc01.deviantart.com/fs48/f/2009/195/4/4/ASUS_XONAR_D2X_LINUX_by_modmadmike.png[/IMG]

[Karmic Alpha 3]
[IMG]http://fc09.deviantart.com/fs46/f/2009/210/0/3/Volume_control_P1_Karmic_by_modmadmike.png[/IMG]
[IMG]http://fc05.deviantart.com/fs47/f/2009/210/3/3/Volume_control_P2_Karmic_by_modmadmike.png[/IMG]
[IMG]http://fc05.deviantart.com/fs48/f/2009/210/4/b/Volume_control_P3_Karmic_by_modmadmike.png[/IMG]
[IMG]http://fc08.deviantart.com/fs48/f/2009/210/a/e/Volume_control_P4_Karmic_by_modmadmike.png[/IMG]
[IMG]http://fc04.deviantart.com/fs48/f/2009/210/d/7/Volume_control_P5_Karmic_by_modmadmike.png[/IMG]

SEEEEEE

---

### Post by NinjaNumberNine on 2009-09-02
Wow, that post slowed down my cpu chip by 50% like I knew it would!

---

### Post by modmadmike on 2009-09-02
> **modmadmike said:**
> yup its the biggest p.o.s since vista!!!!!!!!!!!!!!

> **NinjaNumberNine said:**
> Wow, that post slowed down my cpu chip by 50% like I knew it would!

my quad core ate it up lol

---

### Post by burtzacarach on 2009-09-02
> **Znupi said:**
> **System &#8594; Administration &#8594; Update Manager** and install all updates. After that, reboot. If it still doesn't work, **System &#8594; Administration &#8594; Hardware Drivers** and see if you get anything. If it still doesn't work, post.

Others seem to keep forgetting this (no offense, I just don't want the new user to screw his Ubuntu installation), although it is very important, so I will write it here in big letters:
[size=7][color="red"]**Install all updates first!**[/color][/size]

Ok, I've updated my system, and the only new driver I got was one for a modem, which I'm not even sure what it's for but I installed it anyway:
[IMG]http://farm3.static.flickr.com/2619/3882021409_2c0d5e2a91_b.jpg[/IMG]

And I tried the jockey-gtk commands, the first one returned nothing and the second brought up my Hardware Drivers dialog again, without any changes:
[IMG]http://farm4.static.flickr.com/3438/3882021413_ea098e7fcd.jpg[/IMG]

As you can see I'm still only using the top-left 3/4th of my monitor... NEED MORE WORKSPACE!
Although nothing has really worked yet, I thank you all for helping out; I'm actually having fun trying to troubleshoot this. And we've already got my modem working, so thanks again!

---

### Post by modmadmike on 2009-09-02
> **burtzacarach said:**
> Ok, I've updated my system, and the only new driver I got was one for a modem, which I'm not even sure what it's for but I installed it anyway:
[IMG]http://farm3.static.flickr.com/2619/3882021409_2c0d5e2a91_b.jpg[/IMG]

And I tried the jockey-gtk commands, the first one returned nothing and the second brought up my Hardware Drivers dialog again, without any changes:
[IMG]http://farm4.static.flickr.com/3438/3882021413_ea098e7fcd.jpg[/IMG]

As you can see I'm still only using the top-left 3/4th of my monitor... NEED MORE WORKSPACE!
Although nothing has really worked yet, I thank you all for helping out; I'm actually having fun trying to troubleshoot this. And we've already got my modem working, so thanks again!

did you try the command i posted a few pages back that goes ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` also try this: ```
sudo rm -f /etc/X11/xorg.conf
sudo cat /etc/X11/xorg.conf.failsafe > /etc/X11/xorg.conf
```

---

### Post by Znupi on 2009-09-02
Can you post the contents of the xorg.conf file? (Use ```
 tags, please)

> **modmadmike said:**
> did you try the command i posted a few pages back that goes sudo dpkg-reconfigure..... (can't remember the rest off the top of my head lol)

[code]sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by modmadmike on 2009-09-02
> **modmadmike said:**
> did you try the command i posted a few pages back that goes ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` also try this: ```
sudo rm -f /etc/X11/xorg.conf
sudo cat /etc/X11/xorg.conf.failsafe > /etc/X11/xorg.conf
```

the second set of comands will replace your xorg.conf with the xorg.conf.failsafe which may or may not work better (you have to restart for it to take effect)

---

### Post by modmadmike on 2009-09-02
> **modmadmike said:**
> the second set of comands will replace your xorg.conf with the xorg.conf.failsafe which may or may not work better (you have to restart for it to take effect)

Fixed

---

### Post by modmadmike on 2009-09-02
im gonna restart my computer to apply the dist upgrade from Karmic Alpha 3 to Alpha 4.... I may or may not be back for a while since my nvidia driver will most likely need to be reinstalled lol

EDIT: if it fails Ill be back only ill be using w3m to view the page so i wont see any pictures lol

---

### Post by burtzacarach on 2009-09-02
> **Znupi said:**
> Can you post the contents of the xorg.conf file? (Use ```
 tags, please)



[code]sudo dpkg-reconfigure -phigh xserver-xorg
```

yes, here you go:
[IMG]http://farm4.static.flickr.com/3420/3882610524_a2c6a5df62_b.jpg[/IMG]

---

### Post by burtzacarach on 2009-09-02
[IMG]http://farm4.static.flickr.com/3523/3882157489_38f0fab95a.jpg[/IMG]

---

### Post by burtzacarach on 2009-09-02
```
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
```

---

### Post by Znupi on 2009-09-02
Hmm, quite a bummer. It isn't able to fix itself, so you'll have to start hacking. Try searching for your graphics card model / laptop model + "ubuntu" on Google, see if anything comes up. Just for the record, post them here, too, so we can have a look.

---

### Post by burtzacarach on 2009-09-02
maybe should have searched first...
[http://ubuntuforums.org/showthread.php?t=776187&highlight=mx3231]("http://ubuntuforums.org/showthread.php?t=776187&highlight=mx3231")
i'm gonna try all of this.
Thanks for all your help!

---

### Post by Znupi on 2009-09-02
Good luck! :)

---

### Post by modmadmike on 2009-09-03
> **burtzacarach said:**
> maybe should have searched first...
[http://ubuntuforums.org/showthread.php?t=776187&highlight=mx3231]("http://ubuntuforums.org/showthread.php?t=776187&highlight=mx3231")
i'm gonna try all of this.
Thanks for all your help!

According to the link replace your xorg.conf with ```
# xorg.conf (xorg X Window System server configuration file)
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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "ZAxisMapping" "4 5"
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
Identifier "Generic Video Card"
Driver "vesa"
BusID "PCI:1:0:0"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 30-65
VertRefresh 30-60
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Generic Video Card"
Monitor "Generic Monitor"
DefaultDepth 16
SubSection "Display"
Modes "1280x768"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"

InputDevice "Synaptics Touchpad"
EndSection 
``` and reboot and it should work

---

### Post by burtzacarach on 2009-09-03
I only needed this
```
Section "Screen"
Identifier "Default Screen"
Device "Generic Video Card"
Monitor "Generic Monitor"
DefaultDepth 16
SubSection "Display"
Modes "1280x768"
EndSubSection
EndSection
```
section.

---

### Post by modmadmike on 2009-09-03
> **burtzacarach said:**
> I only needed this
```
Section "Screen"
Identifier "Default Screen"
Device "Generic Video Card"
Monitor "Generic Monitor"
DefaultDepth 16
SubSection "Display"
Modes "1280x768"
EndSubSection
EndSection
```
section.

true lol

---

### Post by NinjaNumberNine on 2009-09-03
So it works now? :D

I know, a lot _**I**_ helped, I got lost we got to the xorg.conf file too. Thank the mad mod, bro!

---

