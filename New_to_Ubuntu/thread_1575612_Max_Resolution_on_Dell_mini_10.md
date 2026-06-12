---
title: "Max Resolution on Dell mini 10"
date: 2010-09-16
forum: New to Ubuntu
---

### Post by 2die4uk on 2010-09-16
Hi I decided that i was going to try out Ubuntu on my netbook as i had once tried to install it on my ps3 i have never used linux prior to trying to install it on my ps3 and never really got anything to work other then boot it up and browse a little with firefox and so wanted to see how good it was on a netbook.

I installed ubuntu 10.4 onto my dell mini 10 and used a distro that already had the drivers for the gma500 and the max resolution that i get is 1024x576 i can not take it to the max resolution that the laptop can do 

I was wondering if theirs anyway i can take it up to the max resolution i have googled alot and used the ubuntu google to try and fix the resolution but i cant figure out what i have to do or if i can make the gpu do the max resolution under ubuntu if it is at all possible.

Poulsbo driver is already installed with the 2d and 3d on i just want the 720p resolution and then i think i will be able to migrate from windows to ubuntu using this netbook as a stop over learning tool

Thanks alot guys i have already looked around alot and i dont understand some of the terms and what

deb http:// etc stuff is so thanks again

---

### Post by Acheron3 on 2010-09-16
Hey, I can't figure out why you are unable to get an higher resolution but it could be due to the driver. Is the driver in your computer a open-source driver? If so try to uninstall it and installing the proprietary driver. If it works try to send the bug to the free driver developers!
Hope it helps!

---

### Post by mikewhatever on 2010-09-16
Some of the Dell minis are equipped with screens that have the max resolution of 1024x576. If you want to go higher, an external screen would be required, but as HDMI output doesn't work with the current poulsbo driver available for 10.04, that's out of the question for now.

---

### Post by 2die4uk on 2010-09-16
thanks but mine can do the full 720p as thats what it was when it was on windows xp and how do i update the drivers to work with the full resolution are their terminal commands or should i use the synaptic package manager

---

### Post by snowpine on 2010-09-16
Here is the definitive source of information for GMA500 support in Ubuntu:

[http://ubuntuforums.org/showthread.php?t=1229345](http://ubuntuforums.org/showthread.php?t=1229345)

If your physical screen resolution is 1024x576 then Ubuntu cannot make it go higher.

---

### Post by 2die4uk on 2010-09-16
> **snowpine said:**
> Here is the definitive source of information for GMA500 support in Ubuntu:

[http://ubuntuforums.org/showthread.php?t=1229345](http://ubuntuforums.org/showthread.php?t=1229345)

If your physical screen resolution is 1024x576 then Ubuntu cannot make it go higher.

[COLOR=Red]Thanks for that i have managed to get to this part undernethath also when i try to save the file it says i do not have permission yet i am the only account[/COLOR]

Once rebooted open a terminal and make a back up of your xorg.conf  file.(fresh install may have a null xorg.conf file this is normal and  ok)

 	Code:
 	sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak 
[COLOR=Red]When i try to add the contents below and save it wont let me the permissions problem but i made the back up no problem[/COLOR]

Open up your xorg.conf and add the below contents inside it.
 	Code:
 	sudo nano /etc/X11/xorg.conf 
Make the Section "Device" Look like this :

 	Code:
 	Section "Device"
        Identifier      "Configured Video Device"
        Option "AccelMethod" "EXA"
        Option "MigrationHeuristic" "greedy"
EndSection

---

### Post by mikewhatever on 2010-09-17
> **2die4uk said:**
> ...

Open up your xorg.conf and add the below contents inside it.
 	Code:
 	sudo nano /etc/X11/xorg.conf 
Make the Section "Device" Look like this :

 	Code:
 	Section "Device"
        Identifier      "Configured Video Device"
        Option "AccelMethod" "EXA"
        Option "MigrationHeuristic" "greedy"
EndSection

The **sudo nano ...** command should open the file you want to edit with the right permissions, however, I rather doubt any of those options will give you 720p resolution, whatever that is. I've read about dell minis with the 1366x768 resolution, but wouldn't be surprised if the psb driver for Linux didn't support it.

---

