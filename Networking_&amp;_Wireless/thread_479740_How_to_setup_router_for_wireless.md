---
title: "How to setup router for wireless"
date: 2007-06-20
forum: Networking &amp; Wireless
---

### Post by HgBoy on 2007-06-20
I have a dlink wbr-1310 wireless router. It is connected by an ethernet cable to my pc, and I am trying to setup the wireless portion of the router for a laptop. The laptop is picking up networks, so I am going to assume it is configured properly( I might just need to change it from ad-hoc mode). The wireless light on the modem is on, so it is transmitting data. The program (Kwifi manager) sees the connection, but says "no access point". Is there a specific IP adress I can give the card to look for as opposed to DHCP? This is my first attempt at netwroking, so I'm a little lost here.

---

### Post by Gannin on 2007-06-20
If your laptop is in ad-hoc mode, it won't work with the router properly.  As for an IP address, you could try 192.168.0.1.

---

### Post by HgBoy on 2007-06-20
how do I turn off the ad-hoc mode? It is a broadcom 43xx based integrated wireless card

---

### Post by Gannin on 2007-06-20
Do you know what device your wireless card is listed as?  I mean wlan0, eth0, etc.

---

### Post by HgBoy on 2007-06-20
I am pretty sure it is eth1.

---

### Post by Gannin on 2007-06-20
From a terminal, type "iwconfig", and it should tell you both the device name for your wireless card and what mode it's currently in.

---

### Post by HgBoy on 2007-06-20
the card is connected to the network now, but firefox still wont allow me internet access. What now????

---

### Post by Gannin on 2007-06-20
So you're saying the card is indeed in managed mode and not ad-hoc?

---

### Post by HgBoy on 2007-06-20
Yes.

---

### Post by Gannin on 2007-06-20
Just to be safe, I'd say restart the laptop.  After that, if Firefox or any other programs can't access the Internet, then it sounds like it might be an issue with security settings.

---

### Post by HgBoy on 2007-06-20
still nothing. I dont have a firewall setup, or a proxy as far as I know. Is there somewhere I can check these things?

---

### Post by loserboy on 2007-06-20
can you connect to the router itself?

---

### Post by Gannin on 2007-06-20
Have you ever enabled any security on the router, like WEP or WPA?  Some routers come with security enabled by default.

---

### Post by HgBoy on 2007-06-20
I have the router configured as an open connection, as I expected a little bit of diffu=iculty setting it up initially. As for connect to the router itself, I have a connection in my wifi manager, with an IP address and an access point on the router.

---

### Post by Gannin on 2007-06-20
But can you access the router's internal web page from both your wired and wireless connections?

---

### Post by HgBoy on 2007-06-20
not on thw wireless connection

---

### Post by HgBoy on 2007-06-20
thanks for the help guys. got it up and running.

---

### Post by HgBoy on 2007-06-20
Well, it worked for about 30 minutes.... I hooked up the laptop to an HD tv, and everything went smoothly. I had to restart the laptop, and now the wireless card seems to have stopped working altogether. It shows up in iwconfig, but I cant seem to get it to respond through any of the wifi managers. What to check first??

---

### Post by steveyeager on 2007-06-26
I am having trouble seeing my router.  I also have a broadcom wireless card and it works to see my neighbor's routers but not my dlink router.  Any suggestions?

---

