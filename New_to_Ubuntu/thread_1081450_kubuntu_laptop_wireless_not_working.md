---
title: "kubuntu laptop wireless not working"
date: 2009-02-26
forum: New to Ubuntu
---

### Post by steve joe bob on 2009-02-26
hello i'm mainly a windows user but like to use the linux os's for a hobby really. i recently re partitioned my laptop and put kubuntu on it so i'm dual booting :) i'm having problems with the wireless though... i don't know where to go to see if the drivers are working or not? i also do not know how to scan for available wireless if it is indeed working :P any help would be appreciated.

---

### Post by BOZG on 2009-03-06
> **steve joe bob said:**
> hello i'm mainly a windows user but like to use the linux os's for a hobby really. i recently re partitioned my laptop and put kubuntu on it so i'm dual booting :) i'm having problems with the wireless though... i don't know where to go to see if the drivers are working or not? i also do not know how to scan for available wireless if it is indeed working :P any help would be appreciated.

Well, if you open up your network manager from the menu, it should tell you what devices are connected.  If wlan0 is listed, then your wireless is working.  If it isn't which is a pretty good chance, you probably need to use ndiswrapper to install the Windows drivers for your wireless card.  Hopefully you have an ethernet internet connection at home also, otherwise it's going to be a nuisance downloading the packages and dependencies on Windows and transferring them to Kubuntu.

Here's a guide on how to use ndiswrapper anyway: [http://thelinuxnewbie.blogspot.com/2006/08/installing-wifi-wireless-c_115515845577896146.html](http://thelinuxnewbie.blogspot.com/2006/08/installing-wifi-wireless-c_115515845577896146.html)

---

