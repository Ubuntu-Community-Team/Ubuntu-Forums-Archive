---
title: "Netgear driver + ndiswrapper"
date: 2006-12-04
forum: Networking &amp; Wireless
---

### Post by fhslacrosse13 on 2006-12-04
I'm probably going to install ubuntu 6.10 tomorrow on my Dell desktop but first I need to figure out a way to get my Netgear USB wireless adapter to work.  I will not have a direct internet connection to the desktop, but I will be able to download files onto my laptop and transfer them over via a usb harddrive.  I was just wondering if anyone had a very discriptive walkthrough on getting the wg111v2 drivers for the adapter working in Ubuntu.  I've tried in the past but have not had any success with the tutorial on the ndiswrapper page.  Please Help me.  I am new to linux so I really need help with this one.

---

### Post by FrodoB on 2006-12-05
This device seems to have about a 50% chance of just working out the box with Edgy using the kernel driver. 

Temporarily turn off all security on your access point router. Boot the live CD and after it is up insert the device and wait about 10 seconds, and then open a terminal and see if you can get positive results from the following:

sudo iwlist wlan0 scanning

You may need to try this a few times before it finds the access point.

If you see your router then see if you can associate:

sudo iwconfig wlan0 essid My_Essid

run iwconfig and see if wlan0 reports the MAC identifier of your access point, if so you are connected.

Run dhclient to see if you can get a route to the internet, your router is connected to the internet, right?

sudo dhclient wlan0

If all of this works from the live CD you are on your way. You can do an install with some level of confidence and you do not need ndiswrapper. Else you are probably going to need ndiswrapper.

---

