---
title: "Help on college campus"
date: 2006-08-13
forum: Networking &amp; Wireless
---

### Post by Scheater5 on 2006-08-13
I'm trying to get my ubuntu laptop on the wireless network of my college campus, but I'm having issues.  First of all, I need to actually get on the network - I used to use the ubuntu Wireless Assistant, but this desktop no longer has that.  Is there a way I can get on without that program (so that I could download it, and then use it in the future) or can I use the Windows machine I am writing this on to download the files, and then transfer them to the laptop?
But, more importantly, the network here uses Clean Access Agent, and anyone who isn't logged in can do only the most minimal of tasks (mostly related to aquiring CAA) on the net.  Is there some way of getting around this?  Thanks!

---

### Post by jeff_ on 2006-08-13
You can download the packages on a windows machine and then transfer them to your ubuntu laptop.

What's happening when you try to connect to the wireless network? i.e. what are your iwconfig and ifconfig outputs?

If you're using linux you probably won't have to use Clean Access Agent, but will have to log in from time to time on the web. From searching google this seems to be the dominant policy.

---

### Post by Scheater5 on 2006-08-13
Ok, I am really a linux noob - where do I get the packages on the net, and then where do I transfer them to on my laptop?

And I really don't know what the iwconfig and ifconfig outputs are - I don't even know what iwconfic and ifconfig means, other than it probably has something to do with a command prompt, a part of linux I am painfully slow at learning.  I appreciate your patience with me.  :D

---

### Post by Gun_Smoke on 2006-08-13
Look around here... [http://packages.ubuntu.com/dapper/net/](http://packages.ubuntu.com/dapper/net/)

WiFi Radar might do you good.

Click on any of them, scroll down and look for your architecture.  Download it and put it on a disk.  

Here is WiFI Radar, [http://packages.ubuntu.com/dapper/net/wifi-radar](http://packages.ubuntu.com/dapper/net/wifi-radar)

---

### Post by Scheater5 on 2006-08-14
Well, apparently my problem was a driver issue - not entierly sure why the driver wasn't running in the first place, I've never had issues with it before.  But, I have a copy of the windows version of the Intel proset driver, so I loaded up ndiswrapper and plugged in the proset driver, and lo and behold, I suddenly had an active connection.  CAA let me sign in, and now I'm up and running.

---

### Post by Gun_Smoke on 2006-08-14
Cool beans.

---

### Post by jeff_ on 2006-08-14
> **Scheater5 said:**
> Well, apparently my problem was a driver issue - not entierly sure why the driver wasn't running in the first place, I've never had issues with it before.  But, I have a copy of the windows version of the Intel proset driver, so I loaded up ndiswrapper and plugged in the proset driver, and lo and behold, I suddenly had an active connection.  CAA let me sign in, and now I'm up and running.

Congrats! For future reference you can open up a terminal and type 'iwconfig' or 'ifconfig' and press enter to see the output I was talking about.

---

