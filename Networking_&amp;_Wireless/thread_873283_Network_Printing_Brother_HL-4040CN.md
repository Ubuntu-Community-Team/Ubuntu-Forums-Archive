---
title: "Network Printing Brother HL-4040CN"
date: 2008-07-28
forum: Networking &amp; Wireless
---

### Post by HD Chang on 2008-07-28
Hi, I hope someone can help.

I am trying to print from my laptop wirelessly to my Brother HL-4040CN printer.  It has a built-in print server and I have a feeling they arent communicating, but i am not entirely sure of that.

I am running Hardy Heron Xubuntu with a Broadcom legacy wireless driver.
I can get into the print server via firefox and also my other windows networked computer, but i cannot get any life out of my printer.

I followed the instructions on Brothers website:
Install LPR driver then the CUPS wrapper driver, add printer via cups.
I did all this and setup my printer on "lpd://xx.xx.xx.xx/binary_p1".
(yes i put the printers IP in there)

here is my printers conf file:
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
</Location>

# Restrict access to the admin pages...
<Location /admin>
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

My error log gives me these readings when I try to print:
E [28/Jul/2008:19:47:30 -0500] Cancel-Job: Unauthorized
E [28/Jul/2008:19:49:33 -0500] Pause-Printer: Unauthorized
E [28/Jul/2008:19:49:33 -0500] Pause-Printer: Unauthorized
E [28/Jul/2008:19:49:40 -0500] Resume-Printer: Unauthorized

I am on day 2, I need help.

Thanks,

HD

---

### Post by HD Chang on 2008-07-28
By the way, I tried downloading pconf-detect to find my printer on the network and it wont find it.
running
pconf_detect -m NETWORK -i "192.168.1.99-105" or any other ip variation.

---

### Post by HD Chang on 2008-07-28
This probably has nothing to do with anything but when i use netcat

nc -nv 192.168.1.100 *port*
port 80 is open, my webadmin print port
port 515 is closed and 9100 is closed

I just got DSL from cable and had to use PPoe on my router, is it possible its screwing up my connection or do i need to setup a gateway or something?

---

