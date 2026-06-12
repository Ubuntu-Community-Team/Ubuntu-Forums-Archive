---
title: "[how to] how to install what ever wireless card with ndiswrapper on TWO ways"
date: 2008-08-22
forum: Networking &amp; Wireless
---

### Post by U-P-S on 2008-08-22
First way: (it works on hardy 100%!)
enable all ubuntu.com's additional repos
type
```
sudo apt-get install ndisgtk ndiswrapper-common ndiswrapper-utils-1.9
```

Then, simply go to System, Administration, Install Windows wireless drivers.
Open it, type your sudo password, click Install new driver, find your .INF file where ever it is, click DONE.
enable your hardware drivers in System-administration-hardware drivers
Then reboot.



Second way (probaly wont work on hardy... idk why, look for marked line, it fails, use first way)

enable all ubuntu.com's additional repos
type
```
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
```

Then, insert your CD with drivers in CD rom,
Find folder/directory drivers
Get in and copy 2 files, called <name-of-driver>.inf and <name-of-driver>.sys .
Notice that you may have a <name-of-driver>**a**.inf but don't use it!
So, copy those two files into your home folder, open terminal and start typing line by line:

```


sudo ndiswrapper -i <name-of-driver>.inf
sudo ndiswrapper -l
sudo modprobe ndiswrapper           --->fails in hardy
sudo ndiswrapper -m                 --->fails in hardy


```

enable your hardware drivers in System-administration-hardware drivers

Then, hopefully reboot your computer and try to connect to wireless with your fresh installed wireless card

HINT: if you fail at sudo ndiswrapper -i <name-of-driver>.inf , you need to remove it, with 
```
sudo ndiswraper -r <name-of-driver>
``` INPORTANT: without .INF!!

So, that was my first how-to on my ubuntu community's wiki page, it has also how to make internet from wlan to spread into LAN, that'd be next howto =)

RYL! (reed ya later :))

---

