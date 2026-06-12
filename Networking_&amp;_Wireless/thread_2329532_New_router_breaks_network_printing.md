---
title: "New router breaks network printing"
date: 2016-07-02
forum: Networking &amp; Wireless
---

### Post by rwigle on 2016-07-02
I replaced my DT-Link wireless router. With the configuration described below I was able to print to my Samsung printer. Since replacing the router, I can no longer print.

My Samsung ML3051ND printer is connected via a switch connected to my new ASUS
RT-N16 wireless router. I have used two approaches to try to print to the printer.

1.  "System Settings => Printer => Search
Network Printer. The printer si found and I select the "found"
printer. But then when I try to print to it, the message I get from
cups is either Unable to locate printer or printer not connected.

2. Choose ipp from Printer's report and then select correct driver.
Same result as above.

To try and follow up I ran the following two commands one after the
other. The SAMSUNG ML3050 series was found. Back to 1. and or 2. above using the supplied address with the same result. 

$ sudo /usr/lib/cups/backend/snmp
$ sudo /usr/lib/cups/backend/dnssd

P.S. Wireless network seems to work fine except when I try to set up printer.

P..P.S. I also noticed that the notification area shows a printer icon and queued jobs for the
printer, but if I open the printer dialog, they have already been deleted. Still the indicator shows jobs to print. This is resolved on reboot.

---

### Post by rwigle on 2016-07-04
I *think* this is now solved. It appears that the printer in question was set to use a fixed IP address (versus allowing it to be set by DHCP). Once I reconfigured that, everything seems to be working.

I am still puzzled that CUPS found the printer and allowed me to install drivers for it, but then could not print to it. If someone can briefly explain why I'd love to hear it just for curiosity sake.

---

