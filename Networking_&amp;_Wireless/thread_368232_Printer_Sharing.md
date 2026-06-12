---
title: "Printer Sharing"
date: 2007-02-23
forum: Networking &amp; Wireless
---

### Post by durty_dawg on 2007-02-23
I got a hp psc1200 usb'd to my windows box, then I got ethernet connection through a linksys 4 port/ IEEE 802.11a/b/g/ wireless router, and my linux box getting wireless internet from the router. So what do I need to do on both ends to share the printer with my linux and windows machines. There is no NIC card in the printer, so it will have to remain USB connected through the windows box.

---

### Post by jethro10 on 2007-02-23
In windows Right click the printer and select "Share"

On the Linux box Add a new printer select the "Samba" type. Use the windows PC name and the Printers share name to get to it.

That should get you closer.

J

---

### Post by durty_dawg on 2007-02-23
Ok so I did the instructions, well i get to the screen where it is requesting the drivers and stuff. SO what do I do now. This is  little confusing.

---

### Post by koenn on 2007-02-23
choose the driver that matches the make and model of the printer

---

### Post by jethro10 on 2007-02-26
> **koenn said:**
> choose the driver that matches the make and model of the printer

Or a near equivalent if there is no such match. Mine does not exist on linux, but the one model number off did. I chose that and its fine.

Your driver comes off linux.

J

---

