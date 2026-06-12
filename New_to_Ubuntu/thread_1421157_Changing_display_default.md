---
title: "Changing display default"
date: 2010-03-03
forum: New to Ubuntu
---

### Post by myolbug on 2010-03-03
My wife bought us a really nice 24 wide screen monitor, but the computer likes to default to 1280X960 from the 1920X1080 that I have it set to.  So, whenever the computer reboots or even when I change the background, it reverts to the 1280 resolution.  How do I change this so it stays?  

I don't have a choice in system> preferences> display and while it asks me to save to X configuration file, it gives me and error that says; *Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.*  If this is the default I am looking for, what do I do to correct this?

---

### Post by diesch on 2010-03-03
Have a look at [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by myolbug on 2010-03-04
I am still reading this, but I haven't seen where it covers changing the default from 1280X960 to 1920X1080 at start up.  All I have read in this article is about what I can already do with the Sys> Pref> Display.

I need something persistent.  I do see where there is parts for a persistant change, but this is written with certain assumptions and is missing some basic steps.  Anyone have a dummy's guide?  Can't this be done in the boot process?

---

### Post by Sir Jasper on 2010-03-04
Hi,

If you go to Settings>Display, how many items down (from the top) is 1920 x 1080 and what is the refresh rate you need?

I will come back in about two hours with a simple solution to try if you can answer those two questions.

My regards

---

### Post by myolbug on 2010-03-04
1920X1080 is the second one from the top of the list.  The refresh rate is set to auto or I am given the choice of 60hz.  I like simple.

---

### Post by gdea73 on 2010-03-04
Interesting... what graphics drivers are you using, that may affect it?

---

### Post by Turkey Baster on 2010-03-04
I found that this worked for me after I made the dastardly mistake of plugging into a TV and switching back to my monitor, inexplicably losing my settings forever and stuck on 800x600 at best, just like you.

[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)

Remember to use your specs, obviously, and not the ones in the guide, though that is made abundantly clear regardless.

---

### Post by Sir Jasper on 2010-03-04
Hi,

Go to Settings>Session and Startup>Application Autostart, then
click on + Add, then in the window that appears type in the:
Top line             Resolution
Second line       (1920x1080 60)
Command line   xrandr -s 1 -r 60   [or copy and paste]

then close 
then reboot

My regards

The command line includes 1 [not 2] because the top line count starts at 0 
[not 1]. The first two lines are merely descriptive so you can use whatevever suits you.

---

### Post by myolbug on 2010-03-05
> **Sir Jasper said:**
> Hi,

Go to Settings>Session and Startup>Application Autostart, then
click on + Add, then in the window that appears type in the:
Top line             Resolution
Second line       (1920x1080 60)
Command line   xrandr -s 1 -r 60   [or copy and paste]

then close 
then reboot

My regards

The command line includes 1 [not 2] because the top line count starts at 0 
[not 1]. The first two lines are merely descriptive so you can use whatevever suits you.

Where do I find *Settings>Session and Startup>Application Autostart*

---

### Post by myolbug on 2010-03-05
Never mind, anyone have any more ideas?  Nothing above seems to make a difference.

---

### Post by myolbug on 2010-03-05
FWIW, I am running a GEForce 6100 NVIDIA GPU.  Works great, no issues with it.  I just can't seem to change the default from 1280x7something to 1920X1080.

Anyone?

---

### Post by pj_kare on 2010-03-05
> 
Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.

 
I also had this problem with my Nvidia 6200,512mb card, I managed to solved this by doing this.....
 
Set resolution, then click "Save to X Configuration File" (you get the quoted error above) click the "Preview" button (I am assuming you get a preview button like I do in my Nvidia Control panel), then COPY (highlight, right click and select copy) the entire text in the preview.
 
Open a terminal window and type the following:
 
```
sudo gedit /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
 
2 (Two) pages/files should open in gedit, xorg.conf and xorg.conf.backup, (xorg.conf.backup does not exist yet which is why changes can't be saved, and you get the error)
 
In xorg.conf "select all" and paste the text copied previously in the "Preview".
 
In xorg.conf.backup (which should be blank) simply paste the copied text.
 
Save both and exit, reboot/shutdown-do-whatever to test. Cheers.
 
P.S. I am a newbie to Ubuntu/Linux (check my bean count) I can only help you with my fix. No guarantee this will work for you. Also, the text you paste into xorg.conf may already be the same as what is in there now....I forgot to look when I did it.

---

### Post by myolbug on 2010-03-05
> **pj_kare said:**
> I also had this problem with my Nvidia 6200,512mb card, I managed to solved this by doing this.....
 
Set resolution, then click "Save to X Configuration File" (you get the quoted error above) click the "Preview" button (I am assuming you get a preview button like I do in my Nvidia Control panel), then COPY (highlight, right click and select copy) the entire text in the preview.
 
Open a terminal window and type the following:
 
```
sudo gedit /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
 
2 (Two) pages/files should open in gedit, xorg.conf and xorg.conf.backup, (xorg.conf.backup does not exist yet which is why changes can't be saved, and you get the error)
 
In xorg.conf "select all" and paste the text copied previously in the "Preview".
 
In xorg.conf.backup (which should be blank) simply paste the copied text.
 
Save both and exit, reboot/shutdown-do-whatever to test. Cheers.
 
P.S. I am a newbie to Ubuntu/Linux (check my bean count) I can only help you with my fix. No guarantee this will work for you. Also, the text you paste into xorg.conf may already be the same as what is in there now....I forgot to look when I did it.

Thanks, but this didn't work either.  I am stumped.  Where did you save yours to?  I had to select a location, but maybe I put it in the wrong spot .  I saved it inside Xorg, but as it is now 2:09am here, I am getting a sleepy and I don't recall where.  I may have saved it in the incorrect location.

---

### Post by pj_kare on 2010-03-05
They should both save directly to the correct location.....
 
I'd suggest you copy the code and paste that into terminal, but then you have to re-copy the text from the x preview.
 
```
sudo gedit /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
 
Good luck.

---

### Post by pj_kare on 2010-03-05
It all has to be in the same "Case" (upper or lower) X11 has to be a capital X etc.

---

### Post by Paddy Landau on 2010-03-05
> **pj_kare said:**
> ```
sudo gedit /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
When you use GUI programs, such as gedit, do not use [FONT=Courier New]sudo[/FONT]. Instead, use [FONT=Courier New]gksu[/FONT].
```
**gksu** gedit /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```The reasons are not easy to explain, but sometimes it can cause problems not to do this.

Also, for a GUI, you can press Alt-F2 to enter the command (including the [FONT=Courier New]gksu[/FONT]). It saves you from having to open a terminal.

(Note: You can always use [FONT=Courier New]gksu[/FONT] instead of [FONT=Courier New]sudo[/FONT], but you can't always use [FONT=Courier New]sudo[/FONT] instead of [FONT=Courier New]gksu[/FONT].)

---

### Post by Sir Jasper on 2010-03-05
Hi,

> **myolbug said:**
> Where do I find *Settings>Session and Startup>Application Autostart*

I am using Xubuntu 9.10. If you tell us (perhaps again) which OS and version you are using then I expect someone will be able to translate the above path.

My regards

---

### Post by pj_kare on 2010-03-05
> **Paddy Landau said:**
> When you use GUI programs, such as gedit, do not use [FONT=Courier New]sudo[/FONT]. Instead, use [FONT=Courier New]gksu[/FONT].
```
**gksu** gedit /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```The reasons are not easy to explain, but sometimes it can cause problems not to do this.
 
Also, for a GUI, you can press Alt-F2 to enter the command (including the [FONT=Courier New]gksu[/FONT]). It saves you from having to open a terminal.
 
(Note: You can always use [FONT=Courier New]gksu[/FONT] instead of [FONT=Courier New]sudo[/FONT], but you can't always use [FONT=Courier New]sudo[/FONT] instead of [FONT=Courier New]gksu[/FONT].)
 
 
Thanks Paddy, I am aware of the gksu thing, but I'm still learning. ;)
Only suggested sudo as it worked OK for me in both Jaunty and Karmic without any ill effect.

---

### Post by Paddy Landau on 2010-03-05
> **pj_kare said:**
> Only suggested sudo it as it worked OK for me in both Jaunty and Karmic without any ill effect.
Well, from a terminal, one normally would put an ampersand at the back, thus:
```
gksu gedit /etc/X11/xorg.conf &
```This lets the command run "in the background", i.e. without tying up the terminal.

To see how sudo could cause a problem, compare the following two versions. The first is the correct way, and the second will leave you scratching your head in puzzlement. Type them exactly as I show.
```
sudo -k
gksu gedit &
```
Close gedit, and then...
```
sudo -k
sudo gedit &
```This example is only a minor and temporary problem; but it can cause more serious problems, such as causing certain files in your home directory to be owned by root. To recover from the second version, either close the terminal window or enter [FONT=Courier New]fg[/FONT].

(By the way, I said that you can always use [FONT=Courier New]gksu[/FONT] instead of [FONT=Courier New]sudo[/FONT]; that's only true if you don't use the options. With [FONT=Courier New]sudo -k[/FONT], you can't substitute it.)

---

### Post by myolbug on 2010-03-09
> **pj_kare said:**
> I also had this problem with my Nvidia 6200,512mb card, I managed to solved this by doing this.....
 
Set resolution, then click "Save to X Configuration File" (you get the quoted error above) click the "Preview" button (I am assuming you get a preview button like I do in my Nvidia Control panel), then COPY (highlight, right click and select copy) the entire text in the preview.
 
Open a terminal window and type the following:
 
```
sudo gedit /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
 
2 (Two) pages/files should open in gedit, xorg.conf and xorg.conf.backup, (xorg.conf.backup does not exist yet which is why changes can't be saved, and you get the error)
 
**In xorg.conf "select all" and paste the text copied previously in the "Preview".**
 
In xorg.conf.backup (which should be blank) simply paste the copied text.
 
Save both and exit, reboot/shutdown-do-whatever to test. Cheers.
 
P.S. I am a newbie to Ubuntu/Linux (check my bean count) I can only help you with my fix. No guarantee this will work for you. Also, the text you paste into xorg.conf may already be the same as what is in there now....I forgot to look when I did it.

I just re-read this and realized that I have missed the part in bold.
However, when I went to save it in the beginning, I believe I saved it to the wrong location.  Now I get an error when I go to save xorg.conf:  *Could not find the file /etc/X11/xorg.conf* and the next line reads *Please check that you typed the location correctly and try again.*

Can someone give me the correct path to track down the correct location, starting from Home or System?  I cannot remember how to get to the correct spot to save this to.

I can do a save as, but I don't know the path.

---

### Post by myolbug on 2010-03-09
I just noticed something that may or may not be part of the problem.  When I went to reboot, I noticed a message that said to the effect of usplash attempted to set to 1574Xxxx resetting to 1280X720, ect ect.  Does this have anything to do with the fact that my resolution keeps defaulting to 1280X720?

Also, when I go to System> Preferences> Display, as soon as I click display I get this message:
[I]It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?
[yes] [no][/I]

As far as I know my driver is up to date and for some weird reason on this install, I have always gotten this message even with my old CRT hooked up with a much lower resolution.

How do I reset my usplash to see if this would work?

---

### Post by patchwork on 2010-03-09
View your /var/log/Xorg.0.log .  In it (somewhere near the middle, there will be an entry specifying why the current resolution (mode) was selected.   )

The answer to your problem may be as simple as specifying a preferred mode in your xorg.conf, with the mode, modeline and timings.

EDIT:  The x server automatically sets the display to the "best" mode, which may or may not be the highest resolution.  If your higher resolution mode is considered valid by the x server, adding the higher resolution to the preferred mode will bypass this selection process.

---

### Post by myolbug on 2010-03-09
> **patchwork said:**
> View your /var/log/Xorg.0.log .  In it (somewhere near the middle, there will be an entry specifying why the current resolution (mode) was selected.   )

The answer to your problem may be as simple as specifying a preferred mode in your xorg.conf, with the mode, modeline and timings.

EDIT:  The x server automatically sets the display to the "best" mode, which may or may not be the highest resolution.  If your higher resolution mode is considered valid by the x server, adding the higher resolution to the preferred mode will bypass this selection process.
I have not been able to get the newmode commands to work.

---

### Post by myolbug on 2010-03-09
> **patchwork said:**
> View your /var/log/Xorg.0.log .  In it (somewhere near the middle, there will be an entry specifying why the current resolution (mode) was selected.   )

The answer to your problem may be as simple as specifying a preferred mode in your xorg.conf, with the mode, modeline and timings.

EDIT:  The x server automatically sets the display to the "best" mode, which may or may not be the highest resolution.  If your higher resolution mode is considered valid by the x server, adding the higher resolution to the preferred mode will bypass this selection process.

I commented before I saw your addition to you post.  If you have the time, please reread this thread and see if you have any comments or commands to add.  I agree with the second part of your post, but I just don't know how to do this.

---

### Post by patchwork on 2010-03-09
Was there any indication of why your current resolution was chosen in your log? (i.e. hsync out of range for the higher resolution or something similar?)

---

### Post by patchwork on 2010-03-09
Can you post your xorg.conf?  You will need to add a line to the "Monitor" Section indicating the preferred mode, but since you will need to add a modeline to the file corresponding to the preffered mode, I'd like to see if the modeline is already there.

For kicks, the line to add will be```
Option "PreferredMode" "Mode_Name_Here"
```
but won't be effective unless you match the mode name with a validated mode name.  

If I understand correctly, you can choose the higher resolution manually?  If so, the mode name should be listed in your /var/log/Xorg.0.log in the validated mode pool, and you will not need to add a new modeline, instead just substituting the validated mode name verbatim into the "Mode_name_here"

---

### Post by myolbug on 2010-03-09
Thanks Patchwork for the advice.  
My xorg.conf:
> # xorg.conf (X.Org X Window System server configuration file)
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

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection


My xorg.conf backup:
> # nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@crested)  Sun Feb  1 20:25:37 UTC 2009

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
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Acer P244W"
    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 76.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6150SE nForce 430"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1920x1080 +0+0; nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection



My backup saved, but not the xorg.conf
Your bit about the "PreferredMode sounds spot on but where do I add it?

---

### Post by myolbug on 2010-03-09
> **patchwork said:**
> Can you post your xorg.conf?  You will need to add a line to the "Monitor" Section indicating the preferred mode, but since you will need to add a modeline to the file corresponding to the preffered mode, I'd like to see if the modeline is already there.

For kicks, the line to add will be```
Option "PreferredMode" "Mode_Name_Here"
```
but won't be effective unless you match the mode name with a validated mode name.  

If I understand correctly, you can choose the higher resolution manually?  If so, the mode name should be listed in your /var/log/Xorg.0.log in the validated mode pool, and you will not need to add a new modeline, instead just substituting the validated mode name verbatim into the "Mode_name_here"

Yes I can change the resolution manually, which is what I have been doing.  It just changes to 1280x720 as a default and then I change it to 1920x1080 to fit my monitor.

---

### Post by patchwork on 2010-03-09
First, I'd set the backup to the default config file (it looks like it has what you're looking for)
..and save the current xorg.conf to xorg.conf.backup2, just in case you need to access it again


**Check the file name for your back-up, I'm trying to go on memory**
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup2 
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```Then, I would change the monitor section as seen below:

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Acer P244W"
    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 76.0
Option "PreferredMode" "1920x1080 +0+0"
EndSection

---

### Post by myolbug on 2010-03-09
Maybe I need to file a bug report to Cononical, because none of this is making the slightest bit of difference.

---

### Post by patchwork on 2010-03-09
Can you post your /var/log/Xorg.0.log ?

---

### Post by pj_kare on 2010-03-10
> **myolbug said:**
> 
Also, when I go to System> Preferences> Display, as soon as I click display I get this message:
[I]It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?
[yes] [no][/I]

I get this message also, This happens after you install the Nvidia drivers.
It just means that you now have to use the Nvidia  panel for display settings and not the default Ubuntu display settings.

> **myolbug said:**
> 
Can someone give me the correct path to track down the correct location, starting from Home or System? I cannot remember how to get to the correct spot to save this to.
I can do a save as, but I don't know the path.

Path from top menu is:
Places -> Computer -> Filesystem -> etc -> X11

When saving from gedit it's:
Select "Browse for other folders." (From the "Save/Save As" window.)
From "Places" menu on the left select "File System".
Double click "etc" from list on right.
Navigate down list to "X11" folder.

*Wasn't sure if you still required this info, pj.*

---

