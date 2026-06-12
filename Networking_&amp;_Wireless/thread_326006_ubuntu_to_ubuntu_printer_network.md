---
title: "ubuntu to ubuntu printer network"
date: 2006-12-26
forum: Networking &amp; Wireless
---

### Post by dbbolton on 2006-12-26
i have a desktop machine running edgy with a psc2175 attatched and working perfectly. the desktop is connected to a linksys wireless router via ethernet cable, and i have a laptop running dapper connected to the same router wirelessly.

i edited cupsd.conf to include the following:
```
 <Location />
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
Allow From 192.168.0.*
Allow From 208.253.100.138
</Location>
```and the line "Listen 631" is included in cupsd.conf. the guide i was using specified that i must edit '/etc/cups/cups.d/ports.conf' to include 'Listen 631' in lieu of 'Listen localhost:631', but such directory/file does not exist on the edgy machine, so i ignored that.

on the laptop, i ran gnome-cups-manager and selected "detect lan printers". the psc2175 is detected, but when i try to print to it, it just says "Ready: x Jobs". when i look at the jobs window, it is blank.

so, i added a new network printer with the uri as the ipp of the printer listed above. "PSC-2175 already exists on the network. Renamed to PSC-2175 1". so, i know it's detecting the printer. 

i tried printing on PSC-2175 1, but it just says "printing" forever and never actually prints anything.

any thoughts ?

---

### Post by halw on 2006-12-28
Man, I hope someone comes along with an answer for you or at least points to a wiki that explains setting up cups print sharing. 

I've been struggling with this myself for sometime now.

---

