---
title: "HP laptop - resolution issue"
date: 2010-08-14
forum: New to Ubuntu
---

### Post by Baldrick_NZ on 2010-08-14
I have an HP Laptop that only displays 2 resolutions 640/400 and 800/600 when using the Lucid LiveCD. I really need it to run at a higher resolution if I install Lucid.

The Laptop currently supports Vista, and someone has had a go at installing Mandrake (not me), which has better resolution options than the liveCD. However, I'd rather have Ubuntu run as a dual boot with Vista.

My question is, if I install Ubuntu over (or in place of) Mandrake, will I be able to achieve higher resolutions than offered on the LiveCD?

Looking on the Vista settings, it looks like it has an SiS video chipset. Does this help?

Any help would be greatly appreciated.. :-)

---

### Post by NCLI on 2010-08-14
Please enter "sudo lspci" into a terminal in Linux and post the output here, just to make sure what we're dealing with.

---

### Post by Baldrick_NZ on 2010-08-14
> **NCLI said:**
> Please enter "sudo lspci" into a terminal in Linux and post the output here, just to make sure what we're dealing with.

Thanks for the quick reply..

Here's the output:

ubuntu@ubuntu:~$ sudo lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)

---

### Post by Baldrick_NZ on 2010-08-23
Bump... :p

---

### Post by Grenage on 2010-08-23
In theory it should be simple, with a worst-case scenario of a custom xorg.conf.  I have no personal experience of SiS cards, so can make no guarantees as to what the drivers are like.

---

### Post by Baldrick_NZ on 2010-08-24
> **Grenage said:**
> In theory it should be simple, with a worst-case scenario of a custom xorg.conf.  I have no personal experience of SiS cards, so can make no guarantees as to what the drivers are like.

Thanks for that, so how do I go about creating a custom xorg.conf?

Cheers.

---

### Post by Grenage on 2010-08-24
I have a guide [here]("http://grenage.com/xorg.html"), but there are many others around.  If you get stuck, post back here and I'll help where I can.

---

### Post by Baldrick_NZ on 2010-08-31
> **Grenage said:**
> I have a guide [here]("http://grenage.com/xorg.html"), but there are many others around.  If you get stuck, post back here and I'll help where I can.

Hey, thanks for this! However, I've just checked and I can't find any xorg.conf file under /etc/X11. 

When I run: $ sudo cp /etc/X11/xorg.old, I get this message: "cp: missing destination file operand after '/etc/X11/xorg.old' Try 'cp --help' for more information".

Should I create a xorg.conf file? and, if so, how would I go about it?

Thanks again for your help, it's very much appreciated!

---

### Post by Grenage on 2010-08-31
xorg.conf is no longer created, at least by default, but it will get used if it exists.  You can manually create the file:

```
sudo touch /etc/X11/xorg.conf
```

Then the filling out begins!

Edit:  See wojox's solution first, you'll get a proper template that way.

---

### Post by wojox on 2010-08-31
> **Grenage said:**
> xorg.conf is no longer created, at least by default, but it will get used if it exists.  You can manually create the file:

```
sudo touch /etc/X11/xorg.conf
```

Then the filling out begins!

Isn't 

```
sudo Xorg -configure
```

better Grenage? Won't that load the video drivers and probe the hardware?

---

### Post by Grenage on 2010-08-31
> **wojox said:**
> Isn't 

```
sudo Xorg -configure
```

better Grenage? Won't that load the video drivers and probe the hardware?

Hi, Wojox.

You're right! I haven't used that function for a couple of years, when I first started with Linux - I'd forgotten it even existed.

---

### Post by Baldrick_NZ on 2010-08-31
> **wojox said:**
> Isn't 

```
sudo Xorg -configure
```

better Grenage? Won't that load the video drivers and probe the hardware?

Really appreciate the help guys!

When I execute: '$sudo Xorg -configure', I get the following:

'Fatal server error:
Server is already active for display 0
	If this server is no longer running, remove /tmp/.X0-lock
	and start again.


Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 

 ddxSigGiveUp: Closing log'

So, do I remove /tmp/.X0-lock? And, if I do, will that leave me without any graphics at all?

Cheers.

---

### Post by Grenage on 2010-08-31
I haven't done this in a very long time, but:

Ctrl-alt-f1 should bring you up a terminal.  Log in, then:

```
sudo /etc/init.d/gdm stop
```

I think that should stop X.

---

### Post by Baldrick_NZ on 2010-08-31
> **Grenage said:**
> I haven't done this in a very long time, but:

Ctrl-alt-f1 should bring you up a terminal.  Log in, then:

```
sudo /etc/init.d/gdm stop
```

I think that should stop X.

and then run the previous command?

---

### Post by Grenage on 2010-08-31
Yup, it should run ok once X has stopped.

---

### Post by Baldrick_NZ on 2010-09-01
> **Grenage said:**
> Yup, it should run ok once X has stopped.

Ok, so I tried
[HTML]sudo /etc/init.d/gdm stop[/HTML] and my screen went all hay-wire, like a TV with a severe horizontal hold problem. Couldn't decipher anything, so I couldn't run
[HTML]sudo Xorg -configure[/HTML].

Restarted the PC and it returned to normal.

I then tried
[HTML]sudo /etc/init.d/gdm stop Xorg -configure[/HTML] thinking I was being creative, and that netted the same result. Any other ideas?

Cheers.

---

### Post by Grenage on 2010-09-01
> **Baldrick_NZ said:**
> I then tried
[HTML]sudo /etc/init.d/gdm stop Xorg -configure[/HTML] thinking I was being creative, and that netted the same result. Any other ideas?

Creative indeed; it was a good bet, you'd just need to change the syntax and add a *&*:

```
sudo /etc/init.d/gdm stop & Xorg -configure
```

I could have sworn it used to be *&&*, but a local test works with just one.  Assuming the reconfigure doesn't require input, you could probably add a third command to start gdm again.  I don't know why the screen went haywire, I'm afraid.

---

### Post by Baldrick_NZ on 2010-09-01
Nope, didn't help. Same results as before.

Would it help if I connect a external monitor to the laptop and boot into that? Or would the SiS drivers control that too?

---

### Post by trikster_x on 2010-09-01
[http://www.ubuntugeek.com/how-to-install-sis-771671-mirage-3-video-drivers-in-ubuntu-10-04-lucid.html]("http://www.ubuntugeek.com/how-to-install-sis-771671-mirage-3-video-drivers-in-ubuntu-10-04-lucid.html")

Maybe have a go at this?

---

### Post by StrungOut101 on 2010-09-01
> **Grenage said:**
> xorg.conf is no longer created, at least by default, but it will get used if it exists. You can manually create the file:
 
```
sudo touch /etc/X11/xorg.conf
```
 
Then the filling out begins!
 
Edit: See wojox's solution first, you'll get a proper template that way.
 AWESOME
worked
;)

---

### Post by Grenage on 2010-09-01
> **trikster_x said:**
> [http://www.ubuntugeek.com/how-to-install-sis-771671-mirage-3-video-drivers-in-ubuntu-10-04-lucid.html]("http://www.ubuntugeek.com/how-to-install-sis-771671-mirage-3-video-drivers-in-ubuntu-10-04-lucid.html")

Maybe have a go at this?

Interesting, looks like the OP isn't alone in having the display go.

> **StrungOut101 said:**
> AWESOME
worked
;)

Are you having similar problems?

---

### Post by Baldrick_NZ on 2010-09-01
> **trikster_x said:**
> [http://www.ubuntugeek.com/how-to-install-sis-771671-mirage-3-video-drivers-in-ubuntu-10-04-lucid.html]("http://www.ubuntugeek.com/how-to-install-sis-771671-mirage-3-video-drivers-in-ubuntu-10-04-lucid.html")

Maybe have a go at this?

Nope, tried 4 times, still didn't help. Thanks anyway.

---

### Post by Baldrick_NZ on 2010-09-01
> **StrungOut101 said:**
> AWESOME
worked
;)

So, could you please alude to what commands you actually made in order to make this work for you, StrungOut?

@Grenage, yes this seems to be a wide spread issue. It surprises me that Ubuntu doesn't offer some form of downloadable work around, seeing that it seems such a common issue. Odd.

---

### Post by Grenage on 2010-09-01
Ok, screw that then.

What's your laptop model, and what resolution are you after?

---

### Post by Baldrick_NZ on 2010-09-01
I have a Packard Bell Easynote, Intel Core2 duo T5450 @ 1.66GHz 1.67GHz. 893MB ram.

Looking for 1280x800px, 32bit true colour, 60Hz.

---

### Post by robert shearer on 2010-09-01
Just looked at your lspci output and **maybe** this thread may be of use ??

[http://ubuntuforums.org/showthread.php?t=958967&page=38](http://ubuntuforums.org/showthread.php?t=958967&page=38)

---

### Post by Baldrick_NZ on 2010-09-01
After running that script, I now get a window upon start-up that says:

"Ubuntu is now running in low-graphics mode

The following error was encountered. You may need to update your configuration to solve this.

(EE) open /dev/fb0: No such file or directory
(EE) Screen(s) found, but none have a usable configuration.

OK"

When I click on OK, another box comes up with 5 options. They are:
[LIST]
[*]Run Ubuntu in low-graphics mode for just one session
[*]Reconfigure graphics
[*]Trouble shoot the error
[*]Exit to console login
[*]Restart X
[/LIST]

I click on 'Reconfigure graphics' and get 3 options:
[LIST]
[*]Use default (generic) configuration
[*]Create new configuration for this hardware
[*]Use your backed-up configuration
[/LIST]

My guess at this point would be to 'Create new configuration for this hardware', would it not?

I may need some step-by-step help past this point, please..

EDIT: Actually, when I go to create a new configuration, it doesn't do anything.
So, my options seem to be to use the default(generic) conf, or to use the backed-up conf. 

Any ideas? The generic one would be the one I started with, would it not?

Never Mind. It would only accept using the generic option. Oh well, back to square one again *sigh*

Silly $2 SiS graphics drivers - actually they ain't even worth that! Hope they go broke, and soon!!

---

### Post by Grenage on 2010-09-01
> **Baldrick_NZ said:**
> I have a Packard Bell Easynote, Intel Core2 duo T5450 @ 1.66GHz 1.67GHz. 893MB ram.

Looking for 1280x800px, 32bit true colour, 60Hz.

Try something like this, as an xorg.conf:

```
gksu gedit /etc/X11/xorg.conf
```

```
Section "Monitor"
	Identifier "Monitor0"
	VendorName "PB"
	ModelName "Easynote"
Modeline "1280x800_60.00"   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync
EndSection

Section "Device"
	Identifier "Device0"
	Driver "sis671"
	VendorName "sis"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device "Device0"
	Monitor "Monitor0"
	DefaultDepth 32
	SubSection "Display"
		Depth 32
		Modes "1280x800"
	EndSubSection
EndSection
```

This is assuming that the appropriate driver is installed, did you install the SiS driver in the previously [linked]("http://ubuntuforums.org/showthread.php?t=958967&page=38") howto?  If it all goes wrong and X doesn't then load, you can simply delete the xorg.conf.

---

### Post by robert shearer on 2010-09-01
I'm with Grenage on that xorg.conf.
 
It would be good to see your current xorg.conf. Can you copy and paste here before replacing it with Grenage's.

(Grenage, is that meant to be.......?) ```
gksu **gedit** /etc/X11/xorg.conf 
```

---

### Post by Grenage on 2010-09-01
> **robert shearer said:**
> (Grenage, is that meant to be.......?) ```
gksu **gedit** /etc/X11/xorg.conf 
```

It was! I'll correct my post. :)

---

### Post by Baldrick_NZ on 2010-09-01
Grenage, You are da bomb!!!

Perfect! Actually, it didn't like 32bit so I changed it to 16. 

Other than that, perfect. Thanks again. 

The PC was actually one that my Dad bought a couple of months before he passed away. Now it's Mum's PC. But lately she's been having problems with the constant nagging of Vista to do stuff that she has no idea about. 
Being the die-hard fan of Ubuntu that I've become, it just seemed to make sense that she too experiences life beyond windows.

Grenage (and others who have helped me out), you have probably just helped to add a few more years to not only my mothers life, but also her PC.

Thanks so much.:D

---

### Post by Grenage on 2010-09-01
Glad to hear that it's working. :)

While I don't think it's a bad thing that xorg.conf is being made redundant, we're really still in that 'transition' phase, where it's often easier to go back to it.

---

