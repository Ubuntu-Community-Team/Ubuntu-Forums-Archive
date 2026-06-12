---
title: "desktop graphic problems"
date: 2011-05-08
forum: New to Ubuntu
---

### Post by toxictex on 2011-05-08
I am very new to ubuntu. Since upgrading from Maverick Meerkat to Natty Narwhal My desktop has been unusable. At login I chose Ubuntu classic as instructed when installing Natty Narwhal as my hardware wouldn't support the new desktop. At startup the desktop appears for a second and then disappears and I am left with the ubuntu startup screen with the usual desktop menus across the top. When I click on a menu  the submenu appears and a rectangular box slightly larger than the menu with the desktop visible in this box. If I select anything it flickers on and off and appears to be underneath the ubuntu startup screen as if it were a layer. Please help I am at a complete loss. Is there anything I can do? Could I reinstall Maverick Meerkat from a C.D.? Thank you.My computer is a Dell Dimension 1100 and has integrated Intel Extreme Graphics 2. I am dual booting with Windows XP, which is working normally.

i clicked on a card game it flickered but didn't come on, then I pressed shutdown and the game was visible behind the shutdown dialogue box but was not responding to mouse clicks but if I click shutdown that works.

---

### Post by Rubi1200 on 2011-05-09
Hi and welcome to the forums :-)

As you discovered, your hardware is probably unable to handle the requirements for Unity-3D.

See here for more:
[https://wiki.ubuntu.com/DesktopExperienceTeam/UnityHardwareRequirements](https://wiki.ubuntu.com/DesktopExperienceTeam/UnityHardwareRequirements)

However, you should consider installing and trying Unity-2D which seems, from my testing so far, to be up to the job with older Intel graphics cards.

But, if you have less than 1GB of RAM it could be an issue.

Unity-2D is available for download and installation from the official repositories, so either via Synaptic or Ubuntu Software Center.

Another thing I recommend you try to help resolve the problem is the following:

Open a terminal and paste in this command:

```
gksudo gedit /etc/X11/xorg.conf
```This requires root privileges, so enter your password when prompted. An empty file will then open.

Copy and paste the following into the empty file:

> Section "Device"
        Identifier      "Configured Video Device"
        Driver          "intel"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSectionSave the file and close. You may need to log out and in again to see any changes.

Okay, so what have you just done?

The default X configuration on 11.04 is set to use the fbdev driver. But, you need it to use the Intel driver. So, we create a configuration file that tells the system to use the driver for your chipset.

Let me know if this helps and whether you are successful with installing and using Unity-2D.

---

### Post by toxictex on 2011-05-09
I am using windows XP to access the forum so I can't copy and paste commands I will try to type commands into terminal if I can access it can you tell me how to do this please as my desktop is unusable. Would I be able to download unity 2D using windows and if so how? Thank you for taking the trouble to help me. another thought occurs to me if I bought a new graphics card would Natty Narwhal detect and install it automatically?

---

### Post by Rubi1200 on 2011-05-09
If/when you get to the desktop in Ubuntu start a terminal with Ctrl+Alt+T and then follow the commands. Perhaps write or print it out before you start but make sure it is exactly as given.

You cannot install software via Windows.

In almost all cases, Linux will autodetect new hardware when it is installed, so basically yes.

---

### Post by toxictex on 2011-05-09
I tried what you suggested which was difficult as the graphics kept going wrong. The graphics are still not right but I managed to open Firefox and it seemed to run properly for the first time. I will try to download and install Unity-2D. Are there any keyboard shortcuts I could use to download and install this file as it is extremely difficult to get the desktop menus to work.Could I download it in Windows and put on a usb drive and install in ubuntu from there? Thank you very much for your time

---

### Post by Rubi1200 on 2011-05-09
Just open a terminal again as before and run this command:

```
sudo apt-get install unity-2d
```

This requires that you enter your password. You won't see any visual feedback but just enter it and then Enter to start the command. All dependencies will be added too. When it is done, close the terminal and log out and back in again. 

You should then see Unity-2D as the default desktop environment when starting.

---

### Post by toxictex on 2011-05-09
I managed to download and install unity-2D but i am still having the same graphic problems, is there anything else I could try? How do I know what the default desktop environment is. Do you think buying and installing a new graphics card would solve this problem? Thank you for all the help you have given me.

---

### Post by Rubi1200 on 2011-05-10
When you start Ubuntu and get to the login screen you can click on your name. Before entering the password, change the desktop environment at the bottom of the screen. Unity-2d should be the default if you installed it, but you can also change to it on the menu there. Then enter the password and continue.

I am not sure what to tell you about another graphics card. It might work, it might not.

In any event, look at the hardware requirements for Unity before buying something:
[https://wiki.ubuntu.com/DesktopExperienceTeam/UnityHardwareRequirements](https://wiki.ubuntu.com/DesktopExperienceTeam/UnityHardwareRequirements)

I'll keep looking to see if I can find a solution for you in the meantime.

---

### Post by toxictex on 2011-05-10
I log in automatically but I logged out and when I logged in I chose unity-2D from the menu and it WORKED, I got the new interface (desktop). I haven't spent much time on the computer yet but I am very hopeful. Is there anyway I can make Unity-2D the default environment or can I change the way I log in so that I don't log in automatically i.e. I have to enter the password and I am able to choose Unity- 2D then. Thank you so much for all your help, I am very grateful.

 The next time I booted up Natty Narwhal it used the Unity-2D desktop environment and everything seems to be working perfectly, I think you have solved my problem thank you.

---

### Post by Rubi1200 on 2011-05-10
It's working? Excellent, that is really good news.

Please mark this thread Solved using the Thread Tools function near the top of the page if you are satisfied that the original problem has been resolved.

Enjoy :-)

---

### Post by toxictex on 2011-05-10
Will do and thanks again

---

