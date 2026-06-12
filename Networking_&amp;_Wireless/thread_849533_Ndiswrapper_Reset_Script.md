---
title: "Ndiswrapper Reset Script"
date: 2008-07-04
forum: Networking &amp; Wireless
---

### Post by Syncman9 on 2008-07-04
Hi All, 

I'm looking to create a reset script, which I can run via terminal, to reset my wireless connection when it stops working. 

I know until a fix / solution is found, I have to live with it, but I'm looking for a script to reset the device/connection for the time being. 

Any help appreciated

---

### Post by kevdog on 2008-07-04
Want do you want in your script?  

Youve seen this post:
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

### Post by Syncman9 on 2008-07-04
Basically, I'm using a Netgear USB dongle to connect to my wireless network. 

I'm looking to create a script to take it down and re-start it, so I can avoid having to power down my machine each time. 

Thanks

---

### Post by kevdog on 2008-07-04
Take the interface down like eth1 or wlan0 or unload the ndiswrapper kernel module.  The two are not one in the same.

---

### Post by Syncman9 on 2008-07-04
ok, 

But how do I unload the ndiswrapper, so I can set this up in a script. 

Sorry for my ignorance, but I'm still learning. 

Thanks

---

### Post by kevdog on 2008-07-04
sudo ifconfig <interface> down
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo ifconfig <interface> up
...
...
..


The remainder of the script ... is used to actually complete the network connection (if this is what you want to do).  This would come from the link I pointed you to earlier.

---

### Post by supercommodore on 2008-07-19
KevDog: Thank YOU! :-) I finally found a way to reset my WIFI connector without having to do the dreaded 15 reboots until I get 5 minute of connection time before it crashed.

Tried compiling the iwl* drivers that lead to a dead end for an Intel 4965AGN internal wifi on a Toshiba laptop.  Once you get it installed with Windows drivers with ndiswrapper. (There are 1,000 places to look for those instructions via google. Not going to recount them here.)

With your above command structure of:

sudo ifconfig wlan0 down
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper (reload it in)
sudo ifconfig wlan0 up

Anyone other connection stuff can be found at your above link.  So I guess I'll be writing a small executable script with this, so *each* and every time I have a problem with this driver, just click on the script.

Thanks again and hopefully this script will help others who have spent a week going up and down init.d, modprobe.d and many other trees of Linux trying to find a command that will just reset the darn driver!

I'm using Mepis on this machine but have a dual boot of ubuntu Hardy Heron with the same problem.  So this just cleared up my masterful headache!

---

