---
title: "In need of Major Help"
date: 2008-04-06
forum: Networking &amp; Wireless
---

### Post by Lloyd09 on 2008-04-06
Ok, I just recently found out about Ubuntu and decided to give it a go. I got it to install and get it to adjust to my screen. And now i am trying to get it so i can connect to the internet through my wireless card. My wireless card is a Linksys by Broadcom Corp., BCM4306 model, and has the BCM43xx ver: 2.6.22-14 driver. I literally need a stupid person directions of how to get this to work. I have used the documentation and forum area to try to solve it on my own, and have had no luck. If anyone could help me here that would be great. 


P.S. Sorry if someone already went through this.

---

### Post by pseudo-random on 2008-04-06
[http://ubuntuforums.org/showthread.php?p=1071920&mode=linear](http://ubuntuforums.org/showthread.php?p=1071920&mode=linear)

---

### Post by mr.loco on 2008-04-06
First follow what the person before me has posted, if that wont work, try this.

STEP 1: install ndiswrapper

[LIST=1]
[*]Open up synaptic package manager (it is in the administration menu)
[*]search for ndiswrapper
[*]select ndiswrapper
[*]Click apply changes
[*]synaptic will tell you to install another package, do it.
[*]Close synaptic when its all done installing
[/LIST]

Step 2: get windows drivers
[LIST]
[*]Find the CD for the card or otherwise get the windows driver from somewhere.
[*]copy the folder with the drivers to somewhere on your somputer (doesnt really matter where, jsut make sure you know where youre putting them.
[/LIST]

Step  3: follow this HOWTO_*** from step 4***_
[http://ubuntuforums.org/showthread.php?t=31926](http://ubuntuforums.org/showthread.php?t=31926)

---

### Post by tonyh703 on 2008-04-06
i did a backup of all my drivers from windows, and the driver for wireless is bcmwl6.sys.  It will not install this driver on ubuntu.. any ideas??

---

### Post by Lloyd09 on 2008-04-06
> **pseudo-random said:**
> [http://ubuntuforums.org/showthread.php?p=1071920&mode=linear](http://ubuntuforums.org/showthread.php?p=1071920&mode=linear)

tried couldn't get past get fwcutter to install

---

### Post by tonyh703 on 2008-04-06
I typed in command lshw -C network, and I am getting everything except a logical adress and serial number... What can be the cause of this???

---

### Post by unutbu on 2008-04-06
Hi Lloyd09, I think you couldn't install bcm43xx-fwcutter because it is in the universe repository, and you need internet access to reach the repo.

Are you by chance trying to connect to a wireless router which has ethernet ports?
If so, perhaps you can place your computer (temporarily) near to the router, and use an ethernet cable to connect to the internet. Usually this is much simpler than connecting wirelessly. Then you can install bcm43xx-fwcutter and hopefully follow the rest of the howto guide.

---

