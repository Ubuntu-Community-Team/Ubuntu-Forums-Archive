---
title: "invalid driver errors for Belkin wireless PCI card"
date: 2007-01-07
forum: Networking &amp; Wireless
---

### Post by miraje on 2007-01-07
Hi everyone,

I've recently installed Ubuntu 6.10 (kernel 2.6.17) as a dual-boot with XP, and I'm having issues getting it to work properly with my wireless network card (Belkin Wireless G Desktop PCI card - F5D7000 most likely, although I can't find anything on my computer that will tell me the model number of the card). I've gone through five or six tutorials to try to get it working, but none of them really address what to do when the driver is invalid. Here's what I've done so far:

-installed all versions of ndiswrapper off the ubuntu CD

-copied the card's driver (bcmwl5.inf) over to ubuntu's desktop from my Windows drive

-ran ndiswrapper with the driver -- installed correctly

-"sudo ndiswrapper -i bcmwl5.inf" says that the driver is installed

-sudo ndiswrapper -l" says that the driver is invalid

The driver works perfectly in Windows, so I'm not sure why Ubuntu's not liking it. Another issue I'm having is that the Network Manager keeps disabling the wireless card and defaulting to the wired connection even though there is nothing plugged into the wired ethernet port. 

I'm not sure what to do from here. Is there another driver that I should be looking for? Any help would certainly be appreciated!

---

### Post by n00b@linux on 2007-01-07
You can get details of your wireless PCI card using the 'lspci' command:```
lspci
```This lists details of ALL PCI devices.  If you want more information type```
sudo lspci -v
```The '-v' stands for 'verbose'.

Then look it up on this page:
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported) and see how you go from there.

P.S. ndiswrapper on Edgy is broken: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper/edgy?highlight=%28WifiDocs%29%7C%28ManufacturerModel%29%7C%28AND%29]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper/edgy?highlight=%28WifiDocs%29%7C%28ManufacturerModel%29%7C%28AND%29")  I had to recompile from source: [http://www.ubuntuforums.org/showthread.php?t=333355](http://www.ubuntuforums.org/showthread.php?t=333355)

---

### Post by miraje on 2007-01-07
Well, it's a F5D7000 Rev 03, so according the link you provided it sounds like I have my work cut out for me to get it working.  ](*,)  

At least I have a little bit of direction now. Thanks. :)

---

### Post by miraje on 2007-01-07
I just tried using the bcmwl5a.inf driver provided by the Dell package included in the link, and that's also invalid.

---

