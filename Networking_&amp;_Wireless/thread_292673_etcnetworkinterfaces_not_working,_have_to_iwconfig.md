---
title: "/etc/network/interfaces not working, have to iwconfig"
date: 2006-11-04
forum: Networking &amp; Wireless
---

### Post by caolan on 2006-11-04
Hi everyone,
I've recently managed to set up my RT61 chipset wireless card :D , but I always have to type:

sudo iwconfig ra0 essid XXXX key XXXXXXXXXX

in order to connect to my wireless network. I would like it to just connect automatically at start-up. I have edited my /etc/network/interfaces file and the bit for my wireless interface now looks like this:

iface ra0 inet static
wireless-essid XXXX
wireless-key XXXXXXXXXX
address 192.168.1.44
netmask 255.255.255.0
gateway 192.168.1.1

auto ra0

Unfortunatley this isn't working and I'm having to manually type out the iwconfig command all the time. Can anyone see something wrong in that set up? Do I need to change anything else in order for it to work automatically?

Thanks in advance!

---

### Post by squibT on 2006-11-04
Add the line: "/etc/init.d/networking restart" (sudo not needed, no quotes) to /etc/rc.local. This will run at startup. No permission changes needed on rc.local file either.

---

### Post by nikopol on 2006-11-04
Good fix mate - thanks for that.

Seems to be a strange bug for me as after a fresh install I have no trouble at all for a few weeks then suddenly, the wifi won't connect on startup (or sometimes misconnects - it connects but doesn't get an IP)

 It was there under Dapper and is also under Edgy so I suspect it can't be happening to everyone with wifi but just to a few hardware configs....

---

### Post by squibT on 2006-11-04
Yea, strange....



Glad I could help....

---

