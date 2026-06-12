---
title: "DWL-G122 wireless setup"
date: 2008-02-12
forum: Networking &amp; Wireless
---

### Post by SadaraX on 2008-02-12
Hello, I have a wireless D-Link network card I am trying to get working. The card specs are these:

> D-Link
Model No. DWL-G122
H/W-Version: B1
F/W-Version: 2.02
P/N: BWLG122NA.B1

I tried both of these guides for setting up my DWL-G122

[https://help.ubuntu.com/community/WifiDocs/Device/DWL-122]("https://help.ubuntu.com/community/WifiDocs/Device/DWL-122")
[https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb]("https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb")

But nothing worked. Unfortunately, I have a problem. I cannot unplug and plugin the device, since this is on a remote computer I am far from. I do not know if this is a crucial problem.

When I use the ndiswrapper solution, using 'ndiswrapper -l' lists:
netprism : driver installed

But no hardware detection.

---

### Post by Alien.col on 2008-02-12
Hello I just fixed the same problem, the guy that has the correct idea posted here [http://ubuntuforums.org/showthread.php?t=596751](http://ubuntuforums.org/showthread.php?t=596751)

You have to blacklist the rt2500usb as explained there. That should make linux stop recognizing the stick. Then you download the serialmonkey drivers and install them with "make" and "make install" commands, follow the read me. At the end of the installation there could be a message that says something like "*** Update the aliases in....". That's the key because you have to associate the driver to the real neame of the device which is rasub0. On the post i linked above there is the line you should add to the aliases file.

The problem is that the rt2500usb driver intervenes first over anything you do and assigns the name wlan0 to the stick. For the stick to work you have to stopubuntu from doing that by blacklisting the rt2500usb driver. Then you alias the driver to the rausb0 device. 

Also try and remove any driver you have from ndiswrapper first and use the configuration utility provided by Ubuntu. I'm sorry that i don't have detailed  instructions, i didn't actually write down all the things i tried.

---

### Post by SadaraX on 2008-02-14
Thanks for the reply Alien. I tried what the other thread recommended but it still did not work. I asked them for help.

---

