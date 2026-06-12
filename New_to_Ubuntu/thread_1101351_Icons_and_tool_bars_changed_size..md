---
title: "Icons and tool bars changed size."
date: 2009-03-20
forum: New to Ubuntu
---

### Post by gordon33 on 2009-03-20
Hello all

What happened to my screen's display? I am using a Ubuntu 7:10 for an
operating system.  Installed some updates yesterday.  Today the Icons on the desk top are larger then they were yesterday.  When I open the yahoo screen the screens display and tool bars are larger then it was.  Even by using ctrl+- leaves this text looking fuzzy.

When first loging on today it was going through the long check.  At about 95% I hit the escape key.  Nothing seemed to chang so I pushed the computers off button.  On restarting the computer it came up with a box saying a graphics card was not found of un recognizable.  Did i kill some thing.

The pre login screens, wallpaper, photos and other documents look normal.

Hope their is a simple solution.

Gordon33

---

### Post by ivanvajar on 2009-03-20
Does Ubuntu start normaly on restart?

---

### Post by gordon33 on 2009-03-20
Hello ivanvajar

Yes untill the screen switches to log in name.  Now the box where the user name goes is larger and the ubuntu brown/tan wallpaper is a little fuzzy.  The pass word screen is the same large box fussy wall.  other then that it works the same.

Gordon33

---

### Post by Therion on 2009-03-20
Sounds like an update borked your video driver.  You could try resetting your resolution under System/Preference/Display and/or checking for a restricted driver under System/Administration/Hardware.  Things are looking fuzzy because, I'm betting, you're running at 480x600 or 600x800.

What video card or chipset does your PC have, do you know?  If not post the output of ```
lspci
``` please.

As a last resort, you could try resetting your xorg.conf using the following:```
sudo dpkg-reconfigure -phigh xserver-xorg
```Since you're running Gutsy, that should prompt you to re-enter your monitor resolution.

---

### Post by ivanvajar on 2009-03-20
Can you change your screen resolution in System/Preferences/Screen Resolution?

---

### Post by gordon33 on 2009-03-20
Hello Therion, & Ivan Vajar

Therion
Could not find "Display" after System/Preference. (Please see responce to  Ivan Vajar below.)

Did the System/Administration/Hardware check.  After a few screens it said "The following resolution was detected for your display:

640 x 480 @ 61.0

Is this a good resolution for your display?"  All I have done is highlight the no button.  What should I do now?  If it ask me for a prefered resolution what should it be?

A friend helped me with finding the video card information with lspci.  "01:00.0 VGA compatible controller: nVidia Corporation GeForce 8300 GS (rev a1) I have a nVidia GeForce 8300 GS"

I will wait untill I hear back before I try the code:  
sudo dpkg-reconfigure -phigh xserver-xorg


Ivan Vajar
I have not been able to change my screen resolution in System/Preferences/Screen Resolution.  Their is a box that comes up with 640x480 with an arrow next to the box.  clicking the arro highlights the 640x480 but nothing changes when I type in diffrent numbers.  i will need to know what the screen resolutin should be.

Gordon33

---

### Post by ivanvajar on 2009-03-20
1024 x 768 is what you are looking for, I guess.

You might try detecting your monitor from Screen Resolution window. On several computers I was unable to get higher resolutions without detecting monitor.

nVidia should not make any problems. Look in System/Administration/Hardware drivers to see if proprietary driver is in use.

---

### Post by gordon33 on 2009-03-20
Hello Ivan Vajar

When the screen resolution screen is up I clicked on the "Detect Display" bar at the bottom of the screen.  No changes in the responce from the resolution box.... still stays at 640x480.

Checked System/Administration/Hardware drivers and found NVIDIA driver is NOT in use.  at the top of this screen is a log message that is titled "No Proprietary Drivers Are in Use On This System"


Gordon33

---

### Post by Therion on 2009-03-20
> **gordon33 said:**
> Checked System/Administration/Hardware drivers and found NVIDIA driver is NOT in use.
Do you see drivers LISTED in that menu though? If you do you should be able to click on them to activate one.  

If you *don't* see any nVidia drivers listed we'll need to take another approach.

---

### Post by gordon33 on 2009-03-20
Hello all  

Went to the terminal to run code: sudo dpkg-reconfigure -phigh xserver-xorg.  That cleared up the large tool bars and icons.  I Was then able to click System/Preferences/Screen Resolution and make the necceary changes.  Thank you Ivan Vajar and Therion.

The wife will be happy the computer screen looks good again.  

Gordon33

---

### Post by Therion on 2009-03-20
> **gordon33 said:**
> Went to the terminal to run code: sudo dpkg-reconfigure -phigh xserver-xorg.  That cleared up the large tool bars and icons. 
Excellent.  Glad that worked out for you.

---

### Post by ivanvajar on 2009-03-21
Great!

---

