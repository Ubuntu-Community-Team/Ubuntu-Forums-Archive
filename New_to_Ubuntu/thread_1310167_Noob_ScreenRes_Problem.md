---
title: "Noob ScreenRes Problem"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by saintadamm on 2009-11-01
I just installed Ubuntu 9.10 on an old laptop--A Toshiba Tecra to be exact.

I'm new to Ubuntu, and Linux in general.  I know this problem has come up a lot, and it's been 'solved' but I still don't understand how to do it, and I was hoping someone could walk me through it a bit.

There's a black margin around my screen.  My monitor isn't recognized, and my screen resolution is only 800x600, when it should be 1024x768.  I have no clue how to fix this, despite looking through the forums.

I'm sure this could easily be fixed, but I need it to be spoonfed to me, anyone's help would be greatly appreciated.

---

### Post by lyni on 2009-11-01
for your screen resolution did you try System>Preferences>Screen Resolution?

---

### Post by travmanx on 2009-11-01
If for some reason the answer stated above does not work, try this in the terminal:

xrandr --size 1024x768

I don't remember what I had to do in Ubuntu 8.10 when I got it to work, I do remember fiddling with a certain file to force wide screen.

Edit: The menu item above is listed System>Preferences>Display in Ubuntu 9.10. There's no screen resolution tool in Koala, its all built in one (including a monitor detection tool)

---

### Post by saintadamm on 2009-11-01
I need to change my resolution settings to 1024x768.  There's all this talk in the forums about xorg this and xrandr that.  None of it seems to be working for me... such as the dpkg-reconfigure BS and such.  Do I need to download drivers?

It's an older laptop--A Toshiba Tecra M1

I just need help.  This black border around this tiny little display is DRIVING ME TO THE BRINK OF INSANITY!!

Could someone please help me out, or at least give me some guidance?

---

### Post by sandyd on 2009-11-01
> **saintadamm said:**
> I need to change my resolution settings to 1024x768.  There's all this talk in the forums about xorg this and xrandr that.  None of it seems to be working for me... such as the dpkg-reconfigure BS and such.  Do I need to download drivers?

It's an older laptop--A Toshiba Tecra M1

I just need help.  This black border around this tiny little display is DRIVING ME TO THE BRINK OF INSANITY!!

Could someone please help me out, or at least give me some guidance?
from
[http://ubuntuforums.org/showthread.php?t=70069](http://ubuntuforums.org/showthread.php?t=70069)
add

```
Section "Device"
    Driver      "trident"
EndSection
```

to /etc/X11/xorg.conf
by
running
```

gksudo gedit /etc/X11/xorg.conf

```

---

### Post by hansdown on 2009-11-01
Welcome to the forum saintadamm.

Can you click system> administration> hardware drivers?

It should give you an idea if you have the drivers or not.

---

### Post by sandyd on 2009-11-01
> **hansdown said:**
> Welcome to the forum saintadamm.

Can you click system> administration> hardware drivers?

It should give you an idea if you have the drivers or not.
their already on the computer, he only neeeds to activate them.

---

### Post by overdrank on 2009-11-01
Hi and welcome, please do not create multiple threads on the same issue. Threads merged :)

---

### Post by saintadamm on 2009-11-01
Ok I check System>Admin>Hardware Drivers and it said that no proprietary drivers were in use on this system.

I followed the command you gave me, and edited the xorg.conf file to:

Section "Device"
    Identifier    "Configured Video Device"
    Option        "UseFBDev"        "true"
        Driver          "trident"
EndSection

is this right? I just added the 'Driver "trident"' part to the end of the section.

---

### Post by Buuntu on 2009-11-01
Yes, they were trying to get you to reconfigure your xorg file, which manages your resolution.
First try typing this in to the Terminal (Applications > Accessories > Terminal).  It may not give you any output, and that is ok.
```
sudo dpkg-reconfigure xserver-xorg
```
I think you'll have to choose a few options then on how you want to configure it.

Then go to System > Administration > Hardware Drivers and install the drivers it recommends on the window that opens up.  After installing those you'll need to restart for those to take effect.  Hopefully this will fix your resolution issue.

---

### Post by saintadamm on 2009-11-01
I tried that.  It paused, then did nothing.  Any other suggestions?

---

### Post by Buuntu on 2009-11-01
Oh sorry, it wasn't supposed to display anything - that means it worked then.  

Now check for proprietary drivers and install the one it recommends in System > Administration > Hardware Drivers.  

Restart after it's done and see if that works.

---

### Post by saintadamm on 2009-11-02
There's no available drivers for download when I look at System>Admin>Hardware Drivers.

---

### Post by hansdown on 2009-11-02
Hi saintadamm.

Let's assume you do have the driver. 

Click system> administration> display.

You should be able to change the resolution there.

---

### Post by saintadamm on 2009-11-02
800x600 is the biggest resolution I can choose in System>Preferences>Display, it also says my monitor is "unknown"

---

### Post by Buuntu on 2009-11-02
Ok, you might have to do a:
```
sudo apt-get update
sudo apt-get upgrade
```
Maybe after typing that and restarting then your driver will appear in System > Administration > Hardware Drivers

---

### Post by saintadamm on 2009-11-03
Okay, I tried both of those........and still nothing.  Any other suggestions?

---

### Post by saintadamm on 2009-11-03
Okay, I tried both of those........and still nothing.  Any other suggestions?

---

### Post by sandyd on 2009-11-04
> **saintadamm said:**
> Ok I check System>Admin>Hardware Drivers and it said that no proprietary drivers were in use on this system.

I followed the command you gave me, and edited the xorg.conf file to:

Section "Device"
    Identifier    "Configured Video Device"
    Option        "UseFBDev"        "true"
        Driver          "trident"
EndSection

is this right? I just added the 'Driver "trident"' part to the end of the section.
yup. that **should** be right.

---

