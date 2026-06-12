---
title: "Does Genius MousePen i608 work with 10.4"
date: 2010-09-26
forum: New to Ubuntu
---

### Post by itsols on 2010-09-26
Hi, I need to know if the Genius MousePen i608 tablet works with Ubuntu. Any thoughts/experiences are really appreciated.

---

### Post by ronnielsen1 on 2010-09-26
It appears so

[https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen)

---

### Post by itsols on 2010-09-26
Thanks for your prompt reply.

I noticed that these gadgets need a lot of manual configuring... Don't you know of a model that works 'out of the box'?
Or does this i608 work out of the box with the new OS (10.4)?

Thanks!

---

### Post by itsols on 2010-09-30
I've tried everything possible but I can't seem to get the tablet working.

The only thing that I can do is righ click and left click with the tablet mouse.

Please help

---

### Post by Favux on 2010-09-30
Hi itsols,

What is the output of?:
```
xinput --list
```

---

### Post by itsols on 2010-09-30
Thank you Favux for your response. My Inspiron 1150 laptop is used with an external USB keyboard and mouse. Now I've removed the mouse and plugged the tablet instead...
Here's the output:
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Generic USB K/B                         	id=11	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=14	[slave  pointer  (2)]
&#9116;   &#8627; UC-LOGIC Tablet WP8060U                 	id=9	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; Generic USB K/B                         	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]

---

### Post by Favux on 2010-09-30
Looks good so far.

Did you install DoctorMo's latest WizardPen driver for Lucid?  How did you do it?  Any problems?

What does your 70-wizardpen.conf in /usr/lib/X11/xorg.conf.d look like?

---

### Post by itsols on 2010-09-30
Thanks again.

Yes, I installed it. I inserted the PPA in sources. It shows also in my synaptic package manager as installed.

here's the conf file:
Section "InputClass"
   Identifier "wizardpen"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/event*"
   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
   Driver "wizardpen"
EndSection
Section "InputClass"
   Identifier "wizardpen ignore mouse dev"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/mouse*"
   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
   Driver ""
EndSection

Nothing really 'worked'. I mean, I can't move the pointer with the tablet mouse. Only the clicks work. And when I place the stylus on the tablet, it activates the APPLICATIONS menu. And when I lift and place it back, it deactivates it.

Since nothing worked, I even tried the troubleshooting section on [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen) and followed the instructions at the section that says "Everything worked great, except the mouse doesn't move at all". As a result of this change, my /etc/X11/xorg.conf file looks like this now:

Section "InputDevice"
       Identifier  "Tablet"
       Option "Name" "usb-UC-LOGIC_Tablet_WP8060U-event-mouse"
       Option "SendCoreEvents" "true"
       Driver          "wizardpen"
       Option           "TopX"          "2650"
       Option           "TopY"          "3563"
       Option           "TopZ"          "10"
       Option           "BottomX"       "30733"
       Option           "BottomY"       "29715"
       Option           "BottomZ"       "511"
EndSection

I really hope this can be done :(

---

### Post by Favux on 2010-09-30
OK, let's look at the output of:
```
xinput list-props UC-LOGIC Tablet WP8060U
```
Don't run xorg.conf and wizardpen.conf at the same time.  So comment out (place a # in front of each line) the wizardpen section.  Besides you'd need a "ServerLayout" section in xorg.conf to make the wizardpen section active.

Then back up your 70-wizardpen.conf and change it to:
```
Section "InputClass"
    Identifier "WizardPen class"
    MatchIsTablet "on"
    MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
    MatchProduct "UC-LOGIC"
    MatchDevicePath "/dev/input/event*"
    Driver "wizardpen"
EndSection

Section "InputClass"
    Identifier "WizardPen ignore mouse dev"
    MatchIsTablet "on"
    MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
    MatchProduct "UC-LOGIC"
    MatchDevicePath "/dev/input/mouse*"
    Option "Ignore" "yes"
EndSection
```
And reboot.  I'm not expecting this to work yet, it's a preliminary step.  I need to see the xinput list-props output.

---

### Post by itsols on 2010-09-30
Ok, I've not commented the wizardpen.conf lines yet. But here's the output you requested.

unable to find device UC-LOGIC
unable to find device Tablet
unable to find device WP8060U

I'm surprised why it says unable to find...
Like I said, the left/right mouse button and scroll wheel work.

And I really appreciate your assistance!

---

### Post by Favux on 2010-09-30
Alright, try either:
```
xinput list-props "UC-LOGIC Tablet WP8060U"
```
or
```
xinput list-props 9
```

---

### Post by itsols on 2010-09-30
Here's the second one's output - 

Device 'UC-LOGIC Tablet WP8060U':
	Device Enabled (125):	1
	Device Accel Profile (251):	0
	Device Accel Constant Deceleration (252):	1.000000
	Device Accel Adaptive Deceleration (254):	1.000000
	Device Accel Velocity Scaling (255):	10.000000
	Evdev Reopen Attempts (240):	10
	Evdev Axis Inversion (256):	0, 0
	Evdev Axis Calibration (257):	<no items>
	Evdev Axes Swap (258):	0
	Axis Labels (259):	"Abs X" (246), "Abs Y" (247), "Abs Z" (248), "Abs Rotary X" (249), "Abs Pressure" (250)
	Button Labels (260):	"Button Left" (126), "Button Middle" (127), "Button Right" (128), "Button Wheel Up" (129), "Button Wheel Down" (130), "Button Horiz Wheel Left" (131), "Button Horiz Wheel Right" (132), "Button Side" (243), "Button Extra" (244), "Button Forward" (245), "Button Unknown" (241), "Button Unknown" (241), "Button Unknown" (241), "Button Unknown" (241)
	Evdev Middle Button Emulation (261):	2
	Evdev Middle Button Timeout (262):	50
	Evdev Wheel Emulation (263):	0
	Evdev Wheel Emulation Axes (264):	0, 0, 4, 5
	Evdev Wheel Emulation Inertia (265):	10
	Evdev Wheel Emulation Timeout (266):	200
	Evdev Wheel Emulation Button (267):	4
	Evdev Drag Lock Buttons (268):	0

---

### Post by Favux on 2010-09-30
OK, is that with or without the wizardpen section commented out in xorg.conf?

Anyway we see the evdev driver is picking up one of the two tablet inputs, either event or mouse.  That means the match line isn't working.  Evdev is the driver of last resort and tries to pick up any device not already matched to a driver.

So I made a change to the wizardpen.conf in post # 9.  Try that.

---

### Post by itsols on 2010-09-30
PROGRESS!!!!

This is GREAT NEWS!

I did the changes you stated in the edited post #9 and restarted.

Now my curiously kept the tablet mouse aside and tried the stylus. And the stylus moves the mouse pointer! So I guess this is good news!

The tablet mouse doesn't move even now and the same buttons continue to work.

I'm not even sure if pressure sensitivity is available.

---

### Post by Favux on 2010-09-30
Great!  :)

Now let's look at 'xinput --list' & list-props with wizardpen xorg.conf commented out and the stylus/pen on the wizardpen driver.

Do you know how to set up the stylus in Gimp and Inkscape etc., using extended input devices, so that pressure works?

We can try to get the tablet mouse working next.  But that might break X.  So do you know how to back up the working wizardpen.conf and restore it from the command line?

---

### Post by itsols on 2010-09-30
> **Favux said:**
> Now let's look at 'xinput --list' & list-props with wizardpen xorg.conf commented out and the stylus/pen on the wizardpen driver.
Actually I think I commented those lines you mentioned. so after the xinput --list, here's my output:

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; UC-LOGIC Tablet WP8060U                 	id=9	[slave  pointer  (2)]
&#9116;   &#8627; Generic USB K/B                         	id=11	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; Generic USB K/B                         	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]


> Do you know how to set up the stylus in Gimp and Inkscape etc., using extended input devices, so that pressure works?

We can try to get the tablet mouse working next.  But that might break X.  So do you know how to back up the working wizardpen.conf and restore it from the command line?

I'm afraid you'll have to spell it out for me.

---

### Post by Favux on 2010-09-30
To back up the wizardpen.conf do:
```
sudo cp /usr/lib/X11/xorg.conf.d/70-wizardpen.conf /usr/lib/X11/xorg.conf.d/70-wizardpen.conf.bak
```
then to restore it from the command line just reverse it like so:
```
sudo cp /usr/lib/X11/xorg.conf.d/70-wizardpen.conf.bak /usr/lib/X11/xorg.conf.d/70-wizardpen.conf
```
Be sure to write down the command to restore the back up.

Normally the WizardPen tablets don't have a tablet mouse and the input from it interferes with the driver.  That's why the second snippet disables it.  Since your tablet did come with a mouse we want the second snippet to enable the tablet mouse.  However I'm not sure the WizardPen driver will actually handle a mouse, even though it should.  That's why the backup.  So here we go, try:
```
Section "InputClass"
    Identifier "WizardPen class"
    MatchIsTablet "on"
    MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
    MatchProduct "UC-LOGIC"
    MatchDevicePath "/dev/input/event*"
    Driver "wizardpen"
EndSection

Section "InputClass"
    Identifier "WizardPen mouse class"
    MatchIsTablet "on"
    MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
    MatchProduct "UC-LOGIC"
    MatchDevicePath "/dev/input/mouse*"
    Driver "wizardpen"
EndSection
```
Be sure to have only the mouse or the stylus near the tablet, not both at the same time.

---

### Post by itsols on 2010-09-30
That was close - lol...

That last set of changes did not work. Instead of a login screen, the computer hangs up. Tried twice with the same result.

Now I have the pen like before - basic movements work. Mouse does not work.

What do you think?

---

### Post by Favux on 2010-09-30
That's what I was afraid of.  It could be a couple of things.  Either the WizardPen driver can't handle a WizardPen tablet mouse or we could be running into a limitation of the default hybrid 1.7 Xserver in Lucid.  The Xserver currently doesn't support configuring of dependent devices.  So if the stylus signal and the mouse signal are multi-plexed (coming over the same channel) then that's the problem.

Let's find out which it is.  We'll turn off the stylus snippet and just leave the mouse snippet active:
```
Section "InputClass"
    Identifier "WizardPen class"
    MatchIsTablet "on"
    MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
    MatchProduct "UC-LOGIC"
    MatchDevicePath "/dev/input/event*"
#    Driver "wizardpen"
    Option "Ignore" "yes"
EndSection

Section "InputClass"
    Identifier "WizardPen mouse class"
    MatchIsTablet "on"
    MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
    MatchProduct "UC-LOGIC"
    MatchDevicePath "/dev/input/mouse*"
    Driver "wizardpen"
EndSection
```
If this works the mouse will be working but not the stylus.

---

### Post by itsols on 2010-09-30
I understand that you're helping me out. But I have a little issue staying up (small health issue ) so I'd like to continue this in the morning - about 7 hours from now.


thank you for all you help and I look forward to your help in the morning.

Cheer!

---

### Post by Favux on 2010-09-30
Not a problem.  Have a good night.

---

### Post by itsols on 2010-10-01
Hi, Favux! Thank you for all your support last night...

Today I was able to successfully configure the brush features on Gimp for the stylus. And thereafter, I tried the changes you gave on post #19. Unfortunately, it did no good.

I mean, neither the stylus nor the tablet mouse is functional. If I try to move EITHER of them, the machine crashes - shows me my famous 'disaster screen' which brings me into a berserk mode of text flashes and suddenly I find myself logged out and all applications closed. Also at this point, the system brings me this warning that I'm in low-graphics mode... Anyway, once I log in, the screen looks rather normal. But most of this is nothing to do with the tablet since this has been a '(at least) twice a week ritual' of crashes with my OS.

Back on the issue, shall I revert back to the changes in this 70-wizardpen.conf file or do you have any better suggestions?

From what I've seen, it seems that I'll have to fore go the mouse.

Please let me have your thoughts...

---

### Post by Favux on 2010-10-01
Hi itsols,

Good! :)  You figured out how to get pressure.

Well it is looking like the WizardPen driver doesn't support the tablet mouse.  That might be unfair to DoctorMO's driver.  It could be the WizardPen usb kernel driver in (presumably the usb hid section of) the kernel needs some new code.  Maybe, if the the mouse and stylus are multi-plexed, to separate them out.

Similar things happen with the N-trig digitizer on the HP TX2z or the Dell XT or XT2.  We discovered that we could set up the stylus and touch through the xorg.conf though, even though the stylus and touch were multi-plexed.  So for completeness sake we could investigate whether or not we can set up the WizardPen stylus and tablet mouse through the xorg.conf.  But using the xorg.conf costs you hot plugging the tablet.

Up to you.  If you feel you are good with just the stylus and no mouse I'd stick with the 70-wizardpen.conf we came up with in what, post #9?

In terms of your crashes that's usually due to video or a mis-configured xorg.conf.  What video chipset do you have?:
```
lspci | grep VGA
```

---

### Post by itsols on 2010-10-01
Thanks a lot for your advice.
If it means I have to always plug my tablet in to the laptop, I really don't mind it if I can get both the mouse + stylus working.

But on the other hand if the stylus is better off with the the WizardPen then let's stick to it; no issues.

My only problem is that the laptop has 2 USB ports and I've got to remove the ordinary mouse in order to plug the tablet in. But any way, I guess I can manage. I tried a USB hub but certain devices like external drives won't run on it due to some issue or the other. Apart from these little hiccups I don't see why I need the tablet mouse - smiles...

As for my display issue, I have TWO MAJOR ones - discussed on other threads. But to-date I've never been able to resolve it. My output from "lspci | grep VGA" is:

00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)


BTW, in the middle of some work, suddenly for no obvious reason, the screen crashes and I'm logged out. During the crash, a common thing I notice is that the screen is full of text and there's an attempt to update the ClamAV databases. Sometimes I see some words about some attempt to access a share on some partition/computer (LAN). I even tried turning off clamAV updates but still it occurs. And all this only after I moved from 8.04 to 10.04. In fact, the very moment I upgraded to 10.4, I had no graphics at all. And I had to update some kernel stuff - all discussed on some other threads.

Thanks anyway for all your help and I really hope that at least some day, the patches/fixes will come in :)

---

### Post by Favux on 2010-10-01
OK, it sounds like you are ambivalent about looking into the xorg.conf route.  No problem.  You can always come back to it later after you've had some time with the tablet working.  That would give you a chance to decide how important the tablet mouse may be to you.

You're correct, the Intel 855GM chipset is a problem.  One thing I gather is important is to make sure the color depth is set to 24.  So in xorg.conf it would be:
```
DefaultDepth    24
```
I'm sure you already know about this.  Remember if you mess with your xorg.conf to back it up like we did with the 70-wizardpen.conf, for the same reason.

I won't give you links to the usual threads, it looks like you have them.  But have you seen?:

[http://ubuntuforums.org/showthread.php?t=1464239&highlight=855GM](http://ubuntuforums.org/showthread.php?t=1464239&highlight=855GM)

[https://launchpad.net/~glasen/+archive/intel-driver](https://launchpad.net/~glasen/+archive/intel-driver)

And that's recommended by the wiki page:  [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)  You'd want to check out the bug report first before using the ppa.

For the ClamAV thing it sounds like there is a cache that is corrupted.  Google that and find out if there is a way to clear the cache.

---

### Post by itsols on 2010-10-01
Thank you very much indeed for all the help you've given.

You're an invaluable asset to the Ubuntu community.

As for the VGA issue, I think I'll check them out slowly. I've already had enough of trouble ever since I upgraded - smiles...

As for ClamAV, I've even removed and reinstalled it but it hasn't done any good.

Anyway, all of that is secondary and I'm really glad I can use my tablet+stylus.

Once again, MANY THANKS and have a great day!

---

