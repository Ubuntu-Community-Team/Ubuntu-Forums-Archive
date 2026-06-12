---
title: "Please Help! New User, with HUGE problems."
date: 2008-12-29
forum: New to Ubuntu
---

### Post by mzdawg123 on 2008-12-29
Hello everyone!

I recently decided to install Ubuntu 8.0.4, due to growing tired of Windows XP. This is a great OS, but I have run into some problems very early on. I will try to be as specific as possible, because this problem is preventing me from being able to even use the operating system!

The biggest hindrance to my ability do anything AT ALL is a problem with my screen resolution. I installed the OS with no problems earlier today, and also enabled restricted drivers for my graphics card (ATI Radeon X1300 PRO), as well as an install of Firefox 3. Everything was displayed just fine, at my preferred resolution of 1280 x 768.  

However, when I restarted my computer (First Restart), the bootup screen loaded up fine, but after that I got a black screen with a "No Signal" message on my 26" Sharp TV/Monitor. Couldn't even view the login screen. Now, I could have pressed esc during bootup to enter in some commands or whatever, but I'm a COMPLETE newbie when it comes to that stuff. So I reinstalled Ubuntu, and I'm using it once again right now. I'm afraid to reboot, because I know the dreaded no signal problem will occur, and I will not be able to log in.  When  this display problem happened on XP I just changed the res to a supported one, and it stayed that way FOREVER.

A while ago I also tried to upgrade to 8.10, and after reboot it happened again....

How am I going to use Ubuntu when I can't even view the login screen? Now, I'm going to specify that I HIGHLY favor graphical interface over that terminal stuff, but, is there anything I can do RIGHT NOW before a reboot, to make sure the Resolution is not CHANGED? I'd love to use this OS, but I need to solve this problem before anything else. I'd prefer to maintain my 1280 x 768.

I still haven't installed Catalyst Control Center or drivers yet, btw, but I think that once I do, this problem will once again bite me in the butt as soon as a restart is initiated...

Help would be GREATLY appreciated so I can actually use my computer! :D

---

### Post by DGortze380 on 2008-12-29
very little experience with ATI, but some things to start with:

try booting the recovery kernel. Press ESC at boot to enter GRUB and select recovery.

At the log in screen you could also try ctrl-alt-f2 to drop to a bash shell

If you find your self at a shell and don't know what to do, the shutdown command is:

sudo shutdown -h now

your password is your regular user password.

---

### Post by mzdawg123 on 2008-12-29
Thanks DG! Hopefully I won't have to resort to shutting down or using recovery mode, but that will help when I run into these problems.

These forums are great. Quick responses ftw.

---

### Post by mzdawg123 on 2008-12-29
Come on guys, any ideas? I REALLY want to solve this problem. As soon as it is resolved, everything will go much more smoothly.:confused:

---

### Post by Hospadar on 2008-12-29
Why not try 8.1O? hardware support is alawys getting better. A lot of time upgrading is the easiest fix

---

### Post by mzdawg123 on 2008-12-29
Well, as I said above, when I upgraded to 8.10, the No Signal problem occurred after the reboot. I just need to know how to keep a supported resolution set for my computer. The res must keep changing or something of that nature. I don't want to have to boot in recovery mode, then change the res afterwards, every time I use my PC! :(

By the way, I'm REALLY starting to enjoy this OS, I need to find a way to fix this, lol.

Thanks for your reply, though!

---

### Post by DGortze380 on 2008-12-29
can you drop to a shell (or open a terminal if possible) and post the output of:

```

cat /etc/X11/xorg.conf

```

---

### Post by RomeReactor on 2008-12-29
Hi. I have very little experience with ATI cards as well, but can you give us more details about your system (CPU, RAM, is the system old)? Have you tried removing the ATI driver, so the system uses one of the open source ones (xserver-xorg-video-ati or xserver-xorg-video-radeon)?

Try completely removing the proprietary ATIdriver:
```
sudo aptitude purge fglrx-amdcccle xorg-driver-fglrx
```
Then reboot:
```
sudo reboot
```
Go into recovery mode and select XFIX.

---

### Post by mzdawg123 on 2008-12-29
Alright, first, these are my specs:

Compaq Presario SR1800NX( Early 2000's)
Sharp 26" LCD
ATI Radeon X1300 PRO
100GB HDD
1GB RAM Kingston 
346 Intel Celeron D Processor
Ubuntu 8.0.4

---

### Post by mzdawg123 on 2008-12-29
Should I enable the restricted drivers, by the way? Or maybe that notification is gone now that I got rid of the proprietary ones.

I tried the thing Rome suggested and had a successful reboot! But I'm going to restart again to make sure it plans to stay this way. So, should I install the latest ATI drivers and stuff, or would this result in the aforementioned problems? Or were the latest ones automatically installed after the XFIX thing I did...idk, lol. I'm a newb. I also hope that installing the 300+ updates for Ubuntu won't result in the No Signal problem somehow. Should I do this? Sorry for all the questions. This problem might be solved already, just making sure.

---

### Post by igknighted on 2008-12-29
> **mzdawg123 said:**
> Should I enable the restricted drivers, by the way? Or maybe that notification is gone now that I got rid of the proprietary ones.

I tried the thing Rome suggested and had a successful reboot! But I'm going to restart again to make sure it plans to stay this way. So, should I install the latest ATI drivers and stuff, or would this result in the aforementioned problems? Or were the latest ones automatically installed after the XFIX thing I did...idk, lol. I'm a newb. I also hope that installing the 300+ updates for Ubuntu won't result in the No Signal problem somehow. Should I do this? Sorry for all the questions. This problem might be solved already, just making sure.

Yes, on a display of that size, you will probably need the restricted drivers to get adequate performance.

What type of connector are you using to connect the monitor to the video card?  It sounds as if when you get the no-signal, that ubuntu isn't recognizing which connector you are using.

---

### Post by mzdawg123 on 2008-12-29
I'm using VGA for the connection to the video card.

Also, I hope enabling the restricted drivers doesn't screw it up. I want the best performance though. I'm going to install Catalyst Control center as well, for better customization of res and refresh rates. And the 300+ plus updates, lol.

But yeah, VGA.

---

### Post by DGortze380 on 2008-12-29
In my experience, updates rarely break anything. Upgrades often do.

---

### Post by mzdawg123 on 2008-12-29
Almost forgot to do this. 

mzdawg@mzdawg-desktop:~$ cat /etc/X11/xorg.conf
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
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

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

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

---

### Post by kelean on 2008-12-29
Now that you haveyour system back up and running.  You could download and burn 8.10 and try installing that.  Hopfully the hardware detection will be improved enough to give you the best resolution.

Second thing burn 8.10 then try the proprietary drivers.  Then you have the dick as a backup if things go bad.  Just a thought, good luck.

Kelean.

---

### Post by balaknair on 2008-12-29
There's a known bug in 8.10 with some ATI cards, where the screen goes into power save mode. To work around it, install from the safe graphics mode and then update the drivers.
Here's how:
1)Boot from CD and at the first screen, instead of selecting "Try Ubuntu without changes..." press F4 for more options
2)Then select "Safe Graphics Mode" and press Enter
3)Now you can start up the Ubuntu GUI in 'Safe Graphics Mode'

The graphics won't be very pretty, probably low resolution as well, but it will enable you to install the OS easily from the GUI. After installing Ubuntu, you can install and activate the latest ATI drivers to get the best out of your card.
1) Boot into the newly installed Ubuntu--> you'll probably get notifications about updates available. Install those but don't reboot yet. Use the Add/Remove Programs entry in the Application menu to get the restricted ATI driver. Now reboot.
2) After rebooting, you can go into System Menu>Administration>Hardware Drivers and you'll be able to activate the restricted drivers.
3) You might have to reboot one more time. This time the system will boot using the restricted ATI drivers and you can now safely adjust the screen resolution.

Hopefully this should do it.


But if Safe mode too does not work:

1) When the screen comes up blank(with the errors etc.), press Control+Alt+F1, to get to a text console(no GUI). Then edit the video configuration file (/etc/X11/xorg.conf) using the command

sudo nano /etc/X11/xorg.conf

2) You'll see a file with # comments and immediately below that a section that says

Section "Device"
Identifier "Configured Video Device"
EndSection

3) Add a line after the identifier which forces the driver, Driver "vesa" so that the file looks like this.

Section "Device"
Identifier "Configured Video Device"
Driver "vesa"
EndSection

4) Save the file, by pressing Control+X, then Y, then press 'Enter'. Now press Control-Alt-F7 to return to the blank screen, then press Control+Alt+Backspace to restart the X server, and if all goes well, the X server will restart and you will have a barebones GUI which you can use to install Ubuntu.


If you install from the Live CD while in safe mode or have modified the xorg.conf file, the installed system will use the same settings you had set up when you installed. So after installation, you will have to boot from the hard disk, log in, and install and activate the proprietary ATI drivers to get a fully functional video setup. Don't make any changes to the basic VESA set up till you have done this(eg. don't try to change the resolution etc.)

Normally, once you boot up, Ubuntu should inform you that proprietary drivers are available for your hardware, but since your video card apparently isn't talking to Ubuntu at all, you can download the the drivers yourself.

Applications menu> Add/Remove Applicationss--> Search for 'Radeon'--> There should be one entry for an ATI driver(package name 'ATI binary X.Org driver') which is maintained by Canonical(it'll have a little Ubuntu logo or a rose next to it)--> Select this, and click 'Apply Changes' to download and install the driver.

Now reboot the system.

Now you have to activate the proprietary driver.

System Menu> Administration> Hardware Drivers --> select the driver you want and click 'Activate'.
This step might take 2-3 minutes and during 'activation' your screen graphics might get a little crazy for a few seconds, but will then stabilize.
You will now have to restart the system again, and this time it should boot up with the correct Radeon drivers for your GPU card.

---

### Post by PierreDeKat on 2008-12-29
Does your computer have an onboard video adapter? If so, connect your monitor to that, reboot, and see if you get some semblance of a desktop to boot up, even if it's only 16 colors.

Or if you have an alternate video card you can slap in temporarily, that will force Ubuntu to shed the ATI drivers, and you should then be able to login to your desktop in some low graphics mode, like 800x600 or something.

Swapping monitors temporarily may also force Ubuntu to reset to low graphics mode and get you into your desktop.

Anywho, once you get to your desktop, double check your video resolution and refresh rates to make sure that both the ATI card and your monitor support the setup.

Anything outside of either's parameters will cause them to puke on what you're trying to feed them. Does that make sense? You have to feed them something they can digest.

---

