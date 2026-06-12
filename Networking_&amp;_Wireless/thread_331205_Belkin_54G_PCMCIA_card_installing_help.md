---
title: "Belkin 54G PCMCIA card installing help"
date: 2007-01-04
forum: Networking &amp; Wireless
---

### Post by scurlaruntings on 2007-01-04
Hi guys im primarily a MS guy who is looking to explore the new world to me of a linux enviroment and i have chosen Ubuntu as my designated OS.Naturally being a microsoft techie my knowledge on this product although not a newbie level is distinctly minimal.Can anyone give me an accurate step by step guide on how to install a Belkin54G card on Ubuntu... I have installed the NDISWRAPPER and attempted to install the driver through the terminal window using the `sudo` commands but im at a loss as i know so little as to what im doing.Any help would be greatly appreciated.

Many thanks

---

### Post by iljusu on 2007-01-04
Hi there,

I had a same problem, but found help from the following links:

Step 1. [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

Use lspci to check for the chipset

Step 2. If your card is Belkin  F5D7010 and chipset Broadcom

Goto: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Step 3. If you´re running 6.06

Goto: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper)

Step 4. Look for reader comments and the following text ... that worked for me :) 

[I]Since you probably don't have net access without the wireless card, use another machine to download the  bcm43xx-fwcutter package and the firmware update that the bcm43xx team recommends,  wl_apsta.o. (You may have to right-click that firmware link to avoid having it open in its own window and save it to disk.) 

Boot into Ubuntu, copy those two files onto your desktop, and do the following: 

cd ~/Desktop 
sudo dpkg -i bcm43xx-fwcutter
sudo bcm43xx-fwcutter -w /lib/firmware wl_apsta.o That should move your current directory to the desktop, install the firmware updater, and drop the firmware image in the right spot.

All you need to do now is to take down the driver and then bring it back up so the new firmware will load. 

sudo ifconfig eth1 down 
sudo ifconfig eth1 upYou may have to use eth2 instead of eth1. Using lspci should tell you.

Go into System->Administration->Networking, and you should be good to go. [/I]

---

