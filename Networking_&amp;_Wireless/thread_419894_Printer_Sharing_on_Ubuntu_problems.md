---
title: "Printer Sharing on Ubuntu problems"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by Anessen on 2007-04-23
Hey
I'm trying to set up a home network using Ubuntu 7.04. I have tried to share a printer between two Ubuntu computers by following the [guide on ubuntuguide.org](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_print_on_remote_Ubuntu_machine_from_another_Ubuntu_machine), but my "Share Printers" option in the Printers dialog is greyed out.

The printer has been added on the host computer, and it can print to it. The printer isn't showing up on the remote Ubuntu computer.

This is my cupsd.conf file on the host computer:

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
Listen *:631
Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
Browsing Off
BrowseOrder allow,deny
BrowseAllow @LOCAL
BrowseAddress @LOCAL

# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Restrict access to the server...
<Location />
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
#Modify 192.168.0.* to match your configuration.
Allow From 192.168.*.*
</Location>

<Location /printers>
 AuthType None
 Order Deny,Allow
 Deny From None
 Allow From All
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Order allow,deny
  Allow localhost
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
  AuthType Basic
  Require user @SYSTEM
  Order allow,deny
  Allow localhost
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

  <Limit All>
    Order deny,allow
  </Limit>
</Policy>

#
#
```

And the cupsd.conf on the remote computer:
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
Listen *:631
Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
Browsing On
BrowseOrder allow,deny
BrowseAllow @LOCAL
BrowseAddress @LOCAL

# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Restrict access to the server...
<Location />
  Order allow,deny
  Allow localhost
  Allow @LOCAL
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Order allow,deny
  Allow localhost
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
  AuthType Basic
  Require user @SYSTEM
  Order allow,deny
  Allow localhost
</Location>

# Set the default printer/job policies...
<Policy default>
  # Job-related operations must be done by the owner or an adminstrator...
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

   #All administration operations require an adminstrator to authenticate...
  <Limit Pause-Printer Resume-Printer Set-Printer-Attributes Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Add-Printer CUPS-Delete-Printer CUPS-Add-Class CUPS-Delete-Class CUPS-Accept-Jobs CUPS-Reject-Jobs CUPS-Set-Default>
    AuthType Basic
    Require user @SYSTEM
  Order deny,allow
</Limit>

  # Only the owner or an administrator can cancel or authenticate a job...

 <Limit All>
   Order deny,allow
  </Limit>
</Policy>

#
#

#
# Printcap: the name of the printcap file.  Default is /etc/printcap.
# Leave blank to disable printcap file generation.
#

Printcap /var/run/cups/printcap

#
# PrintcapFormat: the format of the printcap file, currently either
# BSD or Solaris.  The default is "BSD".
#

#PrintcapFormat BSD
#PrintcapFormat Solaris

#
# PrintcapGUI: the name of the GUI options panel program to associate
# with print queues under IRIX.  The default is "/usr/bin/glpoptions"
# from ESP Print Pro.
#
# This option is only used under IRIX; the options panel program
# must accept the "-d printer" and "-o options" options and write
# the selected printer options back to stdout on completion.
#

#PrintcapGUI /usr/bin/glpoptions
```

Any help would be greatly appreciated!

---

### Post by Anessen on 2007-04-23
Ok, I manager to get the remote computer to see the printer on the host computer by following this tutorial:
[http://occy.net/printing](http://occy.net/printing)

However, although it's listed, I can't print through it. If I try to print a test page or something through Firefox, it seems to send OK, but nothing actually happens. The job is listed on the queue on the remote machine, but not on the printers host. Nothing gets printed, no error messages.

Printer hosts cupsd.conf looks like this now:
```
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
Allow From 192.168.0.*
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
</Location> 
```
...and the remote computers cups was totally reinstalled to defaults, searching for LAN printers.

This is giving me a headache :(

---

### Post by Dusibello on 2007-04-29
> **Anessen said:**
> .... However, although it's listed, I can't print through it. If I try to print a test page or something through Firefox, it seems to send OK, but nothing actually happens. The job is listed on the queue on the remote machine, but not on the printers host. ...

This is giving me a headache :(
i feel your pain... am working the same issue as i write...

mine is a longer story but will keep you posted if i have a breakthrough...

if you computers are connecting through a router you may need to open port 631? that might explain why everything seems to work but no print job gets to the printer?

---

### Post by Andra on 2007-07-06
While searching for solution to my problem, I came to this thread, and now I can share an idea:
what is written in smb.conf for "printcap name"?
Is it
    printcap name = /var/run/cups/printcap
?

---

