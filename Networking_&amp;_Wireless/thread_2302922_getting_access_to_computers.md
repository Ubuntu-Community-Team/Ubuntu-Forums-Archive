---
title: "getting access to computers"
date: 2015-11-14
forum: Networking &amp; Wireless
---

### Post by jgw on 2015-11-14
I have 6 computers in my house.  all but one are now ubuntu machines.  Two of the machines are on my wireless access.  1 is on a power outlet pairing, 1 is wired directly to the router (windows machine), and 2 are connected by a 10/100 cable from the router/modem to a hub.  All of the ubuntu machines are running w/14.04 and the windows machine is using XP.  

My problem is simple (not sure about the solution <g>)  I would like to be able to access each machine with another.  I used to be able to do this with no problem.  Then I seem to have done something clever and they can no longer access each other.  I have no idea what I have done but am equally sure that if I keep up trying to deal with this myself I will end up with everybody crashed.  I don't care if I can access the windows machine or it can access any of the other machines (but that would be nice).  

I have tried to set up a windows network and failed.  One of the problems, I think, is that there are a LOT of tutorials, directions, etc. as to how to do this and they all seem to be a bit different, one from the other.  I suspect this has contributed significantly to my failures.   If anybody can just point me to a current file that should work, I would be grateful.  

Thank you.............

---

### Post by mikewhatever on 2015-11-14
You need to be much more specific to get meaningful answers. When I see "getting access to computers", I might thing pinging would be enough, or is it remote management, or file sharing. In case of file sharing, would it be an option to promote one machine to a file server, or do you want all of them to serve files?

---

### Post by jgw on 2015-11-14
Thanks for the reply...........

Sorry.......  What I would like to do is to transfer files between the computers as well as browse them.  As far as the server thing is concerned.  As long as I can transfer files, and browse I don't care.

---

### Post by tgalati4 on 2015-11-15
Perhaps post a diagram of the network.  Your most reliable setup is to set each machine with a static IP, then define the shared mounts in /etc/samba/smb.conf on each machine.  It takes a lot of work and a lot of patience and careful notes of what your settings are on each machine.  It is not plug-and-play, nor is it easy.

Power outlet network connections are not reliable, so do that machine last.

Some reading:

[https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20(Command-line%20interface/Linux%20Terminal)%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way](https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20(Command-line%20interface/Linux%20Terminal)%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way)!

[https://help.ubuntu.com/lts/serverguide/samba-fileserver.html](https://help.ubuntu.com/lts/serverguide/samba-fileserver.html)

[https://help.ubuntu.com/community/Samba/SambaServerGuide](https://help.ubuntu.com/community/Samba/SambaServerGuide)

---

