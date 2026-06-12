---
title: "Cannot autostart rt2870 (D-link DWA-140)"
date: 2008-06-11
forum: Networking &amp; Wireless
---

### Post by kalkyl on 2008-06-11
I new on this forum and I am trying to connect a DWA-140 USB Wireless card to my Linux Mint 5 Elyssa.

I have used this post [http://ubuntuforums.org/showthread.php?t=683085&page=5](http://ubuntuforums.org/showthread.php?t=683085&page=5) 

It is written for rt2860 Ralink chipset but I followed it for rt2870 driver

Firts of all grab the new drivers from ralink. 
Unpack into a folder.
Code:

Edit the file <your_folder_name>/os/linux/config.mk

Change the following lines:

Code:

# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=y

# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

now go into the root of your folder and:
Code:

sudo make && sudo make install

To autostart the interface just do the following:
Code:

sudo gedit /etc/init.d/rt2870up

Paste this into the File:
Code:

#!/bin/sh

sudo ifconfig ra0 up

Now do the following:
Code:

cd /etc/init.d
sudo chmod +x rt2870up
sudo ln - s /etc/init.d/rt2870up /etc/rcS.d/S33rt2870up

Last but not least:
Code:

sudo rm /etc/Wireless/RT2867STA/RT2870STA.dat

Now to the problem. Since I am not so familaiar with linux i am not sure what this does

sudo ln - s /etc/init.d/rt2870up /etc/rcS.d/S33rt2870up

The terminal says 33rt2870up is not a directory.

If I do

sudo ifconfig ra0 up

then I can use network manager 

At this point I had to actually disable and re-enable networking to get the wireless card searching: Just right click on the Network icon at the top right of your desktop (two little computers) and uncheck 'Enable Networking' and then right click icon again and re-enable. If you then left click on this icon a few secs later you should see a list of available network access points.

Then I am able to connect with network manager using WPA encryption:)

Anyone have any ideas to autostart wireless??

---

