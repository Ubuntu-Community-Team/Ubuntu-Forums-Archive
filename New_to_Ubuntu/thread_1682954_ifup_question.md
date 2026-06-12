---
title: "ifup question"
date: 2011-02-06
forum: New to Ubuntu
---

### Post by smarmytime on 2011-02-06
I'm trying to start the wireless internet connection on my laptop. It works just fine, but sometimes I'll run a tethering program to use my cell phones internet connection. When I get home, I want to switch back to my home wifi connection, which I want to start from the command line (logging out and back in works, but I want to understand how to do this). I try to use sudo ifup wlan0, but it gives me the following output:

Ignoring unknown interface wlan0=wlan0.

What am I doing wrong?

---

### Post by Brandon Williams on 2011-02-07
If logging out and back in works, then you probably aren't using ifup/down to manage your interfaces ... at least not wlan0. You're most likely using network manager, so the following questions/suggestions are based on that assumption.

What do you do (if anything) to turn of the wifi nic when you start the tethering program? If you click on the network manager icon in the status tray, do you see the local wifi network's ssid listed? If not, right-click on the network manager icon and make sure that "enable wireless" is checked.

---

### Post by smarmytime on 2011-02-07
> **Brandon Williams said:**
> If logging out and back in works, then you probably aren't using ifup/down to manage your interfaces ... at least not wlan0. You're most likely using network manager, so the following questions/suggestions are based on that assumption.

What do you do (if anything) to turn of the wifi nic when you start the tethering program? If you click on the network manager icon in the status tray, do you see the local wifi network's ssid listed? If not, right-click on the network manager icon and make sure that "enable wireless" is checked.

What I do is I run two commands, the following in one terminal:

easytether connect

Which then tells me to run the following in another terminal:

sudo dhclient easytether0

So you're right, I'm not using ifdown to turn off the wifi, but I didn't realize that the one was related to the other. Would the proper command then be:

sudo dhclient wlan0?

Without the ?, obviously ;-)

When I run the dhclient command, it does give me some output...I can run it, and cut and paste the output, if that would help.

---

### Post by Brandon Williams on 2011-02-08
Ordinarily your wifi interface would be managed by network-manager. Is network-manager running on your system? And if so, please check the things that I suggested checking previously (left-click and right-click popups from the network manager icon).

---

