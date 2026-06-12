---
title: "Windows network access."
date: 2008-05-27
forum: Networking &amp; Wireless
---

### Post by Nickolaus on 2008-05-27
I'm running hardy and am trying to access files on other computers via my network. The computers I'm trying to gain access to are running XP and ugh, vista. I could really use some help on this one. I installed Samba but I seem to be missing something and someone told me to install SWAT so I did and this still hasn't resolved the issue.

Please be very detailed in the solution. I have had a couple people toss me to a few pages that if I could understand them would have solved my problem.

---

### Post by superprash2003 on 2008-05-27
firstly ensure that you are able to ping the xp machine.. in your ubuntu machine.. go to the terminal and type ping x.x.x.x where x.x.x.x is the ip address of the xp machine

---

### Post by mapes12 on 2008-05-27
I couldn't get sharing to work at all across my home LAN therefore I gave up on Samba network shares. Having read a number of posts my network now accesses clients using Secure Shell - SSH. I find it much easier. There are utilities to connect XP and Ubuntu boxes via this protocol.

These links may be helpful:

[http://pigtail.net/LRP/printsrv/cygwin-sshd.html](http://pigtail.net/LRP/printsrv/cygwin-sshd.html)

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

[http://www.openssh.org/](http://www.openssh.org/)

[http://ubuntuforums.org/showthread.php?t=793308&highlight=ssh](http://ubuntuforums.org/showthread.php?t=793308&highlight=ssh)

---

