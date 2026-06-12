---
title: "Wireless is disabled"
date: 2010-09-08
forum: New to Ubuntu
---

### Post by bharesc on 2010-09-08
On upgrading from Ubuntu 9 to 10 the wireless network stopped working. The computer is a Medion MD 96290 and the USB wireless card is a RTL8187B. Running ndisgtk indicates that driver "net8187b" is installed and that the hardware is present. 
Running "ndiswrapper -l" returns
bobharesceugh@ubuntu:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.save.1, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
net8187b : driver installed
    device (0BDA:8189) present (alternate driver: rtl8187)
The wireless button above the keyboard is inoperative.
I have spent days trying to resolve this problem using the many forums available but with no success.[IMG]file:///tmp/moz-screenshot.png[/IMG]

---

### Post by NightwishFan on 2010-09-08
Please be more specific. In the network manager does it say "Wireless Is Disabled"? Does it detect networks and just not connect, or does no network card show up?

If it says "Wireless Disabled" right click on the network manager icon in the panel, and check enable networking and enable wireless.

---

### Post by raysfan81 on 2010-09-08
> **NightwishFan said:**
> Please be more specific. In the network manager does it say "Wireless Is Disabled"? Does it detect networks and just not connect, or does no network card show up?

If it says "Wireless Disabled" right click on the network manager icon in the panel, and check enable networking and enable wireless.

If that doesn't work and no networks are available then go to system ->administration ->hardware drivers

Make sure the wireless card driver is enabled.  If it is and it still doesn't work click remove and then enable it again that should solve your problem.

In the future it would be easier for us to help you if you were more specific about your problem.

---

### Post by bharesc on 2010-09-09
Thanks for your replies and sorry for being vague. In Network Manager Wireless Network is greyed out as is "Wireless is disabled". Right clicking wireless network reveals a greyed out "Enable Network" which won't respond.
In hardware drivers the only one shown is a "Software Modem" and this is activated and currently in use.
Bob

---

### Post by seventhsamurai on 2010-09-09
Connect to the internet using a LAN cable.

Go to system>>administration>>hardware drivers.

Search for available drivers. If your networking hardware is connected, it should throw up some options. Try installing them. One of them should get your wireless card detected and working.

---

### Post by JohnHeikkila on 2010-09-09
You tried "sudo ifconfig wlan0 up"?
Try suspending or putting your PC to hibernate and then resuming. That usually fixes that when it happens to me.

---

### Post by bharesc on 2010-09-09
With laptop connected to the internet the only driver shown under hardware drivers is the software modem, so nothing to install.
Tried running, "sudo ifconfig wlan0 up" with following result: -
bobharesceugh@ubuntu:~$ sudo ifconfig wlan0 up
[sudo] password for bobharesceugh: 
SIOCSIFFLAGS: Unknown error 132
bobharesceugh@ubuntu:~$ 
How can i check if the correct driver is installed? Running Ndiswrapper -l indicates a driver installed. Is this the correct one?
net8187b : driver installed
    device (0BDA:8189) present (alternate driver: rtl8187)
I have copied the windows drivers and installed these as instructed in the ndiswrapper information. What can i run in terminal to check the system?
Any other thoughts?

---

### Post by Silent Warrior on 2010-09-09
I think I have the same wireless-thing, actually - and I have it working just fine and dandy. What happens if you throw this at the terminal:
```
sudo modprobe rtl8187
```
(I think modprobe assumes the -i, but if that gives you a funny message - you SHOULD receive nothing at all - just replace modprobe with modprobe -i.)
lsmod | grep rtl8187 will tell you if you managed to activate the driver.

---

### Post by bharesc on 2010-09-09
bobharesceugh@ubuntu:~$ sudo modprobe rtl8187
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.save.1, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
bobharesceugh@ubuntu:~$ 

bobharesceugh@ubuntu:~$ sudo modprobe -i rtl8187
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.save.1, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
bobharesceugh@ubuntu:~$ 


bobharesceugh@ubuntu:~$ lsmod | grep rtl8187
rtl8187                50680  0 
mac80211              205146  1 rtl8187
cfg80211              126517  2 rtl8187,mac80211
eeprom_93cx6            1333  1 rtl8187
led_class               2864  2 rtl8187,sdhci
bobharesceugh@ubuntu:~$ 

These are the outputs to your suggestions. Any clues?

Bob

---

### Post by inkrypted on 2010-09-09
The network manager has been horrible at managing wireless for my customers most of the time. My suggestion is try a different network manager like WICD. It is available in the universe repository but if you need the deb you can get it here. [http://packages.ubuntu.com/jaunty/all/wicd/download](http://packages.ubuntu.com/jaunty/all/wicd/download). Best of luck.

---

### Post by bharesc on 2010-09-09
WICD tells me there are "no wireless networks found". Works ok with Windows.
Bob

---

### Post by NightwishFan on 2010-09-09
Wicd does not enable wireless by default. Go into preferences, it will be blank, and make the wireless network: wlan0

---

### Post by inkrypted on 2010-09-09
How to at bottom of this page [http://wicd.sourceforge.net/moinmoin/Wicd%20on%20Ubuntu](http://wicd.sourceforge.net/moinmoin/Wicd%20on%20Ubuntu).

---

### Post by bharesc on 2010-09-09
In WICD preferences Wireless Interface is already wlan0.
WICD indicates that there are "no wireless networks found". and therefore i can't get beyond step 1 of inkrypted's URL. There are wireless networks out there and they are not hidden, at least to Windows.

I guess i need: -
1. A wireless card
2. The relevant driver installed
3. The card to be switched on

I know i have the card.
I don't know whether i have the correct driver installed and talking to the card, and
I don't know whether the card is switched on. In Windows this has to be done physically with a switch above the keyboard and it is illuminated. In Ubuntu this switch is ineffective.

How can i check that the correct driver is installed and that it is talking to the wireless card?
How can i check that the card is switched on?

Bob

---

### Post by bharesc on 2010-09-09
Should i post this thread in Networks and Wireless?

---

