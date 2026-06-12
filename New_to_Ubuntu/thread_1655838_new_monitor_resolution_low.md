---
title: "new monitor resolution low"
date: 2010-12-29
forum: New to Ubuntu
---

### Post by akaawol on 2010-12-29
I had G-OS before upgrading to ubunto 10.10 because I got a new **Acer P215H. ** I looked threw the form to see what video card i have and it came back with this:
 01:00.0 VGA compatible controller: VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] (rev 01)
the highest resolution I can get is 800x600. 

I so need help. I'm really new to Linux based computers so go easy on me and how to resolve this plz

---

### Post by Jerry N on 2010-12-29
Has Ubuntu offered to install new drivers for your video?  What resolution were you able to use prior to getting the ACER monitor and installing Ubuntu?

Your monitor is capable of 1080 x 1920 at 60 hz so it shouldn't be the problem.  

You may need to post this on the Multimedia & Video forum.

Jerry

---

### Post by akaawol on 2010-12-29
before this new monitor I had the resolution at 1024x768 (it was an older IBM VGA) 

I haven't found a way to install drivers. I did try to use the ARandR but it didn't help me get any other resolutions than the ones that were there

---

### Post by Locke_99GS on 2010-12-29
You can set a modeline. This is a good tool for building proper modelines.
[http://amlc.berlios.de/](http://amlc.berlios.de/)

Make sure your chrome drivers are installed.
```
sudo apt-get install xserver-xorg-video-openchrome
```

---

### Post by akaawol on 2010-12-29
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-openchrome is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-22 linux-headers-2.6.35-22-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Didn't work :confused:

---

### Post by akaawol on 2010-12-30
I had G-OS before upgrading to ubunto 10.10 because I got a new Acer P215H. I looked threw the form to see what video card i have and it came back with this:
01:00.0 VGA compatible controller: VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] (rev 01)
the highest resolution I can get is 800x600.

I've learned that the monitor is capable of 1080 x 1920 at 60 hz

I've also made sure your chrome drivers are installed

I so need help. I'm really new to Linux based computers so go easy on me and how to resolve this plz

---

### Post by cipherboy_loc on 2010-12-30
Open up a terminal (Applications -> Accessories -> Terminal) and type:
```
xrandr
```

This will give us the resolutions supported by your monitor.


Cipherboy

---

### Post by realzippy on 2010-12-30
Open a terminal,type:

```
gksudo gedit /etc/X11/xorg.conf
```

If an empty file pops up,paste in this:

```
Section "Device"
 Identifier "Configured Video Device"
 Driver "openchrome"
EndSection
Section "Monitor"
 Identifier "Configured Monitor"
 Option "DPMS"
 HorizSync 28-80
 VertRefresh 43-60
EndSection
Section "Screen"
 Identifier "Default Screen"
 Monitor "Configured Monitor"
 Device "Configured Video Device"
 DefaultDepth 24
 SubSection "Display"
  Depth 24
  Modes "1920x1080"
 EndSubSection
EndSection
Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
EndSection
```

Close the file saving changes.Reboot & pray...


If it does not work:

Write the commands below down/print them before going on.
Press Alt+Ctrl+F1,a shell opens,log in with username/password.
Run (line by line):

```
sudo service gdm stop
      sudo Xorg -configure
      sudo reboot
```

Now you have a generated file:
*xorg.conf.new*
in your user's home directory.
Post the content of this file,so we can add a modeline that fits your needs.

---

### Post by realzippy on 2010-12-30
.

---

### Post by Iowan on 2010-12-30
Threads merged.

---

### Post by akaawol on 2010-12-30
WOW! The first long script worked. I'm totaly excited and so was the wife......Until we went to "switch users" now her login is still at the 800x600 max. Do I do the same script under her login?

---

### Post by realzippy on 2010-12-31
No!
It was not exactly a script...it was the content for the file:
xorg.conf you created.This file is a "system" file for all users,owned by root.log in in your wife's account,open a terminal,run:

```
rm ~/.config/monitors.xml
```

Then log out,log in again (wife's account).If still not working,open
System/Preferences/Monitors ;the resolution should be now available..
good luck.

---

### Post by akaawol on 2010-12-31
didn't work gave the message: 
rm: cannot remove `/home/denise/.config/monitors.xml': No such file or directory

---

### Post by realzippy on 2010-12-31
Can you create a new "test" user to see if the resolution is limited also?

---

### Post by akaawol on 2010-12-31
Nope that new account works perfect. So I've given her the new account and deleting the old one. Thanks for all your help. 

you rock!:guitar:

---

### Post by turbo9 on 2011-01-22
I just had this problem (again) and blamed my ATI card. This was with Ubuntu 10.10 running on bare hardware.

It turns out that Ubuntu could not get the right video resolution from my monitor. I see a number of these messages in dmesg


[ 12.905074] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 63
[ 12.905125] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[ 12.905166] <3>40 ff ff ff ff ff ff ff 22 64 b3 06 01 08 00 00 @......."d......
[ 12.905170] <3>2e 0f 01 03 0a 22 1b 78 ea fd 59 a5 53 4a 9d 24 .....".x..Y.SJ.$
[ 12.905173] <3>14 4f 56 bf ef 80 81 80 31 0a 31 ca 01 01 01 01 .OV.....1.1.....
[ 12.905176] <3>01 01 01 01 01 01 30 2a 00 98 51 00 2a 40 30 70 ......0*..Q.*@0p
[ 12.905179] <3>13 00 52 0e 11 00 00 1e 00 00 00 fd 00 38 4b 1e ..R..........8K.
[ 12.905182] <3>50 0e 00 0a 20 20 20 20 20 20 00 00 00 ff 00 35 P... .....5
[ 12.905185] <3>34 36 44 44 31 4b 43 41 32 30 34 39 00 00 00 fc 46DD1KCA2049....
[ 12.905188] <3>00 48 61 6e 6e 53 74 61 72 20 55 31 37 31 00 80 .HannStar U171..

Now, this worked in Ubuntu 10.04, but didn't in 10.10. Then, it magically started working in 10.10 for a few weeks and then the problem came back.

Here is how I fixed it:

You don't need to be root to do this.

Check to see if the video mode exists. 

xrandr

If the one we want is missing, we need to add it. 
Get the mode line from the desired resolution:

cvt 1280 1024	

which barfs out something like:

# 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
Modeline "1280x1024_60.00" 109.00 1280 1368 1496 1712 1024 1027 1034 1063 -hsync +vsync

Grab the modeline from the second line of output and add it to the known modes:

xrandr --newmode "1280x1024_60.00" 109.00 1280 1368 1496 1712 1024 1027 1034 1063 -hsync +vsync

Things might shimmy a bit, which you might interpret as a good sign.

Associate this mode with the appropriate video output

xrandr --addmode VGA-0 1280x1024_60.00

Then use your normal video resolution gui to set it and then make it the default.

This setting does not survive a reboot. You get a bunch of "could not set monitor resolution" messages.
The default setting survives the restart, but the system does not know the mode exists (same problem as before).
So, write a script with the steps above and execute it once you login (put a call to it on the panel). 

xrandr --newmode "1280x1024_60.00" 109.00 1280 1368 1496 1712 1024 1027 1034 1063 -hsync +vsync
xrandr --addmode VGA-0 1280x1024_60.00

Things should shimmy and then go to the resolution you set as default before.

This is not a permanent fix - it is a hack, but I can live with it (rather than buying a new monitor).

---

