---
title: "Unable to configure broadcom wireless card on a mac pro10,1, Ubuntu 12.04, BCM4331"
date: 2014-11-29
forum: Networking &amp; Wireless
---

### Post by anastasios2 on 2014-11-29
Hey folks

I have tried everything. specifically:

* Identified my wireless card (4331)
* Tried to install b43 and b43fwcutter (had to copy the files from another computer over)
* Tried to blacklist the bcma driver since apparently I have to unload it and use b43 instead. I did this in two locations.
* I have installed the linux drivers as well as indicated on a few posts.
* Tried to unload bcma and load b43. I have been getting errors when trying to unload it (Module in Use error)

I have found the script that gather info about the wireless card and I am attaching it.

---

### Post by Bucky Ball on 2014-11-29
Welcome. Do you have  firmware-b43-installer installed? And also b43-fwcutter? 

If you can get online with a cable, do an update and then check Additional Drivers, you should find an option for the STA driver. Install it, reboot if required, and the card should be up. 

If it's not, try following the instructions for 12.04 [HERE]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#A12.04_.28Precise_Pangolin.29").

Good luck. ;)

---

### Post by anastasios2 on 2014-11-29
Hey Bucky!

I have followed the instructions on the link for 12.04. I did the steps on "install without an internet connection". Do you know how I can check if the installation is correct? When you say "check Additional Additional Drivers" do you mean a UI option? Or from the command line?

thanks
==a

---

### Post by Bucky Ball on 2014-11-29
It is a GUI and you should find it with a quick search (not using a regular Ubuntu install, but for me it is in the Settings menu). If you have no internet connection through a cable, though, you can't update and the option will probably not be there, and if it is, you can't install it 'cos you're not online! Catch 22.

To check if you have the STA driver installed, open a terminal and issue this command:

```
sudo lshw -C network
```

Look for where it says 'driver=' in the output (somewhere near the bottom). Driver should = something. Post the output back here.

If you haven't rebooted, do that, and if it installed and working, then you should be notified that there are wireless networks available. Click the network icon and see if any are offered and if 'Enable Networking' and 'Enable Wifi' are ticked.

---

### Post by anastasios2 on 2014-11-29
hey man, first of all, thanks for responding. I really appreciate it!

Sadly, mac pro and it does not have ethernet port. I did find the UI while you were posting your reply :). Like you said, due to lack of internet connection the options are empty. I do not have a cable USB to Ethernet. 

I will do the command above and post back.

---

### Post by anastasios2 on 2014-11-29
sudo lshw -C network

 *-network UNCLAIMED
       description: Ethernet controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 10
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:c1800000-c180ffff memory:c1810000-c181ffff memory:c1830000-c18307ff
  *-network UNCLAIMED
       description: Network controller
       product: BCM4331 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:c1900000-c1903fff

---

### Post by Hadaka on 2014-11-29
Hi, your appl box requires the bcma module,
please go back in and un blacklist it..then
remove the network cable and do,,
*Be sure to get the zip file first..
go here..Post #7
```
http://ubuntuforums.org/showthread.php?t=2098717
```
the above requires no internet access, so after you load it, connect the cable
and boot...then do..
```
sudo apt-get update
sudo apt-get upgrade
```
thanks

---

### Post by anastasios2 on 2014-11-29
Hey Hadaka!

thanks for the pointers. I did everything except the last two since I need to go get a cable first. I will try it in the next few days. In the meantime, when I did the 

sudo rmmod -f b43
sudo rmmod -f ssb

I got module not found on both. I have removed the blacklisting for the bcma module too. I think once i have the cable this will become so much easier!

I should have had that before I started :)
thanks again
-a

---

### Post by wildmanne39 on 2014-11-29
Do:    
```
sudo apt-get purge b43-fwcutter firmware-b43-installer
```

Download the b43updated.zip file to a usb flash drive then drag and drop the file to your ubuntu desktop. Right-click it and select Extract Here. 

Open a terminal and do:

```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43_updated.zip/*  /lib/firmware/b43
sudo modprobe -rv b43 
sudo modprobe -v b43
```
if you get any errors just continue with the other commands, if it does not come on reboot .
Wireless should now be working.


  [https://dl.dropboxusercontent.com/s/19e7y7w6ndozdzq/b43_updated.zip?dl=1&token_hash=AAEELVjeW3iSm3d0ScTg17BSplJ01qhPGCkhav5o9EYiJA&expiry=1400713892](https://dl.dropboxusercontent.com/s/19e7y7w6ndozdzq/b43_updated.zip?dl=1&token_hash=AAEELVjeW3iSm3d0ScTg17BSplJ01qhPGCkhav5o9EYiJA&expiry=1400713892)

---

### Post by anastasios2 on 2014-11-30
Wild man! Thanks man! this worked! Thread closed :) 

I appreciate the help in getting the bad version uninstalled. 

-a

---

