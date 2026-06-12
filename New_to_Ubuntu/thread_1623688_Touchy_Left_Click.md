---
title: "Touchy Left Click"
date: 2010-11-16
forum: New to Ubuntu
---

### Post by slowtype on 2010-11-16
Recently installed Unbuntu 10.10.  Maybe the easiest operating system install I have ever done.  

I'm having one annoying problem though.  The left mouse button on the touchpad is ultra sensitive.  When dragging folders it drops them and or opens them.  When trying to drag a window it often ends up maximizing it.  

If I press the touchpad button with a lot of force the problem isn't as bad which would lead me to believe that its a hardware issue.

BUT!  I was not having this problem while previously running windows 7 on the computer.

It seems like it is over sensitive.  Can any adjustments be made?

---

### Post by Hippytaff on 2010-11-17
Hi
 
Have a browse in the System Menu on the top panel. There are some settings in relevant meus in there, but I'm not at home to be able to check which ones and where they are :-)

---

### Post by ironic.demise on 2010-11-17
> **Hippytaff said:**
> Hi
 
Have a browse in the System Menu on the top panel. There are some settings in relevant meus in there, but I'm not at home to be able to check which ones and where they are :-)

>System >Preferences >Mouse

---

### Post by Hippytaff on 2010-11-17
> **ironic.demise said:**
> >System >Preferences >Mouse
 
Thankyou :-D

---

### Post by ironic.demise on 2010-11-17
> **Hippytaff said:**
> Thankyou :-D

Hippy, you seem to be EVERYWHERE lately...

---

### Post by Hippytaff on 2010-11-17
> **ironic.demise said:**
> Hippy, you seem to be EVERYWHERE lately...
 
Just lunchbrreaks in work and the odd post in the evening when the kids are in bed, but maybe your right, I should give it a rest for a bit and do something healthy :-)

---

### Post by ironic.demise on 2010-11-17
> **Hippytaff said:**
> Just lunchbrreaks in work and the odd post in the evening when the kids are in bed, but maybe your right, I should give it a rest for a bit and do something healthy :-)

Haha no, It's cool seeing somebody I recognize here and there and you do good work, keep it up.

---

### Post by slowtype on 2010-11-17
Thanks for responding

I checked out and tried some mouse settings without any sucess. 

I need to add some "cushion" so if my mouse button is released for a fraction of a moment it does'nt register as releasing my mouse button.  

And or there is something funky with the driver and it causes the mouse button to release while using the touchpad at the same time.

---

### Post by ironic.demise on 2010-11-17
Have you set the double click and drag_and_drop_threshhold timeout to as long as possible?

---

### Post by slowtype on 2010-11-18
I have set both of those to as long as possible and it is more bearable.

---

### Post by ironic.demise on 2010-11-18
It may be a driver or a hardware malfunction.

A few things you might try if you want to
```

Try a livecd of Ubuntu, see if it's a hardware problem
Try a livecd of another distro, see if it's Ubuntu specific
Try a Windows partition
Looks for other drivers for your trackpad
Turn your trackpad off, use a mouse

```

---

### Post by slowtype on 2010-11-18
> **ironic.demise said:**
> It may be a driver or a hardware malfunction.

A few things you might try if you want to
```

Try a livecd of Ubuntu, see if it's a hardware problem
Try a livecd of another distro, see if it's Ubuntu specific
Try a Windows partition
Looks for other drivers for your trackpad
Turn your trackpad off, use a mouse

```

OK, just booted off a live cd with KUNBUNTU 8.10 and it works fine.  

Now what?

---

### Post by slowtype on 2010-11-20
There are a few other complaints about this posted around the web but they lack any solutions.  

I'm thinking that an older or other touchpad driver might do the trick.

Where do I find optional drivers?

---

### Post by slowtype on 2010-11-21
UPDATE:

Alright, just installed KDE desktop and I am not having a problem.

---

### Post by slowtype on 2010-11-26
Can't stand the KDE for some reason, too much clicking to get through the menus and I keep clicking the wrong things, maybe related to the touchpad issue. 

I found some info on another board about what file I should edit and what to edit but I cant open it.  

I have the following line to input in the terminal so I can open this file.  But it says gnomesu command not found.  I have invested far to many hours into this today.  What is wrong with gnomesu?

```
gnomesu gedit /etc/X11/xorg.conf.d/20-synaptics.conf
```

---

### Post by slowtype on 2010-11-28
I can open the file as only a read only.  

How do I open it so I can edit it? 


Please help, going slightly mad trying to figure out this relatively simple thing and windows resizing whenever I try to move them

---

### Post by slowtype on 2010-11-28
Finally, solved the problem

I came across a solution on an opensuse forum.  This worked on my dell xps m1210 with no guaranties on anything else. The files I had to edit were in a different location and had slightly different names than the users on that web page as well.  Also I have little idea what I am doing which can be seen in my previous posts on this page.

```
gksudo gedit /usr/share/X11/xorg.conf.d/50-synaptics.conf
```

The file should look like this with the exception of the yellow highlighted text which is what I added to fix the problem.

```
Section "InputClass"
        Identifier "touchpad catchall"
        Driver "synaptics"
        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/event*"
	[COLOR="Yellow"]Option "ClickFinger3" "1"[/COLOR]
EndSection



```

---

