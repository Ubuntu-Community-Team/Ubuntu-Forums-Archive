---
title: "Wireless problems"
date: 2010-02-05
forum: New to Ubuntu
---

### Post by Marc St Louis on 2010-02-05
I decided to take the plunge yesterday with ubuntu.  I had an old HD that I wiped and installed in my work PC.  I kept my windows installation on the main drive and used the smaller drive for ubuntu.  Installation went reasonably well.  I do have connection problems though.  

The problem is that Ubuntu doesn't seem to see the USB wireless adapter as it's not listed with the other hardware. It does see the memory card reader that I have though.  The adapter I am using is an Edup ED-1296.  It works well on Win XP and Win 2000 but not Ubuntu.  Oddly I tried unplugging it and a window opened saying that the wireless network was disconnected.  

I've tried finding a solution through google but nothing comes up.  Does anyone know of a solution to this problem?

---

### Post by Cabs21 on 2010-02-05
you need to update your drivers first.  SYSTEM>ADMINISTRATION>HARDWARE DRIVERS

make sure you are connected to the web to update through a LAN cable in your case.  Otherwise you will not find any drivers.

also try entering this into the terminal and posting the results on this thread

```
ifconfig
```

```
iwconfig
```

---

### Post by Marc St Louis on 2010-02-05
> **Cabs21 said:**
> _you need to update your drivers first.  SYSTEM>ADMINISTRATION>HARDWARE DRIVERS_

make sure you are connected to the web to update through a LAN cable in your case.  Otherwise you will not find any drivers.

also try entering this into the terminal and posting the results on this thread

```
ifconfig
``````
iwconfig
```

That is going to be next to impossible to do.  My work pc is in my shop and the modem is in the house and ne'er the 2 shall meet.  Is there another way?

---

### Post by Cabs21 on 2010-02-05
yes but I do not know exactly how to do it.  You need to find out what wireless card you have (the codes above can help you find out) then on another computer find the drivers DL them to a portable media then install them in the correct location on your shop machine.  There is a special way to do this that I have no idea how to but some searching on this forum will post several examples as to how to do it right.

---

### Post by Tholley on 2010-02-05
you might try this also, since you are using a usb adapter, make sure you have full rights over all usb devices.
 
System/Administration/Users and Groups
click on you user-name
click on Unlock
Properties button/User Privileges
check off every category
 
Even if that doesn't actually fix your problem, it should be done anyways.

---

### Post by bkratz on 2010-02-05
> **Marc St Louis said:**
> That is going to be next to impossible to do.  My work pc is in my shop and the modem is in the house and ne'er the 2 shall meet.  Is there another way?




If you go to the terminal (Applications>>Accessories>>Terminal ( in Ubuntu)) and type lsusb (that is LSUSB in lowercase) and either decode or copy/paste the output back here it should give the part number for your adapter and the code xxxx:xxxx

---

### Post by Marc St Louis on 2010-02-05
Here's the results from running the ifconfig and the iwconfig code, took me awhile since I had to install the printer and then print and scan the text

---

### Post by Marc St Louis on 2010-02-05
I will stumble my way through the rest of the suggestions

---

### Post by bkratz on 2010-02-05
> **Marc St Louis said:**
> Here's the results from running the ifconfig and the iwconfig code, took me awhile since I had to install the printer and then print and scan the text

the output says "mode-managed" so I believe you have the correct driver installed whatever you usb dongle is. It also says that "power management is on so do you have a switch or key combination that enables wireless? Is it turned on in the bios? In the terminal do a

sudo iwlist scan

it requires your password which will not be echoed to you, just hit enter. You should see all the wireless A/P's around you and if they are encrypted or not.  If you see this your wireless is working and just needs to be associated with your AP (the easy part).

---

### Post by Marc St Louis on 2010-02-05
Here's the result from running - lsusb 

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 148f:2070 Ralink Technology, Corp.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 1976:1307 Chipsbrand Microelectronics (HK) Co., Ltd
Bus 002 Device 002: ID 0e8f:0016 GreenAsia Inc.
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


This is the result of running - sudo iwlist scan

1o  Interface doesn't support scanning.

eth0  Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning

wlan0  No scan results

---

### Post by bkratz on 2010-02-05
This is your wireless
Bus 001 Device 003: ID 148f:2070 Ralink Technology, Corp.

Searching for that ID number on Google shows this

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1285828](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1285828)

---

### Post by crf on 2010-02-05
You could try:

sudo iwconfig wlan0 essid *your network's name*
sudo iwconfig wlan0 key *your wireless password, in hex*
sudo dhclient


// I have two computers. On one, I use network manager. On the other, I had constant issues with network manager, so I uninstalled it, and use the above procedure to connect.

---

### Post by Marc St Louis on 2010-02-06
I've tried some of the suggestions but no go.

---

### Post by Marc St Louis on 2010-02-07
> **bkratz said:**
> This is your wireless
Bus 001 Device 003: ID 148f:2070 Ralink Technology, Corp.

Searching for that ID number on Google shows this

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1285828](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1285828)

I've checked out that thread but honestly most of this is beyond me, I'm getting a headache just reading these instructions let alone trying to follow them.  Perhaps Ubuntu is not for me, to bad because I like the rest of it

---

