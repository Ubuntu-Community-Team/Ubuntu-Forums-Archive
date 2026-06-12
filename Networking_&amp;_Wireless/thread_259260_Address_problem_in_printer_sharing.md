---
title: "Address problem in printer sharing"
date: 2006-09-17
forum: Networking &amp; Wireless
---

### Post by R11 on 2006-09-17
Hi,
I´m having a problem with sharing a local printer under ubuntu with an xp system:

[B]Unable to bind socket for address 0.0.0.0:631 - Address already in use.

Unable to bind socket for address 192.168.2.24:631 - Cannot assign requested address.[/B]

Both are from the Cups 1.2.2 error log.
The first one shows up when I "Allow From" any wildcards,
the 2nd one when I specify the IP address of the XP PC.
They come up at every restart of the cupsys.

Here´s my overall setup:

HP Deskjet 520 on an Ubuntu PC via LPT#1. Installed straight via Gnome-Cups-app, works perfectly.

cupsd.conf looks like this:

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
# These settings are configured in /etc/cups/cups.d/ports.conf so that
# changing them does not require to change this file.
# Listen localhost:631
# Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
# The 'Browsing' setting is configured in /etc/cups/cups.d/browse.conf
# so that changing it does not require to change this file.
# Browsing Off
BrowseOrder allow,deny
BrowseAllow @LOCAL
BrowseAddress @LOCAL

# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Restrict access to the server...
<Location />
  Order allow,deny
  Deny From All
  Allow localhost
  Allow From 192.168.2.24
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Order allow,deny
  Allow localhost
  Allow From 192.168.2.24
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
  AuthType Basic
  Require user @SYSTEM
  Order allow,deny
  Allow localhost
  Allow From 192.168.2.24
</Location>

# Set the default printer/job policies...
<Policy default>
  # Job-related operations must be done by the owner or an adminstrator...
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  # All administration operations require an adminstrator to authenticate...
  <Limit Pause-Printer Resume-Printer Set-Printer-Attributes Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Add-Printer CUPS-Delete-Printer CUPS-Add-Class CUPS-Delete-Class CUPS-Accept-Jobs CUPS-Reject-Jobs CUPS-Set-Default>
    AuthType Basic
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

# Include files in /etc/cups/conf.d
Include /etc/cups/cups.d/ports.conf
Include /etc/cups/cups.d/browse.conf

#
#

ports.conf looks like this:

Listen localhost
Listen *:443
Listen 192.168.2.24:631
Listen *:80
Listen /var/run/cups/cups.sock


browse.conf looks like this:

Browsing On


The reason the .confs are so mixed up is because I´ve followed about 6 different tuts on this, all different of course. 

So what´s this "unable to bind socket to address" about, and how can I solve this, as this seems to be my problem.

Both PCs can ping each other, but the XP can´t access Cups via browser (192.168.2.12:631) nor install the printer via IPP (just stops with an unspecified error).

Thanks in advance for any help.

---

### Post by eltorodeoro on 2006-09-26
This is a shot in the dark, as I stumbled onto this post trying to set up my cups charing for the first time - but have you tried removing the **Deny from All** in the Access to Server portion?

If cupsd reads this file anything like a firewall reads access lists, that line will prevent anything from working - it runs into that line, then says "oh - okay, deny all.  done with that task!"  It may not even pay attention to the following lines.

Again - just a shot in the dark.

jc

---

