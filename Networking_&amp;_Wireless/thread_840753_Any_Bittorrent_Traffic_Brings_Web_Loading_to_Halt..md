---
title: "Any Bittorrent Traffic Brings Web Loading to Halt."
date: 2008-06-25
forum: Networking &amp; Wireless
---

### Post by slugicide on 2008-06-25
Whenever I use Bittorrent (currently using Azureus, but have had the same problem with Transmission, etc.) my ability to surf the Web halts.  Even if it's just a trickle (like 3 seeds and 3 peers even).  This is a brand new installation of Hardy, but the problem existed with Gutsy and a previous install of Hardy.  This doesn't happen when I log into XP.  On XP the Web only slows down if I max out the bandwidth.  
This happens both at home (Comcast cable) and at the cafe (fiber optic through local PUD).
Thanks!

---

### Post by Rob Campbell on 2008-06-27
I have a similar issue with Hardy on both my Macbook Pro and an AMD 64bit desktop. Ktorrent and deluge cause the wireless card to disconnect within about 10 minutes (variable time). The connection is fine and stable otherwise and these machines don't cause this problem when running a different OS. So it's unlikely to be the router.

---

### Post by slugicide on 2008-07-06
Can anyone help?  I don't know anything about networks and this is really driving me crazy.

---

### Post by tamoneya on 2008-07-06
im not an expert and I dont know the kernel well enough to tell you how to fix it but i think I may be able to get you pointed in the right direction:

I think it may be that the number of TCP connections is causing your computer to start dropping connections.  I know this happened with my router until I updated the firmware to ddwrt and it makes sense that an improperly configured linux kernel could be have the same problem.  It should be a simple fix like editing some small configuration file.  The only problem is I dont know which file it is.  However this should give you something more descriptive to search for.

---

### Post by slugicide on 2008-07-15
I'm still looking for help for this.

---

### Post by Void1106 on 2008-07-18
I don't think this is linux specific. I just switched from XP and it did it with it. I believe it's comcast screwing with file sharing to be honest.

---

### Post by PinkFloyd102489 on 2008-07-18
I had the problem on Vista with uTorrent. Turns out I had accidently set the connection speed to 10Mbps which is double my actual connection. When it set it down to 2Mbps, it cleared right up. It has to do with the number of upload slots.

---

