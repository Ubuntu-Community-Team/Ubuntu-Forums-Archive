---
title: "Ndiswrapper help"
date: 2008-08-13
forum: Networking &amp; Wireless
---

### Post by ZachS on 2008-08-13
Hi, I have an imac and I set up wireless on my Mac. I used these directions:



"sudo aptitude install ndiswrapper-utils-1.9

wget [http://ftp.us.dell.com/network/R151517.EXE](http://ftp.us.dell.com/network/R151517.EXE)
mkdir driver
unzip -a R151517.EXE -d driver/
cd driver/DRIVER/

sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -l
sudo ndiswrapper -m
sudo modprobe ndiswrapper"


and here is the link: [https://help.ubuntu.com/community/MacBook_Santa_Rosa#Wireless%20Setup](https://help.ubuntu.com/community/MacBook_Santa_Rosa#Wireless%20Setup)

my question is, can I now delete R151517.EXE from my home folder? I may assume so because i unzipped it, but I am new to ubuntu so I don't know. Thank you!

---

### Post by caljohnsmith on 2008-08-13
> **ZachS said:**
> my question is, can I now delete R151517.EXE from my home folder? I may assume so because i unzipped it, but I am new to ubuntu so I don't know. Thank you!
You certainly can as ndiswrapper doesn't need that file now that you have installed the driver. Sometimes things can happen though where you might need that driver again with ndiswrapper, so if you don't want to keep it around, I would at least save the website link where you got it; you might be grateful sometime in the future if you have wireless problems at some point.

---

