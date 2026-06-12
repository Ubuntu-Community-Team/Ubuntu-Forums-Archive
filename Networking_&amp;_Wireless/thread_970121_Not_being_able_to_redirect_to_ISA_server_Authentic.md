---
title: "Not being able to redirect to ISA server Authentication Page"
date: 2008-11-03
forum: Networking &amp; Wireless
---

### Post by Anakondarh on 2008-11-03
[SIZE="4"]Hi All!!

First, a lil' background info: At the place where I work and live (yes, I live in the same place that I work at), we have a wireless internet connection, managed by an M$ ISA (Internet Security and Acceleration 2006) Server. 

Not that long ago (up until last week, when Intrepid Ibex came out) I had (actually, still do) been using PCLinuxOs 2007 as my distro of choice, and firefox as my web browser. 

Now here's the fun part: The company's ISA server resets its authentication list (I think I just made that term up) every 12 hours or so, meaning we have to input our username and password every day to be able to surf the net. To do this, the moment we open a web browser, we are redirected automatically to a local authentication page ([https://guest.nameofthenetwork.local](https://guest.nameofthenetwork.local)), where we are asked for credentials. 

With PCLinuxOS, I've had no problem with this setup: opening Firefox would automatically redirect me to that local page. However, with a clean Ubuntu 8.10 install [EDIT: 9.04 as well], and firefox 3, I for some reason cannot redirect there, or even PING it. 

Funny thing is, if I boot into PCLOS, authenticate there, and then switch over to Ubuntu, I can surf the net no problem (I think the server stores the authenticated system's MAC address, but I might be wrong). This tells me it's something to do with accessing local addresses, and not a proxy or IVP6 problem... (I did double check that my proxy settings were "direct connection to the internet", both in Firefox's proxy and GNOME's proxy, and deactivated IVP6 in firefox (not sure why, just to try all my options I guess...), but I can't put my finger on what exactly it is. 

I've tried different browsers, complete Firefox removal/reinstall (wiping setting files and all) to no avail. This small detail is the main thing stopping me from switching over to Ubuntu as my main OS (well, that and getting FRIGGIN' PROPER DVD playback without the "stuttering", but I haven't looked into that much yet, gotta fix 1 problem at a time...[EDIT: Solved that as well. Recompile your kernel with the AMD74xx module, and that'll take care of bussiness. PATA_AMD blows.)

Any ideas as to what might be causing this or how to tackle it will be appreciated... couldn't find much by searching the forums or googling.

Thanks to all in advance!!

gene[/SIZE]

---

### Post by Anakondarh on 2008-11-04
Bump anyone?

---

### Post by Anakondarh on 2008-11-05
I've pretty much lost hope, but let's bump this again...

---

### Post by Anakondarh on 2009-01-16
I've lost hope... can't figure this one out!!

---

### Post by movingover on 2009-01-16
Sorry, I tried to read your huge block of text but my head blew up. Please use a little spacing and construct some paragraphs.

---

### Post by Anakondarh on 2009-03-07
[SIZE="4"]Done.[/SIZE]

---

### Post by Anakondarh on 2009-05-08
So I finally figured it out. Took me 6 months, ha. The problem was the nsswitch.conf file in /etc. That file in ubuntu was telling the system to NOT query the local DNS, therefore not being able to match the address with a valid IP address. Copying over the file from Mandriva solved the problem. 

If anyone has the same problem (not being able to access sites in the local network) try backing up your nsswitch.conf file and making a new one with these settings:

```
passwd:		files compat [NOTFOUND=return] db
shadow:		files
group:		files compat [NOTFOUND=return] db

hosts:  	 mdns4_minimal files nis dns mdns4 
networks:	files

services:	files
protocols:	files
rpc:		files
ethers:		files
netmasks:	files
netgroup:	files
publickey:	files

bootparams:	files
automount:	files
aliases:	files

```

Cheers!

---

