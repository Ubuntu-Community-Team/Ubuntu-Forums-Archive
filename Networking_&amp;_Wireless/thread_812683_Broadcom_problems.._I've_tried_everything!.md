---
title: "Broadcom problems.. I've tried everything!"
date: 2008-05-30
forum: Networking &amp; Wireless
---

### Post by iamjfarrell on 2008-05-30
I have tried the automatic installer I have tried every other way to get my wireless internet to work! I have a HP DV9000 With that Broadcom wireless card... Any help would be greatly appreciated as I do not know what to do for this!!

The main problem is it doesn't even recognize that I have wireless internet.. the hardware drivers doesn't even show there either!

---

### Post by Ayuthia on 2008-05-30
> **iamjfarrell said:**
> I have tried the automatic installer I have tried every other way to get my wireless internet to work! I have a HP DV9000 With that Broadcom wireless card... Any help would be greatly appreciated as I do not know what to do for this!!

The main problem is it doesn't even recognize that I have wireless internet.. the hardware drivers doesn't even show there either!Can you post the results of:
lspci -nn|grep 14e4

---

### Post by iamjfarrell on 2008-05-30
yes,, here is the results

03:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 02)

---

### Post by iamjfarrell on 2008-05-30
Ok, well I have made some progress with the help of this tutorial.. I used the NDISwrapper [http://ubuntuforums.org/showthread.php?t=659027](http://ubuntuforums.org/showthread.php?t=659027).  My blue wireless light is on and not orange anymore.. Still not online though.. any ideas?

---

### Post by MaindotC on 2008-05-30
Ayuthia how did you know to look for 14e4? Is that number specific to Broadcom?

iamjfarrell are you familiar with the madwifi drivers and if so have you tried installing them?

---

### Post by timcredible on 2008-05-30
i just went through getting a broadcom card to work, wasn't difficult.  first, install ndiswrapper via synaptic.  then you  have a menu item System->Administration->Windows Wireless Drivers.  Use that to pick your windows driver, and then reboot.  The only difficult part was figuring out which driver you need.  Luckily I ran across a post with my wireless card and what driver it used, but you should be able to look on your Windows C: drive and find it too under some system wireless directory somewhere.  i know it's sort of vague, but hope this helps.

---

### Post by saurish on 2008-05-30
I did the same thing but it did not work in Ubuntu 8.04. I have "Windows wireless drivers" under administration and have installed "bcmwl6" and it shows "Hardware present: Yes". However, when I click "configure network" only "wired connection and "point to point  connection" show up - No wireless listed. By the way, I have "Dell 1395 802.11g Mini-Card" which uses broadcom driver for windows.

---

### Post by saxmaker on 2008-05-31
I'm lost too.  i have a dell wireless 1395 mini card with my xps 1530 and I have no wireless listed.  ??  I should say I'm very new to this
Also, my touchpad is all messed up.  just goes crazy.

---

### Post by Ayuthia on 2008-05-31
> **strAlan said:**
> Ayuthia how did you know to look for 14e4? Is that number specific to Broadcom?Yes, that is the code for Broadcom.  The Broadcom cards have a PCI id that will start with 14e4.  Then the chipset number comes after.  For the Broadcom wireless cards they are assigned 43xx where xx is a two digit number that is specific to the chipset.  So I asked for only 14e4 mainly because I was looking to see if I can verify that the wired card was not using the b44 driver.

---

### Post by Ayuthia on 2008-05-31
> **iamjfarrell said:**
> Ok, well I have made some progress with the help of this tutorial.. I used the NDISwrapper [http://ubuntuforums.org/showthread.php?t=659027](http://ubuntuforums.org/showthread.php?t=659027).  My blue wireless light is on and not orange anymore.. Still not online though.. any ideas?Well, you chose correctly to install NDISwrapper for your card.  The 4311 rev 02 does not work with the b43 driver right now in Ubuntu Hardy.

You might try this [guide]("http://ubuntuforums.org/showthread.php?t=769990").  It seems to be more related to your laptop.

Another thing is to try to see if you can see any wireless devices from the Terminal:
```
sudo iwlist scan
```

---

### Post by Ayuthia on 2008-05-31
> **saurish said:**
> I did the same thing but it did not work in Ubuntu 8.04. I have "Windows wireless drivers" under administration and have installed "bcmwl6" and it shows "Hardware present: Yes". However, when I click "configure network" only "wired connection and "point to point  connection" show up - No wireless listed. By the way, I have "Dell 1395 802.11g Mini-Card" which uses broadcom driver for windows.The bcmwl6 (Vista driver) does not work with NDISwrapper yet.  You will need to find a driver for XP.  You might look for a suitable driver from this [link]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff").

---

### Post by Ayuthia on 2008-05-31
> **saxmaker said:**
> I'm lost too.  i have a dell wireless 1395 mini card with my xps 1530 and I have no wireless listed.  ??  I should say I'm very new to this
Also, my touchpad is all messed up.  just goes crazy.You will also need to install ndiswrapper-utils-1.9 (NDISwrapper).  You can do it through Synaptic or you can do it from the terminal (sudo apt-get install ndiswrapper-utils-1.9).  From this [link]("http://forum.fedoraforum.org/printthread.php?t=184143"), it looks like you need to download this driver: [http://ftp.us.dell.com/network/R174291.exe](http://ftp.us.dell.com/network/R174291.exe).  You will need to install cabextract to extract the files.

You might try this [guide]("http://ubuntuforums.org/showthread.php?t=766560").  You will need to replace step 2 with the following:
```
cd /tmp
wget http://ftp.us.dell.com/network/R174291.exe
unzip R174291.exe
cd DRIVER_US
```
This is going to download the file into /tmp and extract the file there.  I have chosen /tmp mainly because it is a temporary folder and will remove the downloaded file once you reboot.  If you want to keep the file, I would recommend creating a folder in your home directory and downloading the file into that folder.

---

### Post by saurish on 2008-06-03
That worked. Thanks a lot!

---

### Post by cdtech on 2008-06-03
I had (have) the same problems. The way I got my wireless to acquire an IP address was to reload the drivers:

And then do the ifdown/ifup thing.

modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44

After which I was able to browse the internet but only for about 2 minutes before I had to reload the drivers again. This has got me so frustrated, I'm thinking of rolling back to Gutsy (no problems with Gutsy).

---

