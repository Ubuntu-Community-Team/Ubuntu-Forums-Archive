---
title: "Help! Can't get my wireless F5D7050 version 300 to work!"
date: 2007-02-17
forum: Networking &amp; Wireless
---

### Post by allstarrunner on 2007-02-17
I have been reading up on this for hours and tried many different things and for the life of me I cannot get this thing to work!! Here is what I know: 
I have the Belkin F5D7050 version 3000 compatible with 802.11b and 802.11g
I ran sudo lshw and said this below, so I assume that it is seeing the card:

*-network DISABLED  (***NOTE:after I did the stuff I listed below, it no longer says disabled which I check it, but my wireless still doesn't work)
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:11:50:c1:a0:3e
       capabilities: ethernet physical wireless
       configuration: multicast=yes wireless=IEEE 802.11g

I have downloaded the drivers for this card (although I don't know where to put them :o):

rt73.cat
*.inf
*.sys

I also did this following some other instructions and got this error:

allstarrunner@allstarrunner:~$ cd /home/allstarrunner/Desktop
allstarrunner@allstarrunner:~/Desktop$ sudo ndiswrapper -i rt73.inf
Installing rt73
allstarrunner@allstarrunner:~/Desktop$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-11-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

and I have no idea what that means!

And when I go to "Networking" I have two wireless options: "wireless connection (wlan0)" and "wireless connection (wmaster0)"
I have clicked on properties and filled in the info I need to and nothing is working as of yet.

any help would be GREATLY appreciated!!!!
And please remember that I JUST switched to linux so what seems obvious to the person explaining details might go over my head!
Thanks in advance for any helpful posts!

---

