---
title: "having trouble getting laptop network card set up."
date: 2007-12-09
forum: Networking &amp; Wireless
---

### Post by memoryproblems on 2007-12-09
i have a Dell 1501 laptop with a Broadcom Dell 1390 WLAN mini-card as my wireless card. I downloaded and installed Ubuntu 7.10 today and other than networking problems its seemed fine.

I downloaded the Ndiswrapper-common, the Ndiswrapper-utils, and ndisgtk for the graphical interface.

I used the gui version from the administration menu and installed using the driver i downloaded from Dell's website. (the wiki on ndiswrapper said which file to use, and i used it). under the gui of ndiswrapper, it shows the driver and says hardware present, but the wifi light on my laptop is not illumiated.

I'm kinda new to ubuntu, i've toyed around with it in the past, but with limited success. If anybody could help me with this, i'd appreciate it.

---

### Post by Original Brownster on 2007-12-10
> **memoryproblems said:**
> i have a Dell 1501 laptop with a Broadcom Dell 1390 WLAN mini-card as my wireless card. I downloaded and installed Ubuntu 7.10 today and other than networking problems its seemed fine.

I downloaded the Ndiswrapper-common, the Ndiswrapper-utils, and ndisgtk for the graphical interface.

I used the gui version from the administration menu and installed using the driver i downloaded from Dell's website. (the wiki on ndiswrapper said which file to use, and i used it). under the gui of ndiswrapper, it shows the driver and says hardware present, but the wifi light on my laptop is not illumiated.

I'm kinda new to ubuntu, i've toyed around with it in the past, but with limited success. If anybody could help me with this, i'd appreciate it.

Hi, I had a quick look and assuming nothing has changed, there is no native driver but just to make sure, from  a terminal window take a look at the output of
$lsmod
you are looking for the module ndiswrapper being loaded and with a reference count higher than 0 in the used column of the display
[URL="http://ubuntuforums.org/showthread.php?t=297092"]
This howto [/URL]I found suggests there is a native driver in ubuntu that maybe loaded by default, something like:

bcm43...

check the output of 
$ifconfig -a
and
$iwconfig

post back the output, it should indicate the name of the device assigned as wireless

do 
$sudo iwlist scan

post the output, if your card is working properly it should report any access points (cells) in range.  Talking of which, let us know how your wireless AP is configured, I normally recommend turning off all encryption just until you get it working and then configure encryption, also make sure the AP is broadcasting the essid for now.

Are you using automatic network configuration of ip (DHCP)?

---

### Post by redDEADresolve on 2007-12-11
[http://www.ubuntu1501.com/2007/06/ubuntu-gutsy-gibbon-710-new-user-guides.html](http://www.ubuntu1501.com/2007/06/ubuntu-gutsy-gibbon-710-new-user-guides.html)

You have two options for wifi, ndiswrapper works a tad better going through the terminal.

---

### Post by memoryproblems on 2007-12-11
thanks for the replies. Original Brownster, your noting the default driver that ubuntu was trying to load helped me alot. I had tried to use that guide a bit to get it all figured out, but all the language of compiliations and stuff had gotten me off topic, so i had opted to go through the ndisgtk route, but I hadn't noticed that i needed get rid of the driver it was already trying to load. I did that, rebooted my computer, and my wireless card worked, and my WiFi light was on.

i'm on an unencrpyted network (i live in a very rural area, nobody within about a kilometer on all sides of me). I did the iwconfig in terminal, and for my eth0 it showed up a bunch of stuff, but for the essid it showed any/none, and i'm not entirely sure what that means.

i'm on a Wireless-B network, and it works perfectly fine in Windows Vista Home Premium , but i've been trying all day to get it set up on Linux with very little luck.

---

### Post by Original Brownster on 2007-12-12
> **memoryproblems said:**
> thanks for the replies. Original Brownster, your noting the default driver that ubuntu was trying to load helped me alot. I had tried to use that guide a bit to get it all figured out, but all the language of compiliations and stuff had gotten me off topic, so i had opted to go through the ndisgtk route, but I hadn't noticed that i needed get rid of the driver it was already trying to load. I did that, rebooted my computer, and my wireless card worked, and my WiFi light was on.

i'm on an unencrpyted network (i live in a very rural area, nobody within about a kilometer on all sides of me). I did the iwconfig in terminal, and for my eth0 it showed up a bunch of stuff, but for the essid it showed any/none, and i'm not entirely sure what that means.

i'm on a Wireless-B network, and it works perfectly fine in Windows Vista Home Premium , but i've been trying all day to get it set up on Linux with very little luck.

Hi,
the essid any/none means you have not specified a wireless network or AP to join hence 'any' so in theory your pc could connect to any unencrypted wireless network in range.

Your wireless access point (AP) will have been assigned an essid, do you know what it is? if not there are a few ways to ascertain it, 1, go into the administration pages of the AP, 2. check how you have windows configured, 3. at a terminal run:
$ sudo iwlist scan
This will find your wireless device then scan the area for AP's hopefully it will see just yours!
this command will also tell you if your router has encryption switched on.

possibly the quickest thing to try is using the built in gui tool network manager, try this and see if it finds your wireless network then try connecting.

if no luck, Post the output of

$ ifconfig -a
$netstat -rn
$ iwconfig
$ sudo iwlist scan

---

