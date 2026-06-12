---
title: "hp pavillion dv6325 can't see wireless networks"
date: 2008-06-13
forum: Networking &amp; Wireless
---

### Post by buckykat on 2008-06-13
just installed hardy with wubi on my uncle's laptop, everything works just great except that the wireless can't even see networks nearby, much less connect to them. any ideas?

---

### Post by Ayuthia on 2008-06-13
> **buckykat said:**
> just installed hardy with wubi on my uncle's laptop, everything works just great except that the wireless can't even see networks nearby, much less connect to them. any ideas?It could be that it is missing firmware for the driver to activate the card.  Can you open a Terminal and post the results of:
```
lshw -C network
or
lspci -nn
```
This will tell us what card you have.

---

### Post by Dark_Stang on 2008-06-13
You've got a broadcom card... If you're using 8.04 (the latest) check the notes at the end.

**Wireless Card Setup**
Download and extract the files I have [here.]("http://www.darkstang.com/wifi.tar.bz2")
If that link doesn't work, go to [this one here.]("http://www.gotode.com/wifi.tar.bz2") - (one of my client's sites, temporary fix)
Now go to System > Administration > Synaptic Package Manager.
	While we're here we're going to unlock all our repositories. Go Settings > Repositories. Check all the boxes on the first page except for the CD, and hit close. A window will pop up telling you that you need to  reload your packages. Go ahead and close that window, and click reload at the top.
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

**Installing on 8.4**
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

---

### Post by timestoby on 2008-06-13
hi,i have a hp pavillion also dv6000 series and was wondering if these are the same steps i need to do in order to get the wireless workn.i also have the broadcom wireless card built in

---

### Post by Ayuthia on 2008-06-13
> **timestoby said:**
> hi,i have a hp pavillion also dv6000 series and was wondering if these are the same steps i need to do in order to get the wireless workn.i also have the broadcom wireless card built in

Just open up a Terminal and type lspci -nn.  If you see a Network Controller or Ethernet Controller that has an id that starts with 14e4:43 then you have a Broadcom card and should be able to use these steps.

---

### Post by timestoby on 2008-06-13
thanks

---

### Post by buckykat on 2008-06-20
alright, all your commands worked just fine except for the last one. ```
sudo update-rc.d /etc/init.d/wifiFix.sh defaults
```returns```
update-rc.d: /etc/init.d//etc/init.d/wifiFix.sh: file does not exist
```still can't see any networks, wifi light still orange

---

### Post by Ayuthia on 2008-06-20
> **buckykat said:**
> alright, all your commands worked just fine except for the last one. ```
sudo update-rc.d /etc/init.d/wifiFix.sh defaults
```returns```
update-rc.d: /etc/init.d//etc/init.d/wifiFix.sh: file does not exist
```still can't see any networks, wifi light still orangeBased on your information, the command should have been:
```
sudo update-rc.d wifiFix.sh defaults
```I have not tested it, but it should work.  I don't use that command.  I tend to use the following based on the no-fluff documentation ([https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-6a90c0182f807f29d1a2f55e8654ac07689542bb):](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-6a90c0182f807f29d1a2f55e8654ac07689542bb):)
```
echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/ndiswrapper 
```
I like this version better mainly because if the b43 driver does work and you want to use it, you don't have to take the extra steps to remove the script.  However, the script given by Dark Stang does work and will be more than fine.

---

