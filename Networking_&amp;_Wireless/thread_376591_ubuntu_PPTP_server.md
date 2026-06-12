---
title: "ubuntu PPTP server"
date: 2007-03-05
forum: Networking &amp; Wireless
---

### Post by allen84us on 2007-03-05
i had jz install the Poptop for my ubuntu as a pptp server.
but the problem is ...where i should to configure those parameter..
thanks

---

### Post by allen84us on 2007-03-05
for ur info.i'm using ubuntu 6.06 dapper

---

### Post by Tuptut on 2007-03-29
...confused , Are you looking for poptop (pptpd) configuration file (/etc/pptpd) ? 
Please elaborate on the issue ?

---

### Post by burgundy on 2007-05-25
I'd like to bump this thread... recently I've been searching around for vpn server or pptpd information.

I know what a VPN is, but not much about how it works from a configuration standpoint.  I'm assuming it is just another service running on my Ubuntu box and I need to open a port for which clients on the outside can connect and gain local network access.

Eventually I'd like to use a WinXP laptop to VPN into my home network and access samba data and/or shared windows folders.

I've seen questions asked and vague answers where people figure things out on their own, but not many specifics.

---

### Post by Steveorevo on 2007-08-03
Here here, I would like to do the exact same thing.... A How To would be nice, or a GUI even better!

---

### Post by LittleCannon on 2007-08-03
Install webmin, open your browser and type "https://localhost:10000" and from there you can configure almost everything on your box, including PPTP VPN server.

---

### Post by Synflux on 2007-08-03
> **LittleCannon said:**
> Install webmin, open your browser and type "https://localhost:10000" and from there you can configure almost everything on your box, including PPTP VPN server.

Seconded. I configured pptp through webmin in all of approx 5 minutes. To get your vpn to work from the internet you'll need to forward tcp port 1723 to your server and also protocol 47 (GRE).

---

