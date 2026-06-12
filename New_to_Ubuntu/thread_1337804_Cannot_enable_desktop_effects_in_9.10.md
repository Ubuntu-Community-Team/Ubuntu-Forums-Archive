---
title: "Cannot enable desktop effects in 9.10"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by Weepleman on 2009-11-25
Hi, I just set-up a dual boot with windows vista and ubuntu 9.10.  At first everything was great
and I really liked the 'extra' graphics setting.  Then, all of a sudden they went away and when I try to enable them it says searching for availible drivers, and then says desktop effects cannot be enabled.  I installed OpenGl, and
a driver for my video card which is an intel 945GM graphics chipset.  I am pretty much a newby, but here is my lspci  

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
06:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
08:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

and here is my glxinfo | grep direct

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
justin@justin-laptop:/$ glxinfo | grep direct
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig


Oh, also if anyone knows how to make my computer require a password when I start it, I seected the do not need password when I installed ubuntu

---

### Post by Shpongle on 2009-11-25
for the password try system-> admin ->login in screen and unselect autologin.  as for the other problem have you googled rgb glx or fbconfig?

---

### Post by lidex on 2009-11-25
Try one of these:
[http://www.webupd8.org/2009/05/graphic-video-drivers-ubuntu-repository.html]("http://www.webupd8.org/2009/05/graphic-video-drivers-ubuntu-repository.html")
[http://www.webupd8.org/2009/06/new-ubuntu-intel-graphics-drivers.html]("http://www.webupd8.org/2009/06/new-ubuntu-intel-graphics-drivers.html")

---

### Post by Weepleman on 2009-11-25
Hey, that thing with changing the login screen is a bad idea, I did that and now I can't login, I am using recovery mode, and I can't change it back.  If anyone knows how to change it from the command line that would be very helpful[[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=8388461")      Yeah! I got the effects to work, I had nVidia drivers installe for some reason, so I ran apt-get autoremove, and the effects work now, but I still need help turning autologin back on, I can't unlock the login screen preferences for some reason, and they are greyed out.

---

### Post by lidex on 2009-11-25
> **Weepleman said:**
> Hey, that thing with changing the login screen is a bad idea, I did that and now I can't login, I am using recovery mode, and I can't change it back.  If anyone knows how to change it from the command line that would be very helpful
Probably because you didn't set a password at install ??

Either way, two tutorials:
[http://www.howtogeek.com/howto/linux/reset-your-ubuntu-password-easily-from-the-live-cd/]("http://www.howtogeek.com/howto/linux/reset-your-ubuntu-password-easily-from-the-live-cd/")
[http://www.watchingthenet.com/ubuntu-guide-for-windows-users-reset-your-password-when-you-have-forgotten-it.html]("http://www.watchingthenet.com/ubuntu-guide-for-windows-users-reset-your-password-when-you-have-forgotten-it.html")

---

### Post by Weepleman on 2009-11-25
No, I have a password, and can log in from the command line when I use recovery mode.  What happens when i login normally is that I see a list where it says my name, and other.  If I start typing my name it selects the name, and the only shows that one.  Underneath it says something along the lines of could not establish communications with user or something.  What I want is to be able to just have it login for like it did when I first installed ubuntu and selected do not require password at startup. Also, now all of the buttons and icons look like they are in front of black squares. It is not a big deal, but is it a problem?  I get this when I press the unlock button for the login screen settings thing:

** (gdmsetup:3970): WARNING **: Failed to unlock: The name org.gnome.DisplayManager was not provided by any .service files

---

### Post by lidex on 2009-11-26
Try going into command line and enter:
```
sudo gdmsetup
``` as a first step.

---

### Post by Weepleman on 2009-11-26
I uninstalled gdm, and now I can login from the command line.  What I need to find out now is how to automatically start X when I login so I do not need to type it every time.

---

### Post by lidex on 2009-11-27
Two utilities:
system>administration>boot-up Manager
system>administration>login window

---

### Post by Weepleman on 2009-11-27
I uninstalled GDM and then reinstalled GDM, and now it work fine.  Another problem is now on all of the icons on my computer there is a black square around them.  Is this a driver problem, should I just learn to ignore it, or is there a way to fix it?

---

### Post by lidex on 2009-11-27
Try disabling compiz effects and see if that helps.

---

### Post by JCollierDavis on 2009-11-27
I removed Compiz a few days ago since I'm running Netbook Remix.  I have no idea why it was there to start with.  Everything worked great after.

Then on Thursday (26 NOV) afternoon a routine updated and reboot ruined my graphics as mentioned previous.  I have black squares below all the icons, the pictures look terrible and all the system graphics like the Ubuntu logo on the panel, the on/off button etc. all look like the anti-aliasing is turned off.  The bootsplash turned into a white square and the animation is distorted.

The regular graphics, like the desktop image and the menu look fine.  Changing the theme helped some but it's still terrible.  Attached is a sample image. 


lspci | grep -i VGA yields below
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)


I'd love a solution.

---

### Post by Weepleman on 2009-11-28
I started a new thread for this here: [http://ubuntuforums.org/showthread.php?p=8399867#post8399867](http://ubuntuforums.org/showthread.php?p=8399867#post8399867)

---

### Post by lidex on 2009-11-28
Were you running emerald with compiz? Plug in 
```
gnome-system-monitor
``` in Alt+F2 Run dialog. In processes look for emerald. If you see it enter ```
metacity --replace
``` in a terminal.

---

