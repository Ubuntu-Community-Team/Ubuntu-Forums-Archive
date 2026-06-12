---
title: "printer sharing please help"
date: 2008-10-07
forum: Networking &amp; Wireless
---

### Post by esmailgad on 2008-10-07
Hi everyone
I followed the  advise of some of you on the modification of the cupsd.conf file. I can not share the linux to linux  printer. 

Please help 
 I appreciate a lot your help and the  file is as follows: and I still stuked. 

LogLevel warning
SystemGroup lpadmin
# Allow remote access
Port 631
listen localhost:631
#Listen /var/run/cups/cups.sock
# Enable printer sharing and shared printers.
Browsing On
BrowseOrder allow,deny
BrowseAllow all
BrowseAddress @LOCAL
DefaultAuthType Basic
<Location />
  deny from all
  Allow from 127.0.0.1
  Allow from 127.0.0.2
  Allow from 192.168.1.*
  # Allow shared printing and remote administration...
  Order allow,deny
  Allow all
</Location>
<Location /printers>
  Order allow,deny
  deny from all
  Allow from 192.168.1.*
</Location>
<Location /jobs>
  Order allow,deny
  deny from all
  Allow from 192.168.1.*
</Location>
<Location /admin>
  Allow from 127.0.0.1
  Allow from 127.0.0.2
  Allow from 192.168.1.*
  # Allow remote administration...
  Order allow,deny
  Allow all
</Location>
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  # Allow remote access to the configuration files...
  Order allow,deny
  Allow all
</Location>
<Policy default>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit All>
    Order deny,allow
  </Limit>
</Policy>

---

