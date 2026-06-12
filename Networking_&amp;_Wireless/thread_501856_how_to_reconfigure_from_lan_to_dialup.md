---
title: "how to reconfigure from lan to dialup?"
date: 2007-07-15
forum: Networking &amp; Wireless
---

### Post by 67GTA on 2007-07-15
I was going to install Ubuntu XFCE edition on my aunt's emachine. I have a lan connection. She uses dialup. If I install and update with my connection, how do I change that once I get it back to her so it uses dialup? I'm assuming the installer will set it up according to my connection info. I've never messed with linux/dialup before. Sorry for the stupid question.

---

### Post by scrooge_74 on 2007-07-16
You are not stupid is just aint plain simple :)

is your aunt lucky enough to have a modem supported in linux?  

I think you have to tell the system to use the modem using something like ppp to dial out.  Check [here]("https://help.ubuntu.com/community/DialupModemHowto")

---

### Post by Bartender on 2007-07-16
You mean Xubuntu, right?
First off, don't even go into the Networking section.  The Networking dial-up GUI has been broken since Dapper.  Take a look at these steps to get a fresh Ubuntu 7.04 dial-up functioning and see if it helps any
[http://ubuntuforums.org/showthread.php?t=480717](http://ubuntuforums.org/showthread.php?t=480717)
I'm assuming that the "touch" command does the same thing in Xubuntu but it might not.  Whatever command you need to just make a blank file, that's what you need to do.
Then use wvdial, or pppconfig as Duncan describes.

All of this is, as scrooge mentions, contingent on having a modem that works in Linux.  External serial is the most reliable.

Check out this cute little USB modem Zoom just released a few days ago.  The 3095, the top one on this page.  I want a dozen.
[http://www.zoom.com/products/dial_up_external_usb.html](http://www.zoom.com/products/dial_up_external_usb.html) 
They claim it works in Linux; I hope they're not kidding.

A guy was working on a similar project a few days ago
[http://ubuntuforums.org/showthread.php?t=497984](http://ubuntuforums.org/showthread.php?t=497984)

---

### Post by 67GTA on 2007-07-16
Well, I actually decided to install Ubuntu instead. I wasn't sure if her comp would have enough memory or not. She has an ETower 800 with 800MHz Intel Celeron proc-256MB DRAM-20GB hard drive-56K v.90 modem. I ran the live cd on it, and I was surprised how well it ran. I can probably get her connected with Gnome. I've never messed with XFCE much. Thanks for the info.

---

