---
title: "Various problems with Nvidia gfx card - Help please!"
date: 2010-07-28
forum: New to Ubuntu
---

### Post by echoburns on 2010-07-28
Hi,

I'm having a nightmare trying to get my Nvidia 7800 gtx gfx card setup under Ubuntu 10.04.

I have spent hours trying to setup and install the appropriate drivers but I'm going round in circles and have reached the limit of my *small* linux knowledge.

The problems are:

- I can't change the monitor resolution

- Whatever I try I can't get nvidia-settings to work.  Every time I start it, it comes up with "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

-ATM, I have nvidia-current installed but under the hardware settings it says "NVIDIA driver activated but not currently in use"

-It doesn't look like that any hardware acceleration is enabled.

Any help would be greatly appreciated,

Thanks

---

### Post by 4Orbs on 2010-07-28
The steps:
1. Enter this in a terminal, which will create a new xorg.conf file:
```
sudo nvidia-xconfig
```
Probably a good idea to reboot afterwards. NOTE: After rebooting, you'll notice the Ubuntu splash screen is messed up. Unfortunately that is the price we pay for using nvidia drivers.

2. Login and the resolution should have adjusted to the native setting for your monitor. If you want to change resolution, open the Nvidia Settings Mgr. as root user by entering in a terminal:
```
gksudo nvidia-settings
```

3. Change the resolution to the desired, click apply and accept the change. Now click the button at the bottom of the settings mgr to "Save Configuration to /etc/X11/xorg.conf" and select the option to merge with the existing file.

4. Reboot. The Ubuntu splash screen will still be messed up, but your resolution in the desktop should be good.

p.s. I'm assuming you still have the recommended driver installed and activated "but not in use".

---

### Post by echoburns on 2010-07-28
Hi,

Thanks for the reply.

Ok, after sudo nvidia-xconfig I rebooted and message appears saying "Ubuntu is running in low graphics-mode" etc.  I continued through and run in low graphics mode.

Next I tried "gksudo nvidia-settings" and got the "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

:(

---

### Post by 4Orbs on 2010-07-28
OK, then let's try going back to a fresh start. Go to the menu System>> Administration>> Hardware Drivers and select the option to deactivate (Remove) the driver. Before you do that, go to your Preferences>> Appearance settings and choose the default Human theme.

After the driver finishes uninstalling, reboot. You should see the Ubuntu splashscreen... small and pretty as it should be with the default nouveau open source driver now in use.

Login and open the Hardware Drivers mgr again and see if there is a (highlighted) recommended driver for your card. If so, click the button to activate it and wait for the installation to complete... maybe a minute or two. When it finishes you should see a notification that rebooting is necessary.

After rebooting, the Ubuntu splash screen will appear messed up if the driver installation was successful.

p.s. I hope you're Ubuntu wasn't installed with wubi inside of Windows. I don't think the drivers will work with that setup.

---

### Post by echoburns on 2010-07-28
Hi,

Thanks again,  I followed you instructions, removing nvidia_current and rebooting but when I now go to Hardware Drivers it's empty and only says "No proprietary drivers are in use on this system".

Also when I rebooted it started in low graphics mode.  I didn't change the default appearance as I couldn't see a Human theme, my defualt theme is Ambiance.

It isn't installed with wubi.

---

### Post by 4Orbs on 2010-07-28
I forgot that Human isn't part of 10.04, so Ambiance is the right thing. Weird that it still throws you into low-graphics mode. Did you previously install more than one nvidia driver, through the Synaptic Pkg. Mgr, maybe?

If not, then you might only need to run your update manager in order to have a recommended driver show up in the Hardware Drivers Mgr again. Did a recommended driver EVER show up in the Hardware Drivers Mgr previously?

---

### Post by echoburns on 2010-07-28
Hi, I think I probably did try and install more then one Nvidia driver as I was trying anything to get it working.

I have the following installed under Synaptic:

jockey-common
jockey-gtk
nvidia-173-modaliases
nvidia-current-modaliases
nvidia-settings
smartdimmer
xserver-xorg-video-nouveau
xserver-xorg-video-nv

Does that look right?

I don't mind doing a complete re-install if need be.

---

### Post by realzippy on 2010-07-28
*Does that look right?*

That looks as you do not have any nvidia driver installed.

Open terminal,run:

```
sudo rm /etc/X11/xorg.conf
```

```
sudo apt-get install nvidia-current nvidia-current-modaliases
```

Then reboot.After restart:

```
sudo nvidia-xconfig
```

Then restart X or reboot...

---

### Post by 4Orbs on 2010-07-28
EDIT: Hopefully realzippy will have the real solution for you. I'll keep watching the thread.

---

### Post by realzippy on 2010-07-28
Do you have the kernel headers for your running kernel installed?
Which kernel are you running?

```
uname -r
```

---

### Post by echoburns on 2010-07-28
Many thanks for the reponses.

realzippy:

after I run sudo nvidia-xconfig, it output the following:

WARNING: Unable to locate/open X configuration file.

New X configuration file written to '/etc/X11/xorg.conf'

I'm not sure if this is correct but about to reboot again, will let you know.

uname -r
2.6.32-24-generic

---

### Post by echoburns on 2010-07-28
ok, after reboot, back in to low-graphics mode.

nvidia_current is now appearing under hardware drivers but isn't activated, should I activate?

Thanks

---

### Post by realzippy on 2010-07-28
Yes,activate and reboot..

---

### Post by realzippy on 2010-07-28
So,if it still does not work,check in synaptic if 

linux-headers-2.6.32-24
linux-headers-2.6.32-24-generic
linux-headers-generic    


are installed..

---

### Post by echoburns on 2010-07-28
ok, rebooted, straight into low graphics mode.  Nvidia_current appears in Hardware Drivers but says "the driver is activated but not currently in use".

All 3 headers are installed.

---

### Post by realzippy on 2010-07-28
Run again:

```
sudo nvidia-xconfig
```

Restart X or reboot.

Post your */etc/X11/xorg.conf* after this.

```
gedit /etc/X11/xorg.conf
```

---

### Post by echoburns on 2010-07-28
GNU nano 2.2.2                          File: /etc/X11/xorg.conf                                                           

    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24


I used sudo nano /etc/X11/xorg.conf,is this correct?

---

### Post by realzippy on 2010-07-28
Which texteditor you use does not matter.

Your xorg.conf is fine for nvidia...
I am out of ideas,sorry.One last:

Maybe a kernel issue (I am running 2.6.32-23,everything fine).
You could boot into 2.6.32-23 and install nvidia-current again,
just to sort this out..


Just saw this:

[https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/602876](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/602876)

*"The Jockey displayed this message after kernel update 2.6.32-24."*

Sure that 3D does not work?Open ccsm,enable e.g. "wobbly windows" and drag a window around..

```
ccsm
```

---

### Post by echoburns on 2010-07-28
ok, thanks for your help anyway.

Could you explain how to boot a previous kernal please?

Thanks

---

### Post by realzippy on 2010-07-28
If the Grub menu (where you can select the kernel to boot) does
not appear automatically,press *ESC* during boot...


Edit :

sorry,it changed to "SHIFT" since grub2

from
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)   :

[I]# On a new install of Ubuntu 9.10 or 10.04 with no other installed operating system, GRUB 2 will boot directly to the login prompt or Desktop. No menu will be displayed.
# Hold down SHIFT to display the menu during boot (formerly ESC in GRUB legacy). [/I]

---

### Post by Sylos on 2010-07-28
Hello there.
I dont know very much about any of this but it might be worth invesitgating the nvidia driver driect from nvidia and installing it manually (or possibly the previous driver version). I seem to recall there was a problem with the drivers that ubuntu downloaded and installed through the manager a while ago.

---

