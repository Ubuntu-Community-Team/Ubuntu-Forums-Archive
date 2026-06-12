---
title: "Help? i need to know where, or how to find drivers for Broadcom 802.11"
date: 2010-12-18
forum: New to Ubuntu
---

### Post by sKRiBEL on 2010-12-18
Well I'm brand new to Ubuntu and i need some serious help, but i think this might be a start, i have an emachines E625 laptop that has had its fair share of scrapes and bruises, today i just set up a multi-boot so that i have Ubuntu and Windows Vista, but anyway I'm getting off track. I'm looking for drivers for the item specified xD, I'm not too technically inclined, well not fully, but i have a few things down, but anyway i was wondering where to find the drivers. I tried to activate and download drivers earlier, but i had to re-install Ubuntu altogether because i couldn't connect to the Internet at all with Ubuntu afterwards, so any help with this beginner problem would be much appreciated. :]

---

### Post by sikander3786 on 2010-12-18
Welcome to the forums :-)

Can you connect to the internet using an ethernet cable? If yes, the appropriate drivers might just pop up under System > Administration> Hardware Drivers once you are connected to the internet.

---

### Post by sKRiBEL on 2010-12-18
> **sikander3786 said:**
> Welcome to the forums :-)

Can you connect to the internet using an ethernet cable? If yes, the appropriate drivers might just pop up under System > Administration> Hardware Drivers once you are connected to the internet.
Thanks :],

unfortunately not, i just use the wireless, and i dont have a spare ethernet cable around, but im not too worried right now, it will connect it just had the little install missing drivers icon at he tp, which kind of annoys me, but I will see if i can get my hands on an ethernet cable soon, but right now im just looking around to see if i can do it without.

---

### Post by sikander3786 on 2010-12-18
You can try installing them from your Ubuntu disc as mentioned here.

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

That is a bit old post but still should work with newer versions.

Ethernet method is the easiest one ;-)

Good Luck!

---

### Post by sKRiBEL on 2010-12-18
> **sikander3786 said:**
> You can try installing them from your Ubuntu disc as mentioned here.

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

That is a bit old post but still should work with newer versions.

Ethernet method is the easiest one ;-)

Good Luck!
i think i'll hold off for now then, i'll get the ethernet cable, thanks for the help :]

---

### Post by wep940 on 2010-12-18
When you get that cable and hook it up, do the following first before you look for a driver in System/Administration/Additional Drivers:
 
- open a terminal window (Applications/Accessories/Terminal)
 
- type:
 
sudo apt-get update <press enter>
 
- wait for that to finish, then close the terminal window
 
Now look in System/Administration/Additional Drivers for a driver for your wireless.

---

### Post by garvinrick4 on 2010-12-18
Here is a link that solved some broadcom driver problems in repositories.
[http://ubuntuforums.org/showthread.php?t=1597151](http://ubuntuforums.org/showthread.php?t=1597151)

---

### Post by coffeecat on 2010-12-18
@sKRiBEL, depending on your exact Broadcom wireless chipset you may need either the STA driver or the firmware plus b43 driver. This link:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

...tells you how to determine which is your wireless device and gives comprehensive instructions for installing the appropriate driver either using an ethernet cable connection or the Ubuntu install CD as sikander3786 suggests. 

Good luck!

---

