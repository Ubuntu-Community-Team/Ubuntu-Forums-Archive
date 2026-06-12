---
title: "RT2500 card sees AP's but can't get WEP to work"
date: 2008-01-14
forum: Networking &amp; Wireless
---

### Post by osonegro on 2008-01-14
I just installed the latest version of ubuntu and my RT2500 chipset card does see the wireless networks near me but the one I need to connect to uses a WEP key.  I am pretty dumb here so I don't know if it is a 64 bit or 128 bit key.  The key is 5FF2D8361C, I can give you that cuz you have no idea of where I am. Oh and to show my complete dumbness I don't know if this is an ascii or hex key.

Anyhow, I have tried to put in the key using both ascii and hex selections but it will not connect to my provider, it just keeps coming back asking for the key.  Can anyone help me here cuz if I can't use my wireless card I have to go back to windoz... yuk.[http://ubuntuforums.org/images/smilies/icon_sad.gif](http://ubuntuforums.org/images/smilies/icon_sad.gif)
:(

---

### Post by osonegro on 2008-01-14
I also just noticed that when I bring ubuntu 7.10 back up that it now tries to access my wireless provider and ends up doing so indefinetly... hmmm how do I stop this?

---

### Post by MariusSilverwolf on 2008-01-14
Under Gutsy, the Network Manager does not support Roaming Mode for connecting with encryption,  or if it does, it does so sporadically.

Here's what you need to do:

1) Open Network Manager (it will ask for your password)
2) Open the Wireless Connection
3) Uncheck the radio box for "Enable Roaming Mode"
4) Under Wireless Settings, for the ESSID Field enter the name of the wireless network to which you are connecting.
5) For the Password Type field, select "WEP Key (hexadecimal)
6) For the Network Password field, enter the key you (unwisely) listed here.
7) Under Connection Settings, for the Configuration field select "Static IP Address"
8) For the IP address field, type in the address your system will use (such as 192.168.1.100)
9) For the subnet mask, type in 255.25.255.0
10) For the Gateway address, type in the IP address of your wireless router (such as 192.168.1.1)
11) Click OK to close the properties window for the wireless connection
12) Click Close to close Network Manager
13) Give the connection 10 - 15 seconds to establish, then test.


Hope that helps!

---

### Post by kevdog on 2008-01-14
With your rt2500 card, what driver are you using?

You can find this with 

lshw -C network

---

### Post by osonegro on 2008-01-14
I have used that command but it does not list a driver.  The driver has to be install cuz the wlan0 device sees networks when I use the "iwlist scan" command.  The first time I booted unbutu all the wifi networks in my area were shown in the list.

There has to be a way to get this darn thing to work.

I tried the procedure in the post "How To: Troubleshoot your Wireless Network Connection...".  I used the lshw -C network and it showed my wireless interface, logical name but did not list a driver.  When I used the "dhclient wlan0" command it did not get a ip.

I am starting to think that linux is too complicated for little old me....

---

### Post by osonegro on 2008-01-15
I finally went out and bought me a new wireless card that is NOT based on Ra2500 chip.  Installed it and now linux is happy and so am I.

---

