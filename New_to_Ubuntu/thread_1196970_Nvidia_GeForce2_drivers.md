---
title: "Nvidia GeForce2 drivers"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by GSI on 2009-06-25
Hello :) I'm new on ubuntu and I need some help.From where can I get driver for my Nvidia GeForce2 that wont limit my screen resolution to 640x480 ?

---

### Post by wojox on 2009-06-25
I take it you already looked here
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

---

### Post by GSI on 2009-06-25
Thanks. But when I install this driver tomorow will I have the resolution problem?

---

### Post by berksted on 2009-06-25
A previos forum thread on this is here:
[http://ubuntuforums.org/showthread.php?t=265776](http://ubuntuforums.org/showthread.php?t=265776)

For my laptop I had to manually add a specific resolution, look up xorg.conf
let me know if you need help with that.

---

### Post by GSI on 2009-06-25
I had the resolution problem before.... but I can't remember how  I fixed it... :D I remember that i needed Nvidia X server config.How do i turn this menu on?

---

### Post by QIII on 2009-06-25
If you are not in an extreme hurry for an answer this evening...

I'm working on a bug I reported in launchpad regarding nVidia GeForce drivers with Karmic.  I'm still working through a resolution, but what I find my be of use in previous versions.

I'd personally like to get it resolved this weekend so that I can continue testing Karmic...

---

### Post by GSI on 2009-06-25
I'm not in a hurry. I will install ubuntu on my PC tomorrow ;)

---

### Post by Nautilus112 on 2009-06-25
Just install your driver through System > Administration > Hardware Drivers, then go to System > Adminstration > NVIDIA X Server Settings and go to X Server Display Config and change your resolution.

---

### Post by cph05a on 2009-06-25
> Just install your driver through System > Administration > Hardware Drivers, then go to System > Adminstration > NVIDIA X Server Settings and go to X Server Display Config and change your resolution.

You may not see the NVIDIA X Server Settings until after you've installed the nVidia Drivers. 

First, try to see if the restricted drivers will work by going to System>Administrator>Hardware Drivers and enabling the nVidia drivers.

If the restricted drivers don't work for you (which was the case for my GeForce GTX 180), you can get the latest drivers from [nVidia]("http://www.nvidia.com/Download/index.aspx?lang=en-us"). Here are instructions for [installing nVidia Drivers]("http://ubuntuforums.org/showthread.php?t=1030962").

---

### Post by GSI on 2009-06-26
> **cph05a said:**
> You may not see the NVIDIA X Server Settings until after you've installed the nVidia Drivers. 

First, try to see if the restricted drivers will work by going to System>Administrator>Hardware Drivers and enabling the nVidia drivers.

If the restricted drivers don't work for you (which was the case for my GeForce GTX 180), you can get the latest drivers from [nVidia]("http://www.nvidia.com/Download/index.aspx?lang=en-us"). Here are instructions for [installing nVidia Drivers]("http://ubuntuforums.org/showthread.php?t=1030962").

No the restricted drivers dont work for me :( When I enable them screen resolution is only 640x480 ;(

---

### Post by GSI on 2009-06-26
@cph05a

When I type the command :

sudo sh NVIDIA-Linux-x86-185.18.14-pkg1.run 

I get an error: 

sh: Can't open NVIDIA-Linux-x86-185.18.14-pkg1.run

---

### Post by GSI on 2009-06-26
Now something very strange happened :D :D 

I installed from synaptic the driver but only Nvidia X server config showed up...Still no driver.. :(

---

### Post by cph05a on 2009-06-26
try

```
sudo ./NVIDIA-Linux-x86-185.18.14-pkg1.run
```

---

### Post by QIII on 2009-06-26
EDIT:  Cut and paste my instructions below, put them in a text file and print it off before you start.  Once you kill the Gnome Desktop Manager, you won't be able to see this.


Make sure that NVIDIA-Linux-x86-185.18.14-pkg1.run is on your desktop.

Press CTL-ALT-F2 to close the window session.
Type in your username and password when prompted.
In the command line, type

sudo /etc/init.d/gdm stop
sudo sh ~/NVIDIA-Linux-x86-185.18.14-pkg1.run 
    Follow the instructions
sudo /etc/init.d/gdm restart

Depending on the driver and the Linux kernel you are running, you may be asked if you want to compile a driver kernel.  Answer "Yes".

If the driver kernel won't compile, you'll get a message to the effect that the kernel could not be compiled.

If that is the case, you won't be able to install the driver this way.

I'm at work and away from my Ubuntu machines right now.  It is 9:07 am local time right now, so figure what our time difference is -- I think we are GMT - 8.  You should be GMT + 2, unless you've changed your times for Summer already.

Unfortunately, I have some obligations after work, so I may not be back until very late my time (very early for you Saturday morning.)

But I hope this helps.

---

### Post by Tholley on 2009-06-26
I think I will try this as well and see if it helps the problem I have been searching for on this thread...
 
[http://ubuntuforums.org/showthread.php?t=1196674](http://ubuntuforums.org/showthread.php?t=1196674)

---

### Post by GSI on 2009-06-27
The problem is fixed now.. I found my old topic and folowed the instructions there....

Link : [http://ubuntuforums.org/showthread.php?t=1031299](http://ubuntuforums.org/showthread.php?t=1031299)

---

### Post by QIII on 2009-06-27
Did you resolve the problem of having to reset the resolution each time?

Congrats on the solution!

And thanks for posting it back.

That's an older driver, so I wonder where mention of the other one came from.  Sorry.  I got back into the thread and saw that one being discussed.

---

### Post by GSI on 2009-06-27
The resolution problem didnt appeared now. I dont know why :)

But if someone do get the resolution problem.This is how to fix it..

Just open Nvidia X server configuration and set your resolution than click 'save to X server'

---

