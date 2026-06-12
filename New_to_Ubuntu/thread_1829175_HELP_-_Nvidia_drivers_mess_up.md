---
title: "HELP - Nvidia drivers mess up"
date: 2011-08-20
forum: New to Ubuntu
---

### Post by r2d211 on 2011-08-20
I have the natty installed and did some work. I had the ubuntu alternate DVD mounted and suddenly a popup told me that I have Nvidia drivers available for update (note that I don't have internet connection). So I clicked on the recommended driver and then was told to restart the system. I did it but now the monitor is flickering and there's no upper or lower panel, the resolution has changed and I can't access the Preferences/ Monitors to change it and also have no clue about how to use the terminal to reverse the driver installation or to fix the problem. Please help. I am still able to use the keyboard so the alt+ctrl+F2 command is still available but don't know how to use it and what to write.…

---

### Post by scottstensland on 2011-08-20
sudo apt-get update
sudo apt-get install nvidia-current

this works for me - same latest driver version as manually downloading 
from nvidia directly

---

### Post by birkopf on 2011-08-20
> **scottstensland said:**
> sudo apt-get update
sudo apt-get install nvidia-current

this works for me - same latest driver version as manually downloading 
from nvidia directly

Yep, I'd recommend the same. After - you may need to restart system and once in graphical mode try to use "Additional Drivers" from Administration, to be sure everything is up to date. 

PS - You need internet connection now :)

---

### Post by r2d211 on 2011-08-20
Did it, but didn't work. Then I went into safe mode and it showed me a popup saying that the graphic interface is not properly set at offered to fix the problem. I clicked yes the it told me to go into a low res. boot which I did but couldn't change things or rather didn't know what to do. So I rebooted and the booted normally and things are the same as before, even if the popup told me that the driver was inactivated.
What should I do more?

---

### Post by r2d211 on 2011-08-20
Okay finally I reentered the low graphic mode and removed the nvidia drivers. Then rebooted and now all it's okay.

Can anybody tell me how to use an activated nvidia driver? The pop up told me that the driver is active but not in use. How to use it?

---

### Post by r2d211 on 2011-08-21
Any suggestion?

---

### Post by realzippy on 2011-08-21
This sometimes is a bug.
But you can run

```
sudo nvidia-xconfig
```

reboot or restartXserver

---

### Post by r2d211 on 2011-08-21
Oh, thanks, I'll try and keep you update!

---

### Post by cbowman57 on 2011-08-21
The "driver is activated but not in use" message is a bug.  Open up Nvidia server settings, if it opens up and gives you options then you are using the Nvidia driver.

---

### Post by r2d211 on 2011-08-21
Okay, I did it and when opening nvidia settings it twlls me to run in terminal the command suggested above and to restart. I did it but still nothing. I mean thus driver is the one which allows me to run unity or screen effects but I have nothing of these. Also at startup screen it lists Ubuntu and Ubuntu classic and then Ubuntu classic without effects, but even when choosing Ubuntu, I have no screen effects. So: is this driver working or not?

---

### Post by r2d211 on 2011-08-21
Is it possible that the simple fact that I installed natty as a windows application hinders me from running unity?

---

### Post by realzippy on 2011-08-21
can you post output from:

```
lspci | grep VGA
```

please?

---

