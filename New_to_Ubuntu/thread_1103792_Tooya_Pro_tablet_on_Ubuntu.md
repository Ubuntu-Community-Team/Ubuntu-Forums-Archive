---
title: "Tooya Pro tablet on Ubuntu?"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by Nuticulus on 2009-03-23
Does anyone know how to get a Tooya Pro tablet working on Ubuntu? I have been trying and trying to find some information on this, but so far I haven't found anything useful. It's really fustrating... :(

Anyway, I don't want to have to use windows whenever I want to use the tablet, so please help! Feel free to ask if you need any more information.

---

### Post by Sef on 2009-03-23
1) What are your system specs?

2) What happens when you run the live cd?

---

### Post by Nuticulus on 2009-03-24
System specs: Intel Core 2 Duo 2.26 GHz, 2 Gb ram, with up-to-date Intrepid Ibex. Graphics card currently unknown, but I can easily find out should it be necessary.

When I run the live CD and use the tablet, it works fine for moving the mouse around, but if I apply pressure with the pen the tablet stops moving the mouse around for several seconds. There are also two buttons, the second of which has an effect identical to that of applying pressure. For the first button (pen "nib" end), I don't know what it is doing, except that when pressed over a Firefox tab it will close it.

---

### Post by Favux on 2009-03-24
Hi Nuticulus,

Is the Tooya Pro a product of PenPowerInc.?  That's what I'm getting.  After a quick google search it looks like PenPower support was added to the kernel.  But as a touchscreen?

So if I'm correct you probably want to get in touch with the manufacturer (PenPower?) and ask them about Ubuntu (or linux) support.  It is a USB 1.1 device, correct?

I have to admit looking at it it sure looks like a digitizer to me, not a touchscreen.

If it was a touchscreen then "evtouch" is probably the driver you'd want.  You probably have to configure your xorg.conf.

If it is a digitizer and emulates wacom well enough maybe the "linuxwacom" drivers would work.  And again xorg.conf configuration.

Without finding a tutorial or a HOW TO this could require some effort.  Here is the only real reference I found.  But it is from 4/08 and refers to a different (smaller) PenPower device than yours:

[http://www.linuxquestions.org/questions/linux-hardware-18/how-does-linux-handle-usb-mouse-634247/]("http://www.linuxquestions.org/questions/linux-hardware-18/how-does-linux-handle-usb-mouse-634247/")

So it's probably not that relevant.  They seem to be modifying "evtouch"'s C code.

Good luck!

---

### Post by Nuticulus on 2009-03-25
> **Favux said:**
> Hi Nuticulus,

Is the Tooya Pro a product of PenPowerInc.?  That's what I'm getting.  After a quick google search it looks like PenPower support was added to the kernel.  But as a touchscreen?

[COLOR="Red"]Yes, it is a product of PenPower. [/COLOR]

So if I'm correct you probably want to get in touch with the manufacturer (PenPower?) and ask them about Ubuntu (or linux) support.  It is a USB 1.1 device, correct?
port for the pen
I have to admit looking at it it sure looks like a digitizer to me, not a touchscreen.

[COLOR="Red"]I'm not quite sure what you mean by this, but it is similar to the Bamboo tablet, in that it rests on your desk and has a pen tool, as opposed to clipping over your screen or anything like that. I don't know what USB type it is, so is there any way to do this in the terminal?[/COLOR]

If it was a touchscreen then "evtouch" is probably the driver you'd want.  You probably have to configure your xorg.conf.

If it is a digitizer and emulates wacom well enough maybe the "linuxwacom" drivers would work.  And again xorg.conf configuration.

[COLOR="Red"]Ok, I'll try this out.[/COLOR]

Without finding a tutorial or a HOW TO this could require some effort.  Here is the only real reference I found.  But it is from 4/08 and refers to a different (smaller) PenPower device than yours:

[http://www.linuxquestions.org/questions/linux-hardware-18/how-does-linux-handle-usb-mouse-634247/]("http://www.linuxquestions.org/questions/linux-hardware-18/how-does-linux-handle-usb-mouse-634247/")

So it's probably not that relevant.  They seem to be modifying "evtouch"'s C code.

Good luck!
 
Thanks for your help!

---

### Post by Nuticulus on 2009-03-28
Solved it! :P I followed the instructions on [https://help.ubuntu.com/community/Wacom]("https://help.ubuntu.com/community/Wacom"), and then changed my xorg.conf file, and it now works perfectly. The lines I added to xorg.conf are shown below:

```
Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/wacom"
  Option        "Type"          "stylus"
  Option        "USB"           "on"
EndSection
Section "InputDevice"
  Driver        "wacom"
  Identifier    "pad"
  Option        "Device"        "/dev/input/wacom"
  Option        "Type"          "pad"
  Option        "USB"           "on"
EndSection
Section "ServerLayout"
  Identifier    "Default Layout"
  Screen        "Default Screen"
  InputDevice   "stylus"  "SendCoreEvents"
  InputDevice   "pad"
EndSection
```

Thanks for your help, everyone! :)

---

### Post by Favux on 2009-03-28
Hi Nuticulus,

Nice job!

Does your stylus have an eraser?  Does it have buttons?  If so how many?  Also did you use the 0.8.1-6 deb.s on Loic2's Wacom wiki?

---

### Post by Nuticulus on 2009-03-29
I did use both .deb packages for my system (i386). My stylus has two buttons, the current setting of which confuses me. I'm not sure exactly what they do, but they seem to have an identical function, and:

[LIST]
[*]In GIMP, the buttons allow me to drag the canvas around.
[*]In Firefox, they close a tab if the mouse is hovering over it.
[*]And on the desktop the buttons will open a file/folder (same as doubleclicking).
[/LIST]

Unfortunately, the stylus has no eraser: Just the sensitive pad and the stylus.

Now, if anyone could help me find/change the function of the two buttons, that would be really helpful... :)

---

### Post by Favux on 2009-03-29
Hi Nuticulus,

Thanks, so you're on linuxwacom 0.8.1-6.

That's interesting.  Even without being configured.  If your buttons accept Wacom format then try adding:
```
	Option		"Button2"	"2"  # make first button a middle button
	Option		"Button3"	"3"  # make second button a R button
```
to you stylus sections like:
```
Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/wacom"
  Option        "Type"          "stylus"
  Option        "USB"           "on"
	Option		"Button2"	"2"  # make first button a middle button
	Option		"Button3"	"3"  # make second button a R button
EndSection

```
Which should make the first button a middle mouse click and the second button a right mouse click.  With any luck.

---

### Post by cb951303 on 2009-03-29
so tooya pro uses wacom chipset. always good to know alternatives. how is the build quality comparing to a bamboo?

---

### Post by Nuticulus on 2009-03-30
Hi Favux,

I tried what you suggested, but due to my recent upgrade to Jaunty beta, all my xorg.conf lines were commented out with the line "commented out by update-manager, HAL is now used" at the start of my sections. I tried uncommenting that section and then inserting your code, but Ubuntu refused to show the login screen. Luckily I made a backup of xorg.conf beforehand and was able to replace it using backtrack.

I'm not quite sure what you mean by build quality, cb951303. This Tooya pro is my first graphics tablet.

---

### Post by cb951303 on 2009-03-30
> **Nuticulus said:**
> 
I'm not quite sure what you mean by build quality, cb951303. This Tooya pro is my first graphics tablet.

I mean, does it feel sturdy?

---

### Post by Favux on 2009-03-30
Hi Nuticulus,

The problem was probably with "ServerLayout".  That's usually what happens.  You have to configure it correctly when you "activate" a section.  Did you try the button configuration after going to the backup xorg.conf?

How are you liking Jaunty?  By the way, HAL commenting things out first started on the change from Hardy to Intrepid.  A lot of people didn't have backups.  And new people to Intrepid didn't know about the Wacom entries.  Their xorg.conf's were nearly "empty".  So believe it or not you were lucky!

Hi cb951303,

The picture I saw looked pretty slick.

---

### Post by Nuticulus on 2009-03-31
My backup xorg.conf was created after I upgraded to Jaunty beta, so it is also filled with commented lines. Jaunty beta looks pretty slick, although there are a couple of problems. I use Avant Window Navigator, and some of my applets won't start. :(  Oh well.

The tablet is very light and slim, but still feels fairly rugged. The stylus is a bit too light for my liking, but I did buy it for a relatively cheap price, and it now does everything I want (except for the button functionality).

---

### Post by Favux on 2009-03-31
Hi Nuticulus,

The button lines don't work?  Maybe you could show me your current xorg.conf?  I could at least take a look.

---

### Post by Nuticulus on 2009-04-01
Hi Favux

Here is my xorg.conf file:

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
	Load	"dbe"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection
###########################################
# commented out by update-manager, HAL is now used
#Section "InputDevice"
#        Identifier      "Synaptics Touchpad"
#        Driver          "synaptics"
#        Option          "SHMConfig"             "on"
#EndSection
###########################################
# commented out by update-manager, HAL is now used
#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "stylus"
#  Option        "Device"        "/dev/input/wacom" # USB ONLY?
#  Option        "Type"          "stylus"
#  Option        "USB"           "on"               # USB ONLY
#EndSection
# commented out by update-manager, HAL is now used
#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "pad"
#  Option        "Device"        "/dev/input/wacom"    # USB ONLY
#  Option        "Type"          "pad"
#  Option        "USB"           "on"                  # USB ONLY
#EndSection
Section "ServerLayout"
  Identifier    "Default Layout"
  Screen        "Default Screen"
# commented out by update-manager, HAL is now used
#  InputDevice   "stylus"  "SendCoreEvents"
# commented out by update-manager, HAL is now used
#  InputDevice   "pad"                      # For Intuos3/CintiqV5/Graphire4/Bamboo tablets
EndSection
```

---

### Post by Favux on 2009-04-01
Hi Nuticulus,

Check in Synaptics Package Manager to see what version of linuxwacom you have.  Search Wacom or wacom, I think it is 0.8.1-6 in Jaunty.  If it's not installed, go ahead and install it and the same version of wacom-tools.

Right now I think your tablet is being run by HAL (hardware abstraction layer) and a .fdi file.  That's why you don't have buttons.

This xorg.conf should work unless they've done something exotic in Jaunty.  Notice that I added a commented out "Synaptic Touchpad" in "ServerLayout".  If you removed the comments from that section without adding it to "ServerLayout" that might have broken X.  HAL should be able to run the Synaptic Touchpad fine.  Be sure to have a backup of your xorg.conf and be prepared for X to break like last time.
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

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#        Identifier      "Synaptics Touchpad"
#        Driver          "synaptics"
#        Option          "SHMConfig"             "on"
#EndSection

Section "InputDevice"
  Identifier    "stylus"
  Driver        "wacom"
  Option        "Device"        "/dev/input/wacom" # USB ONLY?
  Option        "Type"          "stylus"
  Option        "USB"           "on"               # USB ONLY
	Option		"Button2"	"2"  # make first button a middle button
	Option		"Button3"	"3"  # make second button a R button
EndSection

Section "InputDevice"
  Identifier    "pad"
  Driver        "wacom"
  Option        "Device"        "/dev/input/wacom"    # USB ONLY
  Option        "Type"          "pad"
  Option        "USB"           "on"                  # USB ONLY
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection

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
	Load	"dbe"
EndSection

Section "ServerLayout"
  Identifier    "Default Layout"
  Screen        "Default Screen"
# commented out by update-manager, HAL is now used
#	Inputdevice	"Synaptics Touchpad"
  InputDevice   "stylus"  "SendCoreEvents"
  InputDevice   "pad"                      # For Intuos3/CintiqV5/Graphire4/Bamboo tablets
EndSection
```

Good luck!

---

### Post by Nuticulus on 2009-04-02
> **Favux said:**
> Hi Nuticulus,

Check in Synaptics Package Manager to see what version of linuxwacom you have.  Search Wacom or wacom, I think it is 0.8.1-6 in Jaunty.  If it's not installed, go ahead and install it and the same version of wacom-tools.

[COLOR="Red"]Yep, that's the one.[/COLOR]

Right now I think your tablet is being run by HAL (hardware abstraction layer) and a .fdi file.  That's why you don't have buttons.

[COLOR="Red"]What does the .fdi file do?[/COLOR]

This xorg.conf should work unless they've done something exotic in Jaunty.  Notice that I added a commented out "Synaptic Touchpad" in "ServerLayout".  If you removed the comments from that section without adding it to "ServerLayout" that might have broken X.  HAL should be able to run the Synaptic Touchpad fine.  Be sure to have a backup of your xorg.conf and be prepared for X to break like last time.

[COLOR="Red"]Ok, it broke again. Is there any way to stop HAL from running the tablet? Also, how did HAL determine what hardware to run?[/COLOR]



I guess I should have waited until I had the tablet fully working before upgrading to Jaunty beta. Oh well... :|

---

### Post by Favux on 2009-04-02
Hi Nuticulus,

That may have been a good idea.  So the linuxwacom driver 0.8.1-6 was already installed?

The .fdi file for wacom is the 10-wacom.fdi file.  It should be somewhere in /usr/share/hal/fdi/policy/20thirdparty/.  Or it might be in /etc/hal/fdi/policy/20thirdparty/.  If you look in it you'll see it is in "html" and there is also Waltop and N-trig in addition to Wacom.  You would be looking for something similar, but it would not necessarily be called Tooya Pro.fdi or PenPower.fdi.  May tablet.fdi or touch.fdi, etc.  The Wacom wiki links to this:

[https://help.ubuntu.com/community/Wacom.fdi]("https://help.ubuntu.com/community/Wacom.fdi")

Remember I said I found indications that support had been added to the kernel for PenPower.  And something about "evtouch", which is the touch pad driver.  Your finger is sensed like a stylus.  And you can use a stylus.  But it is not as accurate as a digitizer.

I do not know why X is being broken when you boot.  Several people have reported the linuxwacom driver does not work right in Jaunty.  I've only seen one person who said it did (I helped him set up his tablet pc).  I know evtouch also broke.  Both apparently because of the new Xserver in Jaunty, version 1.6.  Intrepid has 1.5.  I know Tom Jaeger fixed evtouch for Jaunty, but you have to get his fixed evtouch.  It's not in the Ubuntu repositories.  Also the ATI proprietary driver "fglrx" was broken and may still be having problems.

So all you can use for now is the .fdi file.  I know you could not use eraser or touch with HAL, but I'm not certain about buttons.  Maybe a custom .fdi file could be created to work.  And wacomcpl did not work with HAL and .fdi, so you couldn't calibrate your tablet.  I don't know about pressure in Gimp etc.

Edit:  A wild idea from something I just read.  Try it after commenting out the Wacom lines in "ServerLayout" in the xorg.conf I posted in #17 above, ie like:
```
Section "ServerLayout"
  Identifier    "Default Layout"
  Screen        "Default Screen"
# commented out by update-manager, HAL is now used
#	Inputdevice	"Synaptics Touchpad"
#  InputDevice   "stylus"  "SendCoreEvents"
#  InputDevice   "pad"                      # For Intuos3/CintiqV5/Graphire4/Bamboo tablets
EndSection
```
And be prepared for it to break again.  May be worth a shot.

---

### Post by Nuticulus on 2009-04-02
> **Favux said:**
> Edit:  A wild idea from something I just read.  Try it after commenting out the Wacom lines in "ServerLayout" in the xorg.conf I posted in #17 above, ie like:
```
Section "ServerLayout"
  Identifier    "Default Layout"
  Screen        "Default Screen"
# commented out by update-manager, HAL is now used
#	Inputdevice	"Synaptics Touchpad"
#  InputDevice   "stylus"  "SendCoreEvents"
#  InputDevice   "pad"                      # For Intuos3/CintiqV5/Graphire4/Bamboo tablets
EndSection
```
And be prepared for it to break again.  May be worth a shot.

Hi Favux,

It worked, sort of. After I changed the xorg.conf file there didn't appear to be any changes: the buttons still have the same effect (I now think they act as a middle mouse button).

---

### Post by Favux on 2009-04-02
Hi Nuticulus,

Interesting.  So the buttons now work, maybe not quite the way you wanted?  But they work?  See in Intrepid or anything earlier either the wacom sections wouldn't work or Xserver would be broken.  But if the buttons are now working and they weren't before then something other than the .fdi file is working.  Weird.  Can you now calibrate with wacomcpl?  Type it in a terminal and a gui will pop up.  If you see stylus on the left the xorg.conf is working.  You can click on it and calibrated your stylus.

---

### Post by Nuticulus on 2009-04-02
Hi Favux

I tried calibrating with*wacomcpl*, and there was just an empty menu to the left, so no luck there. The buttons were having the same effect when I had xorg.conf almost completely commented out by HAL.

---

### Post by Favux on 2009-04-02
Hi Nuticulus,

Ok, then it still sounds like it's HAL and the .fdi file running things.  So you can comment out the wacom sections too.  You'll have to track down where your .fdi file is and see if anyone has customized one with stylus buttons (if that's possible).  Thanks for giving it a shot.

Thinking about it the guy whose tablet pc worked was a serial tablet pc.  Everybody so far who said they couldn't get it to work in Jaunty had a usb tablet or tablet pc.  What do you think, coincidence?

---

### Post by Nuticulus on 2009-04-04
Hi Favux

Found the .fdi file: is there any way to "convert" xorg.conf to a .fdi file? I looked online, but I couldn't really find anything. The thing about the usb tablets definitely does not look like a coincidence :p. I'll see how it goes, but really I'm not all that troubled by the buttons, as the other functions work fine.

---

### Post by Favux on 2009-04-04
Hi Nuticulus,

> is there any way to "convert" xorg.conf to a .fdi file?
It's been about 4-5 months since I looked at the .fdi file stuff.  I started learning it when it looked like that's what we'd have to do.  I have a vague memory of someone kind of showing that.  I'd look at the Wacom wiki that links to the Wacom .fdi stuff and see if there is anything there.

And this might be of some use:

[http://ubuntuforums.org/showthread.php?t=948154]("http://ubuntuforums.org/showthread.php?t=948154")

Good luck!  Please let me know if you figure something out.

---

### Post by Nuticulus on 2009-04-05
Hi Favux,

Still searching...

If my tablet is being run by HAL and the .fdi file, whereas previously it was being run by the xorg.conf file, is there any way to stop HAL from running it and make xorg run it again?

---

### Post by Favux on 2009-04-05
Hi Nuticulus,

I guess to make sure it isn't HAL the thing to do would be to rename the .fdi file, like changing 10-wacom.fdi to something else.  Say 10-wacom.bak.  You didn't tell me the name of the .fdi file you found.  That should disable it.

Since the stylus is working, apparently with the default linuxwacom 0.8.1-6 driver then either it works with the new Xserver 1.6 natively or has been patched to work with it.  If it has been patched could this be causing a problem with xorg.conf?  Or is it that Xorg has just deprecated xorg.conf further?  Also if patched has wacom-tools been patched too?

This is the kind of thing I've been wondering.  The LWP (linux wacom project) just released a new development version 0.8.3-1.  But they say it doesn't yet work with Xserver 1.6 but 0.8.3-2 will!  So I really don't know what's going on.

You could rename the .fdi file and try the standard xorg.conf with the button entries and see what happens.  As long as you are prepared to recover from a broken X.  It broke with the wacom entries in "ServerLayout" right?  But not when you commented out the wacom entries in "ServerLayout", I think you said.  That may be the sticking point.  Are we suppose to be doing something new and different in "ServerLayou"?  And if so what?

Sorry to lay all this on you.  Just some thoughts.

---

### Post by Nuticulus on 2009-04-06
Hi Favux,

I tried deleting 10-wacom.fdi file with no obvious effects. You said before that HAL used to manage tablets and such on Ubuntu 8.10, so how did it switch to being managed by xorg?

Don't worry about bombarding me with ideas: I'm getting more and more interested in the way the system works by this problem.

---

### Post by Favux on 2009-04-06
Hi Nuticulus,

Boy I hope you meant renaming not deleting.  Anyway didn't you say you found another .fdi file that had your tablet's name in it?  That would be the one running things not the 10-wacom.fdi.  I just used that as an example because you didn't give me the name of that .fdi file.

Xorg's Xserver configures input through xorg.conf.  But that has limitations, like not allowing for hotplugging.  At least not in a natural way.  So starting in Intrepid they introduced HAL (hardware abstraction layer) which uses the .fdi files for configuration of input instead of xorg.conf.  This was to allow hotplugging and other goodness.  But what they didn't realize is that there was a limitation.  HAL could only see one input device.  Since Wacom tablets have multiple input devices along the same input path you in effect only got the stylus.  Not the eraser or touch, etc.  But after they finally realized that they speculated that they could use dBUS to get around this.  DBUS is another basic hardware detection thing.

What you did by configuring xorg.conf with the Wacom sections when you were on Intrepid was to fool the linuxwacom drivers into thinking you had a Wacom tablet.  But apparently in Jaunty the .fdi file for the Tooya Pro isn't being fooled.  It knows your tablet.  Or maybe it is the other way around, the Wacom.fdi knows your tablet isn't a Wacom.  Which ever.

So the question is could we figure out the identifier in the Tooya Pro.fdi file and put it in the Wacom.fdi file and fool it into working with the linuxwacom drivers again?  Or are you happy with the results from whichever drivers are being used?  Something else we haven't figured out.  Unless you have?

Now in breaking news Timo Aaltonen thinks he's overcome the limitation on the HAL/.fdi file combination.  He borrowed it from the Fedora guys.  He wants people to try it in Jaunty.  If it works he's hoping to get it added to Jaunty.  See post #65 here:

[http://ubuntuforums.org/showthread.php?t=1038949&page=7](http://ubuntuforums.org/showthread.php?t=1038949&page=7)

Interesting, isn't it?

---

### Post by Nuticulus on 2009-04-08
Hi Favux,

Sorry for my late reply: I've been completely bogged down by schoolwork. I did mean renaming, not deleting :). I did a search for .fdi files and the only one that seemed relevant to the tablet was 10-wacom.fdi: there wasn't any called tooya.fdi or anything like that. I'll keep trying to get the buttons working, but I really don't mind one way or the other about the buttons: the main thing that I need is the pen functionality.

That post *was* interesting, thanks!

---

