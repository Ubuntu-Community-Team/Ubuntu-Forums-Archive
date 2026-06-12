---
title: "Wireless stopped working after a software update"
date: 2011-04-06
forum: New to Ubuntu
---

### Post by eeprom on 2011-04-06
[SIZE=2]Hello,
I just set up my new wireless connection, and all was working well. The I decided to install all the updates from the software manager.  Now the wireless connection doesn't work.  I'd like to know where I can go in the system to find "view available wireless networks" or something similar.  Can someone tell me how to get to that service?

thanks,
EE
[/SIZE]

---

### Post by Finnius on 2011-04-07
There should be a wireless connection icon on the top bar...

If not you can always connect to a wireless network manually...

Try:

```
iwconfig
```

To see if your wireless card is still showing up, and to get its name (if you don't already know it).

To connect to a wireless network command line style:

```
sudo ifconfig ath0 down
sudo iwconfig ath0 mode managed essid "MYNETWORK"
sudo ifconfig ath0 up
sudo dhclient ath0
```

Where "ath0" is the name of your wireless card we got earlier, and "MYNETWORK" is the name of your wireless network.

Not sure if this is what you were chasing...But hope it helps
Post back with the results if this is not the problem.

---

### Post by wep940 on 2011-04-07
And....the updates probably included a kernel update, so if you used ndiswrapper/ndigtk to install the driver, or had to compile it yourself,
you'll most likely need to repeat those steps for the new kernel.

---

### Post by garvinrick4 on 2011-04-07
What did you upgrade and or install.
```
gedit /var/log/apt/history.log
```If it is a long highlight all and hit the # sign in upper right of message box.

---

### Post by garvinrick4 on 2011-04-07
```
sudo lshw -C network > network.txt
```
Will put a file Network.txt in /home post it so users can see.

---

### Post by eeprom on 2011-04-07
It's been a while since I've been online, so I installed quite a bit.  How would I re-install a kernel manually?

EE


Install Log.

Start-Date: 2011-04-06  21:01:19
Install: linux-image-2.6.35-28-generic:i386 (2.6.35-28.49), linux-headers-2.6.35-28:i386 (2.6.35-28.49), linux-headers-2.6.35-28-generic:i386 (2.6.35-28.49)
Upgrade: ubuntuone-client:i386 (1.4.5-0ubuntu1, 1.4.6-0ubuntu2), linux-headers-generic:i386 (2.6.35.27.35, 2.6.35.28.36), xulrunner-1.9.2:i386 (1.9.2.15+build1+nobinonly-0ubuntu0.10.10.1, 1.9.2.16+build1+nobinonly-0ubuntu0.10.10.1), libdbus-1-3:i386 (1.4.0-0ubuntu1.1, 1.4.0-0ubuntu1.2), linux-image-generic:i386 (2.6.35.27.35, 2.6.35.28.36), gnome-screensaver:i386 (2.30.0-1ubuntu1, 2.30.0-1ubuntu1.1), linux-libc-dev:i386 (2.6.35-1027.48, 2.6.35-1028.49), ubuntuone-client-gnome:i386 (1.4.5-0ubuntu1, 1.4.6-0ubuntu2), software-center:i386 (3.0.7, 3.0.8), libsyncdaemon-1.0-1:i386 (1.4.5-0ubuntu1, 1.4.6-0ubuntu2), dbus:i386 (1.4.0-0ubuntu1.1, 1.4.0-0ubuntu1.2), firefox:i386 (3.6.15+build1+nobinonly-0ubuntu0.10.10.1, 3.6.16+build1+nobinonly-0ubuntu0.10.10.1), tzdata-java:i386 (2011c-0ubuntu0.10.10, 2011e-0ubuntu0.10.10), flashplugin-installer:i386 (10.2.152.27ubuntu0.10.10.1, 10.2.153.1ubuntu0.10.10.1), firefox-gnome-support:i386 (3.6.15+build1+nobinonly-0ubuntu0.10.10.1, 3.6.16+build1+nobinonly-0ubuntu0.10.10.1), tzdata:i386 (2011c-0ubuntu0.10.10, 2011e-0ubuntu0.10.10), firefox-branding:i386 (3.6.15+build1+nobinonly-0ubuntu0.10.10.1, 3.6.16+build1+nobinonly-0ubuntu0.10.10.1), python-ubuntuone-client:i386 (1.4.5-0ubuntu1, 1.4.6-0ubuntu2), dbus-x11:i386 (1.4.0-0ubuntu1.1, 1.4.0-0ubuntu1.2), transmission-common:i386 (2.04-0ubuntu2, 2.05-0ubuntu0.2), linux-generic:i386 (2.6.35.27.35, 2.6.35.28.36), linux-firmware:i386 (1.38.4, 1.38.5), transmission-gtk:i386 (2.04-0ubuntu2, 2.05-0ubuntu0.2)

---

### Post by Hippytaff on 2011-04-07
If you download and run the script found in the link below and post the wireless-results.txt in code tags by highlighting the text and clicking the # button) it will provide all the information needed to help troubleshoot your problem, though it looks as though you just need to reinstall the driver as already suggested.

---

### Post by eeprom on 2011-04-07
How do I reinstall, and what do I reinstall?  The problem is that I used the software manager to add all updates.  I don't really know what was updated and where it was updated from.  Is there a way to repeat the process?  If so, please tell me how.

thanks, 
EE

---

### Post by philinux on 2011-04-07
> **eeprom said:**
> How do I reinstall, and what do I reinstall?  The problem is that I used the software manager to add all updates.  I don't really know what was updated and where it was updated from.  Is there a way to repeat the process?  If so, please tell me how.

thanks, 
EE

One thing to try, is to boot the previous kernel from grub and see if wireless works.

And please post the results of hippytaff's script.

---

### Post by eeprom on 2011-04-07
Can you please explain how to boot from previous kernel?

thanks,
EE

---

### Post by Hippytaff on 2011-04-07
If your dual booting, at the bit where you get the option to choose OS, there should be other ubuntu options. Usually the previous one is the third on the list. Of your not dual booting press shift at boot to enter the menu where you can choose the third on the list :-)

---

### Post by eeprom on 2011-04-08
[SIZE=2]This morning I booted up and I got a message that a recent update did not complete.  I allowed the update to complete and the problem is gone.  Everything works normally again.  That was odd.

Thanks for the help
EE
[/SIZE]

---

### Post by Hippytaff on 2011-04-08
very odd..funky in fact...

Glad it's sorted :-)

remember to mark the thread as solved in te thread tools at the top of the page ;-)

---

