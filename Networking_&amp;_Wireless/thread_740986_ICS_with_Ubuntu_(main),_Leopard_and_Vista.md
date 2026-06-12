---
title: "ICS with Ubuntu (main), Leopard and Vista"
date: 2008-03-31
forum: Networking &amp; Wireless
---

### Post by rhyguy on 2008-03-31
Ubuntu has a usb modem configured to dchp.
It has a network card with a static ip, connected to a wireless router.
The Vista and Leopard both have wireless cards

How do i share the internet between them?
                                                    
**Internet**--->**Ubuntu**-Wiredto->**Route**r-Wireless->**Vista/Leopard**

---

### Post by nixscripter on 2008-03-31
First, I would generally suggest using the features of the router to share the connection like this:

```

<^^^^^^^^^^^^>     +--------+    +-------+
<  Internet  >---> | Router |--->| Ubuntu|
<------------>     +--------+    +-------+
                      |
                      |
                      V
                  +------------+
                  | Macintosh  |
                  +------------+


```
It will mean buying a wireless card for your Ubuntu machine, but they're pretty cheap. Otherwise, you will have to do what the router does. which is quite complicated:

DHCP server - install the dhcp package, and write a long configuration file.
IP Masquerading - a (quite complex but complete) howto can be found here: [http://tldp.org/HOWTO/IP-Masquerade-HOWTO/](http://tldp.org/HOWTO/IP-Masquerade-HOWTO/)

If you are really determined to do it this way, I'll see if I can help.

---

### Post by rhyguy on 2008-03-31
I used to do that, but the ethernet point on the modem got fried, so i have to use a usb one

---

### Post by rhyguy on 2008-04-01
Basically, i want to turn the ubuntu computer into a router (with a usb modem for internet acsess), connected to a wireless router for sending internet to my home, while still beingable to use internet on my ubuntu computer

---

### Post by nixscripter on 2008-04-04
> **rhyguy said:**
> Basically, i want to turn the ubuntu computer into a router (with a usb modem for internet acsess), connected to a wireless router for sending internet to my home, while still beingable to use internet on my ubuntu computer

Alright, let's see if I can talk you through this. Only begin this if you think you can live with only your Ubuntu machine connected to the internet for a while. It will take several steps, and I want to take this one step at a time (meaning there may be real time between posts where you may be left "hanging").

The first step is to hook that machine up to the modem directly and get internet going to it. When you are connected, your ISP should give you an IP address, DNS information and a few other things. This may be what you have now (depending on how you are accessing this forum). 

Once you get that working, run the following commands while connected to give me a better idea of what your configuration is: ```
ifconfig -a
``````
route
``` Also, would help to know exactly what kind of router it is, so I can research how to configure it.

The next step will be getting the router connected to the Ubuntu machine with a simple IP address. Let me know once you get the first step working.

---

