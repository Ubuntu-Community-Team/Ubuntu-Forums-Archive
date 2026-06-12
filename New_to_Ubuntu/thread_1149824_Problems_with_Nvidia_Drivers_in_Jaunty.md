---
title: "Problems with Nvidia Drivers in Jaunty"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by amor0fati on 2009-05-05
What started out as an attempt to fix choppy video and audio in VLC has turned into a ridiculously frustrating driver problem.  First, I saw mention that downgrading the driver from 180 may fix my problems, so I tried that, rebooted, and found that I had to run in low graphics mode.  Not only that, but I also found that I couldn't actually activate either driver from there on out, and of course, lost my second screen.

I tried envyng, but it didn't have any support for my system.

So I found this:
```
Print out this guide, you will be in pure CLI for part of the install.

1)  Download the driver for your Nvidia Card from http://www.nvidia.com/Download/index.aspx?lang=en-us
    1.a) Make sure its in your home directory, this will make it so we don't have to change directories later when were in terminal.

2) Open a terminal: Applications--> Accessories--> Terminal

3) sudo apt-get install build-essential

4) gksudo gedit /etc/modules
    4.a) Add "nvidia" without quotes to the list.
    4.b) Save and Exit

5) gksudo gedit /etc/default/linux-restricted-modules-common
    5.a) Add "nv" without quotes to the restricted list. It should look exactly like this: DISABLED_MODULES="nv"
    5.b) Save and Exit

6) sudo cp /etc/X11/xorg.conf ./xorg.conf.backup

7) sudo rm /etc/X11/xorg.conf
    7.a) Were just deleting your old xorg.conf file, we backed it up in step 6 just in case we ever need it back again.
    7.b) Getting rid of old drivers, use one or more of the sections that apply to you:
        -------------------------------------------------------------------------------------------------------
        If you used Envy to attempt a previous nvidia install please run this command now before you go on:

        sudo envy --uninstall-all 
        sudo dpkg -P envy 
        sudo envyng --uninstall-all
        sudo dpkg -P envyng
        In Depth Instructions on Envy and EnvyNG install/uninstall http://albertomilone.com/pmwiki/pmwi...tionsForUbuntu




        -------------------------------------------------------------------------------------------------------
        If you have some old Ubuntu repository/restricted driver manager attempts installed please run this command before you go on:

        sudo apt-get remove --purge nvidia*
                sudo rm /lib/restricted-modules/.nvidia*

        -------------------------------------------------------------------------------------------------------
        If you have a failed NVIDIA*.run (drivers from the nvidia.com site) run this command before you go on:

        sudo nvidia-installer --uninstall

        -------------------------------------------------------------------------------------------------------
####################################################################################
##................................................................................##
## Alright Now Assuming That You are starting with a clean slate lets move forward##
##................................................................................##
####################################################################################

8) CTRL-ALT-F1
    8.a) Okay were in Command Line only now, we have a little left to do in here.
    8.b)login:
    8.c)Password:

9) sudo /etc/init.d/gdm stop
    9.a) This step shuts down the x-server and gnome desktop manager

10) sudo chmod a+x ./NVIDIA*.run
    10.a) We made the nvidia installer executable.

11) sudo ./NVIDIA*.run
    11.a) Answer to the affirmative for all questions.
    11.b) Be sure to specifically say you DO WANT it to write a new xorg.conf
    11.c) If you somehow answered incorrectly on the last question in the installer then:
        c.I) sudo nvidia-xconfig #this will write a new or attempt repair of
                     an xorg.conf file for you.

12) sudo /etc/init.d/gdm start
    12.a) You should see an Nvidia Logo, and then be put at your login screen, 
              you should also be able to enable desktop effects.

Optional But recommended:
13) To get the driver to update itself when a new kernel is installed from the update
    manager be sure to follow the guide in this link:
     http://ubuntuforums.org/showpost.php...04&postcount=1
```

and it couldn't complete the install due to some sort of kernel problem met while trying to run the driver script in command line.  Now I can't even see any of the video drivers, and I'm still stuck with having to specify low-graphics mode at every bootup.

Jaunty's been a huge pain.  I'd just gotten past my sound issues, and video was running just fine for a day or two, but now this!?  If someone has any kind of solution or workaround for this, please let me know, because everything I've found thusfar has only caused more problems.

---

### Post by blazemore on 2009-05-05
Try downloading the latest drivers from [www.nvidia.com](www.nvidia.com)
Download it to your home directory.
Then press Ctrl+Alt+F1 to switch to a console.
Log in, and issue the command
```
sudo /etc/init.d/gdm stop
```
Wait, then type sudo sh nvidi... (I don't know the actual name of the driver setup file, press Tab to complete the filename).

You can then install the drive using the installer.

---

### Post by amor0fati on 2009-05-05
Thanks for the reply, but I actually already tried:
```
sh nvidia-Linux-x86-173.08-pkg1.run
```
and got the same results.

I also tried:
```
wget http://us.download.nvidia.com/XFree86/Linux-x86-177.82-pkg1.run
chmod +x ./NVIDIA-Linux-x86-177.82-pkg1.run
sudo !$
```
This worked to a point, and then ended up with the installer's borders and a blank black screen in the middle.  I restarted and now can't seem to use any commands in the console.

Edit:
Except now the console seems to sort of work but
```
sudo /etc/init.d/gdm start
```
won't bring me back to the desktop like it used to.

---

### Post by arapa on 2009-05-05
Try changing the driver from 'nvidia' to 'nv' in  xorg.conf to see if you can get your desktop back.

```
sudo nano /etc/X11/xorg.conf
```

Can you paste the results of this command:
```

cat /etc/X11/xorg.conf;lspci | grep VGA
```

---

### Post by amor0fati on 2009-05-05
I'll post this for you and then see if "nv" worked and get back to you.

```
cat /etc/X11/xorg.conf;lspci | grep VGA
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Mon Nov  3 08:46:46 UTC 2008

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
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" 1024 0
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"

# Removed Option "Xinerama" "0"
    Option         "Xinerama" "1"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Main Monitor"
    VendorName     "Hewlett Packard"
    ModelName      "HP vs15"
    HorizSync       30.0 - 63.0
    VertRefresh     50.0 - 76.0
EndSection

Section "Monitor"
    Identifier     "Second Monitor"
    VendorName     "JVC"
    ModelName      "TV-0"
    HorizSync       28.0 - 55.0
    VertRefresh     43.0 - 72.0
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "HP vs15"
    HorizSync       30.0 - 63.0
    VertRefresh     50.0 - 76.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       28.0 - 55.0
    VertRefresh     43.0 - 72.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nv"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "0 NVIDIA Corporation, GeForce 8400 GS"
    Driver         "nv"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "1 NVIDIA Corporation, GeForce 8400 GS"
    Driver         "nv"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nv"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nv"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Main Screen"
    Device         "0 NVIDIA Corporation, GeForce 8400 GS"
    Monitor        "Main Monitor"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Second Screen"
    Device         "1 NVIDIA Corporation, GeForce 8400 GS"
    Monitor        "Second Monitor"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "TV: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "TV: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "ServerFlags"
Option "IgnoreABI" "True"
EndSection
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400 GS (rev a1)

```

Edit:
Yep, it worked alright.  Thanks!  Do you see anything else wrong with my script?

---

### Post by amor0fati on 2009-05-05
Well I found out that I had been booting in Intrepid, as Jaunty had not actually been added to the grub.  I ammended the jaunty to menu.lst:
```
title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		7bd72270-3f33-4a86-91e9-9d14fcc9258b
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7bd72270-3f33-4a86-91e9-9d14fcc9258b ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		7bd72270-3f33-4a86-91e9-9d14fcc9258b
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7bd72270-3f33-4a86-91e9-9d14fcc9258b ro  single
initrd		/boot/initrd.img-2.6.28-11-generic
```

and used envyng to install my drivers.  I used 173 instead of 180, since it looked like 180 didn't support my card.  I'm having trouble getting my second screen back, and VLC still skips.

---

### Post by amor0fati on 2009-05-05
My problem right now is that when I try to configure the xserver in nvidia settings, I get "Failed to parse existing X config file '/etc/X11/xorg.conf" whether with or without root permissions.  I also get this returned in the terminal:
```
VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
At least one Device section is required.

Segmentation fault

```

---

### Post by arapa on 2009-05-05
The option ```
Option "TwinView" "0"
``` is currently off. (0=off=false, 1=on=True)

```
Option "TwinView" "1"
``` will turn on Twinview.

---

### Post by amor0fati on 2009-05-05
I'm actually after separate x screens, but I'll give that a try.

Still wondering why the configuration tool won't work though.

Edit:
Actually, I'm a little afraid to.  This is what I used to have that worked, and I no have it set as my current script.  It doesn't have twinview set to 1, either.

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Mon Nov  3 08:46:46 UTC 2008

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
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" 1024 0
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"

# Removed Option "Xinerama" "0"
    Option         "Xinerama" "1"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Main Monitor"
    VendorName     "Hewlett Packard"
    ModelName      "HP vs15"
    HorizSync       30.0 - 63.0
    VertRefresh     50.0 - 76.0
EndSection

Section "Monitor"
    Identifier     "Second Monitor"
    VendorName     "JVC"
    ModelName      "TV-0"
    HorizSync       28.0 - 55.0
    VertRefresh     43.0 - 72.0
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "HP vs15"
    HorizSync       30.0 - 63.0
    VertRefresh     50.0 - 76.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       28.0 - 55.0
    VertRefresh     43.0 - 72.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "0 NVIDIA Corporation, GeForce 8400 GS"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "1 NVIDIA Corporation, GeForce 8400 GS"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Main Screen"
    Device         "0 NVIDIA Corporation, GeForce 8400 GS"
    Monitor        "Main Monitor"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Second Screen"
    Device         "1 NVIDIA Corporation, GeForce 8400 GS"
    Monitor        "Second Monitor"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "TV: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "TV: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

---

### Post by arapa on 2009-05-05
I don't know if this will help since I'm just running one lonely monitor but it looks like you have things duplicated in your xorg.conf.

I believe you only need the device, screen and monitor stuff listed twice (not four times). Just make sure what you have listed in screen matches the identifiers in device/monitor.

---

### Post by amor0fati on 2009-05-05
Maybe, but this is what I've known to work.  Even if this script is removed, I get the same problems of not being able to save or even preview nvidia settings, so I'm not so sure the problem is related to the script.  I suppose it's worth a shot though.

Changing it to this:
```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Mon Nov  3 08:46:46 UTC 2008

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
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Main Screen" 0 0
    Screen      1  "Second Screen" 1024 0
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"

# Removed Option "Xinerama" "0"
    Option         "Xinerama" "1"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Main Monitor"
    VendorName     "Hewlett Packard"
    ModelName      "HP vs15"
    HorizSync       30.0 - 63.0
    VertRefresh     50.0 - 76.0
EndSection

Section "Monitor"
    Identifier     "Second Monitor"
    VendorName     "JVC"
    ModelName      "TV-0"
    HorizSync       28.0 - 55.0
    VertRefresh     43.0 - 72.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "0 NVIDIA Corporation, GeForce 8400 GS"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "1 NVIDIA Corporation, GeForce 8400 GS"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Main Screen"
    Device         "0 NVIDIA Corporation, GeForce 8400 GS"
    Monitor        "Main Monitor"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Second Screen"
    Device         "1 NVIDIA Corporation, GeForce 8400 GS"
    Monitor        "Second Monitor"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "TV: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by amor0fati on 2009-05-05
Hey, thanks for that!  I guess Jaunty's a bit more picky than Intrepid, or something was going on that I wasn't aware of.  Now I can focus on fixing my VLC problem.

---

