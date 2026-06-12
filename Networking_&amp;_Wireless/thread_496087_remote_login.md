---
title: "remote login"
date: 2007-07-08
forum: Networking &amp; Wireless
---

### Post by edeiten on 2007-07-08
I have attempted to use Real VNC and Putty to remotely log into my Ubuntu box. Neither are responding. When I attempt to use Real VNC viewer from my Windows box I get the error message "reading version failed: not an rfb server?" and ask if I want to attempt to reconnect.  When I use putty from the windows box, it just hangs....I get no prompt to log in. In both cases I can see the requests coming to my Ubuntu box using wire shark. What setting or package am I missing :confused:  I have Ubuntu v7.04 on my server and Windows 2000 on my laptop. Thanks,

---

### Post by aliyanage on 2007-07-08
hey there,

well I haven't tried out the Real VNC but I got the putty remote ssh working. I've wrote down a whole tutorial on my page, go to the site below and check under networks:

[www.mindexchange.ch](www.mindexchange.ch)


regards
aliyanage

---

### Post by edeiten on 2007-07-08
Thanks, and nice web site. But I have done everything listed on your page. I do use port forwarding and I have a port forwarded to 22 on my server (22 is blocked by my ISP). I also checked that ssh and open ssh is installed. I am getting packets to the server, but putty still does not respond on my windows box.

---

### Post by aliyanage on 2007-07-09
hmmm... okay just to get it straight... you are trying to connect via ssh from your windows box to your ubuntu box right?

regards
aliyanage

---

### Post by Mr. C. on 2007-07-09
> **edeiten said:**
> Thanks, and nice web site. But I have done everything listed on your page. I do use port forwarding and I have a port forwarded to 22 on my server (22 is blocked by my ISP). I also checked that ssh and open ssh is installed. I am getting packets to the server, but putty still does not respond on my windows box.

I'm confused - you said your ISP blocks port 22.  That must be inbound.  If so, you're going to need to move the port or port forward to an unblocked port.

How do you know your SSH packets are getting to your server?

MrC

---

### Post by edeiten on 2007-07-09
Yes, I am trying to connect from my windows box to my ubuntu box. 

Yes, port 22 is blocked, so I have created a port forwarding from a port that is not blocked and forwarded it to 22 behind the firewall. So for example, I forward port 1024 on my router to port 22 and send it to the IP address of my Ubuntu box. Then I have the SSH server listening to port 22. 

I know that packets are getting through my port forwarding and to my Ubuntu box because I used Wire Shark and monitored the traffic on my Ubuntu box.

---

### Post by edeiten on 2007-07-09
I got this to work. I found some text on the config file for SSH and after I made the suggested changes I was able to connect from the wondows box to Ubuntu using Putty. Thanks for the help!

---

