---
title: "Mouse no longer works in ubuntu 10.04"
date: 2010-09-06
forum: New to Ubuntu
---

### Post by Martega on 2010-09-06
Hi

I've been using Ubuntuhe 10.04 since June and up until today its been working fine with only a few minor bugs.  Today I booted up my computer and logged in and I was surprised to see that my mouse didn't work.  I can't move my mouse around at all and as a result I can't open any programs including the terminal.

When I start up my computer and I get to the ubuntu login page where I put in my password and what not everything is fine.  I can move the mouse around and everything is normal.  As soon as I input my password and log in the mouse stops working completely.  

How can I fix this?!?!?!?!  Please help!

My computer is an HP Pavilion dv6000.  I am currently on Windows 7 on the same computer where the touchpad does work.

---

### Post by Windows Nerd on 2010-09-06
So you are using a touchpad? Or an actual mouse?

Did you remember disabling the mouse/touchpad at any point?

I am not sure how to re-enable the mouse without the mouse itself. If you know how to via CLI, you can open a terminal by pressing alt+F2, and typing "gnome-terminal".

Scott

---

### Post by X1R1 on 2010-09-06
What type of mouse? USB, Ps/2 or touchpad? If you cant use the touchpad at all go ahead and open up an tty terminal (no mouse required, just hit ctrl+alt+f2 on your keyboard, then log in and try installing the drivers for the touchpad.

Hence you only have trouble after you log in it might be that you dont have the required package installed. so try:

> sudo apt-get install xserver-xorg-input-synaptics

hope it helps

---

### Post by Windows Nerd on 2010-09-06
> **X1R1 said:**
> What type of mouse? USB, Ps/2 or touchpad? If you cant use the touchpad at all go ahead and open up an tty terminal (no mouse required, just hit ctrl+alt+f2 on your keyboard, then log in and try installing the drivers for the touchpad.

Hence you only have trouble after you log in it might be that you dont have the required package installed. so try:



hope it helps

Well, if he says that it worked until now, I think he has the required driver. No harm in re-installing though. Just a thought.

---

### Post by Martega on 2010-09-06
I'm using a touchpad.  I do remember turning off the touchpad last night (there's a button on the touchpad that does this) however I don't think that this is the problem.  When the touchpad is off there's an orange LED that turns on.  Also I remember turning the touchpad back on before I shut down my computer.

I'll try booting into Linux and re-installing the touchpad drivers.

---

### Post by Martega on 2010-09-06
So now everything is really messed up.  I didn't get a chance to open up a terminal and re-install the touchpad drivers because I couldn't even log in.  When I start up 10.04 as usual it takes me to the log in screen.  Except now the graphics and buttons and stuff are extremely basic, they aren't the usual log in icons.

In the upper right hand corner I get the following error message
"Install Problem!
The configuration defaults for GNOME Power Manager
have not been installed correctly.
Please contact your computer administrator."

When I try logging in with my password the screen goes blank and I am eventually returned back to the same login screen with the same error message in the upper right corner.

What the hell is going on?  Ubuntu was working fine for the last few months until this morning!

---

### Post by X1R1 on 2010-09-06
well that is weird indeed. But you dont need to login in the graphical enviroment to do what I suggested, you can just ctrl+alt+f2 right when the pc finishes the boot process. when you switch with ctrl+alt+f2 you will be able to login and get a terminal only screen.

---

### Post by Martega on 2010-09-06
Well I logged into safemode, I was able to get to a command prompt and I tried what you suggested (sudo apt-get install xserver-xorg-input-synaptics).  When it completed it said that I already had the most up to date drivers and nothing had been changed.  I still can't log in though due to the error I mentioned in my last post and as a result I'm forced to use windows at the moment.

---

### Post by X1R1 on 2010-09-06
> **Martega said:**
> Well I logged into safemode, I was able to get to a command prompt and I tried what you suggested (sudo apt-get install xserver-xorg-input-synaptics).  When it completed it said that I already had the most up to date drivers and nothing had been changed.  I still can't log in though due to the error I mentioned in my last post and as a result I'm forced to use windows at the moment.

Well if your system is complaining about gnome power manager, you can also try to reinstall it. First remove the conflicting package:

sudo apt-get remove gnome-power-manager

then install it:

sudo apt-get install gnome-power-manager

maybe that way the default parameters should set up correctly

It might be better to purge the package instead of just removing it. Though I dont remember the command at this time.

---

### Post by sandyd on 2010-09-06
> **Martega said:**
> Hi

I've been using Ubuntuhe 10.04 since June and up until today its been working fine with only a few minor bugs.  Today I booted up my computer and logged in and I was surprised to see that my mouse didn't work.  I can't move my mouse around at all and as a result I can't open any programs including the terminal.

When I start up my computer and I get to the ubuntu login page where I put in my password and what not everything is fine.  I can move the mouse around and everything is normal.  As soon as I input my password and log in the mouse stops working completely.  

How can I fix this?!?!?!?!  Please help!

My computer is an HP Pavilion dv6000.  I am currently on Windows 7 on the same computer where the touchpad does work.
a) [http://ubuntuforums.org/showthread.php?t=1566328](http://ubuntuforums.org/showthread.php?t=1566328)

have you 
a) checked the hard disk for errors (fsck)
b) attempted a package repair? (apt-get -f install)

---

### Post by Windows Nerd on 2010-09-06
> **X1R1 said:**
> 
It might be better to purge the package instead of just removing it. Though I dont remember the command at this time.
```
sudo apt-get purge <package_name>
```

---

### Post by Martega on 2010-09-07
@ carlee, yes I already tried that.  Nothing happend unfortunately.

Would there be any danger in purging the gnome-power-manager application as I am going to install it again right away?

I would do that using the following command, correct?

sudo apt-get remove --purge gnome-power-manager

Edit:  nvm, I didn't see windows nerd's post until after I posted this

---

### Post by Martega on 2010-09-07
Ok, now the login screen is normal again and I am basically back to where I was when I first posted this.  

At the login screen I can move my mouse around normally using my touchpad (I don't have a mouse with me so I haven't been able to test whether it would work).  After I put in my password and login I am able to move my mouse around for a second or two until my desktop pops up in which case the mouse freezes.

I have already tried updating my system and the drivers for my touchpad (xserver-xorg-input-synaptics).  So far nothing has worked.  I am completely stumped as to how this could've happend all of a sudden and as to how to fix it.

Please help.

---

### Post by Martega on 2010-09-07
I still need a lot of help.  I took my computer to the IT people at my college however they didn't know how to fix it as they usually deal only with windows and mac OSX computers.

---

