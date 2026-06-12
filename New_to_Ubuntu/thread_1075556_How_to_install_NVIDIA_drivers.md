---
title: "How to install NVIDIA drivers ?"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by psychx on 2009-02-20
I am trying to install drivers for an NVIDIA Geforce 6600GT on Ubuntu 8.10

I have recently had problems installing the driver and do not want this to happen again. This can be read @ [http://ubuntuforums.org/showthread.php?p=6757543#post6757543](http://ubuntuforums.org/showthread.php?p=6757543#post6757543)

At this point, I am in a fresh install of Ubuntu and have not changed anything, other than backing up my xorg.conf into my /home directory.

---

### Post by overdrank on 2009-02-20
> **psychx said:**
> I am trying to install drivers for an NVIDIA Geforce 6600GT on Ubuntu 8.10

I have recently had problems installing the driver and do not want this to happen again. This can be read @ [http://ubuntuforums.org/showthread.php?p=6757543#post6757543](http://ubuntuforums.org/showthread.php?p=6757543#post6757543)

At this point, I am in a fresh install of Ubuntu and have not changed anything, other than backing up my xorg.conf into my /home directory.

Hi and please do not create multiple threads on the same issue. You could have just bumped your other thread while searching for the answer and waiting for a reply.
Ok I have found some success with the xfix option when booting into recovery mode after installing the nvidia drivers in the way that you linked.  
There is no need to reinstall the OS to get the graphics drivers installed.
Have you tried just using the restricted drivers located under system, administration?

---

### Post by psychx on 2009-02-20
I have  tried to "activate" the drivers that are installed right now, which are 96, 173, 177 [Recommended]. I tried to activate 177 and it says downloading/installing driver. Then nothing happens, and it is not activated. I have restarted. This is why I would like to clarify how to do this.

I did not mean to annoy anyone by creating a new post. I wasn't sure if anyone would have replied to the other because of its length and the only person that was helping me made their last post 22 hours ago. I work full time (actually more than full time because I work in the medical field) and have to use my free time to fix this, which I don't have much of.

---

### Post by overdrank on 2009-02-20
> **psychx said:**
> I have  tried to "activate" the drivers that are installed right now, which are 96, 173, 177 [Recommended]. I tried to activate 177 and it says downloading/installing driver. Then nothing happens, and it is not activated. I have restarted. This is why I would like to clarify how to do this.

I did not mean to annoy anyone by creating a new post. I wasn't sure if anyone would have replied to the other because of its length and the only person that was helping me made their last post 22 hours ago. I work full time (actually more than full time because I work in the medical field) and have to use my free time to fix this, which I don't have much of.

Hi and I do understand you time constraints. :)
Ok if you installed with the alternate cd you may have to enable some of your repositories to download the nvidia drivers for the nvidia graphics.
Then after installing the drivers you may try the xfix option I mentioned is the low graphics mode returns.

---

### Post by cariboo on 2009-02-20
The drivers are not downloading for some reason, I had that happen the last time I did a full reinstall, Manually download the nvidia-glx-177 drivers from Synaptic and the try activating the driver again using System-->ADministration-->HArdware Drivers.

Jim

---

### Post by psychx on 2009-02-20
Ok, I downloaded the nvidia-glx-177 package from Synaptic. I am rebooting, but have to leave for work. I will remote in when at work and update you with information. Thanks!

---

### Post by psychx on 2009-02-20
Ok, so I just got home from work. I had installed the drivers earlier today. I am having the same exact problem in which I was having before. When I start the computer, after restarting or after it has been off, I get a Limit Graphics Mode. This is what I am in now.

I had tried installed the 177 drivers. Can anybody help me? I really enjoy using Ubuntu and really hope that I don't have to revert back to Windows. If you need any information I will be more than generous to give it to you.

By the way, I am currently running: "NVIDIA accelerated graphics driver (version 177) [Recommended]" right now.. "This driver is activated and currently in use."

---

### Post by overdrank on 2009-02-20
> **psychx said:**
> Ok, so I just got home from work. I had installed the drivers earlier today. I am having the same exact problem in which I was having before. When I start the computer, after restarting or after it has been off, I get a Limit Graphics Mode. This is what I am in now.

I had tried installed the 177 drivers. Can anybody help me? I really enjoy using Ubuntu and really hope that I don't have to revert back to Windows. If you need any information I will be more than generous to give it to you.

By the way, I am currently running: "NVIDIA accelerated graphics driver (version 177) [Recommended]" right now.. "This driver is activated and currently in use."

Ok can you use nvidia-setting to change the resolution? ```
gksu nvidia-settings
```

---

### Post by psychx on 2009-02-20
[IMG]http://i39.tinypic.com/xm7clk.png[/IMG]

This is what I'm getting when I run that command.

---

### Post by overdrank on 2009-02-20
Yea and I have seen that many times. :)
Have you tried the xfix option, this may help with activating the driver.
If this does not work sometimes for me by deactivating the driver and reboot. Then enabling the driver again has helped. 
I have to leave for work but will check back later.

---

### Post by psychx on 2009-02-20
Looks like everything is fixed now! XFIX did the trick. While in Recovery Mode, I made sure to run a filesystem check and xfix during the same session. After running xfix, I booted normally. Once in the GUI, at my Desktop, I opened up Hardware Drivers. I had to re-activate the 177 drivers, and did a reboot.

I am now booted up, and running in 1280x960.. Everything seems to be working fine, other than the fact that my monitor itself is bad.. but that is another story. Thank you very much!!

---

