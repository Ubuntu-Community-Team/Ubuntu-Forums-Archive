---
title: "Very Slow access to CUPS"
date: 2008-06-04
forum: Networking &amp; Wireless
---

### Post by fluoblack on 2008-06-04
Hello!
I installed successfully CUPS and my HP 845c printer on my server following this howto: [http://ubuntuforums.org/showthread.php?p=1831119]("http://ubuntuforums.org/showthread.php?p=1831119")

The printer works fine except that i have to wait a least 2 min for the printer to show up in the printing dialogs, one more for the print button to be clickable, and like 5min for the cups web page to load completely.

The computers can see each other on the network and communicate freely, there is no problem with the router/firewall.

I must have made a mistake in the config but I don't know where (I'm a cups newbie).

cupsd.conf looks like this:

```
#
#
#   Sample configuration file for the Common UNIX Printing System (CUPS)
#   scheduler.  See "man cupsd.conf" for a complete description of this
#   file.
#

# Log general information in error_log - change "info" to "debug" for
# troubleshooting...
LogLevel warning

# Administrator user group...
SystemGroup lpadmin


# Only listen for connections from the local machine.
Listen 631
Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
Browsing On
BrowseOrder allow,deny
BrowseAllow all
BrowseAddress @LOCAL

# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Restrict access to the server...
<Location />
  Order allow,deny
  Allow 192.168.1.34
  Allow 192.168.1.35
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Order allow,deny
  Allow 192.168.1.34
  Allow 192.168.1.35
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  Order allow,deny
  Allow 192.168.1.34
  Allow 192.168.1.35
</Location>

# Set the default printer/job policies...
<Policy default>
  # Job-related operations must be done by the owner or an administrator...
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  # All administration operations require an administrator to authenticate...
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # All printer operations require a printer operator to authenticate...
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # Only the owner or an administrator can cancel or authenticate a job...
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  <Limit All>
    Order deny,allow
  </Limit>
</Policy>
DefaultEncryption Never
#
#
```

The server runs Ubuntu hardy server 32bit and the client is running Ubuntu hardy -gnome- 64bits

Any help would be much appreciated.

---

### Post by fluoblack on 2008-06-07
up

---

### Post by willix on 2008-08-14
Hy
I've got similar problem '5min for the cups web page to load completely'.

Have you figured it out by any chance yet???

---

### Post by fluoblack on 2008-08-15
Nope, the beast is still printing but is as slow as a snail: about 1min30 for the print button to be clickable and I don't access the webpage anymore beacause it's too slow.

---

### Post by Manthis on 2010-02-13
I exactly have the same problem. Did someone figure out why?

---

