---
title: "Network Manager not connection to wireless"
date: 2007-09-30
forum: Networking &amp; Wireless
---

### Post by Prothoss on 2007-09-30
I am a relatively new Ubuntu user using 7.04. I installed a bunch of updates and now my network manager will not connect to wireless networks. However I can connect using:

sudo ifconfig eth1 up; sudo iwconfig eth1 essid <WIRELESS NETWORK NAME>; sudo dhclient eth1

Network manager can see the network, but it will not connect to the network.

I am on a Presario C500 Series laptop and am using ndiswrapper with Network Manager being the latest version. Has anyone encountered/solved this problem?

---

### Post by scrooge_74 on 2007-10-01
Network manager is still buggy.  The problem also depends on your type of card.

You can also try using wifi-radar to connect

Also did you put the card in roamming mode?

---

### Post by Prothoss on 2007-10-01
Wifi radar worked fine, thanks. And yeah, my card is in roamming mode.

The problem seems to have fixed itself, after fiddling around a bit I gave up, suspended it and when I came back it was working again... strange that it fixed itself when suspended but not reset though... oh well!

---

### Post by scrooge_74 on 2007-10-01
I had the same issues, I  did all sort of things and it will just come back sometimes by itself.  going into suspend mode had some issues it seems the card would not go down properly.  Latter I had more problems after a kernel update in which the laptop would mot suspend properly.

In the end, since I was on the mood to try something different I went with Debian 4.1 plus xfce4. Never tried this on a laptop, good thing i have more experience now, this is not something noobies should do. Had I done this with Debian a year ago I would probably had gone bonkers

---

### Post by cameronjcc on 2007-10-01
What kind of Wireless Card do you have?

---

### Post by Prothoss on 2007-10-01
I thought the problem was fixed, but alas, it strikes again! Same issue as before...

I have been unable to find what card I have, I am pretty sure it's a Broadcom 1390 WLAN card, I used [this HOW-TO to set my card up initially]("http://ubuntuforums.org/showthread.php?t=297092"). Wifi Radar connects fine.

Network manager can see the networks but cannot connect to them.

---

### Post by Prothoss on 2007-10-02
I think the issue may only be with unprotected networks. Network manager seems to have no issue with connecting to networks with WEP keys but when I try to connect to an unprotected network, it simply does not connect. Not sure if this information is helpful or not...

---

### Post by cameronjcc on 2007-10-10
I did this:

1) Blacklist bcm43xx driver
Open a Terminal window
Type "sudo gedit /etc/modprobe.d/blacklist"
At the bottom add the lines

# get rid of the default kernel drivers
blacklist bcm43xx

2) Make sure network interfaces file is correct
Type "sudo gedit /etc/network/interfaces"

Remove all comments ('#') that you see so that all devices arehandled by the default network manager.

I would reboot here and make sure the wireless light goes out

3) Install ndiswrapper

Put in Ubuntu CD. Open Synaptic Package Manager (ClickSystem -> Administration -> Synaptic Package Manager),search for ndiswrapper-utils, and install it.

You could also type "sudo apt-get install ndiswrapper-utils 
(IF you are not using ubuntu then make sure you have ndiswrapper-utils somhow installed)

4) Conigure ndiswrapper
Open terminal and navigate the folder where your drivers are."cd Desktop/bcm43xx"

Type "sudo ndiswrapper -i oem3.inf"Then type "sudo ndiswrapper -m"
Type "sudo gedit /etc/modprobe.d/ndiswrapper"

Change the one line in that file to read "alias eth1 ndiswrapper"

Now you should reboot so all the drivers load.

Once you reboot the wireless light on your laptop should be lit.


 Let me know how it goes...

---

