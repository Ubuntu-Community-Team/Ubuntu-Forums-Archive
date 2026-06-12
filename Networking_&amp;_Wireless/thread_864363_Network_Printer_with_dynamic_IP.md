---
title: "Network Printer with dynamic IP"
date: 2008-07-19
forum: Networking &amp; Wireless
---

### Post by chickendude1313 on 2008-07-19
Hi,

First off, I'm running Hardy (8.04)
I have an HP 7210 OfficeJet

My network printer is plugged straight into the router. It has its own dynamically assigned IP adress from the router.

The printer configuration administrative tool detects the printer fine, but if the IP of the printer changes, then I have to go back and reconfigure the printer with the new IP.

If I type the printer's current IP into a browser, I'm taken to the config page for the printer. It shows the dynamic IP as well as a hostname of HPOFFICEJET720. How can I make ubuntu configure the printer based on the hostname rather than the IP address (which changes).

---

### Post by bab1 on 2008-07-19
I don't believe it is possible to hand out IP addresses based on hostname.  But you can get around the problem you have.  First reduce the pool of addresses that are dynamically handed out (DHCP range).  Then assign a static IP address *outside* of the dynamic range.  I have dhcp reduced to 192.168.1.50 to 192.168.1.55.  My printer is 192.168.1.200

---

### Post by chickendude1313 on 2008-07-20
Thanks. That's what I figured.

Seems like bad news for ubuntu though because this can be done through XP quite easily.

The printer can have its IP assigned dynamically through DHCP and have its own hostname. It's right in printer settings for XP. You can specify either hostname or IP address.

I'll go ahead and make a static IP.
thanks

---

