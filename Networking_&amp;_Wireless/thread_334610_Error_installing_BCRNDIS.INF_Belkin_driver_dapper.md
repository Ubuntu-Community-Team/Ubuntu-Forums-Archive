---
title: "Error installing BCRNDIS.INF Belkin driver dapper"
date: 2007-01-09
forum: Networking &amp; Wireless
---

### Post by KitChy on 2007-01-09
Right, I've recently moved over to Ubuntu and i'm loving it. Any other problems I've managed to fix by using google or this forum. But I'm so stuck with this problem. When I enter:

Sudo ndiswrapper -i /"location_of_driver"/"driver.inf"

(obviously I change the location of my driver to where it is actually located on my system)

I get the error

"cannot copy bcrndis.inf at /usr/sbin/ndiswrapper line 135"

...or something along them lines. Well i've search high and low and i'm unable to fix this damn problem. So at the moment i'm currently using Vista (dual boot) until I can fix the problem. Anyone have any solutions?!

Kitch

---

### Post by teaker1s on 2007-01-09
which ndiswrapper version are you using? I found compiling worked far better than repository version also try renaming the driver the same name in lower case

---

### Post by KitChy on 2007-01-19
Okay well I managed to compile and install my driver. Now after I "modprobed" it, ubuntu froze. So I did what anyone else would do and restarted. Now it just seems to hang at "configuring network interfaces" on boot up. I then booted into recovery mode and it said something about it can't access port1 or something along them lines! Anyone know what my problem is now?!

---

### Post by teaker1s on 2007-01-19
recovery kernel terminal 

[COLOR="Red"]sudo ndiswrapper -r[/COLOR]

do you know what chipset your driver is? you may be able to use a different driver for the same chipset that will work:wink:

---

### Post by KitChy on 2007-01-31
Okay well I uninstalled the old version (1.23) and installed the newest version 1.35 and everything is installed with no errors /freezing or anything. Only problem is that my wireless usb network card isn't showing up. When I type iwconfig it says there are no wireless network cards or something I believe. Can't remember the exact words. So now that I have my drivers and everything installed, why isn't my wireless USB card showing up so that I can connect to a network?

---

### Post by teaker1s on 2007-01-31
have you 
[COLOR="Red"]sudo modprobe ndiswrapper[/COLOR]

and also set it to boot in modules?

---

### Post by KitChy on 2007-02-01
Just checked the driver again and it's not install properlly according to ndiswrapper so i'm considering just buying a new wireless USB Stick. Can anyone recommend one to me and that works well with ubuntu dapper.

---

