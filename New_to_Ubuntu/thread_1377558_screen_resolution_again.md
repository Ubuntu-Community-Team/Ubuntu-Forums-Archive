---
title: "screen resolution again"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by mystmaiden on 2010-01-10
I scored a larger monitor at a second hand sale yesterday and I'd really love to use it but, plugging it in messed up my screen resolution again (800 x 600 now, ugh!) so I can not even see a whole web page. I need to set it to 1024 x 768 . I tried going through display on the panel but it does not recognize this monitor which is older.  Is there any way besides xorg to fix it? and if not - can someone point me to a very clear cut guide to fixing this, most of what I've seen to date assumes I know things that I do not. 

Thanks - off to backup my machine

mystmaiden



Off to back up my computer

---

### Post by mystmaiden on 2010-01-10
sorry forgot to add - its a dell crt monitor. Not sure if the dell brand is an issue or not. I am just using the on board graphics which I think is SIS (sony vaio desktop)


```
@hal:~$ lspci |grep -i vga
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
```I looked up the monitor specs and found - 19inch

Plug & Play.
( 17.9" Viewable ).
Non-Interlaced.
PC & MAC Compatiable.
Ultra Fine 0.26 mm Dot Pitch.
Sony True Trinitron Flat Screen.
1600 X 1200 Maximum Resolution.
AC 110/220 VDC Power Supply.
Complete On Screen Digital Menu Controls.
Monitor Power Cord And Video Cable Included.
Monitor Dimensions: 18.48" (H) x 17.49" (W) X 17.93" (D).

I'm sure I don't want to set it to max resolution of 1600x1200 though, cause I wouldn't be able to actually See that! I found an article online at [http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)  
but when I got to the --addmode  I got 'command not found'

This is turning into a 'build as you go' post.. but I was able to temporarily change the screen resolution using the above link. I had to unplug my monitor and restart to get the extra resolutions to show on the drop down list (probably because of my kvm) but on restart, it didn't stick. I went back to the page and followed the instructions to make it permanent but it also had no lasting results, but there is a difference in the code I see and what he lists.
He says to add the lines after:

```
PATH=/usr/bin:$PATH
OLD_IFS=$IFS
PATH=/usr/bin:$PATH


```but I found: 

```
PATH=/usr/bin/X11:/usr/X11R6/bin:/opt/X11R6/bin:$PATH
OLD_IFS=$IFS
```I did add the lines specified but it seems to have had no effect, ie doesn't show on the drop down list of resolutions after restart. In a perfect world I'd like to have 1024x768 be the default and also have the max res (1600x1200) on the drop down as an option if I need it.

Last edit - I promise! - I have discovered through much fiddling around that the extra screen resolutions are available but simply do not show on the drop down display gui when I am plugged into the kvm. If I need to restart, it goes back to a bigger resolution. All I -seem- to need at this point is the correct terminal command to tell it to switch to the other resolution. If someone knows that I might just be in business...

---

### Post by mystmaiden on 2010-01-12
Giving this a little bump, in hopes that someone has read through this and seen in the end what the basic problem was - ie, the kvm causes the drop down list on the display gui to disappear. The work around I've found so far (in case anyone else has this trouble) is to first plug the monitor cord directly into the computer, select the correct resolution from the drop down list and Then plug into your kvm). What I would like to test now is a terminal command to change the resolution, instead of going through all the plugging and unplugging. If someone could tell me what that would be, I'd be estactic!

thanks to anyone who's read through all this folderol!

myst

---

### Post by mogwhy901 on 2010-11-12
i am having screen res issues running ubuntu 10.10 on an old mac g4 again only getting 800 x 600 and using what you listed i managed to change the res but worked one time only so the fix is either something to make the xandr work permanently every time it boots up or something different? if i had the right res i would quit using osx on it

---

