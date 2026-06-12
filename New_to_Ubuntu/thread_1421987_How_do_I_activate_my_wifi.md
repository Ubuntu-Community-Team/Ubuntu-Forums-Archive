---
title: "How do I activate my wifi?"
date: 2010-03-04
forum: New to Ubuntu
---

### Post by daveritah on 2010-03-04
Can someone please direct me to where I can information on how to install my wifi on Ubuntu 9.10. I have a Dell Inspiron 1501 with a dual boot, and Ubuntu is on a seperate partition. I was told to use the "Sudo apt-get install b43-fwcutter" command, and my system says it is not there. I went into the drivers section of my Ubuntu and it says there is nothing in there either. I have Broadcomm for my wireless. My other half is Windows XP on the dual boot. - Dave

---

### Post by drpjkurian on 2010-03-04
Hi
Please right click on the network manager icon which is at right corner of top panel in dektop.
In the dropdown you will get an option of wireless. click it and set the settings

---

### Post by undecim on 2010-03-04
Before you can install any additional packages, you will need to update your package list. Connect to the internet via an ethernet cable if possible. Then go to the update manager in System -> Administration -> Update Manager

When you see a list of updates, that means your package list has been updated. You don't have to install all these updates just yet, instead install your Wireless drivers either with apt-get or the Hardware Drivers dialog, reboot, and you should be able to use wireless.

---

### Post by albert s on 2010-03-05
hi, on my dell inspiron after I hard wired to the internet and installed the auto updates my wi-fi was working fine, didnt work before the updates though.
ubuntu 9.10

---

### Post by nothingspecial on 2010-03-05
> **daveritah said:**
> Can someone please direct me to where I can information on how to install my wifi on Ubuntu 9.10. I have a Dell Inspiron 1501 with a dual boot, and Ubuntu is on a seperate partition. I was told to use the "Sudo apt-get install b43-fwcutter" command, and my system says it is not there. I went into the drivers section of my Ubuntu and it says there is nothing in there either. I have Broadcomm for my wireless. My other half is Windows XP on the dual boot. - Dave

The reason the system says b43-fwcutter is not there is because it is not connected to the internet. Plug it in with a cable until you have installed it.

---

### Post by daveritah on 2010-03-05
how do I update the system, when if I have no physical line to the net. I am on a wireless with a neighbors hi-speed router. Presently, I only have access to the net  through my Windows XP. - Dave

---

### Post by alexcckll on 2010-03-05
Umm - maybe pop round to your neighbour's, and ask if you can connect wired for an hour or so?

---

### Post by ublintu on 2010-03-05
Hi,
If you don't have internet connection you can install it from the CD 
Check here the CD section:
[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)
and here the same, just CD, clear: [http://ubuntuforums.org/showthread.php?t=1288865](http://ubuntuforums.org/showthread.php?t=1288865)
After reboot I had internet.

---

### Post by daveritah on 2010-03-05
Problem resolved-Thanks for information - Dave

---

