---
title: "Printing from a xp machine"
date: 2006-09-15
forum: Networking &amp; Wireless
---

### Post by irish1916 on 2006-09-15
I ca not get my wifes windows laptop to print to my kubuntu box.printer works fine in kubuntu.started and stopped server several times with no luck.I can see the windows box but not the other way.I cant get into cups it will not accept passwd sudo or root.any help appreciated

---

### Post by mitch.c on 2006-09-15
> **irish1916 said:**
> I ca not get my wifes windows laptop to print to my kubuntu box.printer works fine in kubuntu.started and stopped server several times with no luck.I can see the windows box but not the other way.I cant get into cups it will not accept passwd sudo or root.any help appreciated

Heres how I set mine up (private network):
```
# /etc/cups/cups.d/ports.conf
#Listen localhost:631
Listen *:631
Listen /var/run/cups/cups.sock
```
Restart the cups daemon
```
sudo /etc/init.d/cupsd restart
```
Then in Windows...
1. Start -> Printers and Faxes -> Add a Printer
2. Select 'A network printer, or a printer attached to another computer'
3. Select 'Connect to a printer on the Internet or on a home network'
4. In URL type: 'http://server:631/printers/nameofprinter' (substitute your info, drop the quotes)
5. Follow through rest of the Wizard to install the driver

Seems to work fine.

---

