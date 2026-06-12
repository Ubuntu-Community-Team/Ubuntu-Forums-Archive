---
title: "Broadcom Wireless Controller still doesnt work..."
date: 2008-06-13
forum: Networking &amp; Wireless
---

### Post by opakedragon on 2008-06-13
I helped to install Ubuntu Hardy Heron on my girlfriend's computer. It went well except the Broadcom Wireless card doesn't work (the menu is there, but no signals are getting picked up). This is what I get when I run:```
mainuser@gateway-laptop:~$ lspci | grep Broadcom\ Corporation
00:0c.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
```I have tried several different guides now I seek help directly.

[http://ubuntuforums.org/showthread.php?p=1169984&highlight=folder+where#post1169984](http://ubuntuforums.org/showthread.php?p=1169984&highlight=folder+where#post1169984)
[http://ubuntuforums.org/showthread.php?t=25683](http://ubuntuforums.org/showthread.php?t=25683)
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty#head-caeaaa52eed95354a055b410c7bd6f72b773f585](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty#head-caeaaa52eed95354a055b410c7bd6f72b773f585)
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Here is a list of guides I have used, that I have already caused me to reinstall the OS since I did not know how to undo the guides that failed. When I completed most of the guides the problem had not changed, and I had another Ubuntu Hardy Heron computer (mine) set up right next to it.  Mine got signal, but not hers.

The computer is a 5 year old Gateway 7405GX, it worked fine (slow, but fine) under Windows, but it had a virus that we just wiped the drive and she figured since I kept advocating it that she'd try it. We don't have money for a new one.

Thanks for any help.

---

### Post by Ayuthia on 2008-06-13
> **opakedragon said:**
> I helped to install Ubuntu Hardy Heron on my girlfriend's computer. It went well except the Broadcom Wireless card doesn't work (the menu is there, but no signals are getting picked up). This is what I get when I run:```
mainuser@gateway-laptop:~$ lspci | grep Broadcom\ Corporation
00:0c.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
```I have tried several different guides now I seek help directly.

[http://ubuntuforums.org/showthread.php?p=1169984&highlight=folder+where#post1169984](http://ubuntuforums.org/showthread.php?p=1169984&highlight=folder+where#post1169984)
[http://ubuntuforums.org/showthread.php?t=25683](http://ubuntuforums.org/showthread.php?t=25683)
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty#head-caeaaa52eed95354a055b410c7bd6f72b773f585](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty#head-caeaaa52eed95354a055b410c7bd6f72b773f585)
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Here is a list of guides I have used, that I have already caused me to reinstall the OS since I did not know how to undo the guides that failed. When I completed most of the guides the problem had not changed, and I had another Ubuntu Hardy Heron computer (mine) set up right next to it.  Mine got signal, but not hers.

The computer is a 5 year old Gateway 7405GX, it worked fine (slow, but fine) under Windows, but it had a virus that we just wiped the drive and she figured since I kept advocating it that she'd try it. We don't have money for a new one.

Thanks for any help.

Let's start off with the basics.  The commands that I will write about are used in the Terminal.  

First check and see if the version of NDISwrapper is going to work and that the device is present:
```
ndiswrapper -v
ndiswrapper -l
```
The version needs to be at 1.50 or higher and ndiswrapper -l needs to show that the device is present.

If all that is ok, then let's remove any possible conflicting modules and then load ndiswrapper:
```
sudo modprobe -r b43 ssb bcm43xx ndiswrapper
sudo depmod -ae
sudo modprobe ndiswrapper
```
If the prompt comes back without any messages, then all went fine.  The next thing to do is to see what module the wireless card is using:
```
lshw -C network
```
The driver should show that ndiswrapper is being used.  If you see b43-pci-bridge, then you need to see dmesg and check for errors for ndiswrapper.  It should show up at the end of the log.  If there are no errors:
```
sudo iwlist scan
```
If you see any wireless networks, then all is well.

---

### Post by Dark_Stang on 2008-06-13
It looks like that's just using the bcmwl5.inf file that most of the other broadcom cards use... I extracted this from my howto for HP dv6636nr. Check the notes on 8.04 if you're going to be using that.

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

### Post by opakedragon on 2008-06-14
> **Ayuthia said:**
> Let's start off with the basics.  The commands that I will write about are used in the Terminal.  

First check and see if the version of NDISwrapper is going to work and that the device is present:
```
ndiswrapper -v
ndiswrapper -l
```
The version needs to be at 1.50 or higher and ndiswrapper -l needs to show that the device is present.

If all that is ok, then let's remove any possible conflicting modules and then load ndiswrapper:
```
sudo modprobe -r b43 ssb bcm43xx ndiswrapper
sudo depmod -ae
sudo modprobe ndiswrapper
```
If the prompt comes back without any messages, then all went fine.  The next thing to do is to see what module the wireless card is using:
```
lshw -C network
```
The driver should show that ndiswrapper is being used.  If you see b43-pci-bridge, then you need to see dmesg and check for errors for ndiswrapper.  It should show up at the end of the log.  If there are no errors:
```
sudo iwlist scan
```
If you see any wireless networks, then all is well.


Unfortunately, ndiswrapper is no longer installed I decided to reinstall fresh after I did all those tutorials.

> **Dark_Stang said:**
> It looks like that's just using the bcmwl5.inf file that most of the other broadcom cards use... I extracted this from my howto for HP dv6636nr. Check the notes on 8.04 if you're going to be using that.

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

The only ndiswrapper-utils is ndiswrapper-utils-1.9, and that prompts me to install ndiswrapper-common is this acceptable?

EDIT: Dark_Stang, I tried it your way with the ndiswrapper-util-1.9 and ndiswrapper-common, but (after a restart) still no wireless. When I ran the last command (update-rc.d) it said that the wifiFix.sh file was not found.

---

### Post by snoopy66 on 2008-06-14
I too have been struggling with getting my wireless to work under Hardy 8.04.  I'm using Kubuntu not Ubuntu, though I suspect for the solution I found, it won't matter.  First, I have a Compaq Presario R4000 laptop, and when I do 'lsmod | grep Broadcom', I see:

03:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

I found a post somewhere else that said for BCM4306 rev 03 and before, I could not use b43.  Instead, I had to use bcm43xx.  To get my wireless card to work, I did the following:

1) Make sure the b43 driver is NOT installed.  In Kubuntu, I click K-menu -> System Hardware Drivers Manager option and make sure the Broadcom driver is not checked.  I suspect this step is similar to the following:

1a) Use lsmod to see if the b43 or the ssb module is loaded:

$ lsmod | grep b43
$ lsmod | grep ssb

Both command should yield nothing.  If either module is loaded, you will get output from the command and you can remove the modules with the following commands:

$ sudo rmmod b43 # remove the b43 module from memory
$ sudo rmmod ssb # remove the ssb module frommemory

2) To prevent the modules from being loaded in the future, my understanding is that you should be able to add them to the blacklist.  To add them, issue the command:

$ sudo vi /etc/modprobe.d/blacklist

Of course, you could also use whatever editor you prefer in place of 'vi'.  If they are not already present, add the following lines to the file:

blacklist b43
blacklist ssb

If you find a line that reads 'blacklist bcm43xx', place a pound sign in front of it because you really do want to load the bcm43xx module:

#blacklist bcm43xx

3) Now install the bcm43xx-fwcutter package with the command:

$ sudo apt-get install bcm43xx-fwcutter

Or use your favorite package manager, if you prefer.  You will be asked if you want to get the firmware necessary.  Simply respond with 'y'.

4) Momentarily, your wireless should start working.  (In my case, I had to press the antenna button on my laptop to get the blue light to come on.)

Everything went fine for me from this point, but when I rebooted, my wireless didn't work.  Hmm.....  Upon investigation, I found that even though I blacklisted both b43 and ssb, ssb still loaded (i.e., the command 'lsmod | grep ssb' yielded output).  I don't know why, but I issued the following commands to correct the problem:

$ sudo rmmod ssb # remove the ssb module from memory
$ sudo rmmod bcm43xx # remove the bcm43xx module from memory so it can be re-initialized
$ sudo modprobe bcm43xx # re-insert the bcm43xx module

There must be a way to make sure ssb does not load in the first place, but I haven't figured that one out yet.

Hope this helps!

---

### Post by Ayuthia on 2008-06-14
> **opakedragon said:**
> Unfortunately, ndiswrapper is no longer installed I decided to reinstall fresh after I did all those tutorials.
Since you have went through DarkStang's guide, have you installed b43-fwuctter or enabled the Broadcom driver through Hardware Drivers?  If so, please try the following:
```
sudo modprobe -r b43 ssb ndiswrapper bcm43xx
sudo depmod -ae 
sudo modprobe b43
sudo ifconfig wlan0 up
sudo iwlist scan
```
Let us know if you see any wireless sites.

@snoopy66-I have the same card with a Dell laptop on Kubuntu and it is working with the b43 drivers.  You might install it through Hardware Drivers or install b43-fwcutter and then do the following:
```
sudo modprobe -r b43 ssb bcm43xx ndiswrapper
sudo depmod -ae
sudo modprobe b43
sudo ifconfig wlan0 up
sudo iwlist scan
```
If ssb keeps coming up at boot, can you also post your lshw -C network?  I would like to see your wired card info.

---

