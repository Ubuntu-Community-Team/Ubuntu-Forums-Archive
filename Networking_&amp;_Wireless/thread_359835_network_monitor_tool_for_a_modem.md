---
title: "network monitor tool for a modem ?"
date: 2007-02-12
forum: Networking &amp; Wireless
---

### Post by Matthijs on 2007-02-12
hi there,

I am new to unix and not want to work on windows anymore. But every computer at my school is running windows :( Now i have made a deal with my teachers that i may use Ubuntu for everything else as an alternative. Great! no more windows. 

But i have to do my homework of course.

So now i have to monitor the traffic between two modem and do some calibration about the quality of the signal. Let's say that i send a 10mb.bin file over the network. does someone knows a program that views this connection and monitors the speed, data loss etc.... just a lot information about the connection. (something like 'iptraf' or 'netstat') 

Also i need to create a hyperterminal connection, i dont even know if thats possible under unix :) 

thanks for the help!

Matthijs

---

### Post by koenn on 2007-02-12
Man, you really got yourself into some serious trouble there. I hope you're not afraid of some serious reading. 

The trick is going to be not to "translate" everything "Windows" to Linux / Ubuntu - but look below the surface and match functionality rather than applications. 

To use modems / serial lines, you might want to look up minicom, getty (+ modem, serial line, etc). "COM" ports are ttyS0, ttyS etc. on Linux. Most of what you find will be command line stuff, developped in the days that unix was run on central computers, and (real, hardware) terminals would connect to it over serial lines (with modems) - GUI stuff for windows was developped later to emulate these, while the unix world then  had already an X window system that could be transported over TCP/IP - so I don't know if you'll find Linux GUI's for this kind of thing.
(someone correct me if I'm wrong)

I'm not sure how you're going to capture traffic on a serial line - it's by definition a point to point link so where would you capture anything for monitoring, exept at one of the ends ? 

What kind a school is it anyway ? what level, etc. ?

---

### Post by Matthijs on 2007-02-12
thank you for your reaction!!

i do like some reading.. days long! and i would then prefer the shell to work with. google is my best friend :) and this forum of course with my 4 beans :) 

It's just an normal ICT education. The project is called 'modem connection in win98' (translated from dutch)

---

### Post by Matthijs on 2007-02-12
iptraf is gonne be a great tool btw

---

### Post by koenn on 2007-02-12
Here's some reading material on modems and terminals

[http://tldp.org/HOWTO/Modem-HOWTO.html](http://tldp.org/HOWTO/Modem-HOWTO.html)  : Modem HOWTO : setup, use, troubleshoot
[http://www.vanemery.com/Linux/Serial/serial-console.html](http://www.vanemery.com/Linux/Serial/serial-console.html) : terminals and serial lines
[http://tldp.org/HOWTO/Serial-HOWTO.html](http://tldp.org/HOWTO/Serial-HOWTO.html) : serial lines - more technical background + some stuff on traffic monitoring.

modems, serial lines and terminals kinda overlap - reading the 3 HOWTO's should give you an idea of the playing field (and tell you what to look/ask for if you need more info)

---

### Post by mips on 2007-02-12
ttysnoop - repos
ttylog - repos
statserial - repos
interceptty - [http://www.suspectclass.com/~sgifford/interceptty/]("http://www.suspectclass.com/%7Esgifford/interceptty/")
sersniff - [http://www.earth.li/projectpurple/progs/sersniff.html](http://www.earth.li/projectpurple/progs/sersniff.html)
slsnif - [http://freshmeat.net/projects/slsnif/](http://freshmeat.net/projects/slsnif/)
linuxserialsniffer - [http://freshmeat.net/projects/linuxserialsniffer/](http://freshmeat.net/projects/linuxserialsniffer/)
serialsnoop - [http://freshmeat.net/projects/serialsnoop/](http://freshmeat.net/projects/serialsnoop/)
gserial-sniffer - Cannot find it

---

### Post by Matthijs on 2007-02-12
wohooo :) thank you all!! this is gonne be interesting. ill put my O'Reilly books aside :) thanks

---

### Post by Matthijs on 2007-02-21
Alright, I now have successful installed the modem and will begin with testing. I've got a intel chip based modem and it's working as it should. Serial line sniffer and iptraf will be used for monitoring the connection. 

good news also... all the projects running here at school are with windows. Now I may use Ubuntu for all the projects with a classmate of mine.

---

