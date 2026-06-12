---
title: "graphics card driver problem"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by lab_rat_mat on 2008-12-18
Hi all,

I recently bought a Dell inspiron 530 with Ubuntu to rid myself of windows but when I upgraded HH to II the graphics went stuttery and if I go into the drivers I get: "ATI/AMD proprietary FGLRX graphics driver" is not activated, and when I press the green button to activate it, nothing happens.  I have seen some threads before on this, but nothing that solves my problem, and I need the most idiot-proof guide to fixing this.

Any ideas?

---

### Post by Michael.Godawski on 2008-12-18
hi, 

have attached the screen-shot of my hardware drivers gui. Any difference?

Have you restarted the machine?
Can you please post the output from this terminal command:
```
sudo lshw -C display
```

---

### Post by lab_rat_mat on 2008-12-18
Hi Michael,

I have re-started the PC many times.

Here is the output you requested:

*-display UNCLAIMED     
       description: VGA compatible controller
       product: RV610 video device [Radeon HD 2400 PRO]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: latency=0

The picture you sent is the same as mine, only the green light isn't on for the driver, and when I press activate, there is a breif timer bar for "downloading & installing driver" that quickly dissappears.

-Matt

---

### Post by Michael.Godawski on 2008-12-18
> **lab_rat_mat said:**
> Hi Michael,

I have re-started the PC many times.

Here is the output you requested:

*-display UNCLAIMED     
       description: VGA compatible controller
       product: RV610 video device [Radeon HD 2400 PRO]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: latency=0

The picture you sent is the same as mine, only the green light isn't on for the driver, and when I press activate, there is a breif timer bar for "downloading & installing driver" that quickly dissappears.

-Matt

But your internet is working? hm perhaps you have to enable the software sources...
Have a look here:

[LIST]
[*][http://godawski.oxyhost.com/howtoinstall.html](http://godawski.oxyhost.com/howtoinstall.html)
[/LIST]
there is a screen shot of the software sources. System> Administration >Software Sources, make sure they are all activated; then reload and try again.

---

### Post by lab_rat_mat on 2008-12-18
Hi Michael,

I checked the software sources and everything was as on the web-link, then I went into "applications" - "add/remove" and took off the "hardware drivers" package and re-installed the same one.  There is another available in system tools also called hardware drivers for KDE interface, and I downloaded that as well.  I then went back to System>Administration>Hardware Drivers and still the button won't press.

Did I do what you suggested...I am really a total beginner at this!

---

### Post by Michael.Godawski on 2008-12-18
Your Radeon HD is a newer card, isn't?

I guess the support for this cards is still in flux. But have a look here:
[https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)
Might be a little tempting so much terminal code, but what did not kill us makes us stronger:

run in terminal
if you are on 8.10
```
sudo apt-get install x11proto* xutils-dev autoconf debhelper diffstat libltdl7-dev libpci-dev quilt libdrm-dev configure-debian git-core gawk xorg-dev libmail-box-perl libgl1-mesa-dev
```if you are on 8.04
```
sudo apt-get install x11proto* xutils-dev autoconf debhelper diffstat libltdl3-dev libpci-dev quilt libdrm-dev configure-debian git-core gawk xorg-dev libmail-box-perl pciutils-dev libgl1-mesa-dev
```then run
```
sudo apt-get build-dep xserver-xorg-video-radeonhd
```restart
run again```
sudo lshw -C display 
```Hopefully you get to the login screen after the installation of these drivers :p

---

### Post by lab_rat_mat on 2008-12-18
Hi Michael,

I followed your instructions, and re-started and ran the following:

matt@dell-desktop:~$ sudo lshw -C display
[sudo] password for matt: 
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: RV610 video device [Radeon HD 2400 PRO]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: latency=0

Does it mean anything to you?  The graphics are still stuttering and the driver window still won't activate.

I am thinking that maybe I could find someone locally who could come and have a look if this line of enquiry fails....

-Matt

---

### Post by Michael.Godawski on 2008-12-18
One last attempt. All or nothing :p

> **Configuring xorg.conf for radeonhd**

 Open your xorg.conf for editing: 
```
gksudo gedit /etc/X11/xorg.conf
```Now change/add the Driver line in the Device section. You can also add the option for Direct Rendering here. 
```
Section "Driver"
        ...     
        Driver   "radeonhd"
        Option   "DRI"    #Only works for X1k cards and RS690 IGP at this time
EndSection
```If you're using DRI, you can explicitly load the dri module. 
```
Section "Module"
        ...
        Load  "dri"
EndSection
```
Also, add this section to give non-root applications access to DRI services 
```
Section "DRI"
        Mode         0666
EndSection
```Save the file and quit. The changes will take place the next time you restart. 

---

### Post by lab_rat_mat on 2008-12-18
Right,

I'm about to do what you said, but two questions - what is direct rendering and do I need it?

Also, when you say all or nothing, is there any chance everything will crash and burn?  If so I may not take the risk!

-thanks for all your help so far btw.:p

---

### Post by lab_rat_mat on 2008-12-18
-and I've gone ahead and done the first step, but in xorg.conf there is no subheading of "Driver"???

?

---

### Post by Michael.Godawski on 2008-12-18
All or nothing. sry for scaring you.:p
Sometimes after the edit of the xorg.conf file strange things happen, and you have to reconfigure the xorg.conf file with
```
sudo dpkg-reconfigure xserver-xorg
```Can you please post your xorg.conf file

```
cat /etc/X11/xorg.conf
```

---

### Post by TyTiger on 2008-12-18
You could try EnvyNG
in a terminal type the following:
```
sudo apt-get -y install envyng-core envyng-qt envyng-gtk
```

then run it either from the Applications menu or by running it from the terminal

```
sudo envyng -k
```
or to run the text based version (good if the Xserver breaks)
```
sudo envyng -t
```

Hope this helps
EnvyNG fixed my graphics drivers and made them work well :)
EnvyNG's about as Beginner friendly as it gets.

---

### Post by lab_rat_mat on 2008-12-18
Hi Michael:

here's the xorg.conf file:

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
# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier  "Generic Keyboard"
#	Driver      "kbd"
#	Option	    "XkbRules" "xorg"
#	Option	    "XkbModel" "pc105"
#	Option	    "XkbLayout" "gb"
#EndSection
# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier  "Configured Mouse"
#	Driver      "mouse"
#	Option	    "CorePointer"
#EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth	24
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
EndSection

Section "Device"
	Identifier  "Configured Video Device"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Option	    "ForceMonitors" "notv"
	BusID       "PCI:1:0:0"
	Driver	"fglrx"
EndSection



AND I ran the first line of the code you suggested in last post and got a box that said "rather than communicating directly...blah, blah..Use Kernel framebuffer device interface?

-should I answer yes?

---

### Post by Michael.Godawski on 2008-12-18
My fault. Shouldn't have posted this sudo dpkg reconfigure code. But I did not say you should run it either. :p If you are in the process of reconfigure xorg just keep going, answer with common sense, if you are uncertain select the default option. Let's see what happens.

Do you have any data that we have to rescue if this fails:p?

---

### Post by lab_rat_mat on 2008-12-18
The reconfigure thing - I just closed the window and nothing has changed so I don't think there's anything wrong or needs rescuing.  Perhaps I should stop messing about for the time being....or try the suggestion about Envy.

Did the xorg.conf file tell you anything useful?

---

### Post by LtPitt on 2008-12-18
If you need a brutal, cheap solution, Envy did great for me :)

If you need learning maybe it's not the greatest idea: it's fully automatic :)

---

### Post by lab_rat_mat on 2008-12-19
Hi,

if anyone can still help - I installed envy, and attached is the screen shot which as far as my pea-brain can tell, indicates that a driver is present.  I'd imagined that there would be some sort of choice for this to work, but as I do not have a NVIDIA card, there is no other choice for ATI.

Any ideas?  Anyone?  The stuttering graphics are driving me nuts, and I cannot watch videos as they make me sea-sick...!


p.s. thanks to everyone for all your help so far.

---

