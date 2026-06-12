---
title: "Static IP in VM Player"
date: 2014-12-25
forum: Networking &amp; Wireless
---

### Post by cole7 on 2014-12-25
Hi, First time poster here.  I have been using Ubuntu on my personal computer for about a year now and have grown to like it.  I have had many question with learning how to use various features of Ubuntu and have been able to answer all using this forum and various other on-line resources.  However, this one I have been unable to find an answer for.  I recently made my work computer into a dual boot using Ubuntu 14.04 as the main operating system.  I run Windows 7 Pro in VM Player 7.  There are times when the Windows 7 needs to have a static ip assigned.  How is this acomplished?  Is it as simple as setting the adapter to bridged and going into the network and sharing center of the VM and configure it there?  Do I need to do this and configure on the host?  

Thank you.

---

### Post by TheFu on 2014-12-28
> simple as setting the adapter to bridged and going into the network and sharing center of the VM and configure it there? 

Yes, but only do it with a static IP that the network admin gave you.  IP collisions are terrible and the network team doesn't like to track down offenders who are breaking the network by stealing an IP.

---

