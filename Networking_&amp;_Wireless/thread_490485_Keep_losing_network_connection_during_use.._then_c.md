---
title: "Keep losing network connection during use.. then completely broken"
date: 2007-07-02
forum: Networking &amp; Wireless
---

### Post by steve457 on 2007-07-02
I'm having a weird problem with Feisty that I just installed on my new machine.  The network connection will completely disconnect at random times when I am using it.  I first noticed this when transferring files from my Windows machine to my Ubuntu machine using Samba.  The ubuntu machine would seem to drop the connection, but when I checked the machine the network icon appeared connected.  Yet, the machine was obviously no longer connected as I was not able to connect to any websites.  I tried doing an ifdown/up, but the ifup would fail or just hang.  

I then noticed this happening again today.  I had an SSH tunnel going so that I could access my computer from work through VNC.  About 2 minutes into my session, I got a message saying that Putty (what I used to form the tunnel) had encountered some error.  My connection was lost, and I could no longer access my machine.  I haven't been able to physically check the machine to see what its status is, but I'm guessing it is similar to what happened when I was transferring files earlier.  

I just got this machine up and running this weekend, so I'm wondering if this is a software or hardware issue.  Do you think it could be a hardware related issue?  I've seen other posts on network issues, so I'm fairly sure it is software.  Are there any logs that I can check that could help me resolve this issue?  I'm completely lost here, and am not sure what to check next.  What is strange is that the connection only seems to break when I'm using it.  If the computer is just sitting there with no activity the connection will remain fine.

---

### Post by steve457 on 2007-07-07
Ok, the problem just happened again!  My machine was running well for a couple of days, then I tried doing an SSH session from within my internal network (using Putty).  About 30 seconds into the session, Putty spit out an error and then my ubuntu machine lost its network connection.  All other machines on the network still worked fine.  

On the Ubuntu machine, I could no longer ping any machines on the network.  ifconfig -a, yielded information that looked ok to me.  I'm using a static IP address in the machine, and eth0 still had the address fine.  I did an ifup/down, but the connection would not come back.  I ended up having to reboot the machine to fix the connection.

 I am now copying files and ssh'ing back into the machine, and the connection is holding.  It only seems to crash on occassion and at random times.  Help!  This is on an Asus P5K, with Intel Core 2 Duo 4300, Marvell chipset.  Running 7.0.4 Fiesty.

---

### Post by gerkin on 2007-07-16
Hi, check out my post here it might help:

 [http://ubuntuforums.org/showthread.php?p=3030748#post3030748](http://ubuntuforums.org/showthread.php?p=3030748#post3030748)

---

