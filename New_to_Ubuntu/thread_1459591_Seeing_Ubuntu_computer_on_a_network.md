---
title: "Seeing Ubuntu computer on a network"
date: 2010-04-21
forum: New to Ubuntu
---

### Post by Tekken on 2010-04-21
I am using Ubuntu 9.10. I am trying to see computer A ( Ubuntu 9.10 ) over a network while using computer B ( windows vista ). I can see multiple computers from computer B and I can even see those computers on computer A. The problem is, I can't see computer A from any computer on the network. I can ping the ip address of computer A, but it doesn't return a name for the computer. 

I searched for a while and I found a few things and tried them: 
gksudo gedit /etc/hostname /etc/hosts
changed the appropriate lines to Anneth1
saved
restarted linux

I then tried to ping the ip address, and nothing had changed. I am wondering if there is something I need to change on the linux side, or if windows will not see a non-windows machine over a network. I don't believe this to be the case because I am also using a mac and the same computers are visible that are visible on windows, but any insight would be helpful.

Thanks in advanced!

---

### Post by LowSky on 2010-04-21
Do you have SAMBA installed?

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

