---
title: "Need help reinstalling default video drivers..."
date: 2010-05-04
forum: New to Ubuntu
---

### Post by TheMustangZone on 2010-05-04
I recently installed the ATI Catalyst Control Center from the applications menu, but soon found out it wiped out my video completely.  I booted up into recovery mode and used these commands in the root shell to get my login screen back:
> apt-get remove --purge xorg-driver-fglrx
apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri
dpkg-reconfigure xserver-xorgThis allowed me to see my login screen and get back into Ubuntu.  However, now my video is very choppy and slow.  I just want to get back to what I had before installing that stupid Control Center.  Is this possible?  I've been searching and searching the forums trying to find a sticky thread or a common consensus on how to make an ATI video card work, but I just keep getting more confused.  What IS the best setup for using 2D?  Thanks so much.

Rob

---

### Post by 3rdalbum on 2010-05-04
Yes, simply remove the file "/etc/X11/xorg.conf".

---

### Post by TheMustangZone on 2010-05-04
> **3rdalbum said:**
> Yes, simply remove the file "/etc/X11/xorg.conf".
 
Thanks for the reply, but may I ask, how do I do this? Would I do it through the terminal like this:
```
sudo apt-get remove /etc/x11/xorg.conf
```
Thanks again.

---

### Post by GSF1200S on 2010-05-04
> **TheMustangZone said:**
> Thanks for the reply, but may I ask, how do I do this? Would I do it through the terminal like this:
```
sudo apt-get remove /etc/x11/xorg.conf
```
Thanks again.

No, apt-get remove tells the APT package manager to remove a package (a package like firefox, for example), where as he told you to delete a file ;) To do what he said, simply run:
```
sudo rm /etc/X11/xorg.conf
```
That command basically means (in order) the following:
superuserdo remove (file located at)/etc/X11/xorg.conf

After doing this, restart X with the following command:
```
sudo /etc/init.d/gdm restart
```

---

### Post by TheMustangZone on 2010-05-04
> **GSF1200S said:**
> No, apt-get remove tells the APT package manager to remove a package (a package like firefox, for example), where as he told you to delete a file ;) To do what he said, simply run:
```
sudo rm /etc/X11/xorg.conf
```
That command basically means (in order) the following:
superuserdo remove (file located at)/etc/X11/xorg.conf
 
After doing this, restart X with the following command:
```
sudo /etc/init.d/gdm restart
```
 
 
Thanks so much.  Willl I need to install anything else after doing this?

---

### Post by GSF1200S on 2010-05-04
> **TheMustangZone said:**
> Thanks so much.  Willl I need to install anything else after doing this?

**EDIT** WAIT. Are you still running 9.04, or have you upgraded to 10.04? If your on 10.04, youre fine. If you are on 9.04, please invoke the following command BEFORE you restart X:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

You should be good to go.. In terms of getting appropriate 2D support, Im not the best guy to ask- I have no experience with ATI cards. Hopefully an ATI user can chime in with any suggestions.

But your desktop should load up no issues :)

---

### Post by TheMustangZone on 2010-05-04
> **GSF1200S said:**
> **EDIT** WAIT. Are you still running 9.04, or have you upgraded to 10.04? If your on 10.04, youre fine. If you are on 9.04, please invoke the following command BEFORE you restart X:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
 
You should be good to go.. In terms of getting appropriate 2D support, Im not the best guy to ask- I have no experience with ATI cards. Hopefully an ATI user can chime in with any suggestions.
 
But your desktop should load up no issues :)
 
 
As usual, you guys are awesome.  Thanks!!! :D

---

