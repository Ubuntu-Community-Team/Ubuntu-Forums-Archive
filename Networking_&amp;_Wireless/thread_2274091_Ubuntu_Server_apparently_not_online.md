---
title: "Ubuntu Server apparently not online"
date: 2015-04-17
forum: Networking &amp; Wireless
---

### Post by Mike_Hughes on 2015-04-17
I have just installed Ubuntu Server 14.04 LTS. I was issuing some apt-get commands without any apparent response. I ran ifconfig -a and shows eth0 has an ip from my router. I was able to ping another computer. So I can't figure out from Web Browser from my other computer I can't see the Apache2 server when I type [http://localhost](http://localhost).

Mike Hughes

---

### Post by TheFu on 2015-04-17
First step is to determine how much of the networking is working and if any isn't.
[http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking)

apt-get won't work without a fully working network stack.

---

### Post by Mike_Hughes on 2015-04-17
I was able to ping out to google.com. I could figure out how to stop the pinging so pulled the bloody power cord and started again. But I ran the line to look at the nics. I have two ethernet nics and a Wireless nic. The first NIC card is a Gigabit by Qualcomm  and it is up and running. The second card is by Intel and it is disabled. Then the wireless card is Disabled as well.  So can't figure out every time I try to use Apt-get this is what I get in return - Reading package lists ... Done Building dependency tree, Reading state information . . . Done then this line. E: Unable to locate package webmin. Is that saying it doesn't know where to go for repositories? I tried to set repository location and it wouldn't take it. When I type the local ip that the server is located on example, not actual address: 192.167.1.106 I get the Apache2 welcome page. If I type [http://localhost](http://localhost) I get an error message. Safari can't connect to Server. But can through the address.

---

### Post by TheFu on 2015-04-18
> **Mike_Hughes said:**
>  I could figure out how to stop the pinging so pulled the bloody power cord and started again. 

Dude.  Save yourself some time. Some directed learning will make you much happier going forward and fill in some basic knowledge. [http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux)  Reviewing the first 5 things in the list will save you hours, days, weeks.  Especially if you are running a server, that knowledge is critical to the success.  Spend 3-5 hrs now, save months of frustration.

cntl-c is how to stop a program. This works across all UNIX, Linux, Windows, OSX to my knowledge.

Localhost is the machine the browser is running on. 127.0.0.1 is usually the IP for localhost. Every machine is "localhost" to itself. Using localhost will never connect to a different machine. That isn't how networking works. Wish I could suggest a network primer.  You'll get it, but all this new information takes time to digest.

I can't help with webmin - never used it. I  recall trying to install it myself when I was just starting out and failing. Spoke with a guru at the time and he explained that I should learn the shell/CLI methods first. I didn't like his answer, but looking back since 1995, think he was correct.

---

