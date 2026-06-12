---
title: "Wireless problems on Asus EEE 1005-HA"
date: 2009-09-11
forum: New to Ubuntu
---

### Post by Zorlee on 2009-09-11
Hi everyone.
Yesterday I installed the latest version of Ubuntu on my Asus EEE PC, after weeks (!) of issues with installing Windows on my Asus EEE PC.
Needless to say, I'm very tired of all this trying and failing, and I just want the thing to work. I dumped Windows, because of all the problems, and installed Ubuntu. I've never used Linux before, but it all worked great - I installed it with a USB-pen, with no problems what-so-ever.

Now, when it's up and running, it won't recognize my wireless connection! My Macbook hooks up with no problems, but via Ubuntu it won't even recognize any of the connections.
I searched for answers on this forum, and found some terminal codes, and tried these, but it looks that they don't work, and I double-checked that I didn't input them incorrectly - it just says: "No such code" or along those lines.
I also tried to connect with a wired ether-net cable, but it didn't connect either.

This machine was supposed to be something fun, but it's been nothing but trouble, so please help me guys! I'm not very good with these things, so I'm dependent on some help.
Thank you so much!! =)

Sincerely,
Zorlee

---

### Post by LewRockwell on 2009-09-11
the following link may be of related reference to your equipment if you have the Broadcom 4312

regardless of that fact, it is interesting reading/information nevertheless

[http://beginlinux.com/appsm/wireless_m/1419-slackware-13-wireless](http://beginlinux.com/appsm/wireless_m/1419-slackware-13-wireless)

.

---

### Post by LewRockwell on 2009-09-11
you might also enjoy this:

[http://ubuntuforums.org/showthread.php?t=1222961](http://ubuntuforums.org/showthread.php?t=1222961)

.

---

### Post by Zorlee on 2009-09-11
Thank you for your fast answer.
First off, I'm un-able to insert a proper command in terminal to figure out what network-card I have in my computer. I only get "command not found"... ?

EDIT: I figured out my terminal problem, and my network card is a Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01).

---

### Post by Zorlee on 2009-09-11
Anyone?
I'm really sorry, but I'm clueless...

---

### Post by LewRockwell on 2009-09-11
> **Zorlee said:**
> Thank you for your fast answer.
First off, I'm un-able to insert a proper command in terminal to figure out what network-card I have in my computer. I only get "command not found"... ?

EDIT: I figured out my terminal problem, and my network card is a Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01).

other threads for reference:

[http://ubuntuforums.org/showthread.php?t=1249187](http://ubuntuforums.org/showthread.php?t=1249187)

[http://www.uluga.ubuntuforums.org/showthread.php?p=7635367](http://www.uluga.ubuntuforums.org/showthread.php?p=7635367)

.

---

### Post by Irvine_himself on 2009-09-11
I am also a  Noob to Ubuntu, (just over two days,) and the two most intractable, hair-raising, scream inducing problems I have had are communications cards and media players. 

After installing Ubuntu, I installed a PCI modem on my box . When I had finished all the screaming, hair-pulling and general sulking, (as outlined above,) I found the most important tool is to down load "Network" in systems utilities. (It's either in Semantic or Add and Remove.)With that you can easily see if the system has drivers and can be configured.

You can use 


sudo lshw -html > ~/Desktop/my_hardware.html


to see if it can see the hardware and if not, (and failing to find suitable Linux drivers,) use


sudo apt-get install ndiswrapper-utils

sudo apt-get install ndisgtk



For a GUI to wrap the Windows drivers in.

Hope that helps, 

happy Ubuntu-ing

---

### Post by LewRockwell on 2009-09-11
[https://wiki.edubuntu.org/HardwareSupport/Machines/Netbooks#Asus%20Eee%201005HA](https://wiki.edubuntu.org/HardwareSupport/Machines/Netbooks#Asus%20Eee%201005HA)


and also a bunch of information about various netbooks and compatability:

[https://wiki.edubuntu.org/HardwareSupport/Machines/Netbooks](https://wiki.edubuntu.org/HardwareSupport/Machines/Netbooks)

.

---

