---
title: "Newbie with a Wacom Bamboo problem..."
date: 2009-04-09
forum: New to Ubuntu
---

### Post by MZ250Supa5 on 2009-04-09
I'm trying to get full functionality for my Wacom Bamboo tablet, and having looked through the forum, have ended up confused.  Whilst far from stupid, I am quite new to Ubuntu, and have yet to get used to the sometimes overly 'geeky' information in the technical help sections - "Wacom Troubleshooting" undoubtedly has all the answers needed, but from what I can fathom, assumes rather too much - it's confusing to someone coming from a Windows XP environment where everything either works, or doesn't.  To be presented with a lot of unfathomable commands, in that no easy-to-understand, (read: idiot-proof) way of using this info in, I assume, Terminal is frustrating for a newbie like me. 

On of the great things about Linux is that it can be 'tweaked' or otherwise played around with, is 'free' and has a great support community, but not everyone wants to get technical.  I can appreciate that the 'geeks' love nothing better than playing around with code etc, (just as I like to take car/motorbike engines apart for fun) but many people want a solution that is straightforward to follow, and relatively easily implemented.  I just want my Bamboo to work as well as it did under Windows XP, so a simply and clearly set out set of instructions would be greatly appreciated.

---

### Post by anewguy on 2009-04-09
Okay, if you state what problems you are having with the tablet (error messages, etc.) it will give us somewhere to start :;

dave :)

---

### Post by MZ250Supa5 on 2009-04-09
Thanks for getting back to me so promptly Dave.

I've installed the xorg input for wacom and wacom tools, and thus far still have only the basic funtctionality of the tablet.  Here is where it all gets a bit difficult: having consulted the 'Troubleshooting' section, it all just went a bit blurry, as I was faced with a seemingly inpenetrable set of words surrounded with quotation marks - I've sufficient nous, (I think...) to realise that all this relates to some way of inputting the information so that it gets the tablet working as it should.

Thus far I haven't attempted to go any further as I risk confusing myself even more, but basically I need to be able to 'translate' what all the quotation marks, etc relate to in the 'Troubleshooting' section.  I know that I'm not the first to have ad all these problems, so it does surprise me a little that no-one has put a concise way of installing wacom tablets in one of the posts - the only reference I can find is where someone thanks someone else for useful information without posting that 'useful information'. Frustrating indeed!  I don't mind having to type in commands, as it's a quick, efficient and pretty foolproof way of installing packages.

Having had a good sleep on the problem, I shall try again and see if I can make more sense of it all.

Padi.

---

### Post by Favux on 2009-04-09
[https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)

---

### Post by MZ250Supa5 on 2009-04-09
Thanks Favux, but it still doesn't solve my fundamental problem, I'm not stupid by a long way, but I am _very_new to Ubuntu, and as I've explained previously, need specific and simple-to-understand explanations - there's too much re-directing to different pages, ( a common fault with technical publication) - what is needed is a gentle, step-by-step guide, in one place that is *systematic*, and doesn't involve someone jumping here, there and everywhere else.  Agreed, once someone is a more experienced user, the above has less relevancy, but it's the early stages that have such a huge impact on perceptions - if people find something initially hard to understand/embrace they will naturally give up - I know this from having spent years teaching a language often perceived as 'difficult' (yet one I learned as an adult to fluency, and didn't find at all difficult, just a lot of work, which is something else).

I've tried to get my pad working, and have been at it now for three hours, and am now somewhat brain-drained.

I'm not very good at solving IT technical problems, but I am a good communicator, and would be happy to compile a 'user friendly' HowTo once others supply me with the techie stuff - but of course, I need to understand it myself first!:confused:

---

### Post by anewguy on 2009-04-09
I found this link which I think is about as simple as it's going to get for doing this:

[http://ubuntuforums.org/showthread.php?t=765915]("ubuntuforums.org/showthread.php?t=765915")

There are varying quote marks in that post.  The ones that look like a single quote tilted on it's side a little is actually what I call (how's this for technical :) ) a "tick" mark, and is on my keyboard with the key that has the tilde (~).  Other single quotes in there are straight up and down, and they are just regular single quote marks (on my keyboard with the key that has the double-quote marks (") ).  I know that one just passes in the text (the single quote one) whereas the one with the tilted quote, the "tick" mark, actually has substitution take place.  Not sure exactly what they do in that post, but you probably don't really need to know to make it work - just copy the text and paste it in a command line (applications/accessories/terminal).  Just do that copy and paste for each group of instructions.  If you have any questions, post back and we'll try to answer!

dave :)

---

### Post by Favux on 2009-04-09
Hi MZ250Supa5,

No need to compile the driver.  Go to the link I gave you.  Near the top are links to deb.s (Debian packages).  They are under the header "1. Download the updated packages:".  Download both the 0.8.1-6 deb.s for your cpu architecture to your desktop.  You haven't mentioned what hardware you are attaching the bamboo to.  Double-click on them and they will install themselves through the Debian package manager.  Afterwards they'll show up in Synaptic package manager just as if synaptic had installed them.  This is step one.

---

### Post by MZ250Supa5 on 2009-04-10
Have downloaded and installed the packages, and they appear in Synaptic as installed.  The hardware the Bamboo is attached to is GeForce6100PM-M2 mother board running an AMD Athlon  64 x2 4400+ with 2GB of RAM

---

### Post by MZ250Supa5 on 2009-04-10
Apologies if this is appearing for the second time, my last reply seemed to disappear.

I have downloaded and installed both packages, and they are apparent in synaptic as installed. The hardware the Bamboo is attached to comprises a GeForce 6100M-M2 motherboard, AMD Athlon 64 X2 4400+ processor and "GB of RAM, though I'm running the 32 bit version of Ubuntu 8.10 as I have been led to believe that it's not worth installing the 64 bit version unless there's 4GB or more RAM available.

---

### Post by Favux on 2009-04-10
Hi MZ250Supa5,

I think you were misinformed.  A 32-bit OS will only see a maximum of 3.2 GB whereas a 64-bit has no RAM limitation (in theory).  But 64-bit is theoretically faster because it's executing twice as much (64 vs 32) at a time.  But in reality you wouldn't notice it except in certain situations.

So which architecture did you install?  Amd64 or i386.  The Debian package manager probably wouldn't let you goof, it would balk if it was incompatible.

After a reboot to see if the install was successful type (actually copy and paste) in a terminal:
```
dmesg | grep [Ww]acom
```
and
```
modinfo -d wacom
```
The output should contain Wacom etc.

Onto step 2.
To edit xorg.conf you need to be root.  You type sudo in a terminal to get root privileges.  Since you will be using gedit (gnome edit) you want to use the graphical version of sudo which is gksudo.  The xorg.conf lives in "/etc/X11/xorg.conf".  So you would type:
```
gksudo gedit /etc/X11/xorg.conf
```
You want to be careful since you can break X (not be able to boot into a graphical desktop) if you mess up.  So first back up xorg.conf with the copy (cp) command.
```
cp /etc/X11/xorg.conf /etc/X11/my_xorg.bak
```
or whatever name you would like.  To restore the back up you just reverse things:
```
cp /etc/X11/my_xorg.bak /etc/X11/xorg.conf
```
What I need to see is your current xorg.conf.  If you don't want to risk damaging it you can copy it without being root.  Just use nautilus (Places on the top menu bar) and navigate to it.  Copy and paste it into the code tags using "#" at the top of the post box.

Edit:  Oh, you have a stylus.  Does it have an eraser?  Does it have buttons on the stylus?  How many?  You don't have a Wacom mouse, correct?  Do you have a Wacom Pad, which is a cluster of buttons and maybe a slider or two on the tablet?

---

### Post by MZ250Supa5 on 2009-04-10
Thanks again for all this Favux, your patience is much appreciated.

This is the output from Terminal:

padi@padi-desktop:~$ dmesg | grep [Ww]acom
[   14.323091] usbcore: registered new interface driver wacom
[   14.323097] wacom: v1.49:USB Wacom Graphire and Wacom Intuos tablet driver

and subsequently:

padi@padi-desktop:~$ modinfo -d wacom
modinfo: could not open wacom: No such device

Current xorg.conf is:

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
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection


For some reason Terminal wouldn't let me back xorg,conf.  I'm using a Bamboo MT 450A which has four buttons, and a central circular slider control.  The stylus has an eraser and two buttons equating to right and left click

---

### Post by Favux on 2009-04-10
Hi MZ250Supa5,

Sorry, try preceeding the cp commands with sudo.  Like "sudo cp etc."  It will ask for your password.

I'll work on your xorg.conf.

---

### Post by Favux on 2009-04-10
Hi MZ250Supa5,

Assuming you've now backed up your xorg.conf now edit it with the "gksudo gedit etc.".  I would just copy and paste this one completely replacing yours.  Then reboot.  You may have to reboot a few times and restart X a few times.  To restart X use "ctrl-alt-backspace".

You are using Intrepid (8.10) correct?  I ask because there wasn't a "ServerLayout" section at the bottom of your xorg.conf.

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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
Identifier "stylus"
Driver "wacom"
Option "Device" "/dev/input/wacom"
Option "Type" "stylus"
Option "USB" "on" # USB ONLY
Option "Button2" "2"  # make first button a middle button
Option "Button3" "3"  # make second button a R button
EndSection

Section "InputDevice"
Identifier "eraser"
Driver "wacom"
Option "Device" "/dev/input/wacom"
Option "Type" "eraser"
Option "USB" "on" # USB ONLY
EndSection

Section "InputDevice"
Identifier "pad"
Driver "wacom"
Option "Device" "/dev/input/wacom"
Option "Type" "pad"
Option "USB" "on" # USB ONLY
EndSection

Section "Device"
Identifier "Configured Video Device"
Driver "fglrx"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 24
EndSection

Section "Module"
Load "glx"
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "stylus" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
InputDevice "pad" # For Intuos3/CintiqV5/Graphire4/Bamboo tablets
EndSection
```

Good luck!

---

### Post by MZ250Supa5 on 2009-04-10
Hi Favux.

Yes, I am using Intrepid 8.10, I think I must have ommitted to copy the end of the the xorg.conf readout.

I have tried the xorg.conf above, and I got this in response:

padi@padi-desktop:~$ gksudo gedit etc
padi@padi-desktop:~$ # xorg.conf (X.Org X Window System server configuration file)
padi@padi-desktop:~$ #
padi@padi-desktop:~$ # This file was generated by dexconf, the Debian X Configuration tool, using
padi@padi-desktop:~$ # values from the debconf database.
padi@padi-desktop:~$ #
padi@padi-desktop:~$ # Edit this file with caution, and see the xorg.conf manual page.
padi@padi-desktop:~$ # (Type "man xorg.conf" at the shell prompt.)
padi@padi-desktop:~$ #
padi@padi-desktop:~$ # This file is automatically updated on xserver-xorg package upgrades *only*
padi@padi-desktop:~$ # if it has not been modified since the last upgrade of the xserver-xorg
padi@padi-desktop:~$ # package.
padi@padi-desktop:~$ #
padi@padi-desktop:~$ # If you have edited this file but would like it to be automatically updated
padi@padi-desktop:~$ # again, run the following command:
padi@padi-desktop:~$ # sudo dpkg-reconfigure -phigh xserver-xorg
padi@padi-desktop:~$ 
padi@padi-desktop:~$ Section "InputDevice"bash: Section: command not found
padi@padi-desktop:~$ Identifier "stylus"
bash: Identifier: command not found
padi@padi-desktop:~$ Driver "wacom"
bash: Driver: command not found
padi@padi-desktop:~$ Option "Device" "/dev/input/wacom"
bash: Option: command not found
padi@padi-desktop:~$ Option "Type" "stylus"
bash: Option: command not found
padi@padi-desktop:~$ Option "USB" "on" # USB ONLY
bash: Option: command not found
padi@padi-desktop:~$ Option "Button2" "2"  # make first button a middle button
bash: Option: command not found
padi@padi-desktop:~$ Option "Button3" "3"  # make second button a R button
bash: Option: command not found
padi@padi-desktop:~$ EndSection
bash: EndSection: command not found
padi@padi-desktop:~$ 
padi@padi-desktop:~$ Section "InputDevice"bash: Section: command not found
padi@padi-desktop:~$ Identifier "eraser"
bash: Identifier: command not found
padi@padi-desktop:~$ Driver "wacom"
bash: Driver: command not found
padi@padi-desktop:~$ Option "Device" "/dev/input/wacom"
bash: Option: command not found
padi@padi-desktop:~$ Option "Type" "eraser"
bash: Option: command not found
padi@padi-desktop:~$ Option "USB" "on" # USB ONLY
bash: Option: command not found
padi@padi-desktop:~$ EndSection
bash: EndSection: command not found
padi@padi-desktop:~$ 
padi@padi-desktop:~$ Section "InputDevice"bash: Section: command not found
padi@padi-desktop:~$ Identifier "pad"
bash: Identifier: command not found
padi@padi-desktop:~$ Driver "wacom"
bash: Driver: command not found
padi@padi-desktop:~$ Option "Device" "/dev/input/wacom"
bash: Option: command not found
padi@padi-desktop:~$ Option "Type" "pad"
bash: Option: command not found
padi@padi-desktop:~$ Option "USB" "on" # USB ONLY
bash: Option: command not found
padi@padi-desktop:~$ EndSection
bash: EndSection: command not found
padi@padi-desktop:~$ 
padi@padi-desktop:~$ Section "Device"
bash: Section: command not found
padi@padi-desktop:~$ Identifier "Configured Video Device"
bash: Identifier: command not found
padi@padi-desktop:~$ Driver "fglrx"
bash: Driver: command not found
padi@padi-desktop:~$ EndSection
bash: EndSection: command not found
padi@padi-desktop:~$ 
padi@padi-desktop:~$ Section "Monitor"
bash: Section: command not found
padi@padi-desktop:~$ Identifier "Configured Monitor"
bash: Identifier: command not found
padi@padi-desktop:~$ EndSection
bash: EndSection: command not found
padi@padi-desktop:~$ 
padi@padi-desktop:~$ Section "Screen"
bash: Section: command not found
padi@padi-desktop:~$ Identifier "Default Screen"
bash: Identifier: command not found
padi@padi-desktop:~$ Monitor "Configured Monitor"
bash: Monitor: command not found
padi@padi-desktop:~$ Device "Configured Video Device"
bash: Device: command not found
padi@padi-desktop:~$ DefaultDepth 24
bash: DefaultDepth: command not found
padi@padi-desktop:~$ EndSection
bash: EndSection: command not found
padi@padi-desktop:~$ 
padi@padi-desktop:~$ Section "Module"
bash: Section: command not found
padi@padi-desktop:~$ Load "glx"
bash: Load: command not found
padi@padi-desktop:~$ EndSection
bash: EndSection: command not found
padi@padi-desktop:~$ 
padi@padi-desktop:~$ Section "ServerLayout"
bash: Section: command not found
padi@padi-desktop:~$ Identifier "Default Layout"
bash: Identifier: command not found
padi@padi-desktop:~$ Screen "Default Screen"
bash: Screen: command not found
padi@padi-desktop:~$ InputDevice "stylus" "SendCoreEvents"
bash: InputDevice: command not found
padi@padi-desktop:~$ InputDevice "eraser" "SendCoreEvents"
bash: InputDevice: command not found
padi@padi-desktop:~$ InputDevice "pad" # For Intuos3/CintiqV5/Graphire4/Bamboo tablets
bash: InputDevice: command not found
padi@padi-desktop:~$ EndSection

---

### Post by Favux on 2009-04-10
Hi MZ250Supa5,

I meant for you to run this command in a terminal:
```
gksudo gedit /etc/X11/xorg.conf
```
The gksudo will cause a little password box to pop up.  Type in your password and then you'll have root privileges.  The gedit will cause a text editor to pop up, like a little word processor.  In it will be your current xorg.conf.  Replace it with the new one and save it.  Reboot.

Also cut and paste is better than typing.  At least until you learn your way around.  For example notice it is capital X not little x.  Case makes a difference in Ubuntu directory paths.  And it is X eleven not two little L's.

Be careful and make sure you have backed up your xorg.conf before doing anything.

The box the command above appears in is obtained by clicking on the # above.  This appears [code][code].  Click in between them and then paste the output you've copied and it will be "boxed" too.  The quote tags is to the left of the # (code tags) and works the same way.  Hover your mouse over the icons to see what they do.

---

### Post by egalvan on 2009-04-10
> **Favux said:**
> Hi MZ250Supa5,

**I think you were misinformed.  A 32-bit OS will only see a maximum of 3.2 GB whereas **a 64-bit has no RAM limitation (in theory).  But 64-bit is theoretically faster because it's executing twice as much (64 vs 32) at a time.  But in reality you wouldn't notice it except in certain situations.



Not completely true...

A 32-bit OS with PAE enabled will see 64GB.

Ubuntu 32-bit SERVER kernel has this flag set.

Add a desktop (Gnome,KDE,XFCE etc) and you have a 32-bit OS that can use more than 3.x amount of RAM.

I use this combo with a Dell maxed out at 8GB.

ErnestG

---

### Post by Favux on 2009-04-10
Sure egalvan,

You can use a server memory setup.  But if you would have looked a little more carefully at this thread you would realize you are being a little ambitious for the poster.

---

### Post by MZ250Supa5 on 2009-04-10
I have installed the xorg.conf input you put on here, and it's now showing as having been installed, as per below:

## xorg.conf (X.Org X Window System server configuration file)
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

Section "InputDevice"
Identifier "stylus"
Driver "wacom"
Option "Device" "/dev/input/wacom"
Option "Type" "stylus"
Option "USB" "on" # USB ONLY
Option "Button2" "2"  # make first button a middle button
Option "Button3" "3"  # make second button a R button
EndSection

Section "InputDevice"
Identifier "eraser"
Driver "wacom"
Option "Device" "/dev/input/wacom"
Option "Type" "eraser"
Option "USB" "on" # USB ONLY
EndSection



But the tablet still isn't functioning, though a short while ago the eraser end of the stylus was showing signs of having comprehending that something was going on that effecting it to behave like... a stylus!  At least there was some progress, but even that seems now to have disappeared

---

### Post by Favux on 2009-04-10
Hi MZ250Supa5,

You are aware that the xorg.conf you just posted is only part of the xorg.conf I posted?  You want to be sure you copied the whole thing in the box.  The sliders along the box edge will show you all of it.  Or were you just showing part of it to show that you got the whole thing in?

---

### Post by MZ250Supa5 on 2009-04-10
Ahh, thereby lies the problem... I guess I must be going blind as well as stupid.  I hadn'noticed the slider at the side of you previous post. 

I shall amend forthwith.

---

### Post by Favux on 2009-04-10
Hi MZ250Supa5,

To get it to "click" in you may have to reboot and restart X a few times.  X is the Xserver which gives you a graphical desktop.  To restart X use ctrl-alt-backspace.

You should also be aware of the old hotplug commands:
ctrl-atl-F1 and then ctrl-alt-F7
in case wacom conks out on you.

Edit:  If you are using quick reply rather than New Reply you won't see the # I'm talking about.  You would have to "Go Advanced".

---

### Post by MZ250Supa5 on 2009-04-10
Here's what it looks like now:

## xorg.conf (X.Org X Window System server configuration file)
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

Section "InputDevice"
Identifier "stylus"
Driver "wacom"
Option "Device" "/dev/input/wacom"
Option "Type" "stylus"
Option "USB" "on" # USB ONLY
Option "Button2" "2"  # make first button a middle button
Option "Button3" "3"  # make second button a R button
EndSection

Section "InputDevice"
Identifier "eraser"
Driver "wacom"
Option "Device" "/dev/input/wacom"
Option "Type" "eraser"
Option "USB" "on" # USB ONLY
EndSection

Section "InputDevice"
Identifier "pad"
Driver "wacom"
Option "Device" "/dev/input/wacom"
Option "Type" "pad"
Option "USB" "on" # USB ONLY
EndSection

Section "Device"
Identifier "Configured Video Device"
Driver "fglrx"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 24
EndSection

Section "Module"
Load "glx"
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "stylus" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
InputDevice "pad" # For Intuos3/CintiqV5/Graphire4/Bamboo tablets
EndSection

---

### Post by MZ250Supa5 on 2009-04-10
Thanks very much for your help Favux, but this doesn't seem to have done the trick - though the eraser again thinks it's a pen.

Would re-loading Ubuntu afresh onto the hard drive so that I'd be starting afresh be a good idea, as it's pretty crucial that the tablet has all it's functions, as this is why I bought it in the first place, I do a lot of graphical stuff, and the pen sensitivity is *very* important, as are the other functions. 

I was intending to stay with XP for a while, I hadn't planned changing to Ubuntu so soon but became increasingly frustrated by XP. 

Will 9.04 offer any greater functionality on wacom tablets from the word go, or will the same frustrating workarounds be the norm.  If 9.04 is going to resolve this problem, then I'll wait, but if not then I shall, reluctantly, be forced to return to XP.

Unfortunately Wacom themselves don't offer a Linux driver for the model of Bamboo that I have, (the black one with the touchring and four blue-illuminated buttons).

I would be sad to have to return to Microshaft, but it seems that Ubuntu and Linux in general is where Microsoft were some 20 or so years ago when faced with the GUI (or WIMP as it was then known...) of Mac and even Atari. 

Once again, many thanks for your help.

Padi.

P.S.

Even if I do return to XP, I shall keep an eye on developments here in the hope that these issues are resolvable in a way that mere mortals are capable of understanding.

---

### Post by Favux on 2009-04-10
Hi MZ250Supa5,

So you now have tablet function.  Does the stylus act as a stylus or just the eraser?  It seems you are giving up just as things are working.  The eraser only works in certain programs that are able to detect it like Gimp and Inkscape and you have to configure their extended input devices options.

Steps:
1)  Install linuxwacom driver and tools-done
2)  Configure xorg.conf-done
3)  Calibrate tablet-pending, probably would clear up your eraser confusion.
4)  Configure rest of buttons (pad) on tablet-pending

---

### Post by MZ250Supa5 on 2009-04-11
Not giving up just yet!  The stylus does perform as a stylus, and as you already know, the eraser works as a stylus/pointer - I know that the eraser and stylus only have their full functions in certain, usually graphics packages, (same in Windows), so wasn't expecting anything in other packages - though it would be good if something like Bamboo Scribe could be enabled, but perhaps that's an expectation too far at the moment... (not that it's crucial for myself, but I do have a friend who is painfully slow on the keyboard who would gratefully appreciate that function).

I would guess that the next step is configuring the setting for the pad buttons and stylus...  I have seen reference to this in another post, or HowTo on here, so I shall try and find it.

I'll let you know how I get on.

Many thanks indeed.

Padi.

---

### Post by Favux on 2009-04-11
Hi Padi,

Good.

3)  To use "wacomcpl" to calibrate your tablet see section 3 here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)

4)  To configure the rest of your tablet buttons see post #7 here:  [http://ubuntuforums.org/showthread.php?t=1098822&highlight=bamboo](http://ubuntuforums.org/showthread.php?t=1098822&highlight=bamboo)

Also if you go to the first link I gave you it will take you to Loic2's Wacom wiki.  Towards the bottom it will tell you how to configure Gimp and Inkscape.

If you read back over this thread you will realize you have learned quite a bit and so a lot of this will make sense to you now.

Good luck!

---

### Post by MZ250Supa5 on 2009-04-11
Sucess!!!  Thank you ever so much for your patience.  

The only thing I have to adjust next is the cursor/tool icon offset which seems to only correspond in the centre of a desktop, the distance between them increasing the further away from the centre of the desktop one is working. I'm finding this a little irritating as the eye tends to follow one or the other.  I'm going to try and find out how this is done, or if the irritating and uneccessary, (for me) tool icon can be disabled in some way.;)

---

### Post by Favux on 2009-04-11
Hi Padi,

Outstanding!  Try the calibration.

Edit:  For your friend you may be talking about Tom Jaeger's Easystroke Gesture Recognition.

---

### Post by MZ250Supa5 on 2009-04-11
Hi Favux

The calibration of the actual pad in terms of X/Y co-ordinates is actually fine, and has been since I first loaded Intrepid - unless of course I'm missing something...

However, after getting the Express Keys sort of working; FN1 and FN2 seem to work in terms of toggling between two open documents/packages,but button FN2 seems to have had another quite unexpected function that I don't think was intended - unless of course the person who wrote the script had something against the query entry box in the Firefox front page - pressing FN2 makes it disappear! The touch ring also has an 'interesting' function - if pressed when on the Firefox front page it puts a dotted line interspersed with + symbols in the query entry box. It works well in terms of zoom in/zoom out in Gimp, bur the scroll function doesn't seem to work at all - though I have to say that I used the touchring in XP mainly whilst surfing as the ability to zoom in/out or scroll without moving my hand was a boon.  

I bought the Bamboo as a replacement for an old Aiptek 600 parallel port model that gave up the ghost one weekend whilst doing a lot of graphical stuff, forcing me to use a mouse instead - I ended up with a bad case of RSI, so the Bamboo was ordered poste haste I'm also at the stage in lie where arthritis has begun to kick in, which means I'm even more wedded to my Bamboo.  To anyone considering whether these pads are worth the much greater cost than a mouse, I would say, don't hesitate, you won't regret it.  Eventhough the Bamboo retails at something like £60 in the UK, and replacement nibs are a king's ransome, they are still worth the money. It's just a bit frustrating that they are a bit of a fiddle to set up on Ubuntu.

Once again, thanks for all your help.  

I shall now go away and scratch my head and try to resolve the few remaining idiosyncracies that my Bamboo seems to have...

Padi.

---

### Post by Favux on 2009-04-11
Hi Padi,

You are welcome.

Real progress!  Anyway post on the thread with Gemnoc's how to and see if anyone knows how to configure it the way you want.

If you want gestures to activate stuff here's Tom's Easytroke site.  He just came out with the new version.  Just select the one for your version of Ubuntu and cpu architecture, download it and double click to install.  

[http://sourceforge.net/project/showfiles.php?group_id=229797&package_id=278455&release_id=668742](http://sourceforge.net/project/showfiles.php?group_id=229797&package_id=278455&release_id=668742)

He has a thread that's active too.  It is rare for a developer to participate on a thread but he does.

[http://ubuntuforums.org/showthread.php?t=837032](http://ubuntuforums.org/showthread.php?t=837032)

---

### Post by egalvan on 2009-04-12
> **Favux said:**
> Sure egalvan,

You can use a server memory setup.  But if you would have looked a little more carefully at this thread you would realize you are being a little ambitious for the poster.

Ambitious? :)


Let's see...

I did a bone-stock default install of Ubuntu 8.04.2 Server edition.

then I typed

sudo apt-get install gnome-desktop

and I have a Gnome environment that will use more than 4GB of RAM.
Yay.
And it's basically indistinguishable from the "standard" Ubuntu.

(The kernel is the only part that is actually different...
there is also a way to load the server kernel via Synaptic, but I have never actually done it...)

This was my THIRD Ubuntu install, I was very much the "noobie".
I was curious about that particular method, so I swapped in a blank drive, and had at it :)


Sorry, I guess I am so tired of reading the same FUD over and over...

*32 bit operating systems can't see/use more than 4GB of RAM*

This may be true for Microsoft...

But it's been NOT true for *nix for quite some time...

And the OP also stated 

*I have been led to believe that it's not worth installing the 64 bit version unless there's 4GB or more RAM available.*

More FUD.... There ARE other reasons to go with 64bit other than better memory management...

And now that I have over fifty Linux installs under my belt, I feel better about my initial experimenting with that "server" stuff...

---

