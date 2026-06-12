---
title: "Black screen when enabling graphic drivers for GeForce 6100"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by MockY on 2009-04-27
My wife's computer has a built in GeForce 6100 graphic card, and it has been working in every single release since Feisty. However, now in Jaunty, if I enable the 180 drivers via Hardware Drivers, I am presented with a black screen with a 2px visible line on top of the screen. This is for 1280x1024 (lower resolution works, but something I obviously don't want).
I have looked around and it seems like I am not alone with this issue. However, I can't find any solution.

[quote=Mark Schouten  ]Installing the proprietary drivers did start X, however only the top two pixel-rows were used. The rest of the screen was black.[/quote]

Any ideas?

---

### Post by MockY on 2009-04-27
Still no luck in finding a solution to the problem. I am now forced to go back to Intrepid.... *sigh*
It's sad that the development goes backwards in some areas, and is infact getting worse. Very odd...but oh well...

---

### Post by pspsampsp on 2009-04-28
I think you need to edit your xconf and add the resolution manually maybe someone else will tell you how as i dont know how (hope its not to late).

---

### Post by MockY on 2009-04-28
The problem is that the right resolution is displayed to the monitor, it's just that the drivers only allow a strip of 2 pixels to be visible. So in order to actually see a full desktop is to manually force it to a lower resolution (which like I said earlier, is not acceptable). This is a driver issue, and not an Ubuntu issue.

This is only the case with 6100 since I have tested 6200 and multiple Nvidia card over that, and they all work.

I have played around now on 8.10 with the following drivers downloaded from Nvidia's website

Version: 180.51 - Failed. The result is the same. Only a 2px strip on top is displayed
Version: 180.44 - Failed. The result is the same. Only a 2px strip on top is displayed

Any driver older than these two fails to install completely, so I never managed to test them out.

Oddly enough, the default driver (I'm guessing this is the default driver for Jaunty as well), the 180.51 driver (released April 21) is not the newest driver available. I found Version: 185.18.04 (released April 24) which actually works for GeForce 6100. I installed it on Intrepid and it appears to work just fine, since Compiz is running just fine and I can see the entire desktop.

**CONCLUSION:**
In order for GeForce 6100 to run properly on Intrepid Ibex (assuming the same case is for Jaunty Jakalope, but will try in a minute once I reinstall it again), you have to manually install the 185.18.04 driver which you can download [HERE]("http://us.download.nvidia.com/XFree86/Linux-x86/185.18.04/NVIDIA-Linux-x86-185.18.04-pkg1.run")

**UPDATE:**
I have now tried it in Jaunty as well, and I can confirm that the 185.18.04 (released April 24) works with GeForce 6100.

---

### Post by HeelsFan on 2009-04-28
I'm having the same issues with a GeForce 6100 as well. I downloaded the 185.18.04 driver as you suggested. 

Could you help my through the manual install process? Thanks in advance.

---

### Post by MockY on 2009-04-28
You have to install it via a different ttyl.

1. Press CTRL+Alt+F2 all at once
2. You will now have a text only shell. Type in your username and password as directed
3. Type ```
sudo /etc/init.d/gdm stop
``` or ```
sudo killall gdm
```
then go to the directory you downloaded the file. For example, if it is the desktop, then type ```
cd ~/Desktop/
```
4. Install the file using this command ```
sudo sh NVIDIA*
``` _Hint_, you can press the TAB key right after the first N. It will type in the name of the file for you. Keep in mind that file names and directories are key sensitive, so n and N is not the same thing.
5. Follow instructions at the prompt. I suggest that you select YES on all.
6. Once done, reboot your system using this command ```
sudo reboot
```

Keep in mind that you have to hit Enter after each command. I assume that you know that, but figured it wouldn't hurt to add.

Good luck!

---

### Post by HeelsFan on 2009-04-28
I found a thread that detailed the installation process for the 185 drivers: [http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

Everything worked perfectly and I am back up and running with 3D effects. I hope the 185 drivers make it to the repositories soon as I would rather not have to redo the drivers each time the kernal updates.

---

### Post by kastanedowski on 2009-08-19
Did you have poor quality with the sound? I run the same computer with Windows and the difference is amazing, any advice?

thanks

Geforce 6100


> **MockY said:**
> The problem is that the right resolution is displayed to the monitor, it's just that the drivers only allow a strip of 2 pixels to be visible. So in order to actually see a full desktop is to manually force it to a lower resolution (which like I said earlier, is not acceptable). This is a driver issue, and not an Ubuntu issue.

This is only the case with 6100 since I have tested 6200 and multiple Nvidia card over that, and they all work.

I have played around now on 8.10 with the following drivers downloaded from Nvidia's website

Version: 180.51 - Failed. The result is the same. Only a 2px strip on top is displayed
Version: 180.44 - Failed. The result is the same. Only a 2px strip on top is displayed

Any driver older than these two fails to install completely, so I never managed to test them out.

Oddly enough, the default driver (I'm guessing this is the default driver for Jaunty as well), the 180.51 driver (released April 21) is not the newest driver available. I found Version: 185.18.04 (released April 24) which actually works for GeForce 6100. I installed it on Intrepid and it appears to work just fine, since Compiz is running just fine and I can see the entire desktop.

**CONCLUSION:**
In order for GeForce 6100 to run properly on Intrepid Ibex (assuming the same case is for Jaunty Jakalope, but will try in a minute once I reinstall it again), you have to manually install the 185.18.04 driver which you can download [HERE]("http://us.download.nvidia.com/XFree86/Linux-x86/185.18.04/NVIDIA-Linux-x86-185.18.04-pkg1.run")

**UPDATE:**
I have now tried it in Jaunty as well, and I can confirm that the 185.18.04 (released April 24) works with GeForce 6100.

---

### Post by MockY on 2009-08-25
I don't see what the sound has to do with the graphic drivers. Or are you saying that your sound got worse once you installed the drivers?

---

### Post by zooey on 2009-10-03
thanks,

i find this very useful, i had the same problem:), now is solved, great:)

---

### Post by ron66 on 2009-12-17
Thanks, This procedure worked for me, while on 9.04.   However my video card is a GeForce FX 5200 so I have to use nvidia driver version 173. 

When I upgraded to 9.10, I also had to do the same thing all over again.

---

