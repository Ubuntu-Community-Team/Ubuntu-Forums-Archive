---
title: "Virtual Box and assigning specific NIC to use"
date: 2008-01-10
forum: Networking &amp; Wireless
---

### Post by pimpaulogy on 2008-01-10
I am sorry for this, but I am a newbie, and it doesn't seem as if there are other people out there posting the same question.  If there is already a post about this specifically, please point me in that direction.

Here's my situation:

1 computer running Gutsy with two NICs.  eth0 is connected to our outside DSL line and eth1 will be connected to our internal network.  What I would like to do is run XP under VirtualBox and only let VirtualBox connect to eth1, not eth0.  Basically, our company runs primarily Windows boxes and so I would like to connect to the internal network with my VirtualBox XP.  I would also like to be able to see that VirtualBox XP from other machines that are on the internal network.  I want the VirtualBox XP to be just like a separate computer that is only attached to the internal network (eth1).

Conversely, I only want Gutsy to connect to the DSL.  I think I have this resolved with routing tables, but I am not seeing how to connect my VirtualBox XP to solely eth1.  I tried to follow the steps in the User Guide for Host Interfacing and Bridging, but it didn't work and it's a bit over my head at this point.

If somebody could either list the instructions or point me in the right direction to find the instructions to do just what I am looking for, I would really appreciate it.

Thank you.

---

