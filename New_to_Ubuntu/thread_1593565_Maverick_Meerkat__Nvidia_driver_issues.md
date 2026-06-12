---
title: "Maverick Meerkat : Nvidia driver issues"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by snip3r8 on 2010-10-11
I had problems with Lucid with regards to installing nvidia drivers and therefore stuck with karmic...now Maverick is out and i still cant get the dam thing working ...if i use "sudo modprobe -r nouveau" it says its in use ,even after blacklisting it and killing GDM.please help!....and yes ,i have the latest .run driver from the nvidia site(which works just fine in karmic).

---

### Post by aust77 on 2010-10-11
Have you tried going to System-Administration-Additional Drivers?

---

### Post by snip3r8 on 2010-10-11
> **aust77 said:**
> Have you tried going to System-Administration-Additional Drivers?

Thats just the package drivers which are aged to say the least

---

### Post by ankspo71 on 2010-10-11
Hi,
The hardware manager lets me choose between versions 173 and 185 (which is technically 260.19.06) available for my 8400 GS.

According to [https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes](https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes) :
> The new Xorg 1.9 available in Maverick is not compatible with nVidia based chipsets that use the (nvidia-96) and (nvidia-173) drivers. (626974)
This may or may not have anything to do with you not being able to get working drivers, but I thought I would mention it.

My wife uses an Nvidia 6100 or 6200 card on her computer, but I haven't tried Maverick or Lucid on her computer yet.

* Correction: My wife just let me install Kubuntu 10.10 on her computer and it was a success. The Nvidia card is a GeForce 6100 and the 185 (260.19.06) driver from the hardware manager installed and works without problems. So I think the above quote should have nothing to do with 6100-6200 nvidia cards using "current" drivers.

---

### Post by ubunterooster on 2010-10-11
> **snip3r8 said:**
> Thats just the package drivers which are aged to say the least
try getting the official drivers: [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

---

### Post by Rushyang on 2010-10-11
I just successfully installed NVIDIA Drivers in 10.10 successfully before 10 mins. Follow this very simple guide..

> [http://ubuntuguide.net/how-to-install-nvidia-graphics-driver-in-ubuntu-10-10-maverick-meerkat](http://ubuntuguide.net/how-to-install-nvidia-graphics-driver-in-ubuntu-10-10-maverick-meerkat)

---

### Post by philinux on 2010-10-11
> **snip3r8 said:**
> Thats just the package drivers which are aged to say the least

Errr. Nvidia current is the latest stable driver.

---

### Post by Rushyang on 2010-10-11
> **philinux said:**
> Errr. Nvidia current is the latest stable driver.

Super Cool.. Thanks for confirmation. :)

---

### Post by snip3r8 on 2010-10-12
> **Rushyang said:**
> I just successfully installed NVIDIA Drivers in 10.10 successfully before 10 mins. Follow this very simple guide..

ok ,but i want to install from .run

---

### Post by anezch on 2010-10-12
> **Rushyang said:**
> I just successfully installed NVIDIA Drivers in 10.10 successfully before 10 mins. Follow this very simple guide..

I have a 8400GS card and nvidia-current is not working. Then I downloaded the driver from the official nvidia website, run it and voila! It works like a charm.

---

### Post by snip3r8 on 2010-10-13
> **anezch said:**
> I have a 8400GS card and nvidia-current is not working. Then I downloaded the driver from the official nvidia website, run it and voila! It works like a charm.

how exactly did you run that driver ,when i try and run it i get problems and it wont install

---

### Post by ubunterooster on 2010-10-13
post the error messages below

---

### Post by snip3r8 on 2010-10-13
well the first error is 

"The distribution-provided pre-install script failed! Continue installing anyway?"

---

### Post by ubunterooster on 2010-10-13
Oh. Sorry, I am not able to help there. 

That sucks.

---

### Post by Clawinus1 on 2010-10-13
I am on Windows XP SP3 and attempted to install Ubuntu 10.10 via WUPI.
I can see the Boot entry UBUNTU, if I click on it the installation starts. I can only hear it, the screen is totally blank.
After 10 Minutes the installation ceases and I hear some drum noise but no picture. I can only proceed by cutting power and going back to Windows.

Here is my configuration:

HP Pavilion
AMD Athlon 64X2 Dual Core Processor 4200+ 2.20 GHz 1.93 GB RAM

Model: NVIDIA GeForce 6150 LE  
Driver: nv4_mini.sys
Sunday, June 01, 2008
Supported 

Type: HP f1905 flat panel monitor 
Color: True Color (32 Bit) 
Resolution: 1280 x 1024 
Screen Saver: Not Active 

Model: NVIDIA nForce Networking Controller - Packet Scheduler Miniport 
Driver: nvenetfd.sys
Sunday, June 01, 2008
Supported 

I gather from other threads and this one that the NVIDIA driver may be at fault.
But I cannot install any alternative NVIDIA drivers because Ubuntu is not installed yet
Any help?

---

### Post by snip3r8 on 2010-10-13
> **Clawinus1 said:**
> I am on Windows XP SP3 and attempted to install Ubuntu 10.10 via WUPI.
I can see the Boot entry UBUNTU, if I click on it the installation starts. I can only hear it, the screen is totally blank.
After 10 Minutes the installation ceases and I hear some drum noise but no picture. I can only proceed by cutting power and going back to Windows.

Here is my configuration:

HP Pavilion
AMD Athlon 64X2 Dual Core Processor 4200+ 2.20 GHz 1.93 GB RAM

Model: NVIDIA GeForce 6150 LE  
Driver: nv4_mini.sys
Sunday, June 01, 2008
Supported 

Type: HP f1905 flat panel monitor 
Color: True Color (32 Bit) 
Resolution: 1280 x 1024 
Screen Saver: Not Active 

Model: NVIDIA nForce Networking Controller - Packet Scheduler Miniport 
Driver: nvenetfd.sys
Sunday, June 01, 2008
Supported 

I gather from other threads and this one that the NVIDIA driver may be at fault.
But I cannot install any alternative NVIDIA drivers because Ubuntu is not installed yet
Any help?

Ubuntu uses a default driver so install should not need a driver,drivers are only needed for fancy 3d effects,so i think you have the wrong thread. also personally i think its better to partition than use wubi

---

### Post by snip3r8 on 2010-10-13
anyway i have a new idea.....anybody know how i can update to the latest gnome on karmic?

---

### Post by alzie on 2010-10-13
I had the same error, I just went ahead and installed anyways.

> **snip3r8 said:**
> well the first error is 

"The distribution-provided pre-install script failed! Continue installing anyway?"

It worked.

I followed Kosimo's directions here: [http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

I hope this helps.  

NB I'm on 10.04 Dual Boot with Win XP SP3 WUBI install.

---

### Post by snip3r8 on 2010-10-14
> **alzie said:**
> I had the same error, I just went ahead and installed anyways.



It worked.

I followed Kosimo's directions here: [http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

I hope this helps.  

NB I'm on 10.04 Dual Boot with Win XP SP3 WUBI install.

That's how i installed drivers in karmic...lucid and maverick seem to have issues though

---

### Post by snip3r8 on 2010-10-14
> **snip3r8 said:**
> anyway i have a new idea.....anybody know how i can update to the latest gnome on karmic?

Anybody?

---

### Post by oxygenfarm on 2010-12-16
OK I'm using the same NVIDIA card with Ubuntu 10.10 and stupidly went to "System-Administration-Additional Drivers" and told it to install the _RECOMMENDED _driver, Now Ubuntu won't load. Is there anyway to backdate or remove the RECOMMENDED driver?
Help appreciated.

---

