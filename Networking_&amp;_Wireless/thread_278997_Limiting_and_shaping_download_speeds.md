---
title: "Limiting and shaping download speeds"
date: 2006-10-17
forum: Networking &amp; Wireless
---

### Post by whiterabbit on 2006-10-17
I've seen so many threads on bandwidth shaping and whatnot but to be honest, being a newbie, alot of what I've read doesn't make sense.  

I'm currently using wonder shaper.  

Firstly, is there a way to limit and shape the download of an application like "DownThemAll"(the firefox extention download manager)?   

Secondly, is there a gui download manager that will allow me shape my bandwidth with ease?  

Ok, one more question.  I notice that my laptop(also connected to my adsl modem/router) shows as eth0 when I ifconfig.  If I limit eth0 on my pc, does it affect my laptop?  

Sorry, I know this sounds a little muddled but I'm confused.  I'd really appreciate the help.

---

### Post by airtonix on 2007-04-14
yep, limiting eth0 will affect all traffic to your laptop..

eth0 is the gate that all traffic travels through from outside your laptop to the inside of it.

ie it is your network port.

your modem port might (if you have one) be > ppp0

and if you plug a wifi adapter via the pcmia slot it will most proly be shown as > ath0

An ethernet card is also known as a [**network interface controller**]("http://en.wikipedia.org/wiki/Network_card"), and i have here in front of me a NIC device that plugs into the usb port....providing me (in most cases)with an instant extra network port...and it shows up as > eth1

all these devices all provide a tunnel for traffic to travel from/to your laptop and th outside world (if they have established a connection)

---

