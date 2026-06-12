---
title: "Problems w/ D-Link DWL G132 Airplus Extreme G 802.11g USB wireless adapter"
date: 2008-03-10
forum: Networking &amp; Wireless
---

### Post by dodgeemegee on 2008-03-10
Hi!
I am completely new to Linux (2 days since install) and am having problems with my D-Link DWL G132 Airplus Extreme G 802.11g USB wireless adapter.  The device shows in Device Manager as a WLAN device.  My problem is that I can't get a driver that will work.  I have installed ndiswrapper and its GUI, ndisgtk.  Using this, I installed the only .inf file I could find that was related to the device,  athfmwdl.  ndisgtk says this is valid driver but there is no hardware device for it.  It sounds from whatever information I have gleaned that I need to install neta5agu.inf  but I can't find this anywhere on my Windows hard drive and I can't find a way to extract it from the Windows .exe.  I tried to install WINE to open this .exe, but got some binary compatibilty error so I stopped there, as I reckoned that wouldn't work anyway.   Please someone help! How do I get that .inf file?!  Will that .inf file work anyway?!   Please give a very (very very) basic guide as I am very new to Linux.   I have heard that people have got this adapter to work, so I'm sure I'm just missing something basic.  If someone has neta5agu.inf and thinks it will work, can they email it to me (ausmtb@gmail.com).
Thanks in advance.

---

### Post by kapello on 2008-03-10
Hi

You shouldn't need a driver nor any kind of windows file. 

Instead, in Ubuntu, launch System > Administration > Network and have a look at the settings.

See if anything there looks like it needs changing (do you need to enter your wireless network password, for example? Maybe enter the IP address if you have static IP, or else select DHCP?)

If you're not sure about your settings then post back listing the info you see when you launch the Network app.

---

### Post by dodgeemegee on 2008-03-11
Thanks for the reply.
When I open the network app, I see wired connection and modem connection, but no wireless connection.  In device manager, the device is listed as a USB WLAN device.   So my problem is that in the Network app, there is no wireless connection listed.

---

### Post by ELF_O8 on 2008-03-12
open up the terminal and enter in "ndiswrapper -l"

if it shows that the driver you installed is invalid, then thats the problem.

also, do you know the name of your network (SSID)?

---

### Post by dodgeemegee on 2008-03-13
Hi, and thanks for the replies.
Here's the update: found neta5agu.inf on the net, installed, shut down.  Next time I boot, get error. Please see this post:  [http://ubuntuforums.org/showthread.php?t=723084](http://ubuntuforums.org/showthread.php?t=723084)
I tried ndiswrapper -l in the GUI that I got with exec gdm, but this, along with lsusb, doesn't do anything-I get a nonresponsive line to type in, that's all.  This is kind of annoying.

---

### Post by dodgeemegee on 2008-03-14
Hi again.  Fixed the boot problem (see [http://ubuntuforums.org/showthread.php?t=723084](http://ubuntuforums.org/showthread.php?t=723084)).  I still get the same error when I type ndiswrapper -l, and also lsusb, and the gui for ndiswrapper, ndisgtk, doesn't work, even after reinstalling it and ndiswrapper.  The problem is that I just get an unresponsive new line - I can type and enter commands, but they are not executed, and no list data comes up.  I might try it in recovery mode to.  I'll post this problem in a new thread to.

---

### Post by dodgeemegee on 2008-03-14
Tried typing these commands in recovery mode.  When the usb adapter was in a different slot, lsusb reurned IDs of 0000:0000.  When the usb adapter was recognised, I got the same unresponsive line, also with ndiswrapper -l.  Recovery mode didn't boot properly with my memory stick in, and I got another unresponsive line.  Most of the time, when it was booting, it said ndiswrapper had been started and had loaded neta5agu, but one time it said it had loaded athfmwdl.  Also, I do know the SSID of my network.

---

### Post by ELF_O8 on 2008-03-28
do you have the newest version of the drivers?

also you may need to uninstall the drivers and reinstall.
use ```
ndiswrapper -r /etc/ndiswrapper/nameofthefolder/
```

---

