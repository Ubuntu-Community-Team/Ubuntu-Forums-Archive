---
title: "Sharing a printer with XP"
date: 2008-04-07
forum: Networking &amp; Wireless
---

### Post by ockron on 2008-04-07
Hi all.

I installed Feisty on my desktop that I share over a wireless network with 2 XP laptops.
I attached my printer to the desktop and created a shared drive on the desktop.
I was able to solve the pw problem when trying the browse the desktop.

I am still unable to share the printer. 
I have tried this thread   [https://help.ubuntu.com/community/NetworkPrintingFromWinXP](https://help.ubuntu.com/community/NetworkPrintingFromWinXP)
BUT my cupsd.conf file does not have the "Listen" configurations. 
> LogLevel warning
SystemGroup lpadmin
# Allow remote access
Port 631
Listen /var/run/cups/cups.sock
# Share local printers on the local network.
Browsing On
BrowseOrder allow,deny
BrowseAddress @LOCAL
DefaultAuthType Basic
<Location />
  # Allow shared printing...
  Order allow,deny
  Allow @LOCAL
</Location>
<Location /admin>
  Encryption Required
  Order allow,deny
  Allow localhost
</Location>
<Location /admin/conf>
  AuthType Basic
  Require user @SYSTEM
  Order allow,deny
  Allow localhost
</Location>
<Policy default>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Pause-Printer Resume-Printer Set-Printer-Attributes Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Add-Printer CUPS-Delete-Printer CUPS-Add-Class CUPS-Delete-Class CUPS-Accept-Jobs CUPS-Reject-Jobs CUPS-Set-Default>
    AuthType Basic
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit All>
    Order deny,allow
  </Limit>
</Policy>
Printcap /var/run/cups/printcap

Is there anyone that can help me please.

Thanx!!

---

### Post by dstew on 2008-04-08
> # Allow remote access
Port 631
Listen /var/run/cups/cups.sockI think these are the lines that describe how cups should listem for requests. Just add the Listen *<ipaddress>*:631 line after the Listen /var/run/cups/cups.sock line. You might have to restart CUPS after you edit the cupsd.conf file:```
/etc/init.d/cups restart
```

---

