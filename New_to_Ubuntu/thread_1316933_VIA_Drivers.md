---
title: "VIA Drivers"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by Sanguinor on 2009-11-06
Okay here is the situation, I have an old Medion MIM2210 laptop that I have kludged back together (I had to replace the screen with one too small and it's taped on) to use as a web browser machine for when I am at home or out and about etc. Now this laptop happens to have a certain VIA graphics chipset installed within it which I can't get working.  I have downloaded the drivers from the VIA website and followed the instructions on there, this has earn't me the following error messages:

install the via driver!
........./usr/bin/install: cannot create regular file `/lib/modules/2.6.31-14-generic/kernel/ubuntu/via_chrome9/via_chrome9.ko': No such file or directory
...VIAERROR:The /etc/X11/xorg.conf is missing!

I have tried to create the xorg.conf in that place but I have had no avail, I did consider tryign to use the openchrome drivers which are apparently installed with ubuntu but none of it makes any bloody sense, atleast not to me. All I want is for my 3D acceleration to work so I can play a few games and have desktop effects running.

I have a basic idea of what I am doing with all of this but I like any instructions to be a) full and b) in plain english.

Further information: Yes this is Ubuntu 9.10

---

### Post by Bucky Ball on 2009-11-06
Not sure if you can get 3D happening with that graphics chipset. Try System->Admin->Synaptic Package Manager, search for 'via'. At the bottom of the list somewhere you should find this:

xserver-xorg-video-unichrome

Is your card listed there? To find what card you are using if you don't know exactly, open a terminal (Applications->Accessories) and paste this in:

```
lspci
```Should be in that list somewhere.

My other suggestion would be load 8.04 LTS and see if that does the trick. Try the alternate install ISO. That is text based install and might get you further. Runs great on my wife's old machine with VIA chipset and graphics.

---

### Post by Sanguinor on 2009-11-09
First off, sorry for the late reply.  I haven't been anywhere near the internet all weekend and I have managed to forget to bring my laptop into work today, I did have a look at what you suggested on Friday and I remember there being an openchrome (I think) option but no unichrome.

I will drag my laptop into work tomorrow and have a better look then get back to you.

---

### Post by anewguy on 2009-11-09
I had a laptop a few years ago that had a Via S3 Unichrome in it, and from my experience it doesn't do a lot of good trying to get 3D working - if I remember right you had to use the openchrome drivers to get that.  But beyond that, I wouldn't count on it for playing any games, compiz eye candy, etc., - mine just didn't support some of things needed to do so.

Dave :)

---

### Post by Bucky Ball on 2009-11-09
Yea, my wife's machine with the VIA chipset doesn't run Compiz. Lucky it is the household admin machine and doesn't have to. Mind you, would be nice to get better streaming vid, even though it works okay as is. :)

---

### Post by Sanguinor on 2009-11-09
Yeah, the main reason I want to put this on is so I can have a bit of eyecandy and so things will run a bit smoother.  It's pretty annoying because I really want to make the transition to Ubuntu completely for my laptop but this problem is starting to tempt me back to W7 which runs like a mint on it.

---

### Post by Sanguinor on 2009-11-11
Right, according to synaptics package manager I already have the openchrome drivers installed... Fun.  So it looks like I need to install the VIA Proprietary drivers.... This is becoming so much fun.

Not.

As a thought, doesn't this package require a xorg.conf in /etc/x11/ ? If it does I haven't got one, and for some strange reason part of the openchrome driver install keeps timing out.

This is really getting on my nerves now, I want to use my laptop more often but something like this is enough to put me off until I can acquire myself something on either intel, ATI or nvidia.

---

### Post by Bucky Ball on 2009-11-11
Yea, you could be pushing s**t uphill with a pointy stick on this one. I for one left it after hours of trying to track down and install the right driver until I realised that was about as good as it was gonna get. Not real well supported and fairly old and obsolete, not that there's anything wrong with that!

If and when you do get new graphics for it, make sure it is going to suit the motherboard and fit the graphics slot. If it is an older one you could be fairly limited by what will fit and what the MB is capable of in the first place. :)

---

### Post by ukripper on 2009-11-11
Playing 3D games on VIA chipset on Linux hmmmm...Are chalk and cheese

---

### Post by Vaphell on 2009-11-11
via chipsets are absolutely horrible when it comes to support. They just don't work with 3d and via doesn't really care. They promised supporting open source community but there are no actual proofs. They release so called drivers once in a blue moon and they rarely even work. I had to configure Fujitsu Siemens laptop with integrated via gfx/audio, fought with it a lot and that was a world of pain.
There was actually one fully working driver for some chipset families for 1 exact version of Hardy kernel (somethinsomethingsomething-16) and no earlier and no later version could ever work. Total failure :/

---

### Post by Sanguinor on 2009-11-11
In all honesty now I think I'm going to leave it, there is just too much sh!t of the same type to wade through.

As for graphics on the lappy, it hasn't got a slot for it unfortunately it's an old piece of crap! I may know linux very well but hardware has always been my cup of tea!

Cheers for the help folk, maybe one day somebodyu will come up with a sem-decent solution to this problem.  That somebody will not be me.

---

### Post by ukripper on 2009-11-11
> **Sanguinor said:**
> 
Cheers for the help folk, maybe one day somebodyu will come up with a sem-decent solution to this problem.  That somebody will not be me.

Will be VIA themselves!

---

### Post by kansasnoob on 2009-11-11
Not sure if this is helpful or not:

[http://ubuntuforums.org/showthread.php?t=1322984](http://ubuntuforums.org/showthread.php?t=1322984)

[http://webbookblog.com/ubuntu-9-10-the-karmic-koala/#comments](http://webbookblog.com/ubuntu-9-10-the-karmic-koala/#comments)

Bravo to celticbhoy for that!

---

### Post by Bucky Ball on 2009-11-11
Wait for an ARM processor in a laptop; graphics part of the processor so I believe.

---

### Post by Sanguinor on 2009-11-12
I will probably be going with a Dell, I want something pretty & decent for an average price, plus I like the customisability of the laptop builds so I can tailor it to my price range.

Right, I have been following this little guide: [http://www.computechgroup.com/?p=498](http://www.computechgroup.com/?p=498) which is essentially the same thing.  My problem still lies here though:

............VIAERROR:The /etc/X11/xorg.conf is missing!

My xorg.conf which should be in /etc/x11/ is not there! I can take a screenshot to prove it, I can also do a search and not find one, anywhere.

Where the hell do I get one of these from? Everywhere I look seems to say "You should have one! Your build won't work without it!" Well believe it or not, mine is not there.

Any ideas folk?

----Edit----


Hahahahahaha, guess what.... 9.10 does not create a xorg.conf file by default because it doesn't need it.  So much for people using legacy hardware with a new OS eh?  Oh well, looks like I have much more to learn.  I am just about to attempt this process:

Taken from; [http://ubuntuforums.org/showthread.php?p=8280317#post8280317](http://ubuntuforums.org/showthread.php?p=8280317#post8280317)

> **ST3ALTHPSYCH0 said:**
> 
The workaround: Burn a copy of 8.04 LTS and boot to the live desktop. Right click on the main menu, select "edit menus" and enable the "Screens and Graphics" menu item under . Open Screens and Graphics (Applications>other>screens and graphics). Now click on the model of your monitor and choose the type (in my case I chose Generic Monitor 1600x1200). Choose ok. Choose ok again. At this point it will tell you that the changes won't take effect until you reboot, but as we know that will actually cause you to lose all of your configurations, so don't reboot yet. Copy the xorg.conf file that was just generated for your hardware to a partition on your machine (this file is located in /etc/X11/). Now you may reboot into your harddrive installation of Ubuntu.

After rebooting open a terminal and backup your current xorg.conf
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.working

```Next open a root file browser:
Alt+f2
```

gksudo nautilus

```Navigate to /etc/X11/
Copy the xorg.conf that you generated into the X11 folder as xorg.conf(if you named it something else you have to make sure that it's xorg.conf now)
reboot

The configuration file generated for my machine had it startign out in pan mode by enabling 2048x1536 virtually. To change this simply open the xorg.conf file as root (sudo gedit /etc/X11/xorg.conf) and change the "virtual" line to your desired resolution, save, and reboot.

If your machine won't accept the new file, I can help you get back to your original configuration, but I don't know enough about editing an xorg.conf file to repair it.

---

### Post by Bucky Ball on 2009-11-12
Keep at it. Nice work, but you might want to try 8.04 LTS.

It is a great deal of fun learning about this wonderful OS though, however you look at it! Change of scenery and surprises are always good. ;-)

---

### Post by Sanguinor on 2009-11-13
Whoops!...

Okay, looks like those drivers do not, I repeat DO NOT, agree with my laptop.  After using the xorg.conf fix and installing the drivers I was blessed with a loading screen then black.  The little ubuntu symbol in white appears then rather than loading the fancy loading screen it just goes black, I don't actually know if it continues to boot behind it's black veil I have the sound turned off on my lappy, but I can't use it without a image anyway.

[B]FIX:
[/B]
Boot into recovery mode, use shell to uninstall drivers using the built in uninstall script (./vuninstall in the folder you extracted the driver too).  

I also removed the xorg.conf thinking it may of been that first (that didn't fix it), I am going to try pasting that back in before I install a different set of drivers.

**What next:**

I am going to try a different set of drivers, last time I used the 3D ones this time I will use the 2D ones.

I am tempted to go back and try 8.04 LTS but in all honesty I would like to try and stay on the latest version so I can keep up to date with the trends (plus 9.04/9.10 is the version I am looking at rolling out at work).

I will keep you all posted.

**Note to Dev's:**

Somebody needs to update the [Openchrome/VIA article]("https://help.ubuntu.com/community/OpenChrome") to inform people that in 9.10 there is not a xorg.conf because for some reason you guys saw fit to remove it (something about newbies breaking there installs with it, well gratz because you just denied anybody with VIA chipsets an easy'ish driver install).

**----Edit----**

Just so you know, having the xorg.conf sitting in your files doesn't make a difference.

---

### Post by ukripper on 2009-11-13
Sorry mate but you are trying to wake the dead horse up. VIA needs to address this issue if they really like to contribute to opensource (which i think they don't). Looks like every vendor wants to jump on the opensource bandwagon but don't want to contribute to the cause.

However, found VIa portal where some drivers are available to download.
[http://linux.via.com.tw/support/downloadFiles.action#downloadDiv](http://linux.via.com.tw/support/downloadFiles.action#downloadDiv)

---

### Post by Sanguinor on 2009-11-13
Yeah those have been the drivers I have been trying to get working, unfortunately I have come across a bit of a problem.  Certain drivers (the 2d ones) don't have an uninstaller.

I'm going to slap a copy of 8.4 LTS and see if they work on that for the time being.

---

### Post by Bucky Ball on 2009-11-14
> **Sanguinor said:**
> 
... plus 9.04/9.10 is the version I am looking at rolling out at work.



BAD idea. 8.04 LTS is the current long-term support Enterprise release and _definitely_ the advised choice for production machines. 

Stick to the LTS releases for business and production machines and any machine you need to be rock solid for days, weeks, months, years. 

You will notice the majority of threads on these forums concern 9.04 and 9.10.

---

### Post by Sanguinor on 2009-11-16
In my defense, I'm just doing what I am told to by the powers that be.

---

### Post by skymera on 2009-11-16
Hello :)

I've run Ubuntu on my laptop for over 2 years. Started out with a 7.04 based system. It has a VIA K8M800 chip and i've been waiting 2 years for some drives. Even just 2D!

I saw some released not long ago and gave a shot trying to install the source. My rating: They suck.

I couldn't get them to work no matter what i tried.

---

### Post by ukripper on 2009-11-16
> **skymera said:**
> Hello :)

I've run Ubuntu on my laptop for over 2 years. Started out with a 7.04 based system. It has a VIA K8M800 chip and i've been waiting 2 years for some drives. Even just 2D!

I saw some released not long ago and gave a shot trying to install the source. My rating: They suck.

I couldn't get them to work no matter what i tried.

In conclusion - VIA will always suck on Linux. Hence, we should boycott these chipsets.

---

### Post by Bucky Ball on 2009-11-16
> **ukripper said:**
> In conclusion - VIA will always suck on Linux. Hence, we should boycott these chipsets.

+1

Unless something changes avoid in future.

---

### Post by Sanguinor on 2009-11-16
In all fairness, boycotting these chipsets is not a reasonable solution.  It's a silly and childish solution. The easiest way forward would be for the community as a whole to put pressure onto companies such as VIA to produce a set of drivers for Linux based operating systems.

I'm going to mark this topic as closed as I am giving up on this stupid laptop now.

---

### Post by ukripper on 2009-11-16
> **Sanguinor said:**
> In all fairness, boycotting these chipsets is not a reasonable solution.  It's a silly and childish solution. 

hmm not really..It is a reasonable solution...boycott has been always a grounds up approach to show your anger and frustration throughout the history. It could be applied in this situation very easily.

Vendors only will listen to minoroties if you show them their products are not welcome within the community unless they put there act straight and produce better drivers for linux.

---

### Post by Bucky Ball on 2009-11-16
> **Sanguinor said:**
> The easiest way forward would be for the community as a whole to put pressure onto companies such as VIA to produce a set of drivers for Linux based operating systems.


That has been going on for years which is why people building a Linux box don't generally consider VIA; because they know nothing is going to change anytime soon. Boycott is your word. 

When I've built a Ubuntu box there are some component manufacturers that are just not on the radar; common sense and research, not a vendetta. Will you go for VIA if you are buying another box and are intending to use Linux? Is it a boycott if you don't? VIA graphics seems to work fine on my wife's computer in Windows but not to it's full potential in Linux because of crap drivers for an old graphics chip. Her whole board is VIA by the way and there are no other issues with it whatever. Great for a cheap board at the time and still seems to be going strong about 7-8 years later.

Good luck with it all and you can mark your thread 'solved' rather than closed from 'thread tools'. :)

---

### Post by sintacto on 2009-11-25
I have been using the openchrome driver for a few years
on a via pc3500g mobo with no issues (no 3d)
flash player is pretty crappy in full screen but 
enjoy videos in mplayer and vlc no problem and play dvd's
my kids play games. all of the games in the standard installation work great. also (gcompris,childsplay,tuxpaint,supertux,frozenbubble,pingus)
google earth works but not great. I run my pc with a dc-dc atx power supply and solar power. and before the intel atom came out this was a very best power efficient motherboard for a cheap price.
many people may not need compiz and 3d games. I just wanted to tell
people that i love my via pc for it is on 24/7 on a small solar panel with 4 golf cart batteries mostly used for rhythmbox, email ekiga phone
and web browsing. 
remember that low power= lower performance 
vesa works on this chip pretty good max 800x600
on the newer versions with no xorg.conf i just pasted my old xorg.conf in /etc/X11/ works fine (have touchscreen)

 
2.6.30-1-686


lspci
00:00.0 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. CN896/VN896/P4M900 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:03.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. Device 5337 (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC] (rev 01)
04:0e.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 8d)
80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)








Section "Device"
	Identifier	"Configured Video Device"
	Driver		"openchrome"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "InputDevice"
        Identifier "ELO Touchscreen"
        Driver     "elographics"
        Option     "Device"     "/dev/ttyS0"
        Option     "AlwaysCore"
        Option     "screenNo"    "0"
        Option     "MinX" "335"
        Option     "MaxX" "3724"
        Option     "MinY" "511"
        Option     "MaxY" "3665"
        Option     "UntouchDelay" "5"
        Option     "ReportDelay" "1"
EndSection

Section "ServerLayout"
    Identifier     "Default Layout"
    InputDevice    "ELO Touchscreen"
EndSection

---

