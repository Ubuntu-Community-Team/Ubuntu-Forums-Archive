---
title: "Trouble in installing Broadcomm drivers(Without Internet)"
date: 2014-04-02
forum: Networking &amp; Wireless
---

### Post by sathish2 on 2014-04-02
Hi,
I had bought a new Dell Vostro 2520 with default OS Ubuntu 12.04 . Few days back the I the WIFI has not detected , 
- So i just deactivate the broadcomm driver through the "System Settings->Additional Drivers" 
- Then try to activate it again.But its not activating
- Now there is no internet provision in my laptop.
- My Wifi is not detecting.
- LAN Cable is just detecting but i cant able to access internet in both way.
- I tested the Terminal command for any hardware interruption, every thing is fine.


How can i activate or install the Broadcomm again without internet ???????? or i want to completely reboot the system . Please give any suggestion.....

---

### Post by Hadaka on 2014-04-02
Hi, the additional drivers is incorrect for your computer
ignore the message to add it. lest see if we can get this
going for you. please open a terminal...ctrl/alt/t
then - this purges the incorrect driver-- please do
```
sudo modprobe -rf wl
sudo apt-get remove --purge bcmwl-kernel-source
 sudo rm /etc/modprobe.d/blacklist-bcm43.conf
```
boot
then do..```
sudo modprobe b44
```
you should now have a working wired connection
from the hopefully now working wired connection connected to the internet
please do..
```
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
boot...remove the wired connection..you should now have wireless

---

### Post by sathish2 on 2014-04-07
sudo modprobe -rf wl,,,,, for this command ,, the output is           "FATAL: Module wl not found"..
Now what can i do....

---

### Post by Hadaka on 2014-04-07
Hi, not a problem, copy and paste the rest of the commands
one at a time. Some may fail..that is ok, continue with all
commands untill done. Report back any problems.
thanks

---

