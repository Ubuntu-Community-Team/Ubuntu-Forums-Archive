---
title: "TrendNet TEW423PI not working"
date: 2007-05-27
forum: Networking &amp; Wireless
---

### Post by Xylent on 2007-05-27
Hello

Im new to linux. So farthe installation of Ubuntu went really smooth. however the problems started when it came to setting up the internet connection. 

I downloaded the deb package of ndiswrapper, followed the instructions on how to install them and in order.

I black listed the bcm43xx driver or whatever that was as the instructions said.

I followed the rest of the isntructions from here [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) Until about the point after typing in 'ndiswrapper -l' 

it says that the mrv8335.inf driver is installed, and it detects the PCIID of the wireless card. All the isntructions after this doesnt work. the wireless card is not showing in the networking window. All other instructions after that point to that fact that the driver or ndiswrapper isnt working. BTW, I ran into driver problems, right now I have 3 different drivers for the TEW423IP card, turns out the I got the wrong release from the website, could that be a reason? Also the graphical interface for ndiswrapper doesnt work after installing the second wrong driver.

What should I do? Can I just uninstall Ubuntu and start everything from scratch? If there a quicker way to get the wireless card installed?

The card I have is TEW-423 B1.1R



Thanks.

---

### Post by hookzilla on 2008-07-05
I am trying to get a TEW423PI ver B1 to work in Hardy/wubi and haven't had much luck either.  It also uses a Marvel chipset.  I've tried ndiswrapper with network manager and wicd.  I had it working in Gutsy using wicd at one time, but that was just a test.  You may want to try that.   In Hardy, I have a conflict of some kind, but you may be a different situation.  If I make any progress I'll let you know, but it's not my highest priority right now.  Also, any help will be appreciated.

---

