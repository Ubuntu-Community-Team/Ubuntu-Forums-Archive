---
title: "WUSB54GC Usb Adapter problems"
date: 2007-08-21
forum: Networking &amp; Wireless
---

### Post by l337_G33K on 2007-08-21
Hello, I have a WUSB54GC wireless usb adapter. And it doesn't seem to work. I followed a guide on ndiswrapper, I installed the driver and I check to see the status of it with *sudo ndiswrapper -l* and it says the driver is invalid. Also, when the adapter is plugged in to the computer, a wireless connection shows up (wlan0), I select it, to use it, I entered all of the network information and I still can't do anything on the internet. Any suggestions? Thank you very much

---

### Post by linuxwizard on 2007-08-21
Might be something here that will help you

[https://help.ubuntu.com/community/WifiDocs/Device/LinksysWUSB54GC](https://help.ubuntu.com/community/WifiDocs/Device/LinksysWUSB54GC)

---

### Post by Austin_KW on 2007-08-21
What chipset is that, what windows driver are you using. There should be native linux drivers for it.

Either way, You probably have conflicting drivers. what is the output of the terminal command  "lsusb | grep usbcore". This will list all the drivers using the usb.

---

### Post by l337_G33K on 2007-08-24
I tried to use the script from [https://help.ubuntu.com/community/Wi...inksysWUSB54GC](https://help.ubuntu.com/community/Wi...inksysWUSB54GC) and it finished. But when I go into network settings, there is no wireless connection, when I try to add it manually dhclient in the terminal says access is denied. So any help with that? I am on Xubuntu 7.04. I also tried installing the driver from the linksys cd with ndiswrapper and it looked like it worked, there was a wireless connection when the adapter was plugged in, but you couldn't access the internet, and when I looked with ndiswrapper to see what drivers were installed, it said "rt73.inf: invalid driver". I don't know if I mentioned that previously, but either way. Thank you

---

### Post by linuxwizard on 2007-08-25
I just ran across this thought you might want to look at it

[http://ubuntuforums.org/showthread.php?t=534865](http://ubuntuforums.org/showthread.php?t=534865)

---

