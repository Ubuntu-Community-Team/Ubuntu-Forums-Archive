---
title: "HELP! Windows network access problem (Samba server involved)"
date: 2007-08-29
forum: Networking &amp; Wireless
---

### Post by blueturtl on 2007-08-29
Hello everyone.

I recently set up a Samba server (running on Ubuntu Dapper) for my folks to use as a network drive and backup tool. Setting up the server was blissfully easy, but I am now facing some odd problems with the network itself.

On random days all systems loose sight of each other (aka when you go into Network Neighborhood or try to access the mounted share on the other systems). Error messages are of the persuasion: "The network path cannot be found or the network is unavailable." Also none of the systems can see each other during this time, although all systems respond to ping from any of the systems. If the network works, it will work until all the systems (including the server) turn off for the night. Functionality issues arise in the morning when the systems are turned on (the server powers up automatically each morning). If networking doesn't work I have to manually restart the Samba service on the server for things to start working again.

There are four computers on the network besides the server and they all receive IP addresses on the same subnet and range (192.168.1.*, 255.255.255.0). The server is at 192.168.1.107. Two client systems run Windows XP Professional, one runs Ubuntu Feisty and one is an iMac running OS X 10.3.9.

I have tried to track the source of the problem and have determined the following thus far:

[LIST]
[*]It does not matter in which order the systems are started, but if a Windows computer is started first the network is more likely to work and the Samba server be accessible. This is a problem as it should not matter if the server was the first PC to start!
[*]The Samba system has been configured as the browse master system and appears so according to diagnostic tools even when the network is not working. There are no browser wars going on as the windows systems have lower priority than the Samba server.
[*]Either everything works (browsing between computers and server access) or nothing works (none of the computers see each other and the server is inaccessible even though it has been mounted through an IP address locally).
[/LIST]

I am completely stumped, maybe there's someone more experienced than me out there who can help me figure out how to get this to work?

---

### Post by will71110 on 2007-08-29
Do you have a domain setup?  If not that would fix most sharing problems.

---

### Post by blueturtl on 2007-08-29
What is a domain setup and how do apply one?

---

### Post by will71110 on 2007-08-29
Try this..

[http://www.desktoplinux.com/news/NS4539632760.html](http://www.desktoplinux.com/news/NS4539632760.html)

I like picuters and this site has lots of them LOL.

---

### Post by blueturtl on 2007-08-29
Just to clarify, my folks have home router that shares the internet connection and acts as a DHCP server. It remembers each machine so they always receive the same IP address.

This would be so simple if Windows could just hook to the Samba server via it's IP address (since it obviously is there and replies to ping)...

I also suggested to my folks that the server be left running 24/7 after everything works but they do not like the idea.

---

### Post by blueturtl on 2007-08-31
Anyone?

I looked at the domain setup, but it seems like an unnecessary act in what is otherwise a perfectly normal LAN. Also I don't see how it really solves the issue if the workgroup computers fail to detect each other.

Right now I'm leaning on talking my folks into leaving the server on 24/7, maybe with hard-disk sleep or something, at least until I come up with why the Microsoft networking randomly decides to not work.

---

### Post by blueturtl on 2007-09-01
I have applied a temporary fix:
I added the following line to crontab as this seems to fix the problem everytime.

```
/etc/init.d/samba restart
```

I timed the execution of the command so that typically at least one Windows machine will already be running. This is of course a hack, but until I figure out what's going on it's all I can do. :confused:

---

