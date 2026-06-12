---
title: "Linksys Wireless Print Server &amp; Ubuntu Server (Gutsy)"
date: 2008-02-01
forum: Networking &amp; Wireless
---

### Post by karl@gee-family.org on 2008-02-01
Hello, I having a problem where I can print to my epson printer on the Linksys wireless print server but when finished the print job never goes away, subsequent print jobs never go to the printer and I have the following error in the CUPs error_log file.  (cupsdCloseClient: Error in the push function.)

Does anyone have any ideas?

The cups device url is: [http://192.168.100.201:631/ipp/P2](http://192.168.100.201:631/ipp/P2)
I'm using cups v1.3.2

My cupsd.conf file follows.

LogLevel warning
SystemGroup lpadmin
# Allow remote access
Port 631
Listen /var/run/cups/cups.sock
# Enable printer sharing and shared printers.
Browsing On
BrowseOrder allow,deny
BrowseAllow all
BrowseAddress @LOCAL
DefaultAuthType Basic
<Location />
  # Allow shared printing and remote administration...
  Order allow,deny
  Allow @LOCAL
</Location>
<Location /admin>
  # Allow remote administration...
  Order allow,deny
  Allow @LOCAL
</Location>
<Location /admin/conf>
  AuthType Basic
  Require user @SYSTEM
  # Allow remote access to the configuration files...
  Order allow,deny
  Allow @LOCAL
</Location>
<Policy default>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    AuthType Basic
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
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

And the Printers.conf shows:

# Printer configuration file for CUPS v1.3.2
# Written by cupsd on 2008-02-01 18:30
<Printer EpsonR220>
Info Epson Stylus Photo R220
Location Upstairs
DeviceURI [http://192.168.100.201:631/ipp/P2](http://192.168.100.201:631/ipp/P2)
State Idle
StateTime 1201912100
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>

Thanks

---

### Post by kevinmedina on 2008-05-19
This post needs a much deserved BUMP

Can anyone help - I'm stuck on this as well...

---

