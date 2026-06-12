---
title: "Belkin F5D7050 ver 3000 installation problem"
date: 2007-03-13
forum: Networking &amp; Wireless
---

### Post by gewitty on 2007-03-13
Having successfully completed my first installation of Ubuntu on my desktop PC (my first ever experience of Linux). I was really impressed with it, so I moved on to make the same installation on my laptop.

Everything worked pretty much without a problem on the desktop machine, including the wireless network setup. However, when I got to this stage with the laptop, it became apparent that the Belkin F5D7050 wireless USB adapter was not compatible (the desktop machine uses a different Belkin model). I did some research and found the following instructions for installing the correct drivers  - [http://tinyurl.com/2qnb2o](http://tinyurl.com/2qnb2o). After several arduous hours of following these, I thought I had the thing cracked. But when I reached the final stages, I realised that everything was not OK at all.

At Step 6, I entered the command to edit the interfaces file and got a terminal message saying:

GnomeUI-WARNING ** : While connecting to session manager: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

Despite this, the interfaces file opened in text editor and I was able to make the changes specified. I then saved the file and ran sudo modprobe rt73, followed by iwconfig. The result of this was:

lo               no wireless extensions
eth0          no wireless extensions
sit0            no wireless extensions

So now I'm stuck. I don't have enough knowledge or experience of Linux to understand what went wrong or where. I was sure I followed the instructions accurately, but obviously something didn't happen right.

If anyone can point me in the right direction (keep it in simple language please), or better still give me a less long-winded way to get the USB wireless connection working, I'd be most grateful.

---

