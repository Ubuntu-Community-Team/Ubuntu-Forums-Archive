---
title: "Can't get it up... the internet that is."
date: 2007-08-02
forum: Networking &amp; Wireless
---

### Post by cmaksymchuk on 2007-08-02
Ok, so here is my story.  I dual booted win xp and ubuntu server 7.04.  During my ubuntu install I had 2 network cards in my comp - Wired and Wireless.  I chose the wired as the card I wanted to use and ubuntu succesfuly auto configured (or so it said) my dhcp.  

Everything seems to be as it should.  Ubuntu sees my network card, says its enabled (I have now taken my wireless right out of the box).  I have used this card with this version of ubuntu previously and everything worked.  Stranger yet, when I boot in to windows, the internet works sweet.

To sumarize, ubuntu sees my card, says dhcp is configured.  The internet connection works and ubuntu is alright with my network card, but yet my internet does not work.  

Any clues on where do I start?

---

### Post by muddymind on 2007-08-02
type ifconfig in the terminal to see if U have a valid ip..

---

### Post by kevdog on 2007-08-02
Did you install any drivers for the wireless card??  You can check with the following at command line (cut and paste output please):
lspci -nn
lshw -C network

Also you cant use wired and wireless connections (usually) at the same time without some advanced configuration.

---

### Post by Martje_001 on 2007-08-02
Do you get anything as you type an IP?

---

### Post by cmaksymchuk on 2007-08-02
kevdog
- I want trying to use both cards.  I only wanted to use the wired card (as I specified in the install).  I took out the wireless card after I started having problems and am not really interested in a wireless connection.  The wired card has and will work , just need to figure it out.

Martje_001
- Not sure what you mean?

muddymind
- I'm at work right now but will be heading home in 1 hour for lunch. I'll post the results of ifconfig after I run it.

---

### Post by kevdog on 2007-08-02
You can use both, but not at the same time!!

---

### Post by cmaksymchuk on 2007-08-02
Ok, so here's an update ifconfig gives me a eth0 ip of 192.168.2.182 which means my router is giving me an ip.

The interesting part is ping google.com at the shell pings successfuly.  What is going on??

---

### Post by cmaksymchuk on 2007-08-02
ok, no joke, 2 days of it not working, right after i posted the last thread it just started working, no restart, no nothing.  Not sure whats up but glad to have my net back.

Cheers all,

Cory

---

