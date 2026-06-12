---
title: "Need help connecting to home server"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by thehappiestturtle on 2008-04-28
Hello,  I am sort of new to Ubuntu.  I have been playing around with it for about a year now, but was never serious until now.  I now officially use Ubuntu 8 as my primary OS.  I am having a problem however, and any help would be great!

I have a wireless home network setup, as most of you im sure.  I have an Airport Extreme router, connected to that is a 250 gig mybook external HD. I have all my music and shared files on this HD. I am running Ubuntu on my MacBook Pro with a Dual boot configuration.  I got the wireless working, however i am unable to connect to the Mybook HD on my network.  I dont even know where to look to find it. :confused: 

Can you please help me find and connect to this sucka. I miss my music! haha

Info:
MacBook Pro (intel)
Airport Extreme 802.11n
250 gig mybook external HD

---

### Post by Mykle87 on 2008-04-28
I just read [this thread]("http://ubuntuforums.org/showthread.php?p=4811592#post4811592"). Do you have the same product?

Give this a try.
> Ubuntu Places, Network, Windows Network, workgroup, MYBOOKWORLD and identified as /PUBLIC, but in Vista or XP it will be assigned a drive letter.
Hope that helps.

---

### Post by thehappiestturtle on 2008-04-28
Hey Mykle87, thanks for the reply. 

That is actually not the same drive that i Have.  I have a simpler USB one. It is plugged via the usb port on my Airport Extreme.  That MyBook World is meant for networks where as mine is not. But has been kinda... foreced into network slavery.  

Sadly i still cannot find my drive.  I checked under places/network and places/connect to server

Thanks for the help again!

---

### Post by mlentink on 2008-04-28
What protocol does that Airport use to serve the files on that drive? Can you see that drive with windows machines?
I suspect this is a protocol issue.

---

### Post by Mykle87 on 2008-04-28
Ok I see. Good luck.

---

### Post by thehappiestturtle on 2008-04-28
> What protocol does that Airport use to serve the files on that drive? Can you see that drive with windows machines?
I suspect this is a protocol issue. 

The Drive Shows up great in both Windows and Mac.  I have it encrypted. Could that be the problem? 

The thing that has me stumpted, it doesnt even show up...

Thanks for the help!

---

### Post by mlentink on 2008-05-01
Hmm. I think this Airport of yours works with Bonjour, which is Apple's zero-config protocol. I don't know whether that's supported under Linux at all, though it might be in some fashion.

---

