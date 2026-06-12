---
title: "WUSB54Gv4 not working"
date: 2011-01-31
forum: New to Ubuntu
---

### Post by noname1000 on 2011-01-31
Hello, I've spent a total of 6 hours messing around looking up guides for my WUSB54Gv4 since it wont work, I just installed Ubuntu 10 04 last night, with windows 7 32bit already installed, getting kind of tired of searching so I decided to post this, sorry if its already been solved.

So far I have done all of this: [http://dinomite.net/2007/linksys-wusb54g-in-ubuntu/](http://dinomite.net/2007/linksys-wusb54g-in-ubuntu/)

It links to another page: [http://ubuntuforums.org/showthread.php?t=478558](http://ubuntuforums.org/showthread.php?t=478558)

"sudo gedit /etc/modprobe.d/ndiswrapper", change "wlan0" to "rausb1".
I can't seem to find wlan0 or rausb1, even when I searched using iwconfig, iwlist, ifconfig, and dhclient

When I first installed Ubuntu I was able to see other wireless connections, but not connect to them, now I can't see any connections at all.

I don't have this "LiveCD" thing. 

I'm completely new to linux.

That is all I can think of at this moment, thank you for reading.

---

### Post by wormyblackburny on 2011-01-31
I had to use ndiswrapper on my first Ubuntu install when I was a total noob, and believe me I feel your pain. What all of the articles failed to mention is that if you have your ethernet cable plugged in, it will disable the wireless. Obviously you have to have internet connectivity to browse the help articles and download the drivers etc unless you have two computers ;)

My solution to start would be to download the drivers using wired connection and install ndiswrapper. Copy paste the two articles into an openoffice doc or text file. Disconnect wired connection, restart, and try it all again. When you are done with the install/config, restart and pray. Other than that, we will need some more info on where you are having problems. List any errors that occur or specific questions you have on the process and we'll go from there.....

---

### Post by noname1000 on 2011-01-31
I already have the drivers and ndiswrapper installed, I just can't locate any wireless connections, and I can't find wlan0 to rename it, when I do 
sudo iwconfig wlan0
sudo ifconfig wlan0
sudo dhclient wlan0
I get "device not found" every time, when I do
sudo gedit /etc/modprobe.d/ndiswrapper
All I get are 3 lines with "alias" and a bunch of stuff I can't figure out how to bring to this computer, but nothing says "wlan0" in it.

---

### Post by noname1000 on 2011-02-01
bump

---

