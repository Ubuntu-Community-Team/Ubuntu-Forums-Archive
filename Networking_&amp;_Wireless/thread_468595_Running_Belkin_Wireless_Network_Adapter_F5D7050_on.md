---
title: "Running Belkin Wireless Network Adapter F5D7050 on 7.04"
date: 2007-06-09
forum: Networking &amp; Wireless
---

### Post by skcll on 2007-06-09
Hello, I've been trying to get my wifi to work.  I'm located in an area with an unencrypted wireless network.  I know the ssid, and the card works beautifully in windows.  However, I cannot get the card to work.  First, the card was recognized as existing during the install of 7.04 (rausb0).  However, it could not find any networks, and I could not configure it.  So, I waited until the installation was complete.  After I booted into Ubuntu, I tried various manual configurations of both wireless connections (wmaster0 and rausb0).  This did not work.  So, I decided to use ndiswrapper around the driver from the card's cd.  I used the instructions from ubuntu help to install the windows drivers with ndiswrapper.  Here was the output:

****~$ sudo ndiswrapper -i ~/Desktop/rt2500usb.inf
Password:
installing rt2500usb ...
****:~$ ndiswrapper -l
rt2500usb : driver installed
        device (050D:7050) present (alternate driver: rt73usb)
****:~$ sudo depmod -a
****:~$ sudo modprobe ndiswrapper
****:~$ sudo ndiswrapper -m
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...
****:~$ ndiswrapper -l
rt2500usb : driver installed
        device (050D:7050) present (alternate driver: rt73usb)
****:~$ 

I saw no change in the system.  I proceeded to reboot.  Then I installed wifi-radar.  This did not recognize any networks either.  When I tried launching from the terminal, it repeatedly listed that wmaster0 could not be loaded or something similar.  I then tried blacklisting rt73usb, but this did not ameliorate the situation either.

What other alternatives do I have as a person who cannot access the internet?  Does Ubuntu 7.04 come with gcc compilers already installed?  If you guys suggest that I should proceed by another route, how would I go about undoing the damage I've already done?

Is wmaster0 (whatever it is) causing problems?  How do I get rid of it/deactivate it?

Thanks in advance for your help.

---

