---
title: "[SOLVED] Different LTSP Client graphic problem"
date: 2007-12-11
forum: Networking &amp; Wireless
---

### Post by Dragonbite on 2007-12-11
I say "different" because I haven't seen this type of error in other posts and I hope it i an easy fix, but I don't know how.

I have Edubuntu 7.10 up and running on a Dell Optiplex GX260 running at 2GHz and with 512MB Ram (going to up that once I can get the clients working). It is connecting a Gigabit NIC to a Gigabit Switch (and a second NIC for internet when it is available).

I can log directly into the server with no issues and have managed to log in a client in before, though the client was a more up-to-date laptop.

I have 2 Dell Dimensions 4100 I've recently gotten (plus 1x4100 I've had for a while) set to PXE boot ( PIII 1Ghz, 256 or 512 mb Ram).  It boots alright, and I get the graphical login screen.
Unfortunately, in the logon screen[LIST=1]
[*]If I move my mouse to the "Preference" (or is it "Options") in the lower left corner of the screen, the whole screen blanks and then returns, but it only happens if I hover over this menu link.
[*]The screen resolution is very high (like 1280x???) which the monitor can handle, but I'd rather something like 1024x768 and have set that up as the default resolution for the computer when I log into the server directly but when connecting via cleint it is always a lot higer.
[*]When I put in the username and password, it takes a long time for the system to go into the desktop where when I log into the server directly it is immediate.
[/LIST]
Now, when the desktop comes up, a couple funky things go on that I have never seen before:[LIST=1]
[*]The (Gnome) panels on the top and bottom wink in-and-out a number of times before dissappearing altogether. This is before any of the icons placed ont he panel show.
[*]When I tried setting up a brand new user account and logging in, the panels showed up until I clicked anything, then they flicker and dissappear.
[*]If I try and open anything that is on the desktop, a nautilus window likewise flickers in-and-out until it dissappears altogether, taking the icons with it
[*]If I right-click on the desktop (before the icons are lost) I get the menu but any selection winks nautilus in-and-out until it dissapears altogether and takes the icons with it.
[/LIST]
After this, all I can really do is CTRL+ALT+Backspace to get out of X and return to the login screen before hard-shutdown the machine using the power button.

I am not sure what the graphic cards are in the Dimension 4100 but in my first 4100 the video card ran fine except during video playback.  Not sure if it is related to this and how to fix it if it is the issue.

I have previously had my original Dimension log in to Edubuntu 6.06 LTS at least once.

I have tried making a new account to log in to in case it was something that was modified in the client.  This did not work.

I did recently run ```
sudo ltsp-build-client --mirror file:///cdrom
```

I am pretty new to networking so if this is a networking issue, please describe what to do in "dummy" details? :)

Thanks

---

### Post by calvarymanagua on 2007-12-15
I would like to post some things I have found out about the LTSP system.  I have been using k12ltsp on Fedora 6 for about a year now, and decided to upgrade to the Ubuntu system.  (I am actually using edubuntu).  I have had many problems with graphics and here are some solutions I have found.  (I am by no means an expert).

I found these examples in an example lts.conf file that was used for k12ltsp.  I generally use the 1024x768 with 60hz and everything seems to work fine.  I also set the X_COLOR_DEPTH = 16  I also found many times it is helpful to specifiy your card.  For example I use, XSERVER = cirrus.

Hope this helps.
Brian


# Below are sample mode lines for a variety of vertical refresh rates and
# resolutions.  They are used to define the default client screen resolution.
# Some lines may not work with a given monitor and video chipset.
# To avoid damaging a monitor and video card, only specify mode lines that
# your client's hardware can support.
# Uncomment only *one* of the following X_MODE_0 lines at a time, or add one
# of your own.

# 60 Hz Resolutions
#   X_MODE_0 = 640x480   25.175   640  656  752  800   480 490 492 525  -hsync -vsync
#   X_MODE_0 = 800x600   40       800  840  968 1056   600 601 605 628  +hsync +vsync
#   X_MODE_0 = 1024x768  65      1024 1048 1184 1344   768 771 777 806  -hsync -vsync

# 70 Hz Resolutions (Use instead of 72 Hz for 1024x768)
#   X_MODE_0 = 1024x768  75      1024 1048 1184 1328   768 771 777 806  -hsync -vsync

# 72 Hz Resolutions
#   X_MODE_0 = 640x480   31.5     640  664  704  832   480 489 492 520  -hsync -vsync 
#   X_MODE_0 = 800x600   50       800  856  976 1040   600 637 643 666  +hsync +vsync
#   X_MODE_0 = 1024x768  75      1024 1048 1192 1296   768 771 777 806  -hsync -vsync

# 75 Hz Resolutions
#   X_MODE_0 = 800x600   49.5     800  816  896 1056   600 601 604 625  +hsync +vsync

# 85 Hz Resolutions
#   X_MODE_0 = 800x600   60.75    800  864  928 1088   600 616 621 657  -hsync -vsync

---

### Post by Dragonbite on 2007-12-18
> **calvarymanagua said:**
> I would like to post some things I have found out about the LTSP system.  I have been using k12ltsp on Fedora 6 for about a year now, and decided to upgrade to the Ubuntu system.  (I am actually using edubuntu).  I have had many problems with graphics and here are some solutions I have found.  (I am by no means an expert).

I found these examples in an example lts.conf file that was used for k12ltsp.  I generally use the 1024x768 with 60hz and everything seems to work fine.  I also set the X_COLOR_DEPTH = 16  I also found many times it is helpful to specifiy your card.  For example I use, XSERVER = cirrus.

Hope this helps.
Brian


# Below are sample mode lines for a variety of vertical refresh rates and
# resolutions.  They are used to define the default client screen resolution.
# Some lines may not work with a given monitor and video chipset.
# To avoid damaging a monitor and video card, only specify mode lines that
# your client's hardware can support.
# Uncomment only *one* of the following X_MODE_0 lines at a time, or add one
# of your own.

# 60 Hz Resolutions
#   X_MODE_0 = 640x480   25.175   640  656  752  800   480 490 492 525  -hsync -vsync
#   X_MODE_0 = 800x600   40       800  840  968 1056   600 601 605 628  +hsync +vsync
#   X_MODE_0 = 1024x768  65      1024 1048 1184 1344   768 771 777 806  -hsync -vsync

# 70 Hz Resolutions (Use instead of 72 Hz for 1024x768)
#   X_MODE_0 = 1024x768  75      1024 1048 1184 1328   768 771 777 806  -hsync -vsync

# 72 Hz Resolutions
#   X_MODE_0 = 640x480   31.5     640  664  704  832   480 489 492 520  -hsync -vsync 
#   X_MODE_0 = 800x600   50       800  856  976 1040   600 637 643 666  +hsync +vsync
#   X_MODE_0 = 1024x768  75      1024 1048 1192 1296   768 771 777 806  -hsync -vsync

# 75 Hz Resolutions
#   X_MODE_0 = 800x600   49.5     800  816  896 1056   600 601 604 625  +hsync +vsync

# 85 Hz Resolutions
#   X_MODE_0 = 800x600   60.75    800  864  928 1088   600 616 621 657  -hsync -vsync

I've heard about reducing the  X_COLOR_DEPTH (I did to 24 instead of 16), but the thing that was getting me was that I cannot find the example file of lts.conf and the lts.conf found in the usual place pointed to somewhere different!

Alas, I made the lts.conf file and entered one line ( X_COLOR_DEPTH=24) and that solved it all!  I even did an ltsp-client-build and it saved the lts.conf file I created!

---

