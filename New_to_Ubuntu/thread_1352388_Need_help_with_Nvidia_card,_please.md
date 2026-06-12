---
title: "Need help with Nvidia card, please"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by guy72277 on 2009-12-11
Hi,

I have installed the right driver (96, which is the recommended driver for my geforce 4000mx card).  

If I look in System > Administration > Nvidia X Server settings, it says " You do not appear to be using the nvidia x driver, edit your x configuration file (just run 'nvidia xconfig' as root) and restart the x server. I do this but end up with a flickering login screen, which I can get past by dropping to a root cli, creating a new xorg file.  I have tried many things over the few weeks I've been trying but have not managed to get any further. Can I submit my xorg or something?

Also if I try to launch XBMC, it comes up with an error saying  "XBMC needs hardware accelerated OpenGL rendering.  

Would appreciate some help on this, as my media box has been out of action for a while now.

Thanks 

Guy

---

### Post by 4Orbs on 2009-12-11
Before activating the driver set the screen resolution and refresh rate back to default or auto (using the regular Ubuntu Display settings manager). Then activate the driver and reboot. If you need to run the nvidia-xconfig after reboot, don't choose the option to merge the new xorg.conf with the existing one. Reboot again after running the nvidia-xconfig. This way you'll be able to see what nvidia has determined your default resolution to be. It might even be your preferred resolution. I you can get to an unblinking login screen, then you should be able to use the Nvidia Settings Mgr to change resolution thereafter (as root, if you want it to survive).

---

### Post by guy72277 on 2009-12-11
Hi,

thanks for replying.  Not sure what you mean by "activating" the driver.  It is installed and I get a 1024 x 678 screen resolution which I just saw in the display settings.  I agree that this is pretty good, (and the screen has always looked OK).  Can't find an auto or default in display preferences though....  Could you give me a hint on how to do this, please?

Thanks

---

### Post by 4Orbs on 2009-12-11
You activate the driver by going in the menu to System > Hardware Drivers and click on the Activate button for the recommended driver. It should show at the top of the window what your recommended driver is. Even if the driver is already installed you need to activate it to generate the initial xorg.conf file.

If I understand correctly, your nVidia settings manager is now functional and showing your resolution as 1024x768. And now you want to change the resolution?

---

### Post by guy72277 on 2009-12-11
Hi,

the driver is already activated.  Should I remove it and start again?  I don't know if the nvidia card is working or not.  if I have a resolution like that does that mean it is working? If it is, why does the nvidia settings manager say "You do not appear to be using the nvidia x driver" and only have a couple of boxes to tick, and why does XBMC give the error message "XBMC needs hardware accelerated OpenGL rendering." on startup?  I'm not sure exactly what my problem is, just that XBMC does not work and that movies that displayed fine with win xp mediacenter addition, stutter with ubuntu.


Hope that's clear?  I am just assuming it has to do with the graphics card, taking into account the error messages.

Thanks again for helping out.

Guy

---

### Post by 4Orbs on 2009-12-11
How have you determined that the driver is activated? Does the Hardware Drivers mgr say the driver is activated?

Don't try to use XBMC until the driver is activated and working correctly. The driver is the first priority.

If the Hardware Drivers mgr says the driver is activated, and you have rebooted, but the nVidia settings mgr says you need to run nvidia-xconfig then that is what you gotta do, In a terminal enter this:
```
sudo nvidia-xconfig
```
After hitting Enter it will ask (maybe) if you want to merge the new xorg.conf with the existing one. Choose No. Then log out or restart the computer, log back in and open the nVidia settings mgr as root by entering in the terminal:
```
gksudo nvidia-settings
```
Then you should be able to change the screen resolution to your preferred, then click the button on the nvidia settings mgr to save you settings to the xorg.conf file located at /etc/X11/xorg.conf

Are you still getting the blinking login screen?

---

### Post by guy72277 on 2009-12-11
Hi,  Hardware drivers says "This driver is activated and currently in use"

On reboot, I get a message about low graphics mode, (which is at the same stage as the flickering screen was before, but is a new development) and I can choose to reconfigure settings or do a low graphics session.  If I try the sudo nvidia-config command in terminal, I get "command not found". If I try the gksudo nvidia-settings, I just get the same message from  the nvidia settings manager saying "You do not appear to be using the nvidia x driver".

I think i'll need to create a new xorg and nove it to etc/X11 again, no?  I've done this countless times in the past...... 

In low graphics mode, I get less display options.  Before there were 6-7 and in low graphics mode I just get 3.  I still don't understand if the card is working or not when there are 6-7 options for screen resolution.

Sorry for being a bit of a medieval dunce on this.....  Maybe i'm just having a problem with the openGL part although i'm not really sure what that is.

---

### Post by 4Orbs on 2009-12-11
> If I try the sudo nvidia-config
Maybe you made a typo error. Command is sudo nvidia-xconfig and this is essential, unless you would rather add the xorg.conf manually.

---

### Post by guy72277 on 2009-12-11
Hi, I did make a typo. 

I used sudo nvidia-xconfig and it backed up the old and made a new xorg.conf file. (no questions about merging).  On reboot I get an error that Ubuntu is running in low graphics mode with a message about failing to initialize the nvidia graphics device.  it also says screens found but none have usable configuration.
Just for info the screen i'm currently using is an HP1502, but I intend to use the pc with the tv using the s-video output like I did when the machine was running Win XP media center edition.

Thanks, it's getting late here in Europe, so not sure how much timr I have let this evening.  I have already spent an eternity tring to sort this out although I only get a couple of hours an evening....

---

### Post by 4Orbs on 2009-12-11
With any luck you may be able to fix it now by just editing the xorg.conf file to remove all the resolution entries that are higher than your desired resolution. You only need to do this on the one line that corresponds to the default depth (probably 24) that you are using. You can log in to low graphics mode, edit the xorg.conf as root, save it and reboot. If, after editing the file, you get a good desktop with a working driver... you shouldn't use the nvidia settings mgr to change resolution again because it will overwrite the (edited and working) xorg.conf so if you want to change resolutions again you should manually edit the file again to your preferred res.

---

### Post by buntunub on 2009-12-11
Hi. Log in to your desktop in whatever mode you can and open a terminal. Type in

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.back
```

then

```
sudo rm /etc/X11/xorg.conf
```

then

```
sudo nvidia-settings
```

and setup your screen as you need and then make sure to save the xorg.conf from that nvidia-settings window. Then log out, then back in and you should be good to go.

---

