---
title: "Multiseat HTPC - can I do it?"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by scrote on 2009-09-20
Hi, I'm new to the boards and also to Linux and was hoping to get some advice about an idea I had.

I'll keep it simple for my own benefit, at least until I have a better idea of what's going on :)

Basically, I am wondering if it is possible under Linux to set up a multiseat HTPC. One machine that can serve two concurrent users and handle independent requests for streaming 1080p media content and then output to separate displays. Imagine a HTPC in the dining room, one user with a keyboard and mouse in the lounge, and another user in the bedroom with a keyboard and mouse, each watching different movies from the same box. 

I have two threads started on other forums regarding this if you're interested in more detail.

[http://www.htpcforums.com/index.php?showtopic=670](http://www.htpcforums.com/index.php?showtopic=670)

[http://forums.whirlpool.net.au/forum-replies.cfm?t=1284677](http://forums.whirlpool.net.au/forum-replies.cfm?t=1284677)

Thanks for your time,
-John

---

### Post by LowSky on 2009-09-21
Personally I rather run a server on the backend with a frontend for one tv and another pc used as a frontend for the other tv, but that costs more.

lets see you will need three session going at once.

one session for the MythTV backend, which will do recoding and file management
second for the first output using myth tv frontend
and the third for the other output using mythtv frontend
each wold need it own user name.

technically you should get two video cards, but you cannot run SLI, each need to run on its own. you can set it up that on of the monitor can switch to any tty at anytime. that way less things to buy. HDMI would be best if possible.

plenty of RAM say 8GB and a good quad core to keep things moving, I'm thinking Intel Core i5 or Phenom II 965, but maybe a server board wth an AMD opteron would be a better idea... nvida 9600 would a good pick,  make sure they have built in hdmi, and its supported.

as you have little linux experience this is a bit harder than you might think. hopefully you find a great tutorial on multiseat

---

### Post by scrote on 2009-09-21
Thanks for the hardware tips! Just the kind of thing I need atm. I have really been struggling trying to work out exactly what my minimum specs. should be. I had figured on SLI/Crossfire board with dual, unbridged GPUS for multiseat.

Been looking at the Palit 9600gt with HDMI and Displayport. However,  I was led to believe that the need to do audio passthrough may be problematic in this setup. So, I started looking at a Gainward HD 4670,  supports audio over HDMI out of the box. I am aware the ATI graphic solutions have driver suppport issues under Linux. Any comments on this?

Point of note, TV recording is a somewhat secondary objective on this build. I plan on having it eventually, but I currently have a proprietary PVR that records my cable (I'm in Australia, so Foxtel and IQ2). Movies and torrents are the immediate priorities. I don't even watch free-to-air.

I wasn't sure how RAM intensive these application would be. I guess it's the instancing that is creating the most load here. 8GB you say? Nice to have a figure :)

CPU wise, am I looking at Quads minimum for decent performance? I figured Quads would be the go, but had no definitive reason as to why duals would not work. In a two seat configuration with Quad, does that mean I can get 2 cores/user? 

A decent Quad may even offer scalability to four users at some stage I suppose, but would change my motherboard selection (for extra GPU's). Speaking of which, can anyone suggest a good CPU/motherboard combination for a two seat config.? It has been a while since I shopped for parts, and there is a LOT to choose from out there. Lets assume i5 for the time being, unless you can offer a good alternative.

The goal for this build is "by Christmas". Once I have a hardware list, I'll be out shopping straight away. Get a machine up and running, then onto Linux!

Alright, looking forward to some answers. 

Thanks for your time.
-John

---

### Post by scrote on 2009-09-23
First, i just wanna say that this [http://www.youtube.com/watch?v=MHHxY8l00io](http://www.youtube.com/watch?v=MHHxY8l00io) looks awesome.

Ok, so that aside, currently thinking of something along these lines:

Mobo: Asus P7P55D pro
CPU:  i5 750
GPU: 2* Gainward 4670
PSU:	 Vantec ION2 600W (too much?)
RAM: DDR3 PC3-10666 4 x 2GB
HDD: 1 * WD Black 640GB short-stroked (maybe two in RAID)

This is only a preliminary build outline and I don't have much time this week to look at it further.

It will be nice to have a testbed and start running through the software, but I don't want impatience to lure me into poor purchase choices. If I manage to get the system functional and documented, then I will look at optimisation measures and upgrade paths (for a second build).

Thanks for your time. Keep the comments coming!

---

