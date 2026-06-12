---
title: "How can I use dual screen?"
date: 2010-06-28
forum: New to Ubuntu
---

### Post by ie91 on 2010-06-28
Hi, I just switched from Windows 7 to Ubuntu 10.4 a few days ago so I'm a complete noob at everything Linux. I have a nVidia GeForce GT 330M graphics card, and I finally managed to get it to work (although I'm not sure how, tried too many suggestions), but now I want to be able to extend my display to another monitor like I did in windows.

If I go system>preferences>monitors I get the following message: 'It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?'
When I click yes the NVIDIA X Server Settings opens...and if I go to Display Configuration and click on detect displays nothing happens, but my external monitor (an old Dell, not sure of the model, does that matter?) is connected to my laptop's VGA port. Also, the configuration is set to Separate X Screen, although I'm not sure what that means, but I can't change it - the other options don't let me click on them (other options being disabled and twinview).

Does anyone know how I can extend my display to the other monitor???

Also, somehow I've done something to get a small pink rectangle on the top left of my screen that writes 'Unknown' on it....

---

### Post by Lpeop on 2010-06-28
I was having the same problem with my Ubuntu not recognizing my second monitor.  It worked fine with Windows XP and 7.  I ended up going to the internet and downloading a new driver for my second monitor.  Ubuntu finally recognized the second monitor and I was able to extend my view to my second monitor.  You can get rid of that pink box in the upper left had corner of your screen by closing the display box you opened when you went to system>preferences>display.  They will both disappear at the same time when you close the display preferences box.  I hope this helps.  Good luck and welcome to the wonderful world of Linux.  The best way to learn the system is to force yourself to onlly work in Linux and just try different things.  You will become familiar with the GUI and everything that it does.  The free apps are awesome!

---

### Post by ie91 on 2010-06-28
> **Lpeop said:**
> I was having the same problem with my Ubuntu not recognizing my second monitor.  It worked fine with Windows XP and 7.  I ended up going to the internet and downloading a new driver for my second monitor.  Ubuntu finally recognized the second monitor and I was able to extend my view to my second monitor.  You can get rid of that pink box in the upper left had corner of your screen by closing the display box you opened when you went to system>preferences>display.  They will both disappear at the same time when you close the display preferences box.  I hope this helps.  Good luck and welcome to the wonderful world of Linux.  The best way to learn the system is to force yourself to onlly work in Linux and just try different things.  You will become familiar with the GUI and everything that it does.  The free apps are awesome!


I've already closed the monitor options thing, and the pink box is still there.
Also, what do you mean by a new driver? I've just gotten the driver for mine. By new driver do you mean updated? Or a driver for that specific monitor? If so, how can I find what type the monitor is exactly? all I know is it's a Dell (but I'll only be using this for a short while, I'm going to buy something new in a few months).

---

### Post by mikewhatever on 2010-06-28
Here is a basic howto for Lucid.
[http://ubuntuguide.org/wiki/Ubuntu:Lucid#Configure_Dual_Monitors_with_nVidia](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Configure_Dual_Monitors_with_nVidia)

---

### Post by ie91 on 2010-06-28
Okay the pink thing went away when I restarted....But I think I know the main problem here. There is absolutely no recognition that I have another monitor connected. The nVidia x server settings program just does not recognize that there is another display....even when I click on detect display, so obviously I can't chose any other option. 

How to I get my computer to recognize the other monitor?

---

### Post by ie91 on 2010-06-28
> **mikewhatever said:**
> Here is a basic howto for Lucid.
[http://ubuntuguide.org/wiki/Ubuntu:Lucid#Configure_Dual_Monitors_with_nVidia](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Configure_Dual_Monitors_with_nVidia)


I followed the instructions for dual monitors on that link, but my Dell monitor  isn't recognized so I can't configure anything.

Also, now when I go to System>preferences>monitors I get a different message: 'Could not get screen information: RandR extension is not present'

---

### Post by ie91 on 2010-07-01
anyone? sorry, gotta bumP!

---

### Post by tomasz74 on 2010-07-19
Hi
I've got exactly the same problems with second monitor. I've got Dell Inspiron 1370 and I connected monitor ProLite B2206WS. I set up two monitors on preferences, but on ProLite it was only mouse cursor and nothing more. Once i went to second monitor I can't get back. I did set something and now when I go to system/preferences/ monitors I've got the same message RandR extension is not present. I checked in Synaptic Package M and I think it is installed.
I also get my ubuntu 10.04 a few days ago and I'm a newbie. :(
Any one knows what extension exactly should it be?
Please click one of the Quick Reply icons in the  posts above to activate Quick Reply

---

### Post by Quentumknight on 2010-07-19
I too am a newbie having a little problem with nvidia settings... The options other than "Separate X-screen" (that require to restart X)  are  in gray and can't be selected. Even using the "gksu nvidia-settings" command I found somewhere on this forum.  Also, it seems that the configuration  file doesn't get saved, as I have to configure my screen from 800X600 to  his normal 1440X900 every single time I start the computer.

The strangest thing here for me is that I am not even using a separate  screen. (I don't need that) but still can't deactivate the separate  screen mode. Maybe this just doesn't really matter, but it would be more logical to deactivate it.

Thanks for helping me...

---

