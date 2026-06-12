---
title: "Ubuntu issue with Bit Torrent"
date: 2009-07-11
forum: New to Ubuntu
---

### Post by mojo_man on 2009-07-11
I have set my BitTorrent to listen for port 6667. I have opened that port on my firewall in my router. The BitTorrent still says the port is closed though it seems to work properly.

Question 1: Do I have to do anything more or should I leave it?

Question 20) Is UFW on ubuntu on by default? Write now I have:

To                         Action  From
--                         ------  ----
22/tcp                     ALLOW   Anywhere
22/udp                     ALLOW   Anywhere

---

### Post by fanglore on 2009-07-11
Well sometimes it will say theres a problem and actaully not. you can have no connection and it will still download but with connection it downloads much faster

---

### Post by Cato2 on 2009-07-11
Have you checked the port is actually being forwarded on your router to your PC?  Try (from a PC outside your house) doing "telnet yourpc-ip-address xyz" where xyz is the port number.  You should get something back, not connection rejected/refused.  Or simply use one of the many firewall test websites to tell you status of that port.

I don't think ufw is normally on by default, but I could be wrong in more recent versions of Ubuntu.  

You don't have to open a port in your router to do BitTorrent of course but it does make it work better.

---

### Post by nhasian on 2009-07-11
all you need to do is open the correct port on your router and forward it to your pc's IP address.  you'll need to make sure the dhcp server assigns the same IP address to the particular computer or set a static ip address instead.

you dont need to do anything else on the ubuntu computer except make the port number you set in the router match the bittorrent program.

I assume your talking about the default bittorrent client Transmission.

---

### Post by PureLoneWolf on 2009-07-11
I would recommend changing the port within the software to something random and then changing the router to forward that port instead.

Most ISPs have been blocking or throttling the standard bittorrent ports for many years.

Try setting the port within Transmission to 49182 or something nice and high like that.  Make sure you alter your router to forward this port to your PC too.

---

### Post by mojo_man on 2009-07-11
Okay I have some good news. I have have reset my ROUTER back to the way it was. The problem is with UFW. WHen I turn it off, everything works! It can listen to the port! I added a rule for the 6667/tc/udp port. Everything workds. I also enabled ufw to let in port 80 for web access. Should I do this? 

To                         Action  From
--                         ------  ----
22/tcp                     ALLOW   Anywhere
22/udp                     ALLOW   Anywhere
6667/tcp                   ALLOW   Anywhere
80/tcp                     ALLOW   Anywhere
6667/udp                   ALLOW   Anywhere

---

### Post by Skorzen on 2009-07-11
If you access your PC through SSH and Web, then it's OK. If not, you should lock those ports.

---

### Post by mojo_man on 2009-07-11
> **Skorzen said:**
> If you access your PC through SSH and Web, then it's OK. If not, you should lock those ports.

Maybe I am not understanding something. I thought if I do not enable www/80 I cannot browse the web. Can you clarify?

---

