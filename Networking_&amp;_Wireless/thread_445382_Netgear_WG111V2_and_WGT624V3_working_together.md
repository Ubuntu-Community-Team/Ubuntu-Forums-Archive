---
title: "Netgear WG111V2 and WGT624V3 working together"
date: 2007-05-15
forum: Networking &amp; Wireless
---

### Post by medad on 2007-05-15
For the past month I have been trying to get the Netgear router WGT624V3 and the Netgear wireless USB WG111V2 to link under Feisty.  ](*,)   For the longest time they would barely work together.  After the initial connection, I would eventually lose the ability to surf the internet.  The USB was still shown to be connected to the router, but there was no connection.  It also seemed to be causing the USB Wireless to overheat as it lost the ability to see all the other routers that were out there.  I was quite sure that the USB stick was the problem.  After much surfing and trial and error, and several different versions of Linux, it turned out, at least currently in my case, to be the router.  I'm sure my wife was glad to hear that since I had previously picked up a new USB wireless (Airlink- I couldn't get it to link, even thought it saw all the routers out there) and now could return it.  :-\" 

The following are the main changes that I made to the router.  First I upgraded the router to the most recent upgrade [Beta Version 2.0.17_1.0.1 (for North America only)].  I had read somewhere that there were connection issues with wireless that were cleared when the router was updated to the beta.  I really didn't see any change after this, but then I read somewhere else that if the router is near a wall that the signal might ricochet off the wall and might reduce the clarity of the signal.  So I thought maybe the signal might be too strong since my desk is in a corner, so I disabled the eXtended Range(XR) Feature.   That is when I really noticed the difference.  The connection isn't dropping off anymore and the USB WG111V2 appears to not be overheating as well.  :popcorn: 

The other thing that I learned while surfing was to keep the router and the modem separate.  It never really gave me a problem, but I noticed that the connection speed seemed more stable and a little faster after I separated them.

I just thought I'd put this out since I have had so much help reading the messages from others for other issues that I have had with my different systems.  :KS

---

### Post by sdowney717 on 2007-10-10
many people have had terrible trouble with this router. seems like overheating is the issue.
Just google search wgt624 overheat.
it will just drop the internet connection. no surfing. reboot always brings it back online, but can you trust it not to give out at any random moment?

---

### Post by sdowney717 on 2007-10-10
[http://www.dslreports.com/forum/remark,12918191](http://www.dslreports.com/forum/remark,12918191)
read this mentions a lawsuit regarding this 'netfear' router.
Fears the net so it disconnects in terror.

---

### Post by sdowney717 on 2007-10-15
I did find out if you assign a static IP to the wan side of this router, it seems to stay up. BUT you should not have to.
Perhaps in my case, it was having trouble renewing its IP. I discovered if I unpluged the wan cable and plugged it back in, it started working again. 
So my issue may not have been overheating. Another gateway wgr250, worked set to dynamic and never went down, tested for over a week. Now with this netgear wgt624v3, It has been up over a day and still working.

I had riddled the case with drill holes, ripped off the rf shield and put a heat sink on the atheros chip, tried several different firmwares,left it totally open outside of its case, tried putting a fan on it, moved it all over the room,  changed every setting imaginable, tried different power supplies all with no effect. I still think it is a bad circuit design with systemic issues in play, and wont buy another one.

I also should add, I have it working behind an innomedia voip mta6328-re, so setting it to static is easy, the config will never change. If it were plugged into the cable modem directly where they can change the IP, it could be a problem..

---

