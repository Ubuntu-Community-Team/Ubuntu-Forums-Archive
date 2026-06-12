---
title: "Wireless LG E300"
date: 2008-11-18
forum: Networking &amp; Wireless
---

### Post by Chris_Ba on 2008-11-18
Hello, 
I just got a new LG E300 laptop and installed Xubuntu, I am somewhat familiar with it because I used it on my old laptop, but I'm having some trouble getting the wireless internet working. I've installed ndiswrapper, and ndisgtk. I'm trying to figure out what chipset I have but all I get when I type lspci in terminal is a thing that says "ralink 0871" or something like that. I also tried to use the driver that came on a CD with the computer. the Wireless Windows Driver applet recognizes that its a driver but claims no hardware is present. I'm a little bit lost, any help is appreciated.

---

### Post by Chris_Ba on 2008-11-18
Alright, I figured out my card is Ralink RT2860, I downloaded the driver off their website and now following these instructions ([https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)) I'm trying to unpack the exe using cabextract so i can get the inf and sys files. But when I type in the commands " cabextract RT2860.exe" it says "RT2860.exe: no valid cabinets found". Any help?

---

