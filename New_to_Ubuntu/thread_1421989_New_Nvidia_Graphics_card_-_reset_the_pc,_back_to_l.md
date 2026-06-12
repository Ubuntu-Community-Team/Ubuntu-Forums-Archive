---
title: "New Nvidia Graphics card - reset the pc, back to low resolution mode. Annoying!"
date: 2010-03-04
forum: New to Ubuntu
---

### Post by surelock22 on 2010-03-04
I know this has something to do with my X Server file. I'm not a total wiz with hardware, but if I try to save "To X Configuration File" I get a FAIL - "Unable to remove old X config backup file '/etc/X11/xorg.conf.backup'." 

I'm not even sure if I'm trying to do the right thing, I just don't want to have to re-adjust my display settings everytime I re-boot.

Any help would be totally awesome.

Thanks-surelock22[IMG]http://i2.photobucket.com/albums/y14/surelock22/Screenshot34101.png[/IMG]

---

### Post by n0dix on 2010-03-04
Run with root:
```
 $ sudo nvidia-settings 
```

---

### Post by NightwishFan on 2010-03-04
You may need to run the nvidia settings as root.

```
sudo nvidia-settings
```

Edit: My slow internet caused me to be beaten to the punch! Curses! :D

---

### Post by Thomas Garman on 2010-03-04
I have an nvidia video card that I use for dual monitors and I had the same problem.

I used:

```
 sudo nvidia-xconfig
```

and then also

```
gksu nvidia-settings
```

which I learned about from the forums by googling the same issue you have.  Using gksu nvidia-settings opens the gui in such a way that it gives it root access, so then it can save a config file.

---

### Post by surelock22 on 2010-03-05
I must have done something stupid while tinkering with the stuff. It looks great when I reset it to the correct resolution, but it is rather annoying to have to do it every time I turn off the PC.

I wanted to show you a list of error messages I got in Terminal because apparently I'm either not saving the config. doc in the right place OR my monitor is incorrectly labled. Is it supposed to say that my monitor's name is "0" ? Wouldn't "1" be more appropriate? I do only run a single monitor, although a year ago I set it up for two.

> CODE: root@djsurelock-desktop:/home/djsurelock# sudo nvidia-settings

ERROR: Cannot open display 'djsurelock-desktop:0.0'.


ERROR: Unable to assign attribute CursorShadow specified on line 21 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute CursorShadowAlpha specified on line 22 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute CursorShadowRed specified on line 23 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute CursorShadowGreen specified on line 24 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute CursorShadowBlue specified on line 25 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute CursorShadowXOffset specified on line 26 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute CursorShadowYOffset specified on line 27 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute SyncToVBlank specified on line 28 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute LogAniso specified on line 29 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute FSAA specified on line 30 of configuration
       file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute TextureSharpen specified on line 31 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute AllowFlipping specified on line 32 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute FSAAAppControlled specified on line 33 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute LogAnisoAppControlled specified on line 34 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute OpenGLImageSettings specified on line 35 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute RedBrightness specified on line 36 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute GreenBrightness specified on line 37 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute BlueBrightness specified on line 38 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute RedContrast specified on line 39 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute GreenContrast specified on line 40 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute BlueContrast specified on line 41 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute RedGamma specified on line 42 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute GreenGamma specified on line 43 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute BlueGamma specified on line 44 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute DigitalVibrance specified on line 45 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute ImageSharpening specified on line 46 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute GPUScaling specified on line 47 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute XVideoTextureSyncToVBlank specified on line
       48 of configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoBlitterSyncToVBlank specified on line
       49 of configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoSyncToDisplay specified on line 50 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).

root@djsurelock-desktop:/home/djsurelock# gksu nvidia-settings

ERROR: Cannot open display 'djsurelock-desktop:0.0'.


ERROR: Unable to assign attribute CursorShadow specified on line 21 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute CursorShadowAlpha specified on line 22 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute CursorShadowRed specified on line 23 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute CursorShadowGreen specified on line 24 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute CursorShadowBlue specified on line 25 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute CursorShadowXOffset specified on line 26 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute CursorShadowYOffset specified on line 27 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute SyncToVBlank specified on line 28 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute LogAniso specified on line 29 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute FSAA specified on line 30 of configuration
       file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute TextureSharpen specified on line 31 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute AllowFlipping specified on line 32 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute FSAAAppControlled specified on line 33 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute LogAnisoAppControlled specified on line 34 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute OpenGLImageSettings specified on line 35 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute RedBrightness specified on line 36 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute GreenBrightness specified on line 37 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute BlueBrightness specified on line 38 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute RedContrast specified on line 39 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute GreenContrast specified on line 40 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute BlueContrast specified on line 41 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute RedGamma specified on line 42 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute GreenGamma specified on line 43 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute BlueGamma specified on line 44 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute DigitalVibrance specified on line 45 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute ImageSharpening specified on line 46 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute GPUScaling specified on line 47 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute XVideoTextureSyncToVBlank specified on line
       48 of configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoBlitterSyncToVBlank specified on line
       49 of configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoSyncToDisplay specified on line 50 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).

root@djsurelock-desktop:/home/djsurelock# gksu nvidia-settings

ERROR: Cannot open display 'djsurelock-desktop:0.0'.


ERROR: Unable to assign attribute CursorShadow specified on line 21 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute CursorShadowAlpha specified on line 22 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute CursorShadowRed specified on line 23 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute CursorShadowGreen specified on line 24 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute CursorShadowBlue specified on line 25 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute CursorShadowXOffset specified on line 26 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute CursorShadowYOffset specified on line 27 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute SyncToVBlank specified on line 28 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute LogAniso specified on line 29 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute FSAA specified on line 30 of configuration
       file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute TextureSharpen specified on line 31 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute AllowFlipping specified on line 32 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute FSAAAppControlled specified on line 33 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute LogAnisoAppControlled specified on line 34 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute OpenGLImageSettings specified on line 35 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute RedBrightness specified on line 36 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute GreenBrightness specified on line 37 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute BlueBrightness specified on line 38 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute RedContrast specified on line 39 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute GreenContrast specified on line 40 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute BlueContrast specified on line 41 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute RedGamma specified on line 42 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute GreenGamma specified on line 43 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute BlueGamma specified on line 44 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute DigitalVibrance specified on line 45 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute ImageSharpening specified on line 46 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute GPUScaling specified on line 47 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute XVideoTextureSyncToVBlank specified on line
       48 of configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoBlitterSyncToVBlank specified on line
       49 of configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoSyncToDisplay specified on line 50 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to open file '/root' for writing.

root@djsurelock-desktop:/home/djsurelock# 


Thanks again for the generous help.
-SureLock22

---

### Post by surelock22 on 2010-03-05
Oh, in case you couldn't tell from my earlier reply, no, it isn't loading up the X-Config file correctly when I reboot. I guess I should have said that, but you may have gotten the drift anyhow.

:popcorn:

---

### Post by n0dix on 2010-03-05
Do this:
```
 $ sudo mv /root/.nvidia-settings-rc /root/.nvidia-settings-rc.backup 
```
and try again.

---

### Post by pj_kare on 2010-03-06
I'm just a newb and probably shouldn't be suggesting anything, but you might try my fix from here [http://ubuntuforums.org/showthread.php?t=1421157&page=2](http://ubuntuforums.org/showthread.php?t=1421157&page=2) 
 
Though you may want to take Paddy's advice further down the page and replace sudo with gksu.
 
There may be easier and better ways of doing what I suggest, (like maybe copy the text in X config preview and save it in a text file on your desktop) but basically it requires you to make a copy of xorg.conf (after setting required resolution) and save it as xorg.conf.backup in your /etc/X11 folder. 
( The file may also be required to have the same pemissions/attributes etc, I don't know. )
 
This is all I did to fix the same problem on both mine and my gf's machines.
 
Just hope no-one yells at me for trying to help....:-#

---

### Post by surelock22 on 2010-03-06
I'm still not getting the desired resolution at boot, and I'm doing what you folks have done (which is good anyway because now I know how to change the settings in root), but the problem may lie on this little "problem": for whatever reason, my PC thinks that it's in Dual Display mode, and I think I need to turn that off. Even in root, in the Nvidia settings, the submenu doesn't allow me to disable dual display mode. What do you think? How could I correct this?

[IMG][IMG]http://i2.photobucket.com/albums/y14/surelock22/SS36101.png[/IMG][/IMG]

[IMG]http://i2.photobucket.com/albums/y14/surelock22/SS36102.png[/IMG]

Thanks!

---

### Post by NightwishFan on 2010-03-06
I am quite sure mine always says that as well. (Separate x screen)

Did you try nvidia-xconfig as root?

---

### Post by skymera on 2010-03-06
Reinstall the driver?

System > Administration > Hardware drivers

---

### Post by surelock22 on 2010-03-07
> **pj_kare said:**
> I'm just a newb .... blah blah blah, *GOOD ADVICE*, blah blah blah.... 

It's noob noobie .....


Thanks for the good advice, gonna try it now.

---

### Post by pj_kare on 2010-03-07
> Originally Posted by **pj_kare**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=8924056#post8924056")                 
                 *I'm just a newb .... blah blah blah, *GOOD ADVICE*, blah blah blah....*
> **surelock22 said:**
> It's noob noobie .....

Nice...

---

