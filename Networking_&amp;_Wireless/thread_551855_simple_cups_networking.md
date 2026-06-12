---
title: "simple cups networking"
date: 2007-09-15
forum: Networking &amp; Wireless
---

### Post by guy.murray on 2007-09-15
Hi,
    have a printer connected to my Ubuntu 7.04 box which works fine with cups.

Tried sharing it so that my laptop can use it using the instructions in the excellent "Ubuntu Unleashed" book, ie editing cupsd.conf on the server to read 
<Location />
 Order Deny,Allow
 Deny From All
 Allow From 127.0.0.1
 Allow From 192.168.0.*
</Location>

The book also mentions setting /etc/cups/cups.d/ports.conf to read "Listen 631", but I can't find this directory or file on my system. The same line appears in cupsd.conf so I assume thats doing the same thing.

Activated "Detect LAN printers" on the client's printers utility and it detected nothing. Also tried activating "Share Printers" on the server's printers utility, still no success.

Anyone any suggestions as to what to try next?

---

### Post by linuxwizard on 2007-09-15
[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

---

### Post by HereInOz on 2007-09-15
The ports.conf file only reared its head in Dapper.  After that, it went back to using the cupsd.conf file.  

You are right in that you need to put those "listen" lines in the cups.conf file.

Then you treat the printer as an Internet printer, accessed by an IP address.

---

### Post by guy.murray on 2007-09-16
many thanks for the quick response.

Unfortunately still no success using either ipp or http. 

Goes through the motions of installing ppd file, but nothing appears on the Printer GUI.

Guy

---

