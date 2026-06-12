---
title: "ndiswrapper question"
date: 2008-06-26
forum: Networking &amp; Wireless
---

### Post by kristersaurus on 2008-06-26
Hi guys.

I'm looking for an explanation as to why ndiswrapper is giving me an "invalid driver" status for my installed driver. As far as I can tell, this usually results from the inf file not being in the same directory as the files it requires. This does not seem to be the case for me, so I'm checking to see if you guys know of any alternate reasons for this. This is on an old Dell latitude laptop with built-in wireless (I believe truemobile 1500...i got the windows xp driver from their site and extracted the .exe file using wine)

If it is of any interest (not sure why it would be, but you guys know more than me..), heres what lshw has to say about my wifi card:

  ```
*-network:1
       description: Network controller
       product: BCM4309 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:90:4b:73:6c:c7
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

```

Thanks for your time.

P.S. Yes, I tried connecting with network manager and iwconfig and no-go so far...

---

### Post by Ayuthia on 2008-06-26
Did you just copy over the .inf file?  If so, that could cause the problem.  NDISwrapper also requires the use of bcmwl5.sys or bcmwl564.sys.

Otherwise, you might want to post your ndiswrapper -l and possibly check and see if dmesg|grep ndiswrapper gives you any information.

Also, does /etc/ndiswrapper/bcmwl5 have any files in it?

---

### Post by kristersaurus on 2008-06-26
Thank you for responding.

The driver i am installing is the one I got from Dell's website for my latitude c610 - ndiswrapper calls it wldel48b. The .inf file I am giving ndiswrapper is in the same directory as all the other files that were unpacked with the .inf, including .sys, .dll, and .cat files of the same name.

dmesg | grep ndiswrapper doesn't find anything...good thought though.

/etc/ndiswrapper/wldel48b only contains the .inf file after i add the driver. I have tried manually copying all the other files referenced in the .inf file into that directory with no luck.

ndiswrapper -l just gives me:
wldel48b : invalid driver!

I wish it were more verbose.

---

### Post by kevdog on 2008-06-27
Please see this wiki page -- Jamie Jackson is excellent and thorough:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by kristersaurus on 2008-06-27
Ok, thats good info.

I followed that workthrough and seem to be experiencing the 'module=ssb' bug that is addressed there for hardy users. The workaround did not work.

I posted in the related forum thread, but I kind of think it will get lost there. Anyone hear any other ways to fix the module=ssb bug?

---

### Post by kevdog on 2008-06-28
Which workaround did you try since there were a few listed.  The ssb bug is alive and well, but it seems like there has been a successful workaround for the problem.

---

### Post by kristersaurus on 2008-06-28
This is the first one I tried:

sudo rmmod b43
sudo rmmod b44
sudo rmmod b43legacy #this step added Apr 27 2008
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe ssb
sudo modprobe b44 #this step added May 1 2008

I've just now finished compiling and installing ndiswrapper 1.52 and still no joy.

---

### Post by kristersaurus on 2008-06-28
oh, i also added ssb to /etc/modprobe.d/blacklist, but its still being loaded...what am i missing?

---

### Post by kristersaurus on 2008-07-04
Still working on a solution...does anyone know of alternate solutions to the ssb module bug?

---

### Post by kevdog on 2008-07-04
Do you need the ssb module?  

Try:

sudo rmmod b43
sudo rmmod b44
sudo rmmod b43legacy 
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper


Now what happens?

---

### Post by kristersaurus on 2008-07-04
No, I don't believe I need ssb for anything. I tried that workaround last week and, even afterward, lshw still shows my wifi card using module ssb.

Right now, at the point when i try to modprobe ndiswrapper, my machine locks up.

ndiswrapper -l shows:
bcmwl5 : driver installed
	device (14E4:4324) present (alternate driver: bcm43xx)

---

### Post by kevdog on 2008-07-04
Did you blacklist bcm43xx or rmmod bcm43xx?

---

### Post by kristersaurus on 2008-07-04
Yeah, I've done both - I just double-checked /etc/modprobe.d/blacklist.

---

### Post by kristersaurus on 2008-07-04
Im really wondering why rmmod'ing and then modprobe-ing ndiswrapper is locking up my machine...do you have any ideas how to troubleshoot that?

---

### Post by kevdog on 2008-07-04
Usually that is a sign that the windows driver may not be the correct one!  Where did you get the bcmwl5 file?

---

### Post by kristersaurus on 2008-07-04
according to lshw, I have a bcm4309 chipset...that guide referenced earlier (here: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%201:%20All%20BCM43xx%20-%20Install%20NDISWrapper%20and%20Blacklist%20Native%20Driver](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%201:%20All%20BCM43xx%20-%20Install%20NDISWrapper%20and%20Blacklist%20Native%20Driver)) recommended using the driver located at step 2a for all revisions not listed in the table...so thats the one im using.

this problem originally began with me using the driver for my wifi card as supplied by dell - you can see the problems I was having with it at the beginning of the thread.

---

### Post by kevdog on 2008-07-04
How about this:

site:[http://www.linuxant.com/driverloader/drivers.php](http://www.linuxant.com/driverloader/drivers.php)

Look for 4309 broadcom.  Save the file as .zip (not .exe).  Open up the zip bundle.  Inside the TMSetup folder there is a bcmwl5 inf, cat, sys file.

---

### Post by kristersaurus on 2008-07-04
awesome. we're getting somewhere.

i rmmod'd ndiswrapper and modprobed it again. the first time i got a seg fault. the second time it appears to have worked. lshw shows my wifi card driver as ndiswrapper+bcmwl5 and i can see my wireless network.

if i could impose on you a little bit more...when i try to connect to my wireless network, my only security option is LEAP. My network is using WPA...what do I need to do to get this running?

---

### Post by kevdog on 2008-07-04
Is this an enterprise network or a home network?

---

### Post by kristersaurus on 2008-07-04
just my home network

---

### Post by kevdog on 2008-07-04
Why are you using LEAP rather than just plain old wpa or wpa2.  LEAP adds another layer of complexity.  Can you just change it so a shared password is known among the wireless wpa2 clients?

---

### Post by kristersaurus on 2008-07-04
sorry, i guess i wasn't clear - i am using regular old WPA, but gnome network manager only gives me the option of using LEAP. There is a pull-down menu with different network security schemes and LEAP is the only one listed.

---

### Post by kevdog on 2008-07-04
Ok -- do me a favor -- can you reset your router?  Ive seen other strange things like this before -- and reboot your computer.  Also after a router reset, just for the time being lets turn the wireless security off on the router to see if you can just make a simple connection --- call it lets verify your current setup prior to adding more complexity.  There are other ways to make a wpa2 connection besides network manager.  We may need to employ some alternate techniques.

---

### Post by kristersaurus on 2008-07-04
sure thing - i will do that. ill try to get to it later today when i have more time.

just fyi, i started playing around with wicd and it sees my network fine, associates with it fine, but hangs on getting an ip address.

ill do some reconfiguring later and see if i can get it to connect with no security, as you suggested.

---

### Post by kristersaurus on 2008-07-05
well, this is too bad.

thank you for your patience.

ive now reset my router and disabled wpa security on my wireless network so it is now running unencrpyted. I'm not seeing anywhere in gnome network manager where i can browse wireless access points (usually a drop down from the icon in the upper right corner that looks like two lcd monitors...now the only options in the drop down are for wired connections)...If I go into the gnome network manager config screen, unlock it, and uncheck roaming mode for my wireless connection, I can select my network from a drop-down menu (so it is seeing it at least..), but I cannot tell it not to use some sort of security...now it has a password field and a drop-down asking what encryption scheme it is using, but "none" is not an option. I've tried selecting WPA and entering my password (when WPA is enabled on the router), and I"ve tried just using iwconfig to set the essid and channel. In both cases dhclient does not get an ip address, although my router config screen shows my mac address as attached.

I'm thinking maybe its time to get an intel wifi card with native drivers...

---

### Post by kevdog on 2008-07-05
Did you try to make a manual connection?   Additionally if Network Manager is not working for you, there ia an alternative called WICD.  This works for a lot of people.

---

