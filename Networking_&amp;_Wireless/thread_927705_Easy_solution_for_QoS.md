---
title: "Easy solution for QoS?"
date: 2008-09-23
forum: Networking &amp; Wireless
---

### Post by Archmage on 2008-09-23
Is there an easy solution for QoS in Hardy?

Somethink like a easy (graphical) interface to handle each port/ip/protocol, saying what should be free and so on.

---

### Post by nixscripter on 2008-09-23
Look at **MasterShaper**, a web-based traffic management tool. I'm not sure if it's quite what you want: 
[http://www.mastershaper.org/index.php/Main_Page](http://www.mastershaper.org/index.php/Main_Page)

---

### Post by Archmage on 2008-09-25
Thanks. Indeed this is a nice program. But is there something that I can use and install via apt-get without altering my sources.list?

So that security fixes will be updated automatical - that is the way I like in Ubuntu.

---

### Post by nixscripter on 2008-09-25
There is a command line tool in the repository called **shapecfg**, but I don't know how powerful it is. It also can only shape sent (not recieved) traffic.

What exactly do you want to do with the program?

---

### Post by Archmage on 2008-09-26
I want to give different ports a different priority in my network so that I can play without any lag, while still downloading.

E.g. give my online-game-ports the maximum speed, if there is still something free, give the rest to VOICEIP, if there is still something free, give the rest to video streaming, if there is still something free, give the rest to surfing/mail, if there is still something free, give the rest to P2P.

I have seen that this would be possibile to do this with HTB, but the script seems to be very complicated, therefore I was hoping that there is an easier solution, when I can simply specifiy the ports and the priority.

The shapecfg seems not to be that what I'm searching for, because it simply limiting the bandwide, but I want that Ubuntu is using the whole bandwide for low priority ports, if no high priority ports are using it.

---

### Post by nixscripter on 2008-09-27
I'm afraid that traffic shaping is almost always complicated. There are many decisions to make about bandwidth you do and don't use, and too many for any real standard policy. As a result, Linux wisely chose the only reasonable solution: make the user tell the kernel what he wants. I'm afraid a complicated script is really the only way to do it.

Try reading Chapter 9 of the Linux Advanced Routing and Traffic Shaping howto for background information:

[http://lartc.org/lartc.txt](http://lartc.org/lartc.txt)

Sorry I couldn't be more help.

---

