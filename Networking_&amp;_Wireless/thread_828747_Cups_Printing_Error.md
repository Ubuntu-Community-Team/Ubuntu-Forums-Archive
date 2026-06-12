---
title: "Cups Printing Error"
date: 2008-06-14
forum: Networking &amp; Wireless
---

### Post by dinkoarun on 2008-06-14
I have installed Ubuntu Server 8.04 with Samba and OpenLDAP authentication. I am trying to make my domain users print the shared printer installed in CUPS. The users are able to install the printer without any problem. But when they try to print anything, nothing happens. It does not even get recorded in the Printer Job Log.

Then I went and saw the Samba log for that user. In the log, there is an error that says:

[B][2008/06/13 14:31:59, 0] printing/print_cups.c:cups_pull_comment_location(1266)
  Unable to get printer attributes - client-error-not-authorized[/B]

The following is my configuration of the cupsd.conf file:

[I]#
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
Listen 10.0.11.10:631
	
# Show shared printers on the local network.
Browsing Off
BrowseOrder allow,deny
BrowseAllow all
BrowseAddress @LOCAL

# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Restrict access to the server...
<Location />
AuthType Basic
AuthClass System

  Order allow,deny
Allow from All
</Location>

# Restrict access to the admin pages...
<Location /admin>
AuthType Basic
AuthClass System

  Order allow,deny
Allow From All
#Allow From 10.0.11.168
</Location>

<Location /printers/>
AuthType Basic

  Order allow,deny
Allow from All
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

#[/I]
#

---

### Post by superprash2003 on 2008-06-14
thats cause it requires authentication.. first try and access a shared folder on the pc which has the printer ( it will ask for username,password etc) then try to print..

---

