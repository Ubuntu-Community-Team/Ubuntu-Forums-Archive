---
title: "Wacom Gateway Tablet help"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by mmitt on 2009-02-02
Here is my situation:
8.10 Kubuntu installed on a Gateway tablet PC with about 3GB RAM and Dual 2.4 Mhz Processors.

Problem: My stylus will not work with my laptop in ubuntu. It works fine in Vista.

Other factors: Is there anyway to make this work without messing with my xorg file? I tried one way and I booted to a command prompt and had to restore my xorg file. 

Any ideas?

---

### Post by Favux on 2009-02-02
Hi mmitt,

Sorry, you're going to have to configure xorg.conf, unless you want to wait for Jaunty.  It is suppose to have a gui to configure the xorg.conf, it it makes it in.  It really isn't that hard!  Promise.  Just be sure to back it up before you make any changes.  And if you have a live CD to boot from you're golden.

What's the model of your Gateway tablet?  Do you know which digitizer your tablet has?  Wacom or the Finepoint Innovations Tablet PC Digitizer?  Serial or USB?  Which features; stylus, side-switch, eraser, touch?

If you do have the Finepoint, the driver you need is called "fpit".  The new version is 1.2.0.  The line to google with is "xf86-input-fpit driver". It's home is:

[http://cgit.freedesktop.org/xorg/driver/xf86-input-fpit/]("http://cgit.freedesktop.org/xorg/driver/xf86-input-fpit/")

There is a deb of 1.2.0-1 at the Debian site, which given the "-1" seems current:

[http://packages.debian.org/sid/xserver-xorg-input-fpit]("http://packages.debian.org/sid/xserver-xorg-input-fpit")

And better, Synaptic Package Manager has it. Search "fpit" and you get 1:1.2.0-1 build 1. So the Synaptic version may be slightly older than the Debian deb. I'd say it's your choice which to install.

Then this thread should have info. on how to configure xorg.conf, etc.

[http://ubuntuforums.org/showthread.php?t=942109]("http://ubuntuforums.org/showthread.php?t=942109")

Good luck!

---

### Post by mmitt on 2009-02-03
Ok thanks for the reply. I have a Gateway C-142XL. I can't tell if it has wacom or finepoint. I found a page from gateway that shows more about it [here]("http://www.gateway.com/product_spec.php?product_recid=529668042"). I do think that it is finepoint though... I'm not sure. Is there anyway to tell for sure?

---

### Post by Favux on 2009-02-03
Hi mmitt,

You know, I don't know.  It came out when I was looking and I think I thought at the time it was a Wacom digitizer.  Maybe because the pen is described as a Wacom pen.  But Gateway is real shy about actually naming the digitizer.  A quick google didn't reveal any definite answer.  I did see stuff like resistive (passive) touchscreen.  And Wacom emulation.  Huh.  At the time I think I thought it was an active Wacom digitizer.  Unless you can find out, you may have to contact Gateway.  I'm reasonably sure they moved away from Finepoint after, say the M275.

We also still don't know if it is a serial or usb digitizer.  From what I read you have a stylus and a side-switch.

Right now my best guess is it is a serial digitizer, which whether it's a Wacom or not, emulates a Wacom.  So then you'd want the linuxwacom drivers.  If you decide it is a "wacom" you probably should first try installing the 0.8.1-6 debs on Loic2's Wacom wiki.  The link is towards the top of this HOW TO:

[http://ubuntuforums.org/showthread.php?p=6546012#post6546012]("http://ubuntuforums.org/showthread.php?p=6546012#post6546012")

Then we can work on your xorg.conf.

Hope this is helpful.

---

### Post by Favux on 2009-02-03
Hi again mmitt,

We lucked out.  I found some posts by minibeardeath and he has a C-142 XL also.  It is a serial "wacom".  And he posted his xorg.conf!  So go ahead and install 0.8.1-6 as per Loic2's wiki.  I took his xorg.conf and cleaned it up and it should work for you.  But please note he has the ATI proprietary driver "fglrx" installed and probably Compiz.  You do have ATI video, right?  If you don't, do not use his video section where "fglrx" is unless you install the proprietary driver.  I also installed a side-switch button he was lacking.  You do have a button on the stylus, correct?  It will act like a right-click.

I'll go ahead and attach it.

---

### Post by mmitt on 2009-02-03
Thanks so much! I'm gonna work on this when I get home... I'll tell you if it all goes well. I'm glad *one* of us can figure out what kind of laptop I have :). And yeah, I have an ATI so I guess I sould install the drivers first... Ok I will get back to you later. Thanks!

---

### Post by Favux on 2009-02-03
Hi mmitt,

I've thought about it a little.  Since you haven't installed the proprietary drivers yet, **don't**.  Only the latest "fglrx" supports rotation and I'm not sure they're in the repository yet.  Please see the top of:

[http://ubuntuforums.org/showthread.php?p=6274392#post6274392]("http://ubuntuforums.org/showthread.php?p=6274392#post6274392")

Use the revised xorg.conf I'll attach below.

---

### Post by mmitt on 2009-02-03
Uh oh... I just installed the prorietary drivers... I can just deactivate them though, right? Truthfully, screen rotation doesn't work with them, but if it will be tough to to do the rest of this, I can live without it. I just finished section 1 of [this]("http://ubuntuforums.org/showthread.php?p=6546012#post6546012") guide and I'm quite proud of myself (the guide got confusing at step 4, but I had to enter something like ./Desktop and then ./linuxwacom-0.8.2-2 and then I did step 5. Is that ok?) All went well, possibly. I'll wait on you for what I need to do next. I mean, I'm in no rush, just as long as I get it done before this August, I'm ok. And I used the System > Administration > Hardware Drivers way so I can disable it. Thanks!

---

### Post by Favux on 2009-02-03
Hi again mmitt,

> I can just deactivate them though, right?  I used the System > Administration > Hardware Drivers way so I can disable it.
You are correct sir!

Say, why didn't you want to use Loic2's debs?  Just asking.

Be sure to back up your xorg.conf before making any changes to it!

---

### Post by mmitt on 2009-02-03
Oops. I didn't know there were .deb's. Oh well, the terminal way is still ok, right? Well now what do I need to do? Here is my guess, tell me if this is right please:
1. Open terminal and type: "gksudo gedit /etc/X11/xorg.conf"
2. Replace all text with your text attached (2nd attachment.)
3. Restart computer
4. If anything goes wrong: "sudo dpkg-reconfigure xserver-xorg"

Correct?

---

### Post by Favux on 2009-02-03
Hi mmitt,

Yes, provided you've uninstalled the ATI proprietary driver "fglrx".  Also rather than step 4 you'd want to replace the new xorg.conf with your backed up original xorg.conf.

---

### Post by mmitt on 2009-02-03
> **Favux said:**
> Hi mmitt,

Yes, provided you've uninstalled the ATI proprietary driver "fglrx".  Also rather than step 4 you'd want to replace the new xorg.conf with your backed up original xorg.conf.
In the link you provided, your xorg file has to be set up first. I figured we were going by your guide for the fglrx screen rotation. Anyway, I haven't backed it up yet. How do I do this and how can I replace it if it messes up?

---

### Post by Favux on 2009-02-03
Not quite sure what you just said, but to back it up do:
```
gksudo cp /etc/X11/xorg.conf /etc/X11/my_xorg.conf.bak
```
and to reverse it you would just reverse it:
```
gksudo cp /etc/X11/my_xorg.conf.bak /etc/X11/xorg.conf
```
You don't have to name the backup file "my_xorg.conf.bak", that's just an example.

---

### Post by mmitt on 2009-02-03
Done. Thanks. Here we go!

---

### Post by mmitt on 2009-02-03
> **mmitt said:**
> Done. Thanks. Here we go!
And... No luck. Maybe it was because I forgot to install the flgrx drivers... I don't understand how to install it though. The line I was talking about was this though:
> The following assumes you have successfully installed the Linuxwacom drivers (see: [http://ubuntuforums.org/showthread.p...12#post6546012](http://ubuntuforums.org/showthread.p...12#post6546012)) and have your xorg.conf set up for a tablet pc (sample xorg.conf's attached below). Several methods can get your screen to rotate, but you also need the tablet features like the stylus and touch to rotate too.
Ok I just installed the driver and am about to reboot. Hang on a second.

---

### Post by Favux on 2009-02-03
Hi again,

Oops.  We don't want to install the "fglrx" drivers at this point.

---

### Post by mmitt on 2009-02-03
Great. I just installed them. And surprisingly, when i rebooted, no luck still. To recap:
1. followed these instructions: (You know what I mean)
2. Edited xorg.conf file with this: (your second attachment)
3. Rebooted and installed "fglrx" drivers through the hardware manager (just checked, said that it wasn't activated yet...). 
4. Rebooted once again and no luck.
5. Just deactivated FGLRX drivers through hardware manager.

How do you propose I go about doing this now?

---

### Post by Favux on 2009-02-03
Wow!  OK.  First I recommend you delete all the quote stuff, since I know where we are.  The "fglrx" video driver has nothing to do with getting a functioning tablet.  It just interferes with rotation.

So we've got three possibilities.

1.  The kernel driver didn't compile correctly.

2.  The kernel driver wasn't copied to the right directory (step 6)

3.  The device input in xorg isn't correct for some reason.

Let's ignore 1 & 2 for now.

I just noticed some extraneous garbage got into my copy of the xorg.conf I sent to you.  Could you attach your current xorg.conf?  The one you posted in quotes looks good, I just want to be sure.  Use manage attachments in Additional Options.

Let's try changing the input.  Using "gksudo gedit /etc/X11/xorg.conf".  Instead of:
```
Section "InputDevice"
	Identifier	"stylus"
	Driver		"wacom"
	Option		"Device"        "/dev/input/ttyS0"   # SERIAL ONLY
	Option		"Type"          "stylus"
	Option		"ForceDevice"   "ISDV4"               # Serial Tablet PC ONLY
	Option		"Button2"	"3"    # make side-switch a R button
EndSection

```
Change it by adding the line "Option		"Device"        "/dev/input/wacom" " to:
```
Section "InputDevice"
	Identifier	"stylus"
	Driver		"wacom"
	Option		"Device"        "/dev/input/wacom"
#	Option		"Device"        "/dev/input/ttyS0"   # SERIAL ONLY
	Option		"Type"          "stylus"
	Option		"ForceDevice"   "ISDV4"               # Serial Tablet PC ONLY
	Option		"Button2"	"3"    # make side-switch a R button
EndSection

```
Be sure to comment "#" out the "ttyS0" line.  And see if that works.  You don't have to reboot, you can restart X by using <ctrl><alt><backspace>.

---

### Post by mmitt on 2009-02-03
Ok I tried that with no success. Here is my xorg.conf file after the line replacement.

---

### Post by Favux on 2009-02-03
The bottom portion of your xorg.conf didn't come through.
```
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
# commented out by update-manager, HAL is now used
#	Inputdevice	"Synaptics Touchpad"
	Inputdevice	"stylus"	"SendCoreEvents"
EndSection

#Section "Module"
#	Load		"glx"
#EndSection
```
I'm assuming that was a copying error.  Comment out the input/wacom line and re-enable the input/ttyS0 (remove the comment).  It still might be an input detection problem but not likely.  Let's not get into that thicket if we don't have to.

Rather than trying to talk you through compiling, go to the top of the kernel driver HOW TO and use the link to go to Loic2's Wacom wiki.  Download the linuxwacom 0.8.1-6 debs there and follow his instructions to install them.  With just a tiny bit of luck that should do it for you.

Good luck!

---

### Post by mmitt on 2009-02-04
Arghhh. Sorry about that. Here is the other one (full I hope...). To tell you the truth, I can't find those lines. Maybe thats the problem... Thanks for helping!

---

### Post by Favux on 2009-02-04
Hi mmitt,

No need to be sorry, it wasn't your fault.  I looked through all the xorg's again and it looks like the second xorg got truncated during the upload somehow.  The forum has never done that before!  So I removed it, renamed the original (added a (2)) and re-uploaded it.  And then double checked it.  It's good.

It definitely could have made a difference.  Without the "ServerLayout" section at, or towards the end of xorg.conf and the "stylus" "SendCoreEvents" line in it, there is no way your stylus could be detected!  Download it and carefully compare it to your current xorg.conf.  Study the sections, so you know what's suppose to be in it.

The only difference you should currently see is your xorg.conf is set up for ATI's proprietary driver "fglrx".  Whereas I was trying to set you up for Xorg's "radeon" driver.  Notice the ATI proprietary driver needs another section, the one with "glx" in it.  Also notice you now have a commented out duplicate "glx" section.

So if your stylus isn't detected try switching the line:
```
	Option		"Device"        "/dev/input/wacom"
```
back to:
```
	Option		"Device"        "/dev/ttyS0"   # SERIAL ONLY
```
And see if that works.  The next step would be to try an install the linuxwacom 0.8.6-1 debs using Loic2's wiki.  And again try both lines.

Luck!

---

### Post by mmitt on 2009-02-04
Nope no luck here. I'm just going to attach the xorg.conf file again to make sure I have the correct things in it. I tried renaming the ttySO part and that didn't work either. So I switched it back. If you think it is the linuxwacom stuff, then I can try that. But only if you are sure ;). Thanks!

---

### Post by Favux on 2009-02-04
Hi mmitt,

I spent some time looking at other folks postings re serial Wacom tablets and "/dev/input/wacom" should work.  But I did notice that minibeardeath looks like he has a error in his original xorg.conf that we modeled off of.  Instead of:
```
Option        "Device"        "/dev/input/ttyS0"          # SERIAL ONLY
```
it should be:
```
Option		"Device"	"/dev/ttySO"   # SERIAL ONLY
```
That is the only problem I see.  The use of "wacom" instead of a specific serial path is a relatively recent innovation made possible by introducing "symlinks".  It's possible that somehow yours aren't established, but that seems very unlikely.  I think I'd leave the "wacom" input path.  But if you haven't been, go ahead and run Update Manager to make sure your system is up to date.

To begin establishing what serial port is active you'd use:
```
dmesg | grep ttyS
```
and
```
ls /dev/ttyS*
```
A very few serial tablets require adding to their "/etc/setserial.conf" a line something like:
```
/dev/ttyS0 port 0x03F8 irq 4 baud_base 38400
```
but minibeardeath didn't mention anything like that.  Normally the active serial port is one of four.  Either ttyS0, ttyS1, ttyS2, or ttyS3.  Again in a few tablets it's something different and you have to use a program "setserial" to configure it.

Since you have a stylus, it should work out of the box with Intrepid through HAL (Hardware Abstraction Layer).  HAL wouldn't let you use the side-switch or calibrate it through "wacomcpl".  But you get no stylus activity at all.  Hmmm?

To get a working stylus (without HAL) you need a working linuxwacom driver and a correctly configured xorg.conf.  Since your xorg.conf is now correctly configured ...

So it seems you want to install the 0.8.1-6 debs using Loic2's wiki.  Installing debs is easy.  After downloading them to the desktop you basically just double click them.

The only concern is would there be a conflict between the version you tried to compile and the older version in the debs?  I don't know.  I've compiled after the debs without a problem but not vice versa.

OK mmitt, with that background you should be up to speed and be able to make an informed decision.  The choice is up to you.

---

### Post by mmitt on 2009-02-05
> **Favux said:**
> Hi mmitt,

I spent some time looking at other folks postings re serial Wacom tablets and "/dev/input/wacom" should work.  But I did notice that minibeardeath looks like he has a error in his original xorg.conf that we modeled off of.  Instead of:
```
Option        "Device"        "/dev/input/ttyS0"          # SERIAL ONLY
```
it should be:
```
Option		"Device"	"/dev/ttySO"   # SERIAL ONLY
```

Tried that. No luck still. Maybe I need to uncomment it for changes to take effect?
> 
That is the only problem I see.  The use of "wacom" instead of a specific serial path is a relatively recent innovation made possible by introducing "symlinks".  It's possible that somehow yours aren't established, but that seems very unlikely.  I think I'd leave the "wacom" input path.  But if you haven't been, go ahead and run Update Manager to make sure your system is up to date.

Up to date. I'm not sure about symlink though.
> 
To begin establishing what serial port is active you'd use:
```
dmesg | grep ttyS
```
and
```
ls /dev/ttyS*
```
A very few serial tablets require adding to their "/etc/setserial.conf" a line something like:
```
/dev/ttyS0 port 0x03F8 irq 4 baud_base 38400
```
but minibeardeath didn't mention anything like that.  Normally the active serial port is one of four.  Either ttyS0, ttyS1, ttyS2, or ttyS3.  Again in a few tablets it's something different and you have to use a program "setserial" to configure it.

It says I have ttyS0.
> 
Since you have a stylus, it should work out of the box with Intrepid through HAL (Hardware Abstraction Layer).  HAL wouldn't let you use the side-switch or calibrate it through "wacomcpl".  But you get no stylus activity at all.  Hmmm?

wacomcpl doesn't even show my stylus in list of devices...
> 
To get a working stylus (without HAL) you need a working linuxwacom driver and a correctly configured xorg.conf.  Since your xorg.conf is now correctly configured ...

So it seems you want to install the 0.8.1-6 debs using Loic2's wiki.  Installing debs is easy.  After downloading them to the desktop you basically just double click them.

The only concern is would there be a conflict between the version you tried to compile and the older version in the debs?  I don't know.  I've compiled after the debs without a problem but not vice versa.

OK mmitt, with that background you should be up to speed and be able to make an informed decision.  The choice is up to you.
Ok, I'm going to try the debs. I'll tell you if any problems occur. Thanks again!

EDIT: Followed [this]("https://help.ubuntu.com/community/Wacom/LatestDriver") guide with no luck. Any ideas?

---

### Post by Favux on 2009-02-05
Hi mmitt,

> Maybe I need to uncomment it for changes to take effect?
Yes it has to be uncommented (the # removed) and either X restarted or reboot.

> It says I have ttyS0
The relevant output would have been interesting and maybe useful.

Until stylus starts showing activity on the screen wacomcpl won't show anything.  Once you start getting response to stylus if you type "wacomcpl" in a terminal and it pops up, but there is no "stylus" to click on and calibrate then HAL is running your stylus.

Why that guide?  Did you try to compile again?  Not sure I know why you linked to Wacom/Latest Drivers.  Maybe expanding your response a tad would help.  I have been asking you to go here:

[https://help.ubuntu.com/community/Wacom/]("https://help.ubuntu.com/community/Wacom/")

Near the top, under Ubuntu 8.10, under "1. Download the updated packages:".  The links in red.  You are i386, right?

Slightly off topic.  Your stylus isn't one of the ones that requires a battery is it?

---

### Post by mmitt on 2009-02-05
Argh. I will include output when I am back on ubuntu, have to write a paper right now :(. I will definently try the debs then too. I never could find that page though, thanks for a direct link. Will report back soon!

---

### Post by mmitt on 2009-02-05
> **Favux said:**
> Hi mmitt,

Yes it has to be uncommented (the # removed) and either X restarted or reboot.

No luck this way. Commented the wacom part and uncommented the ttyS0 part. Didn't work so I undid this.
> 
The relevant output would have been interesting and maybe useful.

Output: "[    1.530609] 00:02: ttyS0 at I/O 0x6a8 (irq = 4) is a 16550A"
> 
Until stylus starts showing activity on the screen wacomcpl won't show anything.  Once you start getting response to stylus if you type "wacomcpl" in a terminal and it pops up, but there is no "stylus" to click on and calibrate then HAL is running your stylus.

Why that guide?  Did you try to compile again?  Not sure I know why you linked to Wacom/Latest Drivers.  Maybe expanding your response a tad would help.  I have been asking you to go here:

[https://help.ubuntu.com/community/Wacom/]("https://help.ubuntu.com/community/Wacom/")

Near the top, under Ubuntu 8.10, under "1. Download the updated packages:".  The links in red.  You are i386, right?

Slightly off topic.  Your stylus isn't one of the ones that requires a battery is it?
Ok I'm going to try that link now. I never compiled again. Haha I found the debs! Yay! And yep I am i386, and no my stylus does not require a battery. Ok I'll tell you what happens.

---

### Post by mmitt on 2009-02-05
Yes! It works! Thank you so much for all of your help. If you ever need anything, ANYTHING at all, just let me know. Once again thank you.

---

### Post by mmitt on 2009-02-05
Argh. I defintently hate to bother you now, but how can I work screen rotation from an external button on my gateway, or configure the stylus?

---

### Post by Favux on 2009-02-05
Great!  Finally stylus activity.  And you are using ttyS0, correct?

Now is stylus running through HAL or linuxwacom?  The way to find out and to calibrate the stylus is to type "wacomcpl" in a terminal.  The linuxwacom calibration gui should pop up.  Stylus should be on the left.  Click on it and options will pop up including calibration.  If you don't see stylus then HAL is running things.  Which means we just need to find the right input path for xorg.conf.

To key bind rotation to a bezel key see:

[http://ubuntuforums.org/showthread.php?p=6274392#post6274392]("http://ubuntuforums.org/showthread.php?p=6274392#post6274392")

---

### Post by mmitt on 2009-02-05
Yep I'm using ttyS0. I think. Here are the two lines I think are important in figuring that out:
```
	Option		"Device"        "/dev/input/wacom"
#	Option		"Device"	"/dev/ttyS0"   # SERIAL ONLY
```
So maybe I'm using wacom. However, if I type wacomcpl in terminal, a gui pops up but no stylus. :(. 
Truthfully, I don't understand that link you provided. I believe that my screen rotates in 4 90 degree steps counter clock wise on vista. If that
helps any :). Ok thanks!

---

### Post by Favux on 2009-02-05
Hi mmitt,

OK, sounds like your stylus is working through HAL.  You have working linuxwacom drivers and HAL (Hardware Abstraction Layer) is handling the stylus.  The input through the xorg.conf is not being picked up, so our entry isn't right yet.  Because there isn't any signal detected through xorg.conf the calibration gui "wacomcpl" isn't seeing your stylus.

Does the side-switch do anything when you click it?  Does the stylus cover the screen OK.  Is it accurate?  If so we could call it quits.

If not then we want the stylus working through the xorg.conf rather than HAL.  Try this instead of the above in your xorg.conf:
```
#	Option		"Device"        "/dev/input/wacom"
	Option		"Device"	"/dev/ttyS0"   # SERIAL ONLY
```
See we're shifting the comment "#", deactivating one line and activating the other.  Then try wacomcpl again.

The rotation HOW TO really isn't that complicated.  There are basically three ways shown to get rotation.  Just read through it a couple times and you'll get it.  Pay attention to the stuff at the beginning about ATI.  If you need more help on rotation just ask.  Also because you have only the stylus, the script could be simplified (remove the eraser and touch lines).

---

### Post by mmitt on 2009-02-05
The stylus works fine. I just like being able to use a GUI to calibrate it if I need to :). Oh well. I changed the commented line anyway and it still works fine, but "wacomcpl" still doesn't give me any stylus options. Is the side-switch button like the right click button? If so, then yeah it works like it should. And I guess I'll give the screen rotation thing a shot... I'm scared haha. Ok thanks I'm going to try now.

---

### Post by mmitt on 2009-02-05
Oh no... I'm already confused... "xrandr -q --verbose" gives me the output
```
default connected 1280x768+0+0 (0x92) normal (normal) 0mm x 0mm
```
Which is sort of similar to what you said it should look like:
```
default connected 1280x800+0+0 (0x1ad) normal (normal left inverted right) 0mm x 0mm
```
So yeah. What now?

---

### Post by Favux on 2009-02-05
> The stylus works fine.  I changed the commented line anyway and it still works fine
Good, and now we know the symlink for "wacom" is working!

> Is the side-switch button like the right click button?
Yes it is.  We made the side switch work like a right click button by using this line:
```
	Option		"Button2"	"3"    # make side-switch a R button
```
in your xorg.conf.  I don't think you get the side-switch through HAL.  You downloaded and installed both i386.debs right?  Maybe try having Synaptic package installer or the Deb package installer reinstall the wacom-tools one?

On the left side of the Wacom Control Panel is a blank grey box.  Beneath it is kind of a scroll columns.  Stylus should show in the "scroll column".  If you click on it it then appears in the box above and options appear on the right.  One of them should be calibration.

---

### Post by Favux on 2009-02-05
Hi mmitt,

I'm not sure what that output means either.  Is it saying rotation isn't available?  I don't know.

Do you know your ATI video chipset?  That would be useful to know.  Could you attach your xrandr output and xorg.conf?  And we still don't have wacomcpl.  Problems, problems.

Never mind, you gave that link.  So it's a:  ATI Mobility&#8482; Radeon® X2300 HD 128MB GDDR3 Dedicated Memory PCI Express Graphics ( with up to 256MB using HyperMemory&#8482; Technology) [It turns out that technically it is a renamed X1350]

---

### Post by Favux on 2009-02-06
Hey mmitt,

I think I've got it.  "fglrx" will only support rotation if it is the latest two versions (see top of HOW TO).  Do you have an older version?  In other words the newer version may not be available in Ubuntu yet.  You would have to figure out how to get it.

The other option is using Xorg.'s "radeon" driver.  Since neither works for rotation with Compiz, there isn't much to choose between the two.  You should get "radeon" by just deactivating the ATI proprietary driver in Hardware Drivers.  Remember to first comment out "fglrx" in xorg.conf and remove the comment from "radeon" in xorg.conf.  Then restart X or reboot.

Another option is "radeonhd":
[http://www.x.org/wiki/radeonhd]("http://www.x.org/wiki/radeonhd")

So think about it a bit.  Maybe investigate more.

---

