---
title: "CUPS recent HowTo"
date: 2009-09-02
forum: New to Ubuntu
---

### Post by ozzyprv on 2009-09-02
I am having problems finding a relatively recent HowTo for setting up a headless server with CUPS.

I tried this one [http://ubuntuforums.org/showthread.php?p=1831119](http://ubuntuforums.org/showthread.php?p=1831119) but I get stuck at some kind of authentication problem when trying to print from a client.

Any help.

Thanks.

---

### Post by cariboo on 2009-09-02
HAve you got:

```
Use Kerberos authentication
```

Checked in the administration section of the cups interface?

---

### Post by ozzyprv on 2009-09-04
I cannot even get access to the website at the server.

All I get is:> 403 Forbidden

Here is my cupsd.conf file:

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
Listen localhost:631
#Listen /var/run/cups/cups.sock
Listen 192.168.1.151:631

# Show shared printers on the local network.
Browsing on
BrowseOrder allow,deny
BrowseAllow all
BrowseAddress @LOCAL

# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Restrict access to the server...
<Location />
  Order allow,deny
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Encryption Required
  Order allow,deny
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  Order allow,deny
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

#
#
```

---

### Post by ozzyprv on 2009-09-05
I wasn't going to give up, so I kept looking.

Added a printer to my server with the help of the information posted here:
[http://www.brennan.id.au/15-System_Printing.html](http://www.brennan.id.au/15-System_Printing.html)

---

