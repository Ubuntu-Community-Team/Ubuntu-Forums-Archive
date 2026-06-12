---
title: "Ethernet Between Two Computers"
date: 2009-07-11
forum: New to Ubuntu
---

### Post by Ranemills on 2009-07-11
Hey,

I've been having some trouble getting my wireless card to work. That's not what I want to ask though. As some of the guides which I have read require an internet connection. My Ubuntu desktop is upstairs, whereas the router is downstairs. Would it be possible to connect the Ubuntu desktop to my Vista laptop via an ethernet cable and get the internet through the laptop?

I wasn't sure whether I'd posted in the right forum here, so please tell me if I didn't put it in the right place. 

Thanks in advance,

Ryan

---

### Post by Yvan300 on 2009-07-11
Well i have tried this before in the past and what i heard was that you can't share an internet connection between computers using ethernet becasue neither computer knows when to begin receiving data or giving data and thus they will be confused. But then again, i could play games using ethernet and that involves data transfer so i may be wrong.

---

### Post by LewRockwell on 2009-07-11
this might help you along a bit:

[http://techrepublic.com.com/5208-11190-0.html?forumID=46&threadID=184459](http://techrepublic.com.com/5208-11190-0.html?forumID=46&threadID=184459)

.

---

### Post by oldsoundguy on 2009-07-11
What I do .... I set up the computer HARD WIRED into the router.  If you have to have it in the router room when setting it up, so be it!  You can just unplug it and move it after your basics are installed and all of your updates installed.

THEN move it to where it is to live and go via wireless.

Right now I have 3 Linux machines, 1 Windows machine, and a pair of PDA's all running wireless on my home net. ALL were set up hard wired in my media room and then moved to their new homes.

I have found that one of the easiest PCI wireless cards to install is the D-Link DWL 520+ (it is a super G card) and it installs in Ubuntu right out of the box. (there may be others .. and most likely ARE others, but this works for me.)

---

### Post by LewRockwell on 2009-07-11
> **oldsoundguy said:**
> What I do .... I set up the computer HARD WIRED into the router.  If you have to have it in the router room when setting it up, so be it!  You can just unplug it and move it after your basics are installed and all of your updates installed.

THEN move it to where it is to live and go via wireless.

Right now I have 3 Linux machines, 1 Windows machine, and a pair of PDA's all running wireless on my home net. ALL were set up hard wired in my media room and then moved to their new homes.

I have found that one of the easiest PCI wireless cards to install is the D-Link DWL 520+ (it is a super G card) and it installs in Ubuntu right out of the box. (there may be others .. and most likely ARE others, but this works for me.)

I'll agree that a wired connection is most often more efficient than wireless, especially during initial installations and updating/upgrading sessions...

however, that being said...

The OP is requesting assistance regarding using the wireless laptop as a hub/switch/router/repeater via the ethernet port on the laptop and then being wired to the desktop in a remote location

FWIW, with DDWRT firmware a Linksys WRT54G can be used in the manner you desire and will also act as an extender for the range of your primary wireless transceiver(the WRT54G is hugely popular with the linux crowd but when the windows folks upgrade you can find them for free or cheap!)

[http://en.wikipedia.org/wiki/Linksys_WRT54G_series](http://en.wikipedia.org/wiki/Linksys_WRT54G_series)

[http://en.wikipedia.org/wiki/DD-WRT](http://en.wikipedia.org/wiki/DD-WRT)

.

---

### Post by Ranemills on 2009-07-11
Thanks a lot for the quick replies. I might just try moving the router to the desktop or moving the desktop to the router. I was just wondering if there was a way around it without moving anything. It seems that it's best not to try connecting through the laptop.

---

### Post by dhtseany on 2009-07-11
OK, nevermind. I can't seem to find the tutorial I was looking for. Really, all you need to do is setup a couple of IP table entries, then bringing up eth0 and assign a static IP. (I use 192.168.11.2 for eth0). Then, Setup a static IP address on your XP machine to something like 192.168.11.3 and set the default gateway to 192.168.11.2. Do an ipconfig /all and find out what your ISP's DNS servers are and specify those addresses manually too on the XP machine.

For more information on the specifics of what I'm talking about, I'd google something like "ubuntu ICS tutorials" and you should be able to figure it out from there.

Post back if you need more help :)

Peace
Sean

---

### Post by LewRockwell on 2009-07-11
> **Ranemills said:**
> Thanks a lot for the quick replies. I might just try moving the router to the desktop or moving the desktop to the router. I was just wondering if there was a way around it without moving anything. It seems that it's best not to try connecting through the laptop.

FYI

Maximum length of a CAT5 from router to powered hubs/switches/computers/etc. is 100 meters(330ft)

.

---

