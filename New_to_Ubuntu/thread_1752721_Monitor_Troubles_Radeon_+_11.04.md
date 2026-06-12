---
title: "Monitor Troubles Radeon + 11.04"
date: 2011-05-08
forum: New to Ubuntu
---

### Post by den160593 on 2011-05-08
Hi,

I'm having troubles with configuring my new monitor. I used to have a dual screen setup, now I'm switching to just this one, so that might be the cause of the issue, but I really don't know.

The problem can be seen in this following screen shot, but the screen is stretched out (as you can see by the file cut in half on the right edge) plus I have a black background, which isn't my normal one. I have tried adjusting the resolution, this fixes it, but it means the screen isn't proportional and is lower quality (ie: fuzzy)

[IMG]http://i12.photobucket.com/albums/a247/den160593/Screenshot-1.png[/IMG]

My graphics card is: Radeon HD 4870

Any help would be greatly appreciated.

Thanks!

---

### Post by sikander3786 on 2011-05-08
Can you please post the output of this command.

```
cat /etc/X11/xorg.conf
```

---

### Post by den160593 on 2011-05-08
Thanks for reply/

This is the message I get: > "cat: /etc/X11/xorg.conf: No such file or directory"

---

### Post by Blasphemist on 2011-05-08
This link should help you.

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

At the least it tells you how to test the driver and how to tweak the driver. You don't need an xorg.conf file.

---

### Post by den160593 on 2011-05-09
I had a look at that page, couldn't find anything that might help though :(

---

### Post by Blasphemist on 2011-05-09
Ok, so let me ask a few questions. What Toshiba monitor model do you have? It looks like this resolution doesn't quite fit the monitor and I'd like to know what all of the valid resolutions are for that monitor. Is it possible that you have desktop zoom turned on in ccsm? Or enhanced desktop zoom? Just covering all bases. 

Please post the results of 
```
xrandr
```. 
Did you run this to ensure Kernel mode setting is being used? 
```
dmesg | grep drm
``` 
Did you check the man page for Radeon to see if there are any other options?
```
man radeon
```

---

### Post by den160593 on 2011-05-12
Thanks for reply!

Result of xrandr:
> xrandr
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 8192 x 8192
DVI-0 disconnected (normal left inverted right x axis y axis)
DVI-1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 521mm x 293mm
   1920x1080      60.0*+
   1680x1050      60.0  
   1280x1024      75.0     60.0  
   1440x900       59.9  
   1280x960       60.0  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  


I ran the next command, nothing changed :( Not to sure which options to look at for the man radeon command as well :(

Not to sure exactly what model as well, what the manual says is: 

Toshiba 23.6 Full HD Wide LCD Monitor

Thanks again for the reply!

---

### Post by coffeecat on 2011-05-12
If yours is a full HD widescreen monitor, it would almost certainly have a native pixel resolution of 1920x1080 and the  screenshot in your first post shows that Monitor Preferences is correctly set up for this. It also shows a refresh rate of 60Hz which is correct for a LCD screen.

A couple of comments about that screenshot. I can't explain the half off-screen file icon, but I can say that the shutdown icon in the top-right of the screen is in the correct place, as is the launcher and Ubuntu button on the left. Which means that your horizontal placing is correct and the screen is not stretched out. Which would mean in turn that the misplaced file icon would have nothing to do with your monitor settings. Have you tried moving it on the desktop?

Your other points. The black background: have you tried changing the wallpaper? And the fuzziness. Have you tried the auto button on the monitor? If you don't have an auto button, there should be an auto option somewhere in the monitor menu.

---

### Post by den160593 on 2011-05-12
Hey, for some reason it fixed itself. Not to sure if that's a result of the commands before, me running update manager or what, but all good now. Thanks heaps for your help!!!

---

