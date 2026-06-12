---
title: "[SOLVED] Share internet connection via ethernet cable"
date: 2008-03-02
forum: Networking &amp; Wireless
---

### Post by stooshbunutu on 2008-03-02
Have been trying to connect laptop and desktop (both Gutsy Gibbon) so that the desktop can access the internet to install updates and required drivers for wireless internet connection (laptop has wi-fi).

I have installed firestarter on both and and have configured it according to the website so that both use the server gateway 192.168.1.1 with the laptop being 192.168.0.1 and the desktop being 192.168.0.2

I have managed to get it to the point that both computers can ping each other with speedy response via the ethernet cable "eth0". However the desktop is still unable to connect to the internet whereas the laptop is (via Netgear WG111v3 USB to Netgear router connection).

Any Ideas as to what I can do from here?

Replies much appreciated.

Regards, Stooshbunutu

---

### Post by SpaceTeddy on 2008-03-02
mhm... i don't understand the setup fully... 

is it

laptop <--ethernet---> PC <--USB--> modem <----> internet

or am i misunderstanding somethere there ?

also, is the pc the one that shall share the internet with the laptop ?
what is the internet device on the PC then ?

if this is the setup, i think i can help...

---

### Post by superprash2003 on 2008-03-03
i too had a lot of problems in configuring ICS in firestarter.. i used the ICS guide here [www.ubuntuguide.org](www.ubuntuguide.org) .. its through another way...

---

### Post by stooshbunutu on 2008-03-03
> **SpaceTeddy said:**
> mhm... i don't understand the setup fully... 

is it

laptop <--ethernet---> PC <--USB--> modem <----> internet

or am i misunderstanding somethere there ?

also, is the pc the one that shall share the internet with the laptop ?
what is the internet device on the PC then ?

if this is the setup, i think i can help...

Using the same symbols my setup it

internet <----> modem <----> router <--USB(Netgear WG111v3)--> laptop <--ethernet--> PC

So laptop to give internet access to PC.

---

### Post by stooshbunutu on 2008-03-03
> **superprash2003 said:**
> i too had a lot of problems in configuring ICS in firestarter.. i used the ICS guide here [www.ubuntuguide.org](www.ubuntuguide.org) .. its through another way...

Cheers, will have a look and see what I can do.

---

### Post by Dennis on 2008-03-03
Unless I am misunderstanding this completely, why do you want to go through the laptop and not just plug the ethernet cable into the router?

---

### Post by stooshbunutu on 2008-03-03
> **Dennis said:**
> Unless I am misunderstanding this completely, why do you want to go through the laptop and not just plug the ethernet cable into the router?

Fair point but its because of where they are, I need the internet to get the drivers for the wireless on the desktop but the PC is in my room and the modem/router is in my dad's office downstairs on the other side of the house, unplugging all the wiring would take ages so I wanted a better way

---

### Post by SpaceTeddy on 2008-03-04
i've written down a few steps - maybe this helps you

> [http://ubuntuforums.org/showthread.php?t=713874](http://ubuntuforums.org/showthread.php?t=713874)

---

### Post by stooshbunutu on 2008-03-04
> **SpaceTeddy said:**
> i've written down a few steps - maybe this helps you

Cheers Space Teddy, will give it a properlook and try it out when I get home.

---

### Post by stooshbunutu on 2008-03-25
So I coppide accross via a USB pen all the necessary drivers and installed my USB wireless on the Desktop

---

