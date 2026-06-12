---
title: "almost got it can someone get the horse in the barn"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by clay woodruff on 2009-11-21
ok i think i'm getting somwhere at last. i actually managed to get into my xorg.conf file but this is all there was in it

Section "Screen"
    Identifier    "Default Screen"
    Option    "AddARGBGLXVisuals"    "True"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection


what do i need to do to make this file work for my nvidia 5200fx card and a hp vf51 flat panel monitor, i guess what i need is the right format to enter in the file. please be specific i have no clue as to how or what to do. it took me 3 days just to figure out how to get the file open. and countless hours searching forums youtube and google. i'm running 9.10 only no windows.

---

### Post by akelsall on 2009-11-21
Clay, check and see if you have the nvidia GUI "Nvidia X Server Settings" installed already

   System | Administration | Nvidia X Server settings

If so, try using that first. If it's not installed, you can install it using the following command:

     sudo aptitude install nvidia-settings


Andy

---

### Post by clay woodruff on 2009-11-21
ok i checked and didn't see it anywhere. not that i know where to look but i went through the settings control panel and didn't see it anywhere. ssssoo i ran that command and this is what came up

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 22 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

lol couldn't tell you what this means but......... hopefully you do

---

### Post by mjwilson1313 on 2009-11-21
did you go to system > admininstration > hardware drivers

---

### Post by clay woodruff on 2009-11-21
uhh no i did what prior post said.
Clay, check and see if you have the nvidia GUI "Nvidia X Server Settings" installed already

   System | Administration | Nvidia X Server settings

If so, try using that first. If it's not installed, you can install it using the following command:

     sudo aptitude install nvidia-settings
 
and thats what i did and i got this from terminal.


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 22 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

please understand i'am not all that sharp when it comes to doing these kinds of commands. this has been an issue for about three days and i thought i had it down to just modify my xorg file but now i'm being told to go another direction........not that your advice is wrong, but i wouldn't know what GUI was anyways. trust me i appreciate your efforts. i'm just going in circles it seems.

---

### Post by clay woodruff on 2009-11-21
but to answer your question i just did and it searched and came up with a version 173 which is activated as well as the recommended install and a version 96 not activated
 my problem has been the resolution wont go higher than 640x480 and both my card and monitor support 1024x768

---

### Post by mjwilson1313 on 2009-11-21
okay well i was just trying... i had the same issue for about a week and when i went into the hardware drives it asked me to install some thirdparty app that fixed everything with my graphics card... sorry

---

### Post by stderr on 2009-11-22
Hi Clay. 

Can we assume that System->Preferences->Display doesn't show resolutions larger than 640x480?

nvidia-settings is quite a nice GUI (graphical user interface - i.e. not command-line) tool for configuring the proprietary NVIDIA driver's settings. I think it only edits xorg.conf, but it may do more. You appear to be running the proprietary driver from the output in your xorg.conf

> Driver "nvidia"

I believe "nv" is the largely inferior open source driver, and "nvidia" the proprietary binary. In other words, the easiest way to configure it should be through nvidia-settings. What happens when you try running this from a terminal - it looks like it may already be installed:

```
gksudo nvidia-settings
```

edit:To clarify, you should be able to solve your resolution issue by editing xorg.conf alone, but nvidia-settings would take care of this for you if you can get it running. As another fix, uninstalling your current ubuntu nvidia driver and installing the latest nvidia driver from their site would also give you the new nvidia-settings, but ask for more help if you want to try to do that. 

If you want to try editing your xorg.conf (don't forget to save a backup copy in case you can't boot into the GUI again, and don't forget you need to edit it as root: "gksudo gedit /etc/X11/xorg.conf"), you could try adding a metamodes line in the Screen section, maybe something like:
```

    Option         "metamodes" "1024x768 +0+0"
```

---

### Post by clay woodruff on 2009-11-22
no please i apologise i wasn't trying to be rude thanks for trying. i really have no clue about this type of OS i just installed it 4 days ago and can't seem to get this problem solved. i started 3 or 4 other threads with little help. one was a complete disaster because i sort of blew a fuse and used language i later found out wasn't very appropriate. was accused of trolling which i have no clue as to what that is.........uinless i have a fishing pole in my hand. got a dimarite from the admin. ending in a closed thread.

---

### Post by louieb on 2009-11-22
Have the fx5200 in my desktop. Its probably not the driver thats the problem. It that the display is not reporting itself correctly.  
Do you have its manual? Can probably come up with an xorg.conf file
 
of intrest to you are the lines highighted in red 
Driver could be nvidia (restricted driver) or nv (open source driver)
sync and refresh - need your display document.
and metamodes gives  resolution options.
 ```

Section "Device"
    Identifier     "Videocard0"
   [COLOR=Red] Driver    [/COLOR]     [COLOR=Red]"nvidia"[/COLOR]
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
EndSection

Section "Monitor"
    # HorizSync source: xconfig, VertRefresh source: xconfig
    Identifier     "Monitor0"
    VendorName     "Acer"
    ModelName      "CRT-0"
    [COLOR=Red]HorizSync       28.0 - 64.0
    VertRefresh     43.0 - 60.0[/COLOR]
    Option         "DPMS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
   [COLOR=Red] Option         "metamodes"  "1024x768 +0+0; 800x600 +0+0; 640x480 +0+0"[/COLOR]
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "DRI"
    Mode    0666
EndSection

```

---

### Post by clay woodruff on 2009-11-22
to stderr when i go to that i get a message that says " it appears that your graphics driver does not support the necessary extensions to use this tool. do you want to use your graphics driver vendors tool instead.

---

### Post by clay woodruff on 2009-11-22
@ louib. give me a few minutes and i will try and get info from nvidia web site also my monitor settings

---

### Post by stderr on 2009-11-22
Interesting... 

I'd be tempted to recommend installing the latest nvidia driver from their website, but I'd rather some others pool in with their ideas first (moving from repositories with automatic updates to a one-off installation with no updates is not the best move). Anyway, I'll post the rough procedure:

o Go to the drivers section of nvidia.com, search through for a Linux driver for your 5200, download it. 
o Find the file and "chmod +x thefile" to enable you to execute it
o Logout
o Switch to another tty (Ctrl+Alt+F2 or the like, login)
o Uninstall your current nvidia driver (something like "sudo apt-get remove nvidia-glx-*")
o Install the new driver (find correct directory, and "sudo ./thefile")
o Reboot and !hopefully! login to the GUI
o "gksudo nvidia-settings"

---

### Post by clay woodruff on 2009-11-22
ok i will give that a try. although i think i did this once before but if i remeber right it wouldn't install.........probably because the other was in use...... right? how will i know if it is the same driver or different?  the version numbers?

---

### Post by clay woodruff on 2009-11-22
ok let me make sure i got this right. first off the driver from nvidia web site was x86-173.14.22-pkg1.run.  the one i have installed is x86-173.14.20 etc. ok so i open the terminal and enter chmod + X x86-173.14.22-pkg1.run then hit enter then log out...... open terminal again enter sudo apt-get remove nvidia-glx-*" hit enter then install new driver? is that right?

ohh i forgot to tell you i couldnt find the spechs for the card but i do have them for the monitor they are

display type              15" xga tft LCD active matrix
viewable area             15" diagonal
input connector types
analog                    n/a
digital                   n/a
panel format              n/a
max. dot rate             80 mhz
oixel pitch               n/a
                          800 x 600 @ 56, 60, 70, 72, 75 hz
supported resolutions
                          1024 x 768 @ 60, 70, 72, 75 hz
audio
speakers                  no
microphone                no
frequencies
line (vertical)           56-75 hz
raster (horizontal)       31-63 khz
power source              100-240 vac, 50-60 hz
maximum power consumption 30 w
operating conditions
temperature               5 to 40 c
relative humidity         20% - 85%
mpr-II compliant          n/a
energy star compliant     yes
plug & play               yes
product dimensions
                          n/a
(h x w x d)
product weight            n/a

if i need to modify my xorg file how would i set that up

---

### Post by louieb on 2009-11-22
Try this
```

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "whatever"
    ModelName      "CRT-0"
    HorizSync       31.0 - 63.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes"  "1024x768 +0+0; 800x600 +0+0; 640x480 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection



```

---

### Post by clay woodruff on 2009-11-22
wow did i f something up or what. i'm useing my live session cd to use ubuntu. lastnight i copied the other xorg layout you posted and added it to my xorg file and saved it. ok here is where i think everything went arye. i didn't go back to my xserver and save it there. i just logged out and restarted. lol i'm so lame. at restart i get a message saying monitor is out of range please reset monitor to 1024x768. only problem was i couldn't because i was stuck on that black screen. so this AM i went and got my old relic monitor and hooked it up and BAM 1024x768 went to my nvidia control panel and checked and all my resolutions where there. i about crapped myself i was so happy. so i tried to save my xserver and it said it failed because of some parse issue. so my dumb self rebooted the computer and it got stuck in my desktop login mode. or i guess it was like command promp hell. so here i'am back to square one. so lou before i go and do something stupid again what do i do with the info already in the xorg file? also the driver is recommended from hardware manager is a X86-173.14.20-pkg1.run but the driver that nvidias website says i need is a X86-173.14.22-pkg1.run. so i download it but when i try and open it i get an error about it maybe trying to open a bin file and not recognizing the character region or something like that. so whats up with that

---

### Post by louieb on 2009-11-22
I know the open source (nv) driver works - you just can't do 3D or desktop effects.  Right now my desktop (dual boots Hardy and Karmic), has a fx5220 card in it,  is using the 173 nvidia driver in both releases.  (it was the one recommend by the hardware driver screen).  Did not have to go to the nvidia site. So don't know. Seems to me a 173 driver is a 173 driver no matter how you get it.

> i get a message saying monitor is out of range please reset monitor to 1024x768.still sounds like you can use the 3 sections I posted earlier you will have to tweak the  refresh range. I just took those numbers from the list you posted earlier. 

Might try lowering the VertRefresh  60 is a typical max for an LCD screen. The old CRT monitors would go much highter.  
```

    HorizSync       31.0 - 63.0
    VertRefresh     43.0 - 60.0

```

BTW my display is an Acer al1916w - I had to learn a little about xorg.conf to get it to display its 1440x900.   Once i got it working have a saved copy that I've had to use the saved xorg.conf in every version of Ubuntu. 

Know its a pain - but belive it or not things have gotten better (easier). One day...

---

### Post by clay woodruff on 2009-11-22
got it. yeah i've been learning the hard way thats for sure<laughin> but i'm not giving up. but anyway so what do i do with the info thats already in the xorg file

---

### Post by louieb on 2009-11-22
> **clay woodruff said:**
> so what do i do with the info thats already in the xorg file

Lets have a look. it would help to put it your next post.

---

### Post by clay woodruff on 2009-11-22
sorry about that,i had in an earlier post but i reinstalled linux. and i haven't upgraded to 9.10 yet. still running 9.4. i noticed there is a difference. but this is what is there now

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

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

---

### Post by clay woodruff on 2009-11-23
hey lou i just want to say thanks fore your time and patience, you've been a big help. i dont know how i did it but i did it. my res is at 1024x768 and the control panel has all my spechs correct. so i'm marking this one solved. thanks again



clay

---

