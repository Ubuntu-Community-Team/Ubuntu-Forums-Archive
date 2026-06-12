---
title: "Virtualbox &quot;Failed to access the USB Subsystem&quot;"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by mr.big_gun on 2009-01-19
I am running Ubuntu 8.10 and i have virtualbox with xp sp3 as my machine. i am trying to use my webcam but i cant get my usb ports to pick up in xp. i have searched all around and i just cant get anything. i also dont know much about ubuntu. plzz i really need help. my mom wants to see me on webcam on yahoo messenger from a few states away. plzz help   and plz explain everything step by step because im new to ubuntu. i smart enough to work with though :P  thanks

---

### Post by x33a on 2009-01-19
first of all, are you sure your usb port is working.

if it is working, then you might not have configured virtualbox properly.

under the virtual machine's preferences you'll have to enable  usb support. after that install the proper webcam driver on the xp virtual machine, and hopefully everything will work out.

---

### Post by empty_spaces on 2009-01-19
Please follow the instructions for **Intrepid** in the link below.
[https://help.ubuntu.com/community/VirtualBox#USB](https://help.ubuntu.com/community/VirtualBox#USB)

---

### Post by anewguy on 2009-01-19
Try accessing it via "sudo ......".  With 8.04 and carried into 8.10 came changes to the way the USB permissions are handled in the udev permissions files.  Basically, some USB devices are being mounted as owned by root, and without root permissions you can't use them. If you can access it with sudo, then it is probably these permissions.  There are other posts in this forum for USB permissions in 8.04 and 8.10.  If sudo doesn't work, then we need to look further.

With your device plugged in, try lsusb from the command line and see if your device shows.  Then try sudo lsusb and compare the outputs.

I believe, though it's been a while, the changes are made in 40-basic-permissions.rules.  I had to do this for some specific USB equipment, and have noticed this has continued for other USB devices, including some USB cameras, flash drives, etc..

If you can't find those post by doing a search in these forums, post back and I'll try to refresh myself so I can help you further.

Dave :)

---

### Post by mr.big_gun on 2009-01-19
okay i did what you said and this is what i got



ubuntu@Ubuntu:~$ lsusb
Bus 002 Device 003: ID 0733:0430 ViewQuest Technologies, Inc. Intel Pro Share WebCam
Bus 002 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
ubuntu@Ubuntu:~$ sudo lsusb
[sudo] password for ubuntu: 
Bus 002 Device 003: ID 0733:0430 ViewQuest Technologies, Inc. Intel Pro Share WebCam
Bus 002 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
ubuntu@Ubuntu:~$ 




so yea my usb ports do work and it is picking up my camera      i have tried a few things to make it work and none of them worked but i am guessing it is because i and not used to using root or terminal yet but  i have been trying my *** of for like 4 days for this.

---

### Post by mr.big_gun on 2009-01-19
heyy empty_spaces   i just tried it and my xp still wont pick up any usb

---

### Post by mr.big_gun on 2009-01-19
is there a way i could completely erase all of the virtual box info so that when i install it i will start fresh   even in the settings and root scripts

---

### Post by b0b138 on 2009-01-19
Which version of vbox are you using? Is it the ose or puel one?

---

### Post by stderr on 2009-01-19
Did you make sure you switched to the closed source version as empty_spaces link states? You need the closed source edition of Virtualbox to get USB support. 

If you installed it from the repos, it'll be the open source edition, and you'll need to remove that package and download the closed source edition from the Virtualbox website. 

Another way is to add their repository to your sources list. There's instructions and downloads [here]("http://www.virtualbox.org/wiki/Linux_Downloads").

---

### Post by empty_spaces on 2009-01-19
If you did all the steps in the link I provided, you still need to set up device filters for each usb device that you want to use in virtualbox. To add a filter, make sure the device is plugged in, then start virtualbox (but don't boot the guest yet), and click on the usb option for your virtual machine to enable the usb controller and then add a filter.

---

### Post by diablo75 on 2009-01-20
1. In terminal, type:  sudo gedit /etc/fstab
   2. Paste the following text at the bottom of the fstab file:  ```
none /proc/bus/usb usbfs devgid=46,devmode=666 0 0
```
   3. Save the changes to the fstab file and close Gnome Text Editor.
   4. Reboot the PC.

---

### Post by mr.big_gun on 2009-01-20
i have virtualbox 2.1.0  the  one that is supposed to have usb support

---

### Post by diablo75 on 2009-01-20
> **mr.big_gun said:**
> i have virtualbox 2.1.0  the  one that is supposed to have usb support

Right, but you have to alter your fstab to grant Virtualbox permission to access your USB ports.  That was that line of text does.

---

### Post by mr.big_gun on 2009-01-20
Thankxxx everyone for your help
i finally got it working thanks to... Well i dont really know who   idk if it was a combination of the things i tried together idk but thanks for your effort     okay u! Diablo75  <<<<< your help   that last bit of info is what made it start working just now! Thank u   u r the ****!!!!!

---

### Post by diablo75 on 2009-01-20
Glad to help.  Check my sig out for more tips.  It's my blog.

---

### Post by quasi43 on 2009-01-20
hey, people.  noobie here. is there anything in unix that would be useful?  i do have a q regarding VM.  is there any specific type that the community is having more success with, vis-a-vis, non beta version xp pro studentVM in an ubuntu distro?  and if there is anything specific that the books are`nt saying about large system installs/maint? 1tb+

---

### Post by anewguy on 2009-01-20
> **diablo75 said:**
> 1. In terminal, type:  sudo gedit /etc/fstab
   2. Paste the following text at the bottom of the fstab file:  ```
none /proc/bus/usb usbfs devgid=46,devmode=666 0 0
```
   3. Save the changes to the fstab file and close Gnome Text Editor.
   4. Reboot the PC.

Exactly, and the change can be made in the udev permissions files, as I mentioned in my post, so that any or individual USB devices can be granted access by devmode or even by group or userid.  This can be helpful in the case of things like cameras or other USB devices that you may not want the world to access but control access instead.

Dave :)

---

