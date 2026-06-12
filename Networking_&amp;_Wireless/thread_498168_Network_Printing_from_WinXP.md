---
title: "Network Printing from WinXP"
date: 2007-07-11
forum: Networking &amp; Wireless
---

### Post by john8791 on 2007-07-11
Hello,
  I have followed advice from the following sources to use my computer (running Feisty) as a print server for a Windows XP client:

[https://help.ubuntu.com/community/NetworkPrintingFromWinXP](https://help.ubuntu.com/community/NetworkPrintingFromWinXP)
[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu#head-cb00b99d5ce2a0365de68dee4be273405c97b865](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu#head-cb00b99d5ce2a0365de68dee4be273405c97b865)

The instructions work great.  The problem is that the Win machine asks for a username and password.  I have tried all the following and none work:
1.) My username & password on the Ubuntu machine
2.) The username and password for the Win machine.
3.) username "root"
4.) I used the web interface [http://localhost:631](http://localhost:631) to add me as an allowed user
5.) I verified that "cupsys" is in the /etc/shadow file

Here is my /etc/cups/cupsd.conf file:
# Log general information in error_log - change "info" to "debug" for
# troubleshooting...
LogLevel warning

# Administrator user group...
SystemGroup lpadmin

# Only listen for connections from the local machine.
Port 631
#Listen 631
Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
Browsing On
BrowseOrder allow,deny
BrowseAllow @LOCAL
BrowseAddress @LOCAL

# Default authentication type, when authentication is required...
#DefaultAuthType Basic

# Restrict access to the server...
#<Location />
#  Order allow,deny
#  Allow localhost
#  Allow @LOCAL
#</Location>
<Location />
  Order deny,allow
  Deny from All
  Allow From 127.0.0.1
  Allow From 192.168.0.*
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


I would appreciate any help!

---

### Post by pebo on 2007-07-11
You need to set smbpasswd:


```
sudo  smbpasswd -a [your username on the client]
```

Set the password. Then you can log in on the client machine.

---

### Post by john8791 on 2007-07-11
Thanks! Now I can log into the machine set up the printer (by browsing) and it prints.

 But.... I was under the impression that the other method of setting up the printer through the "add printer" dialog as "http://192.168.1.110:631/printers/DeskJest-882C" was independent of Samba.  I do not want to have to log on to use the printer every time the Windows machine restarts.  Any ideas?  You certainly got me off ground zero and I appreciate it.

---

