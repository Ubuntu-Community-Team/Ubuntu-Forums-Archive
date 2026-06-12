---
title: "Howto: Most Broadcom cards with ndiswrapper"
date: 2008-06-13
forum: Networking &amp; Wireless
---

### Post by Dark_Stang on 2008-06-13
After seeing that a lot of posts here are questions concerning broadcom wireless cards, I decided to make this.

**Update** 7/26/08
I've added an automated installer. I will leave it up to you what you if you want to do it with the installer or manually.


**Auto Installer** - You need 8.04 for this to work well
Download [this package.](http://darkstang.com/uploads/broadcom_install.tar.bz2) Extract it anywhere, and run the installer. You need an internet connection for this to work.


**Manual Install**
Okay, with version 8.04 and newer there is an extra step at the end. You can do this step at any time, just reboot your machine afterwards.
**Pre-Setup Instructions**
Hook up your laptop to a wired high speed internet connection.
...that's pretty much it for presetup...

**Broadcom Wireless Card Setup**
Download and extract the files I have [here.]("http://www.darkstang.com/wifi.tar.bz2")
If that link doesn't work, go to [this one here.]("http://www.gotode.com/wifi.tar.bz2") - (one of my client's sites, temporary fix)
Now go to System > Administration > Synaptic Package Manager.
	While we're here we're going to unlock all our repositories if you haven't already. Go Settings > Repositories. Check all the boxes on the first page except for the CD, and hit close. A window will pop up telling you that you need to  reload your packages. Go ahead and close that window, and click reload at the top.
	Once that is finished click in the main window and start typing &#8220;ndiswrapper&#8221;. It will automatically scroll down and find it. Click the box next to &#8220;ndiswrapper-utils&#8221; and click &#8220;Mark for Installation&#8221;. Now go ahead and click Apply at the top.
	After that is installed open a terminal window. Applications > Accessories > Terminal. Navigate to where you saved the drivers I had you download and extract. Now run the following
```
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -m
```
	Our wireless driver is now installed but not working just yet. It's currently being blocked by another driver that is trying to run, so we need to block this other driver. Run 
```
sudo gedit /etc/modprobe.d/blacklist
```
A text editor will pop up with the blacklist. Go to the end, start a new line, and enter &#8220;blacklist bcm43xx&#8221; without quotes. Save the file.
	Now for some reason ndiswrapper doesn't load automatically when it starts up. So now let's add it to the modules list. 
```
sudo gedit /etc/modules
``` 
Make a new line and add "ndiswrapper".

	After a restart your wireless should be working and the light should be glowing blue. Congratulations, you now have a functional wireless card.

**Installing on 8.04**
Follow the wireless card guide plus these extra few steps.
enter ```
sudo gedit /etc/init.d/wifiFix.sh
```
Now copy and paste this into the file, then save it.
```
#!/bin/bash

modprobe -r b44
modprobe -r b43
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44 
```
Now enter this into a terminal
```
sudo chmod 755 /etc/init.d/wifiFix.sh
sudo update-rc.d /etc/init.d/wifiFix.sh defaults
```
Now reboot.

---

