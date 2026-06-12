---
title: "[SOLVED] No internet on Gutsy. How to install WICD?"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by mjitkop on 2007-10-19
Using Windows XP (dual boot) I have searched and read many threads about wireless issues but I haven't found the solution to my problem. I have Gutsy and I have a Linksys WMP54G PCI wireless card (RT2500 chip.) 

Many people said that the default network manager does not work and they had better luck with WICD. They seemed to have installed WICD with the "sudo apt-get" command in Ubuntu. Big problem with me: I have zero internet connection in Ubuntu. I have to use Windows to go online.

I would like to try WICD but I can't use "sudo apt-get" since Gutsy can't connect. How can I install WICD? :confused:

---

### Post by Whateverist on 2007-10-20
You can download the .deb file from [Sourceforge]("https://sourceforge.net/project/showfiles.php?group_id=194573&package_id=229460").

---

### Post by unisol on 2007-10-20
download it from sourceforge. burn it to some removable media and put it on your desktop to install. you probably will need to remove network manager. make sure you get wicd 1.3.3 or later for ralink support.

---

### Post by shouravv on 2007-10-20
I had the same problem at first, but then once I activated my network connection from System > Administration > Network , it started working just fine.

The weird thing is after installation Gutsy would not automatically enable the network connection available. I drove me nuts.

---

### Post by Dave in Tempe on 2007-10-20
> **unisol said:**
> download it from sourceforge. burn it to some removable media and put it on your desktop to install. you probably will need to remove network manager. make sure you get wicd 1.3.3 or later for ralink support.

The latest version I can find is 1.3.1 (which I've found to be buggy).  Where are you finding 1.3.3?

Edit:  NM, I found it.  It's here for anyone else who can't find it.
[http://sourceforge.net/project/showfiles.php?group_id=194573](http://sourceforge.net/project/showfiles.php?group_id=194573)

---

### Post by toasterboy1 on 2007-10-20
Sorry to piggyback but having problems with WICD in Gutsy. I am running Kubuntu and get this message after trying to run wicd after install.

attempting to connect daemon...
daemon not running, running gksudo ./daemon.py...
You need to start the daemon before using the gui or tray.  Use the command 'sudo /etc/init.d/wicd start'.
daemon still not running, aborting.
Traceback (most recent call last):
  File "/usr/local/bin/wicd", line 36, in <module>
    daemon = dbus.Interface(proxy_obj, 'org.wicd.daemon')
NameError: name 'proxy_obj' is not defined

Anybody got any ideas.

---

### Post by kevdog on 2007-10-20
You dont really need network manager or wicd to make a connection if you can do it from the command line.  This is a very valuable skill to have when upgrading or if everything just quits working.  Check out the post in my signature.  This should help you.  Its extremely reliable with no encryption or WEP.

---

### Post by mjitkop on 2007-10-21
Thank you all for your replies. I used the links to SourceForge to download the latest DEB package and I managed to install WICD. My original problem has now been solved. :)

---

### Post by beltman713 on 2007-10-28
I uninstalled Network Manager and then installed Network Selector through add and remove programs and now I can connect normally to the internet.

---

