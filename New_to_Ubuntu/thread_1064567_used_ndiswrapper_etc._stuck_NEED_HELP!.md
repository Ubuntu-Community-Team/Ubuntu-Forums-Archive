---
title: "used ndiswrapper etc. stuck NEED HELP!"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by Seathan93 on 2009-02-09
First: i'm a complete newb to linux and i've already tried what i could find on the forum:

Ok, so i've tried installing ubuntu/linux three times already, and each time i get so frustrated that i cant connect to the internet and have to keep booting windows to come to the forum that i end up uninstalling it...this time however i'm determined to get it working.

Basically, i have a Linksys WMP54GS wireless PCI card (Broadcom chip i believe last i checked using the lspci thing), so with the advice of the forums and my friend who uses Linux i downloaded ndiswrapper, put it on my flashdrive and then used it in ubuntu.  When i run ndiswrapper -l it says the driver and hardware are present but i still cannot connect to the internet through my (hidden) wireless network.

Things i think may be the problem based on other threads:
1. i'm using the wrong kind of WEP selection but cant try anything with that until tomorrow night
2. there's something else or i used ndiswrapper wrong

I'm using Ubuntu 8.10 if that's any help

---

### Post by newbee70 on 2009-02-09
> **Seathan93 said:**
> First: i'm a complete newb to linux and i've already tried what i could find on the forum:

Ok, so i've tried installing ubuntu/linux three times already, and each time i get so frustrated that i cant connect to the internet and have to keep booting windows to come to the forum that i end up uninstalling it...this time however i'm determined to get it working.

Basically, i have a Linksys WMP54GS wireless PCI card (Broadcom chip i believe last i checked using the lspci thing), so with the advice of the forums and my friend who uses Linux i downloaded ndiswrapper, put it on my flashdrive and then used it in ubuntu.  When i run ndiswrapper -l it says the driver and hardware are present but i still cannot connect to the internet through my (hidden) wireless network.

Things i think may be the problem based on other threads:
1. i'm using the wrong kind of WEP selection but cant try anything with that until tomorrow night
2. there's something else or i used ndiswrapper wrong

I'm using Ubuntu 8.10 if that's any help

if you left click on then network connection icon in the upper right toolbar, do you see your wireless connection enabled? if you dont see a wireless connection there.

have you gone into System ---> Administration --> Hardware Drivers and checked to see if you have yours enabled?

---

### Post by adult swim on 2009-02-09
i know back in the day there was an issue with ndiswrapper and ssb interfering with eachother.  im not sure if that was ever straightened out.  try running these commands, one at a time, from a terminal when you get the chance.
```
sudo modprobe -r b44
sudo modprobe -r b43
sudo modprobe -r b43legacy
sudo modprobe -r ssb
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe b44 
sudo iwlist scanning
``` the last command should print the networks available if things went well.  if thats the case, left click on the network applet in your tray and select connect to hidden network.  if you can get on the internet, post back and we can make what you did above a script to run at startup so you dont have to do it everytime you restart your computer.

---

### Post by Seathan93 on 2009-02-09
Hi, oh yeah finally...that last one worked, i'm currently posting from firefox inside ubuntu.  Do i have to do that every time i log in though?  Because that could get annoying :-?

how do i make it that script thing you were talking about?

---

### Post by adult swim on 2009-02-09
to make and run the script youll need to go to a terminal and enter in ```
gksudo gedit /etc/init.d/wirelessfix.sh
``` when the text editor pops up, paste in ```
#!/bin/bash

modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44 
```

now save the file and close the window.  now go back to the terminal and enter these in one at a time ```
cd /etc/init.d/

sudo chmod 755 wirelessfix.sh

sudo update-rc.d wirelessfix.sh defaults
```  now your wireless should work automatically when you restart your computer.

---

### Post by Seathan93 on 2009-02-10
works perfectly...thank you! =)

---

### Post by cpbrock3 on 2009-03-09
OK.  After searching the forums for many hours and trying all the different scripts for getting this wmp54gs network card to work this one finally worked.  Thank you for posting these instructions.

I am curious as to what all the commands actually did to make this thing work.  Can you tell me what happened when I typed these commands?  I'm thinking it was something to do with getting rid of a driver and replacing it with a different one.  I'm new with linux so I don't know what the commands do.

I did make the script for it so I don't have to keep doing it but now I get asked for something about a keyring when i start up.  Is there a way to get it to stop doing that?

---

