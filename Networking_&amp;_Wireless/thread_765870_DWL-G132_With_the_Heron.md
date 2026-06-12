---
title: "DWL-G132 With the Heron"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by Dragothien on 2008-04-24
(Cross Posted from: [http://www.uluga.ubuntuforums.org/showthread.php?t=584014](http://www.uluga.ubuntuforums.org/showthread.php?t=584014)    - Sorry thought might be more likely to be seen here)

Hail and well met!

I am almost a complete linux noob here. At my work I've had some experience with ubuntu 7.10 and I know how to use the most basic of commands. One of my goals has always been to learn linux, and now that I've built myself a brand new gaming computer, I have a 'non vital' spare that I can mess with all I want and use for work and school. I've always wanted to have a linux computer to really dive into the operating system, so here I am.


To get to the point. Just a few days ago I installed 7.10 and found that my usb wireless adapter (DWL G132) did not work with 7.10 out of the box. I found [this]("http://www.uluga.ubuntuforums.org/showthread.php?t=584014") awesome looking post here and tried to follow the directions. Low and behold I couldn't get it to work. I theorize this is because I was messing things up from the get go - I noticed that whenever I tried to do:

> apt-get install build-essential 

It would start to do something but then ask me to insert my linux cd..even though it was already in the drive. So I ignored it and moved on and never got it to work. As I said, my theory is that this is the root of the problem.


Well moving on, as timing would have it, Ubuntu 8.04 stable was just realesed and I decided that as I'm trying to get into linux anyways I'd dive in to the newest possible stable, and I've installed the heron.

In an attempt to follow the same instructions with hope that nothing would really be any different, I very quickly found that running the apt-get install build-essential line did absolutely nothing other than to tell me that it couldn't find that package.


Soooo, I've now registered with the forum and start my first round of questions with:


Can anyone please help me get this wireless usb adapter working on Ubuntu 8.04? Kinda sucks to not have internet when your trying to learn an operating system  ...Or in general..

---

### Post by Dragothien on 2008-04-25
Got it working :D

Basically the instructions are mostly the same. A couple differences I encountered though:

1) apt-get install build-essential  : Works great IF you tell linux to look in the right repositories as oppose to assuming it knows as much.

2)XXx sudo ndiswrapper -i athfmwdl.inf xXX 
      sudo ndiswrapper -i NetA5AGU.inf

Only the NetA5AGU.inf file is required. The ath--.inf file didn't exist, but didn't prove to be necessary either. 

3)I had some problem with the network accepting my key and making the connection, but after using :

>  /etc/init.d networking restart 

a few times over, all was well.

4)Network manager is decidedly misleading - But that doesn't really matter, all the power is in the command line anyways.

Just thought I'd throw up my conclusions.

---

