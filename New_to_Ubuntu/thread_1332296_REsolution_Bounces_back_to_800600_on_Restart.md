---
title: "REsolution Bounces back to 800*600 on Restart"
date: 2009-11-20
forum: New to Ubuntu
---

### Post by BalaViknesh on 2009-11-20
I am having Ubuntu 9.04.  I have upgraded my Mother Board to ASUS M2N 68 from Intel. I am able to select the 1024*768 resolution in NVidia Settings but upon restart it goes back again to the eye aching 800 * 600.

Can anyone please advice on this.

---

### Post by ukripper on 2009-11-20
> **BalaViknesh said:**
> I am having Ubuntu 9.04.  I have upgraded my Mother Board to ASUS M2N 68 from Intel. I am able to select the 1024*768 resolution in NVidia Settings but upon restart it goes back again to the eye aching 800 * 600.

Can anyone please advice on this.

can you post your output of xorg.conf using below command:
```
cat /etc/X11/xorg.conf
```

and this:
```
lspci
```

---

### Post by BalaViknesh on 2009-11-24
Please find the attached. As i dont have Internet in Home cant reply @ once. Please resolve this 4 me.

---

### Post by BalaViknesh on 2009-12-01
I have upgraded to Ubuntu 9.10 and the same problem still persists. Can anyone throw some light on this. what i have to do to make 1024*768 as my default.

---

### Post by fooman on 2009-12-01
you need to set the resolution in the nvidia-settings *as root* in order for them to "stick".

open a terminal and type:

```
gksudo nvidia-settings
```set the desired resolution,  then click on "save to x configuration file"

hope that helps.

---

### Post by That new guy on 2009-12-01
I'm having the same problem.... I've tried the gksudo nvidia-settings and it says it saved the conf but when i restart i get the same terrible resolution. im on a 42" plasma btw.....

---

### Post by fooman on 2009-12-01
> **That new guy said:**
> I'm having the same problem.... I've tried the gksudo nvidia-settings and it says it saved the conf but when i restart i get the same terrible resolution. im on a 42" plasma btw.....

when you click "save to x configuration file" and the window opens asking you to save or cancel....try unchecking "merge with existing file"

then save.

see if that makes any difference.

---

### Post by gradinaruvasile on 2009-12-01
I too have this problem. Ubuntu 9.04 on Dell D630 laptop - Nvidia Quadro NVS 135M graphics. 
It appeared from 190.42 drivers upwards (or some update maybe?). I did everything possible to fix the resolution but to no avail. I have to set it back manually every restart. And yes, i launch nvidia-settings with sudo.

Until this i never had a problem like it. I use Ubuntu since 7.10 installed many times on computers, most of them with nvidia graphics card.

Also in Xubuntu 9.10 i dont have this problem with the same drivers. Might be an X server issue?

---

### Post by ed-koala on 2009-12-01
In the "Screen" section, try adding the following right below where it says 

DefaultDepth      24

[B]SubSection "Display":
        Depth      24
        Modes      "1024x768"
    EndSubSection
[/B]

*I indented the depth and modes lines but it didn't show up that way, oh well, it was to make it look pretty, not necessary. :)*

---

### Post by BalaViknesh on 2009-12-01
When i am trying to save the xconfig it says "Failed to Parse Xconfig File '/etc/X11/Xorg.conf"

help me in changing to 1024 resolution. My eyes started soaring and am getting irritated to change everytime i reboot

---

### Post by fooman on 2009-12-01
> **BalaViknesh said:**
> When i am trying to save the xconfig it says "Failed to Parse Xconfig File '/etc/X11/Xorg.conf"


when it says that and you click "ok"....doesn't it still show the option to "save x configuration" ?

are you saying that even after saving...it still reverts to 800x600 ?

try deleting the old xorg.conf,  creating a new one then setting the resolution and saving it:

first delete the old xorg file.  open a terminal and type:

```
sudo rm /etc/X11/xorg.conf
```then create a new blank one:

```
sudo touch /etc/X11/xorg.conf
```next open nvidia-settings as root:

```
gksudo nvidia-settings
```set resolution and save to x configuration file (say ok to the parsing warning). also,  uncheck "merge with existing file"...then restart.

hope that helps.

---

### Post by BalaViknesh on 2009-12-01
thanks 4 ur help fooman.

but i am not able to save it even after deleting.

while runnining gknvdia-settings... was able to see the below error ? 
VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
At least one Device section is required.


my LSPCI:
00:00.0 RAM memory: nVidia Corporation MCP61 LPC Bridge (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 7025 / nForce 630a] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:06.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
01:06.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
01:06.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 63)


show me a way forward outta this tunnel

---

### Post by fooman on 2009-12-01
open xorg.conf for editing...in a terminal:

```
gksudo gedit /etc/X11/xorg.conf
```add (copy/paste) the following to the file:

```
Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection
```save and exit,  then run gksudo nvidia-settings again.  set resolution, save to x configuration (uncheck merge),  then restart.

cross fingers.

---

### Post by BalaViknesh on 2009-12-02
Hi,

Still I am getting this validation error. Do i have to give up with this ? or any solution is there to change my screen resolution.


bala@bala:~$ cat /etc/X11/xorg.conf

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

bala@bala:~$ gksudo gedit /etc/X11/xorg.conf
bala@bala:~$ gksudo nvidia-settings

VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
Undefined Device "(null)" referenced by Screen "Default Screen".

---

### Post by Sir Jasper on 2009-12-02
Hi,

I have Ubuntu 9.04 with an Xubuntu Desktop so I am not sure if what follows will help everybody.

Firstly, for those who see their desired resolution in a Display window (e.g, per picture):

[[img]http://h.imagehost.org/t/0522/Resolution.jpg[/img]](http://h.imagehost.org/view/0522/Resolution)

I have opened two copies of my Display window to make viewing easier.

The red arrow points to 1024x768 which is the 12th item down, but starting the count from Zero it is the 11th item from the top.

So I can set my resolution (and desired refresh rate) with:

xrandr -s 11 -r 60

Which I type into a NEW (ADD) entry in my SESSION & STARTUP > Application Assistant which sets that resolution on booting.

I have also added a multi-launcher to my panel with that code in the Command Line and with Run in Terminal ticked. I have also three other frequently used resolutions available there.

My regards

---

### Post by fooman on 2009-12-02
> **BalaViknesh said:**
> Hi,

Still I am getting this validation error. Do i have to give up with this ? or any solution is there to change my screen resolution.


bala@bala:~$ cat /etc/X11/xorg.conf

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

bala@bala:~$ gksudo gedit /etc/X11/xorg.conf
bala@bala:~$ gksudo nvidia-settings

VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
Undefined Device "(null)" referenced by Screen "Default Screen".

what happens when you run "sudo nvidia-xconfig" in a terminal,  then log-out and back in again?

---

### Post by ukripper on 2009-12-02
This thread may help. look at my posts here - [http://ubuntuforums.org/showthread.php?t=1338242&page=2](http://ubuntuforums.org/showthread.php?t=1338242&page=2)

---

### Post by Gene Rodgers on 2009-12-02
Try installing gnome-control-center and screen-resolution-extra from your package synoptic package manager. If gnome-control center shows installed, re-install it.
Gene-w5ffa

---

### Post by BalaViknesh on 2009-12-02
I have installed gnome control center as well..

@ Fooman : 
Please see the output for me for the below commands

bala@bala:~$ sudo dpkg-reconfigure -phigh xserver-xorg
bala@bala:~$ sudo nvidia-xconfig
bala@bala:~$

but still I am not able to change my screen resolution.

i AM HAVING ONLY THESE ATTRIBUTES IN MY XORG FILE. 

Section "Screen"
    Identifier    "Configured Screen Device"
    DefaultDepth    24
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "nvidia"
EndSection

---

### Post by BalaViknesh on 2009-12-04
plz help me out in resolving this. what else should I do to bring my monitor back to 1024*768 whenever it reboots.

---

### Post by Sir Jasper on 2009-12-04
Hi,

You have made no comment that you tried my suggestion above.

When you set to 1024*768 manually, how many items from the the 1st option is it and what is your choice, if any, of refresh rates?

My regards

---

### Post by BalaViknesh on 2009-12-04
Hi Jasper,

apologies for missing ur reply. I am not able to get what should I do to get taht list exactly. 
plz show what i have to do to get that screen.

---

### Post by Sir Jasper on 2009-12-04
Hi,

After you have booted, how do you do to change to 1024*768?

Can you stay on line for a few minutes?

Cheers

---

### Post by BalaViknesh on 2009-12-04
I have to go to Nvidia Settings and apply the 1024 * 768 resolution and apply it. when i try to save it wont, but it ll apply the 1024 *768 resolution.

Am online Jasper.

---

### Post by Sir Jasper on 2009-12-04
Under the Admin menu do you see  SETTINGS and then DISPLAY?

---

### Post by BalaViknesh on 2009-12-04
Yup... what should i do over there.

---

### Post by Sir Jasper on 2009-12-04
Click on DISPLAY then does it look like the picture I posted earlier?

If it does, how many items down is 1024 x 768 (it may be the top item), then if you click on it what is the Refresh Rate shown as?

---

### Post by Sir Jasper on 2009-12-04
Hi,

I have waited 20 minutes for your reply. I will check for the last time in half an hour or so.

---

### Post by BalaViknesh on 2009-12-04
Sorry jasper. there was power outage. so cant reply @ once.

1024 * 768 is the first option and refresh rate is 60 Hz.

---

### Post by Sir Jasper on 2009-12-04
After restarting type or copy and paste into your Terminal as follows:

xrandr -s 0 -r 60

Surely that works?

---

### Post by BalaViknesh on 2009-12-04
Jasper see the reply for this

bala@bala:~$ xrandr -s 0 -r 60
bala@bala:~$

the same prob persists.

---

### Post by Sir Jasper on 2009-12-04
Hi,

Yes the problem persists on booting, but I asked you if it changed the resolution to your desired 1024*768.

If it does, my first post, with the picture, said how to make it permanent.

My regards

Just read my first post here, but come back if you still have a problem.

---

### Post by Sir Jasper on 2009-12-04
Hi,

Get to the large screen, click Add, enter the details exactly as per the small inset window, click OK, click close. Then restart.

[[img]http://h.imagehost.org/t/0039/ScreenResolution.jpg[/img]](http://h.imagehost.org/view/0039/ScreenResolution)

My regards

If you are not working tomorrow then hopefully you will see this on Monday.

Added:
The details in the small window are specifically for this user. Other users who may wish to try this method of setting their screen resolution on bootup should see Page 2 #15.

---

### Post by BalaViknesh on 2009-12-04
hi Jasper,

now on reboot also i am getting 1024*768 resolution. Many thanks 4 ur help in resolving this. :popcorn::D

---

### Post by Sir Jasper on 2009-12-05
Hi,

Glad to hear it, but pay much closer attention to the replies if you raise another thread and it is Sir Jasper or Algernoon.

My regards

---

### Post by aboud on 2009-12-30
> **Gene Rodgers said:**
> Try installing gnome-control-center and screen-resolution-extra from your package synoptic package manager. If gnome-control center shows installed, re-install it.
Gene-w5ffa

I've heard in different places about "screen resolution extra" but no way i can find it, i reinstalled gnome-control-center but nothing is said about resolution excpet the usual display preference is that what you are talking about . ?  because not long ago I gave up trying to get right resolution on my nVidia and returned to my old Video card.

---

