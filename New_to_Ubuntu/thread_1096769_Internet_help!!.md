---
title: "Internet help!!"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by zickx on 2009-03-15
So basically, I started using Ubuntu a few days ago but have been persistently having internet problems. My wired connection doesn't seem to be working I have a Westel router btw. When i try to connect the Ethernet cord, ubuntu reads it but after a few seconds or so it says the internet connection has been disconnected.I also have a wireless network but i have also been having problems connecting to the internet wireless.

Please help I can't even update or install software because of not being connected!!! :/

---

### Post by diablo75 on 2009-03-15
Something you might check, if possible, is to open your routers configuration from another PC or laptop and look at the "attached devices" listing.

You should also check to ensure that your router has DHCP enabled so that it will assign newly attached devices a dynamic IP address automatically.

As for your Wireless... You might have to install some proprietary drivers to get it working (check System>Administration>Hardware Drivers).

Alternatively you could download the ndiswrapper program from another computer and take it to your non-connected PC via a USB flash drive.  The [community documentation for ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") will tell you what you need to download (there are two deb packages you'll need for it to work).

---

