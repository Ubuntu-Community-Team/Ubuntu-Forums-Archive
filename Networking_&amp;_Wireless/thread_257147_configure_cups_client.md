---
title: "configure cups client"
date: 2006-09-14
forum: Networking &amp; Wireless
---

### Post by hca on 2006-09-14
How can I configure cups client?
On my home LAN cups server is 192.168.1.185 on which an HP Deskjet 1100C is installed locally and working OK. 
Following advice in 'http://ubuntuguide.org/wiki/Dapper#How_to_install_cupsd' I have editid /etc/cups//cupsd.conf to:
# Restrict access to the server...
<Location />
  Order allow,deny
  Allow localhost
  Allow 192.168.1.222
  Allow @LOCAL
</Location>
I then restarted cups.
On the client I cannot find the cups file /etc/cups/client.conf. It does not show up on a sudo ls /etc/cups.
On the client setting up the printer in System>Administration>Printing>New Printer I can set up a printer and request a test page print but nothing comes up on the printer. The request remains on the print queue and several retries of removing and reapeating remain unsuccessful.

From browsing various parts of Ubuntu forums it seems that several users share my problem but no viable solutions are applicable in my case. I believe we have a documentaion problem or we are missing the proper HOWTO. Please can anybody help?

---

### Post by pod25 on 2006-09-14
By the simple fact that no one has replied, should be your answer ! .

I too are having a nightmare of a time trying to configure my printer and network the damn thing.

---

### Post by tbonius on 2006-09-14
```

## Cupsd.conf
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
Allow From 192.168.0.0/24
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
Allow From 192.168.0.0/24
</Location>

```

Be sure and allow browsing from other hosts and tunr Browsing ON in your "cupsd-browsing.conf" (Brwosing On).  In my case I used 192.168.0.0/24.  Once allowed.. the printer should just show up in your Printer List.  From Windows you can either have samba use the cups service.. or install an IP based printer in Windows.  From MACs the printer also just shows up.

---

