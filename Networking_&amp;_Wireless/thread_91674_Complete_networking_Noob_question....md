---
title: "Complete networking Noob question..."
date: 2005-11-17
forum: Networking &amp; Wireless
---

### Post by tomwell on 2005-11-17
Hi all,

Is it possible to view other computers and monitor there internet activities if they are not running linux??

all computers would be connected via a LAN... If its possible i will look more into it... AM a Total Noob but I have been sucked into the Linux world and am Super curious!!!

Peace to all!!!

Tom:D

---

### Post by aznboi on 2005-11-17
for the computer u want to view:
goto 
```
www.tightvnc.com
```
Download that and install it. when it is intalling it might ask if u want to install the service, make sure u have that option enabled. After that is done it will ask you to set the default passwords. The control password will make it so that when u enter that password you will be able to control the whole computer, there is another box that is View only password which u can set so that u dont have to control the computer, u can just view it. Once that is all done and u have typed in hte desired passwords, cllick ok and then hover hte mouse over the VNC symbol in the taskbar, and it should say the IP address. On another computer, open up VNC Viewer, enter in the IP address given (could also be network address like 192.168.0.1 or something for when u r not connected to the internet but to hte computer through a LAN) and then enter the password.

---

### Post by tomwell on 2005-11-18
Hey, Thank you for answering my post...

so in other words with tightvnc am able to view the internet usage of other computers on the network... its just that i have 2 other macs on the network and i want to be able to regulate what the users are viewing... Am i correct in assuming that??

Thanks for your help!!!

Peace 

Tom

---

### Post by pete on 2005-11-18
[QUOTE=tomwell]Hey, Thank you for answering my post...

so in other words with tightvnc am able to view the internet usage of other computers on the network... its just that i have 2 other macs on the network and i want to be able to regulate what the users are viewing... Am i correct in assuming that??

Thanks for your help!!!

Peace 

Tom[/QUOTE]

Not really--  tightvnc allows you to remotely view/control a desktop (e.g., you have a window on your desktop that displays the remote computer's desktop, which you can control via mouse and keyboard, and anyone sitting at the remote computer can see what you're doing).  

Sounds like what you're looking for is more networking traffic monitoring and control...

---

### Post by tomwell on 2005-11-18
I think thats more what i want... what kind of progs can i get...

VNC sounds more like something a naughty person  might use to take control of another computer...LMAO!!!!

Sorry had a couple of beers and am feeling Goofy!!!

Peace

Tom

---

### Post by ranf on 2005-11-18
[QUOTE=tomwell]
Is it possible to view other computers and monitor there internet activities if they are not running linux??

all computers would be connected via a LAN... If its possible i will look more into it... [/QUOTE]
`ethereal' can capture any IP packet floating thru your LAN.
`dsniff' - "Various tools to sniff network traffic for cleartext insecurities"

---

### Post by fakie_flip on 2007-02-17
> **ranf said:**
> `ethereal' can capture any IP packet floating thru your LAN.
`dsniff' - "Various tools to sniff network traffic for cleartext insecurities"

dsniff doesn't seem to be doing anything. I even tried Wireshark, but what good is the packet information it shows if it is all in hex code? What does all that packet information mean, and what good is it to know? This is what I have tried.

Is this correct? The default gateway (the router) of the network is 192.168.1.1, and the computer that I want to sniff packets of on my home network is 192.168.1.100. 

```
sudo arpspoof -i eth0 -t 192.168.1.100 192.168.1.1
0:14:2a:bd:89:a2 0:a:48:12:f9:17 0806 42: arp reply 192.168.1.1 is-at 0:14:2a:bd:89:a2
0:14:2a:bd:89:a2 0:a:48:12:f9:17 0806 42: arp reply 192.168.1.1 is-at 0:14:2a:bd:89:a2
0:14:2a:bd:89:a2 0:a:48:12:f9:17 0806 42: arp reply 192.168.1.1 is-at 0:14:2a:bd:89:a2
0:14:2a:bd:89:a2 0:a:48:12:f9:17 0806 42: arp reply 192.168.1.1 is-at 0:14:2a:bd:89:a2
0:14:2a:bd:89:a2 0:a:48:12:f9:17 0806 42: arp reply 192.168.1.1 is-at 0:14:2a:bd:89:a2
... keeps going
```

While letting that run, shouldn't I be able to see some packets that were supposed to go to the 192.168.1.100 computer or packets being sent from it? I run these commands, but they aren't outputting anything.

```
sudo webspy -i eth0 192.168.1.100
Password:
webspy: listening on eth0
```

```
sudo urlsnarf -i eth0
Password:
urlsnarf: listening on eth0 [tcp port 80 or port 8080 or port 3128]
```

```
sudo dsniff -i eth0 
Password:
dsniff: listening on eth0
```

I tried Wireshark too and it showed some packets, but it is all in hex code and strange symbols, so what good is it?

---

