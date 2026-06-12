---
title: "Another Wireless Card Installation Problem."
date: 2009-09-20
forum: New to Ubuntu
---

### Post by Zeradin on 2009-09-20
Hello,

I wanted to start  using linux and I'm very excited about Ubuntu, but I've done a bunch of searching and I can't figure out how to install my wireless card and that prevents me from moving forward because I have to switch back and forth between windows and linux constantly trying to get it to work.

I guess I have a broadcom 802.11a/b/g That's all I can get for the model number. I tried just copying over the driver but also every time I try to install the ndisgtk program it says dependency not met on the ndiswrapper-utils, but I do have it installed. Please help!

---

### Post by seshomaru samma on 2009-09-20
to know what card you have run th ecommand 
```
lspci
```
it will list your hardware

what version of ubuntu are you using and where did you get ndisgtk from?

---

### Post by DrScum on 2009-09-20
after you know which card you have (see answer above) go to this link
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)
and see if your card is supported. Chances are that you don't need ndiswrap and that it works "out of the box". Do you have the latest Ubuntu release by the way? If not upgrading might solve your problem as well.

---

### Post by Zeradin on 2009-09-20
I am using Ubuntu 9.04

I am using ndisgtk_0.6 I got it from here: [http://packages.ubuntu.com/dapper/ndisgtk](http://packages.ubuntu.com/dapper/ndisgtk)

My wireless card is  Broadcom Corporation BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver (rev 02)

I'm very confused about what that page says about my driver... it kind of looks like it's not supported? But it's listed a bunch of times.

---

### Post by DrScum on 2009-09-20
My take from the Hardware Support Community page is that starting 8.04 your card is supported unless you have a 4306 chipset. In order to make it work you'll have to activate restricted drivers (System > Administration > hardware drivers).

Hope this helps.

---

### Post by Zeradin on 2009-09-20
So I went to this page:

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

everything went well until

#modprobe lib80211

because the file doesn't exist. Did I miss something?

---

### Post by DrScum on 2009-09-20
Sorry, I can't help you with command line details. I'm one of those GUI corrupted mouse clicking former Redwood deciples. But from what I read in the hardware support list your card is supported in Ubuntu 9.04. Maybe you want to uninstall ndiswrapper and completely reconfigure your WLAN card using the restricted driver.

---

### Post by Zeradin on 2009-09-20
Fair enough. I went to enable restricted drivers as you said but there were no proprietary drivers installed and so there was no option when I went to hardware drivers.

I'm trying to stay positive that linux will be good but it's hard when I have to try for three days to get online.

---

### Post by DrScum on 2009-09-20
Did it say there were no proprietary drivers installed or did it say there were no proprietary drivers in use?

In the former case the driver isn't installed, in the latter case your card isn't recognized correctly.

But as I said, I am not enough of an expert on this to really help you diagnose the problem.
Sorry

---

### Post by Zeradin on 2009-09-20
I think it said in use actually, but there were no options in the window.

---

### Post by DrScum on 2009-09-21
Well, I'm sorry that I can't help you further. Try to get someone in the Networking and Wireless section of this forum interested. Post an new catchy thread.

From my experience it might also be an option for you to just do a fresh install in case you didn't tweak the actual install too much.

---

### Post by AMDBuntu on 2009-09-21
I'm concerned that too much has happened with your Ubuntu installation by now to know what's going on.


Try booting from the live CD and see if you can get Jaunty to connect, after looking to see if there's a restricted driver available under "hardware drivers." Seems that your wifi card should work... Are you clicking on the icon at the top right corner of the desktop?

If all else fails and there is not a Linux driver for your wifi card. Then use ndiswrapper. It allows the use of windows XP drivers to enable your wifi card to work.

[http://en.wikipedia.org/wiki/NDISwrapper](http://en.wikipedia.org/wiki/NDISwrapper)

If you can get the live CD working, then apply the procedures to your installation.

---

### Post by Zeradin on 2009-09-21
I tried booting from the live cd, but I dont' know what to do and didn't see jaunty anywhere.

---

### Post by Zeradin on 2009-09-22
I installed Ubuntu without a direct connection to the internet. I started the installation in windows with a wireless connection, but would this fix itself if I installed it with it connected?

---

### Post by DrScum on 2009-09-22
If your wifi card is active and the WLan router is active during the install the wifi card should be configured automatically.

I'd suggest the following:
try and boot with the life CD again and look for a network connections icon on the panel (upper right). If you right click on it you should see Enable networking checked and enable wireless checked. If you left click on it you should see any network available if your card is active. But give it some time after booting wait for 3-5min, if the signal is weak it can take some time.

Another thing you can do is open a terminal (Applications>Accessories>Terminal) and enter ifconfig. The output should have someting like wlan0 and a whole bunch of information next to it. If the card is working it should have an IP adress assigned (inet addr:192.168.0.2 or something like that) and it should say UP BROADCAST.

Jaunty by the way is a alias for Ubuntu release 9.04 (Ubuntu 9.04 (Jaunty Jackalope)

Lastly I'd suggest that you start a similar thread in the Networking and Wireless section of this forum. Maybe you can get someone with more expertize than me interestd.

---

