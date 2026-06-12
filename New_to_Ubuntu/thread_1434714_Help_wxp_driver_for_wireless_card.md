---
title: "Help w/xp driver for wireless card"
date: 2010-03-20
forum: New to Ubuntu
---

### Post by urez2beat on 2010-03-20
As a newbie using Linux /Ubuntu I have been pleasantly surprised at how great Linux is!!!!
I have noticed that the wireless card on my acer aspire 5516 Laptop's performance leaves 
a little to be desired. For example under windows download speeds of 2 Gb/s, under Linux
like 35kbs/s. what gives? why such a difference?( and what's up with the gaming graphics in Linux? Why do all the games looks as though your playing Pong???? Anyway back to the wireless card so I tried installing the Windows XP Wireless driver which seemed to improve the performance of the wireless card but then created other problems like having to reboot all the time to see flash drives etc..So I re-installed Linux and was just wondering why I can't get performance I had in Windows. If anyone out there has had a similar experience
your input would be greatly appreciated. Thanking-Whoever-in-Advance 
                                                                                                         urez2beat

---

### Post by coffeeaddict22 on 2010-03-20
Hi, and welcome.
If you've got a 2 Gb/sec wireless card, you'd better pass on the details.  Nobody's making one of those readily available; the usual standard is 54 MBits/sec.  It's more likely that the quote "There are lies, damned lies, and statistics" applies.
To define the download speed, it'd be useful to try downloading a decent sized file and check the times in each OS; I suspect you'd find the times are pretty equivalent.  If you are having problems, make sure you've gone into System/Admin/Hardware Drivers and enabled the proprietary drivers.

This will also fix your graphics problems; ATI and NVIDIA both have proprietary drivers that can't be included in the vanilla install, but can be installed via the Hardware Drivers page.

Post back if you've got any problems.

---

### Post by Mark Phelps on 2010-03-21
Before you go off hunting for Video drivers, if you've got an ATI card, post the model number here, first.  Unless it's one of the newer HD 3x/4x/5x cards, forcing an install of ATI drivers will only trash your display and force to boot into a console mode to remove them.

---

### Post by urez2beat on 2010-03-21
I'm not sure what you mean by "pass on the details"I routinely download files at 1.5 Gbs/more. Windows XP w/Internet Download manager.Not sure why that would seem odd to you.I just know that I've yet to download files in Linux at anything close to that and was wondering if that's just the way Linux normally operates anyway thanx for the response I guess Linux can't download at those speeds and I'm okay with that. again thanx urez2beat

---

### Post by coffeeaddict22 on 2010-03-21
To quote on transfer speeds ([http://www.lyberty.com/encyc/articles/kb_kilobytes.html]("http://www.lyberty.com/encyc/articles/kb_kilobytes.html"):
"Gigabit Ethernet [1000Base-T] is capabile of speeds up to 1000 mbps (mega-bits per second), or 1 gbps."
To get KB/s values from bit rates, you must divide the total number of bits by 8, then divide by 1,024.

It's not likely your connection is downloading 1 GB per sec, unless you're on very specialised hardware

Like I said, lies, damned lies... and statistics.

---

