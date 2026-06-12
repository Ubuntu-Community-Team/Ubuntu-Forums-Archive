---
title: "its back, Icons and tool bars changed size."
date: 2009-04-17
forum: New to Ubuntu
---

### Post by gordon33 on 2009-04-17
hello all

My previous post for this problem can be sween at:  [http://ubuntuforums.org/showthread.php?t=1101351](http://ubuntuforums.org/showthread.php?t=1101351)



What happened to my start up, and screen's display? 

I am using a Ubuntu 7:10 for an operating system. The Icons on the desk top are larger then they were. When I open the yahoo screen the screens display and tool bars are larger then it was. Even by using ctrl+- leaves this text looking fuzzy.

This started after loging on once in December, it was going through the long check. At about 95% I hit the escape key. Nothing seemed to chang so I pushed the computers off button. On restarting the computer it came up with a box saying a graphics card was not found of un recognizable. at that time the pre login screens, wallpaper, photos and other documents look normal.  


Then I went to the terminal and typed in code: 
sudo dpkg-reconfigure -phigh xserver-xorg
At that time the above code did the trick.  

Now even after typing in the above code the screen's size is still diffrent.  In addition 10 percent of the left side of the screen was cut off.  Also, when trying to turn the computer on boot up takes along time and the screans will have vertical lines.  

So I went back to the post mentioned above to reread the responces.  When I came to the responce by Therion "Do you see drivers LISTED in that menu though? If you do you should be able to click on them to activate one."  I activated "NVIDIA.  The vertical lines went away, the screen went back to cented when I reset the moniter to defalt settings. but the system still takes 2 or 3 trys to get it started.  The screens size is still diffrent.  When try to change the screens resolution to 1024 X 768 no resolutions higher then 640 x 480 are advalible for selection.

Thank you for any sugestions on what to do ro check next.

Gordon33

---

### Post by gordon33 on 2009-04-18
hello

Can the resolution be changed to 1024 X 768 with "NVIDIA" activated?

After having problems with the look of the display" I activated "NVIDIA" from "Hardware Drivers".
After that I try to change the screens resolution to 1024 X 768 no resolutions higher then 640 x 480 were advalible for selection.

My previous post for related problem can be seen at: 
[http://ubuntuforums.org/showthread.php?t=1101351](http://ubuntuforums.org/showthread.php?t=1101351)
and,  
[http://ubuntuforums.org/showthread.php?p=7090983#post7090983](http://ubuntuforums.org/showthread.php?p=7090983#post7090983)

gordon33

---

### Post by overdrank on 2009-04-18
Hi and threads merged. Have you tried using the nvidia-settings to adjust the resolution
```
gksu nvidia-settings
```
Also with that new of the graphics card nVidia GeForce 8300
You may want to try and install the drivers from nvidia. As 7.10 will be reaching the end of life soon :(

---

### Post by gordon33 on 2009-04-18
Hello Overdrank

I tried the code but nothing came back asking for a new resolution.  I guess it is odvious I have limited computer know how.

gordon33

---

### Post by overdrank on 2009-04-18
> **gordon33 said:**
> Hello Overdrank

I tried the code but nothing came back asking for a new resolution.  I guess it is odvious I have limited computer know how.

gordon33

Ok Its been a bit since I seen 7.10. Try and install nvidia-settings.
If you have the nvidia drivers installed. You may use the terminal or synaptic manager. In the terminal you can try ```
sudo apt-get install nvidia-settings
```

---

### Post by gordon33 on 2009-04-18
Hello overdrank

This is what happened when the last code was entered:'

gordon@dell:~$ sudo apt-get install nvidia-settings
[sudo] password for gordon: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  oem-config-gtk libdns32 linux-backports-modules-2.6.22-14-generic
  oem-config libisc32
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  nvidia-settings
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 679kB of archives.
After this operation, 1503kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe nvidia-settings 1.0+20080304-0ubuntu1.1 [679kB]
Fetched 679kB in 3s (192kB/s)           
Selecting previously deselected package nvidia-settings.
(Reading database ... 263400 files and directories currently installed.)
Unpacking nvidia-settings (from .../nvidia-settings_1.0+20080304-0ubuntu1.1_i386.deb) ...
Setting up nvidia-settings (1.0+20080304-0ubuntu1.1) ...

gordon@dell:~$

---

### Post by overdrank on 2009-04-18
Ok now try the command using the alt, F2 keys
```
gksu nvidia-settings
```
And adjust your resolution

---

### Post by gordon33 on 2009-04-18
Hello overdrank

I was able to get the green Nvidia screen ( with Alt F2 amd the code: gksu nvidia-settings) but could not find a spot to change the resolution.  

Also When booting up the vertical lines are back.  The Vertical lines is becoming an intermiten problem for the last 3 days.

Gordon33

---

### Post by overdrank on 2009-04-18
> **gordon33 said:**
> Hello overdrank

I was able to get the green Nvidia screen ( with Alt F2 amd the code: gksu nvidia-settings) but could not find a spot to change the resolution.  

Also When booting up the vertical lines are back.  The Vertical lines is becoming an intermiten problem for the last 3 days.

Gordon33

Hi and in the nvidia settings you will see a list on the left side and the second one down is X server display. Click on it and there you can adjust the resolution. Then click the apply button, see screen shot attached screen shot.

---

### Post by gordon33 on 2009-04-18
Hello

When opening the Nvidia screen the box for changing the screen resolution is out of sight because the screen is large and can not be moved up far enought.

Gordon33

---

### Post by overdrank on 2009-04-18
> **gordon33 said:**
> Hello

When opening the Nvidia screen the box for changing the screen resolution is out of sight because the screen is large and can not be moved up far enought.

Gordon33

Ok using the alt key and then single click and hold with the mouse you should be able to move the nvidia screen where you can use the apply button.

---

### Post by gordon33 on 2009-04-27
Thank you 

I happly installed the ASUS EAH3450/DI/256M Radeon HD 3450 GDDR2 PCI-E Video Card.  The screen looks great.  

The card came with a disk to help the new card's instalation.  BUT, Ubuntu did all the work by its self.  Ubuntu was even kind enough to tell me to shut down and restart the computer.  

Thank you all for your help.

Gordon33

---

