---
title: "Installing graphic card drivers"
date: 2010-03-11
forum: New to Ubuntu
---

### Post by KL_72_TR on 2010-03-11
Hello everybody. I need help. If someone can... Thank you. Firstly I must say that I am totally new in Linux. Basically I don't know nothing.  
 Now my problem. It has been a week since I installed Ubuntu 9.10. At this point I wanted to install the drivers for my graphic card (Palit 250 GTS). I found the drivers in Nvidia.com.  Then I downloaded (Nvidia-Linux-x86-190.53-pkg1.run), When I double click on the file the system show me this:  
 -    -    -    -    -    -    -    -    -    -    -    -    -    -    
 **Could not open the file /home/kriton/Downloads/N...Linux-x86-190.53-pkg1.run**
 gedit has not been able to detect the character coding.  
 Please check that you are not trying to open a binary file.
 Select a character coding from the menu and try again.
 Character Coding: Current Locale (UTF-8).
 -    -    -    -    -    -    -    -    -    -    -    -    -    -    
 I right click on the file and > Properties > Basic > Type: shell script (application/x-shellscript)
 These are the informations I can give you so far. If you need more, tell me how.
 If you think I am not qualified to handle this tell me. It is not a problem. These are my firs days with a new OS.

---

### Post by undecim on 2010-03-11
Have you taken a look at System -> Administration -> Hardware Drivers to make sure your driver isn't there?

If it's not there and you're already getting your full resolution, you probably are already using the correct driver.

---

### Post by redbook4574 on 2010-03-11
> **undecim said:**
> Have you taken a look at System -> Administration -> Hardware Drivers to make sure your driver isn't there?

If it's not there and you're already getting your full resolution, you probably are already using the correct driver.

I agree with undecim, stick with the driver in Hardware Drivers it has usually been tested and is known to work although it may not be the latest.

---

### Post by KL_72_TR on 2010-03-11
I did what you recommended me. And this is what the system told me:
 **NVIDIA accelerated graphics driver (version 185) [Recommended] ** 
 Than I followed:  
 **Activate > (Downloading & Installing) > Restart ** 
 Now I see that my graphics are much better. Sincerely a big THANK.

---

### Post by KL_72_TR on 2010-03-11
Thank you both for your help and time.

---

### Post by gabriel_fatih on 2010-03-11
Hello!

I just installed that nvidia driver last night, what I did was, restart ubuntu as recovery mode (the installer asks you to exit all window X modes, and this was the only way I could do it) then change the permissions of the file to executable (i cant remember the exact command, look for it, it's something like chmod -x) change to init 3

init 3

then run the file 

sh NVIDIAxxxx

from that point forward everything was "next next finish", now everything looks great (twinview), I had the driver you have now, the 185, and some things didn't work the way they should.
Hope my experience helps you, by the way I'm a total newbie too, this is my first reply :D

---

### Post by KL_72_TR on 2010-03-11
Hello &#8211; gabriel - . Thank you to, for your help. I am afraid to make that kind of changes (I'll get lost pretty soon).  At this point I've decided to seat down and read some books on Linux. 
Again thanks for your help.

---

