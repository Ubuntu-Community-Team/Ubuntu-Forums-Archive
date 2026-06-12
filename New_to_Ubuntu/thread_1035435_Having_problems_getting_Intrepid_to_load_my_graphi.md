---
title: "Having problems getting Intrepid to load my graphics card."
date: 2009-01-09
forum: New to Ubuntu
---

### Post by sinnombre on 2009-01-09
Hey Everyone,

So I'm brand spanking new to Ubuntu, and linux in general. I've been a windows jockey for 20 years, and figured it was time to learn another OS.

I'm trying to run 8.10 on an Asus F3S laptop with a GeForce 8600M GS graphics card.

I was able to install 8.10 just fine, I got the dual boot with windows configured just fine, and when I first log in everything seems good. The LCD display is running at it's full resolution, and things seem good. I go into Hardware Drivers and enable the Nvidia driver (177). It says everything is fine, and I reboot.

Once I reboot, it comes up at 800x600, and I get the error "Unable to install the Nvidia Kernel" If I go back and disable the driver, ubuntu comes back up at full resolution.

I've tried using the 177, 173, and even the new 180 beta drivers, same error each time. From what I've been able to gather, I need to rebuild my nvidia kernel, and i've tried to follow the instructions on the nvidia website. I haven't been able to get them working either.

Another thought I had was download the nvidia driver directly and then install it through:

sudo sh NVIDIA-linux......

But I get the error that X Server is still running. I've tried rebooting to just a terminal with no desktop and installing that way, and it tells me to go to telinit3 which just brings up my desktop.

I've searched the forums for ways to kill x server, but none of the methods seem to work for me.

If anyone has any ideas for installing an nvidia driver on this type of machine, I'd really appreciate it!! I am a total linux newb, but I'm trying to pick things up as fast as I can.

Thanks so much guys!!

PS I've tried using EnvyNG to install the drivers as well as that seemed to work for some people, but no dice.

---

### Post by linux_tech on 2009-01-09
Try following these instructions here first.  
[http://ubuntuforums.org/showthread.php?t=514161](http://ubuntuforums.org/showthread.php?t=514161)

if you have 64bit hardware, 64bit ubuntu, then download the 64bit linux driver.  If you have 32bit, then use 32bit driver

To open nvidia settings, in terminal type: 
```
nvidia-settings
```

If this fails to get driver installed, then give envy a try.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Install envy and then from the terminal type:
```
sudo envy -t
```
This will run the installation script from the terminal....follow the instructions to install the correct Nvidia proprietary driver.

---

