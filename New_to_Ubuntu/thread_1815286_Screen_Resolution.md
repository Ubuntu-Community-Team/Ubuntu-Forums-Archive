---
title: "Screen Resolution"
date: 2011-07-31
forum: New to Ubuntu
---

### Post by arun.manuel14 on 2011-07-31
Hey , I'm new to Linux . I've been using windows from ever since i can remember .
My monitor's optimum display resolution is 1600x900
But ubuntu 11.04 has only 1024x768 as the maximum resolution . 
I tried google , but I couldn't understand the whole xorg.conf thing . 
When I opened my xorg.conf this is what was written , 


"
# Minimal xorg.conf for the Nouveau driver

Section "Device"
    Identifier    "Default screen"
          Driver        "nouveau"
EndSection

"


Also I'm unable to install my on board graphics , I went to nvidia and specifically downloaded the drivers for the linux x64 version (Geforce 7025/nforce630a)
When i tried to run the driver this is what it said 

"
Could not open the file /media/FreeAgent GoFlex …A-Linux-x86_64-275.21.run.

Please check that you are not trying to open a binary file.
Select a different character encoding from the menu and try again.

"


It would be really great if anyone could help me out ! 
Thanks in advance! :)

---

### Post by sadaruwan12 on 2011-07-31
> **arun.manuel14 said:**
> Hey , I'm new to Linux . I've been using windows from ever since i can remember .
My monitor's optimum display resolution is 1600x900
But ubuntu 11.04 has only 1024x768 as the maximum resolution . 
I tried google , but I couldn't understand the whole xorg.conf thing . 
When I opened my xorg.conf this is what was written , 


"
# Minimal xorg.conf for the Nouveau driver

Section "Device"
    Identifier    "Default screen"
          Driver        "nouveau"
EndSection

"


Also I'm unable to install my on board graphics , I went to nvidia and specifically downloaded the drivers for the linux x64 version (Geforce 7025/nforce630a)
When i tried to run the driver this is what it said 

"
Could not open the file /media/FreeAgent GoFlex …A-Linux-x86_64-275.21.run.

Please check that you are not trying to open a binary file.
Select a different character encoding from the menu and try again.

"


It would be really great if anyone could help me out ! 
Thanks in advance! :)

Why is that you don't have the appropriate driver for you VGA card from your post I assume that you've nvidia graphics card but when you have a Nvidia normally Ubuntu will prompt you for a confirmation in installing the propitiatory drivers if that didn't  happen do this Go to

System -> Administration -> Hardware Drivers

Now wait for it to check your hardware and get the information form the internet and it'll display the recommended drivers from Ubuntu repos.

If doesn't go to the Nvidia site and from there down load the drivers package but when you want to run it from your PC you need to know a little bit about how to do things in the terminal.

---

### Post by mikewhatever on 2011-07-31
No need to download drivers from sites (this is not Windows). Use the Additional Driver utility under System->Administration.

---

### Post by arun.manuel14 on 2011-07-31
Thanks! 
I managed to install the drivers!
But I still can't get my screen resolution to 1600x900 !!!?

---

