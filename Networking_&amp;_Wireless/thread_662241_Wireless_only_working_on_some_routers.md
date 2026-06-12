---
title: "Wireless only working on some routers"
date: 2008-01-08
forum: Networking &amp; Wireless
---

### Post by da-bitsch on 2008-01-08
Hi

I recently installed ubuntu 7.10 on my zepto 6625 laptop. All my hardware was detected except my wireless lan card (atheros ar5418). I used ndiswrapper to install it. Everything seemed to work fine. By that i mean: it finds all the local networks perfectly, but i can't seem to connect to my own network (or any of the others but they are encrypted). First i thought something was wrong with the driver for the w-lan card, but then i discovered that i can connect to the internet, wirelessly, on my university without any problems. I have a d-link dir 635 router btw. I invited a friend also with ubuntu 7.10 over to see if he could connect. He did that without any problems. I can connect to the w-lan in Windows as well - Can anyone help me solve this issue?

---

### Post by texasjim on 2008-01-08
I have a similar problem on a D-link DIR-615 bought last weekend. It connects & works with a vista laptop, Ubuntu Gutsy with atheros driver on one machine, but not on my other Gutsy machine. Have tried with a Marvell chipset & ndiswrapper (previously worked on the bricked router) and a d-link card with the atheros Chipset(same - worked before but not on new router). It will connect to the net but only transfer data for a short time, then quit. Maybe get google home page up but not go to ubuntu forums.  When it hangs, can't even ping the router.

I have used DHCP and manual configs, updated router firmware, re-booted, reset to factory and reconfigged(twice) but no joy. 
 Would appreciate and suggestions.

  Jim
EDIT Also blacklisted ipv6 in modprobe.d and turned it off in firefox about:config

---

### Post by da-bitsch on 2008-01-09
interesting: i had the same problem as you with the router hanging after a short while. That only accured in xp though... so i had to install vista (sucks)... In ubuntu though, I can't even connect to the router. It finds the router just fine but can't connect. Must be someone out there with an answers :) this 20 meter cable looks awfull.

---

### Post by texasjim on 2008-01-09
Here's the thing I did and the d-link atheros card is working ok:
1. Check Network & Network Tools for SSID, make sure it's your router's name.
2. Straight DHCP on your adapter.
3.I also did a re-install from the repos of Firestarter and KWIFI, and reconfigured both.
This got me connected but Firefox wouldn't work. So,
4. Re installed Firefox from Gutst repo.

5. Works ok now, gonna try the wireless-n card tomorrow.

Good Luck
  Jim

---

### Post by texasjim on 2008-01-09
> **da-bitsch said:**
> interesting: i had the same problem as you with the router hanging after a short while. That only accured in xp though... so i had to install vista (sucks)... In ubuntu though, I can't even connect to the router. It finds the router just fine but can't connect. Must be someone out there with an answers :) this 20 meter cable looks awfull.

Can you access your router's config? If so you can LOOK from any wan or lan box.
If you need to CHANGE something only do it from the system that is cable-connected to the D-link.
Or else you will have a D-link brick.

Open a browser and in the search box at the top, enter the router's address:
192.168.0.1  (for my d-link, yours is probably the same).
click LOGIN at the admin screen (enter password if needed, fac default is empty password).
Click the STATUS tab  and check your settings, particularly the Network Name in the Wireless LAN section on the first page.
Also check below that in the LAN COMPUTERS section for your machine's name. If there,copy the
IP ADDRESS shown go to the TOOLS tab, then SYSTEM CHECK and use that address to ping your machine. If you can ping, most likely the router-to-your machine link is OK.
Check on a linux box that does work in the NETWORK TOOLS , DNS tab; for your DNS server.  Mine 24.93.41.195 & 196. Ping those from the router (should work).
Check D-link for upgraded firmware. My 615 was about 3 upgrades behind NIB.
Sorry if these are too detailed I want to be clear without talking too slow, but I don't know your level of expertise.

  Jim

---

### Post by texasjim on 2008-01-22
Update: Installed WICD from sourceforge.net and my wireless problem went away.  Not completely happy, it only connects to 1 interface at a time, so I had to monkey with the wired connedtion, for internet sharing, but I got it going.  WICD and firestarter seem to be mutually exclusive, so am looking for a firewall that gets along with it.

   Good luck
  Jim

---

