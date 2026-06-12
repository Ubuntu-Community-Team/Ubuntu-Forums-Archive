---
title: "Sharing printer with Vista under CUPS"
date: 2008-06-21
forum: Networking &amp; Wireless
---

### Post by Ocker on 2008-06-21
Hi all, was wondering if anyone could help me with my problem. I have a small home network with three machines and a printer configured as below:

 _ubuntu desktop ____HP C5280 printer
|  192.168.1.101      
|
|_hub __________ router 192.168.1.1 _________ internet
|                    
|
|_ Vista Laptop
|  192.168.1.102
|
|_Vista Desktop 192.168.1.100

All computers & router can talk to each other using Ping. My problem is that while the printer works fine printing from Ubuntu, I can't get the windows machines to detect the printer as a network printer under CUPS. I've tried using the System>Administration>Printing utility, the CUPS web browser interface and manually editing the cupsd.config file to share the printer, all to no avail. My cupsd.config file is shown below, hope someone can give me a hand with this because I'm near stumped with this. Thanks in Advance. :confused::confused::confused:

cupsd.config
~~~~~~~~~~~~~~~~~~~~~
LogLevel warning
SystemGroup lpadmin
# Allow remote access
Port 631
Listen /var/run/cups/cups.sock
Listen *:631
# Enable printer sharing and shared printers.
Browsing On
BrowseOrder allow,deny
BrowseAllow all
BrowseAddress @LOCAL
DefaultAuthType Basic
<Location>
  Allow 127.0.0.1
  Allow 192.168.1.*
# Allow shared printing and remote administration...
  Order allow,deny
  Allow all
</Location>
<Location /admin>
  Allow localhost
  Allow all
  Allow all
  # Allow remote administration...
  Order allow,deny
  Allow all
</Location>
<Location /admin/conf>
  AuthType Basic
  Require user @SYSTEM
  Allow localhost
  Allow all
  Allow all
  # Allow remote access to the configuration files...
  Order allow,deny
  Allow all
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

---

### Post by Ocker on 2008-06-22
Bump

---

