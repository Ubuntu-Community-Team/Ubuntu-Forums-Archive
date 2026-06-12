---
title: "The CUPS server could not be contacted."
date: 2005-11-18
forum: Networking &amp; Wireless
---

### Post by foxy123 on 2005-11-18
It's a wierd problem which almost drove me mad yesterday night, when I need to print something over my home network from the laptop. My desktop, which has a  USB printer was booted in WinXP and I did not have any printer available in OpenOffice printing dialog. All my attempts to run gnome-cups manager ended in 
```
** (gnome-cups-manager:7957): WARNING **: IPP request failed with status 1280

** (gnome-cups-manager:7957): WARNING **: IPP request failed with status 1280

```
and error message: 
```
The CUPS server could not be contacted.
```

Although I could see the printer was available in web CUPS interface (localhost:631).

After 40 min of googling and finding nothing I asked my son to boot in Linux and had no problem to print.

This morning I suddenly realised what happened. Since I have my desktop dual-boot, I configured printing for both scenarios: it's booted in WinXP or it's booted in Ubuntu in that exact order. 

I guess I configured my printing system to use only remote CUPS server. So when desktop either switched off or booted in WinXP, there is no CUPS server available in the network and I got this message. I wonder what I've done wrong, because I only edited one file on the laptop: /etc/cups/cupsd.conf, following instructions from [http://occy.net/printing](http://occy.net/printing). This is how it loks now:

```
DefaultCharset notused
LogLevel info
Printcap /var/run/cups/printcap
User cupsys
Group lpadmin
RunAsUser Yes
Port 631
Include cupsd-browsing.conf
BrowseAddress @LOCAL
SystemGroup lpadmin

<Location />
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
Allow From 10.0.0.*
</Location>

<Location /jobs>
AuthType Basic
AuthClass User
</Location>

<Location /admin>
AuthType Basic
AuthClass System
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
</Location> 

```

How should I change it to make local CUPS server available? Or should I edit anything else. Your help will be very much appreciated as I ran into this problem every time my desktop is booted in Windows....

---

### Post by firecat53 on 2005-11-18
Try "sudo /etc/init.d/cupsys restart".

I managed to accidently kill the cups daemon and got the same message....doh!!

Scott

---

### Post by foxy123 on 2005-11-18
[QUOTE=firecat53]Try "sudo /etc/init.d/cupsys restart".

I managed to accidently kill the cups daemon and got the same message....doh!!

Scott[/QUOTE]
no, it is running all right. The problem is (it's my guess) that it does not listen to a local port or whatever. If I boot desktop, where the printer phisically is, in Ubuntu, gnome-cups-manager appears without ay problem.

---

### Post by foxy123 on 2005-11-18
OK, I have found a reason but not the solution.

I commented off the line in my /etc/cups/client.conf:
```
ServerName 10.0.0.11
```

and I can print to Windows printer.

However, I made this line to be ableto print to the Linux printer as well. It worked fine while I was using Hoary, so I could print my laptop regardless how my desktop was booted. 

What is wrong?

---

