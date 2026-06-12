---
title: "Not able to connect to hotel provided wireless Internet"
date: 2007-02-06
forum: Networking &amp; Wireless
---

### Post by ctsdownloads on 2007-02-06
Using an Ubuntu friendly wireless card - check. Actually, I have tried this with no less than three cards that work out of the box on any residential wifi network. I can connect to the internet just fine on *_any_* wireless access point just so long as their is no captive portal involved. If there is an http login needed for 'Net access, then no way...

So I am confused? Why would I be able to connect to any residential access point, but not be able to connect to wifi offered by a hotel (tried 5 of different hotels), two bookstores, T-Mobile type hotspots, or pretty much anything with a login page for access? I have cleared my cache (/etc/resolv.conf), reset the interface itself, even swapped it out for another one. 

What's really maddening is that I can even connect with ease to any of these locations using a Mac or via Win XP. I askedthe provided tech support for each if Linux was being blacklisted, I was told no. 

So what is the problem? Seriously, this is *not* a minor issue should this prove to not just be a problem on my end. *If* this is a wide spread problem, then it is a definite show stopper. Please help, I have been looking for [help on this]("http://ubuntuforums.org/search.php?searchid=14078639") for no less than four days - does no one have issues connecting to hotel wireless using Ubuntu??

Using Edgy fully patched, every Linux-friendly wifi card I own, no firewalls, network manager and network monitor software. No IP is being assigned or offered.

---

### Post by ctsdownloads on 2007-02-09
Am I alone here?

---

### Post by Super_6_4 on 2007-05-10
I managed to get my laptop to connect on a Best Western provided wifi network. It loads to a default page, and from there you're free to surf. I don't know the specifics of why it worked yet... For some reason, my Ubu wouldn't load my wifi module at boot-time so I did the following in terminal:

1. sudo modprobe ndiswrapper
2. sudo iwlist ethXX scan ( XX is whichever wireless connection)
3. sudo iwconfig ethXX essid SCAN_RESULT (the scan should pull up all the networks, enter one of the SSID's)
4. reboot

I ran through that and it started working. I hope this helps - sorry if its new you've read before.

running: HP Pavillion dv6000 w/Dell 1390 wifi ; Feisty Fawn

---

