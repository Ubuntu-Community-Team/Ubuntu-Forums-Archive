---
title: "[SOLVED] Wired Network Stopped in Ubuntu 7.04"
date: 2008-01-23
forum: Networking &amp; Wireless
---

### Post by hookzilla on 2008-01-23
My wired networking has stopped working.  I'm a relative newbie so bear with me on this.   
I have a home network with 2 boxes running XP SP2 and 2 boxes running Linux. Nothing fancy, just file sharing.  The problem is on the box running Ubuntu 7.04. When I originally loaded Ubuntu, I got the wired networking going pretty easily.  A few days ago, after updating my system, I cannot access the windows network files. (I'm going to Network Places)  Initially, I could not see the workgroup.  After editing smb.conf, replacing MSHOME with my workgroup, I can see the workgroup, but not the files. When  I go to Network under System, the work roup does not always show in the network properties now.

 I don't think this is a problem with the network itself, as I don't have this problem with the other Linux box.   

I'm running Ubuntu 7.04 on an old system, pretty much straight off the  CD.  The only things I've added are Audacity and the Ubuntu recommended updates.

Any help will be appreciated.

---

### Post by hookzilla on 2008-03-05
I have spent quite a while now working in  Ubuntu 7.04 and 7.10 trying to get wireless to work and to get my home network to work.   In 7.10, when I try to see the wired network, I'm asked for a login password.  This did not happen in 7.04 and does not happen on any of the other WinXP or Linux boxes.  I can't seem to find a god reference for this.  Can someone offer any suggestions?  Thanks:confused:

---

### Post by Eiríkr on 2008-03-05
Hey there --

> In 7.10, when I try to see the wired network...

What does this mean?  I'm looking at my own wired network right now, and realizing I need to dust back there where the cables are.  ;)  I assume you mean you're trying to browse the network in Nautilus?  If so, what exactly are you clicking to view the network?

> Initially, I could not see the workgroup. After editing smb.conf, replacing MSHOME with my workgroup, I can see the workgroup, but not the files.

This puzzles me, as I thought I'd understood that the smb.conf file was only relevant when *serving* a share, not when acting as a *client* trying to access another share.  

Anyway, when you say you "can see the workgroup, but not the files", I feel like I'm missing some detail here.  What happens when you double-click the workgroup icon?  You should see a computer icon for each Windows fileserver on your local network.  Clicking one of these should show you the individual shared folders.  Clicking one of these should show you the files (and will likely require a username + password login).  Please explain in a little better detail exactly what steps you take, and then we can help out a bit better.  :)

Cheers,

Eiríkr

---

### Post by hookzilla on 2008-03-07
Thanks for your offer, but my wired networking is working now.  I did a clean install wired and once again got the request for a password when I tried to see the files on another networked PC. This time I didn't do anything.  I cancelled out and went on to try, unsuccessfully, to get my wireless working. When I rebooted today with the wired connection, both the network and internet worked.  

I am using Nautilus to browse the network.  Initially I could only get as far as the other PC's.

As to editing the smb.cnf file, I think I "noobied" the reading (or misreading) of a post.  I haven't done anything to it since the fresh install, so it must not have been involved in the issue.

I'm still very early on my learning curve and appreciate all the help posted in the forum.

I'll try to be more detailed in future posts.  Once again thanks.

---

### Post by Eiríkr on 2008-03-07
Glad the network is working for you now.  Feel free to post with any future issues.  :)

Cheers,

Eiríkr

---

