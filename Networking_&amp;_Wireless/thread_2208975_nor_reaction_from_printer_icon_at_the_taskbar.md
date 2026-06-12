---
title: "nor reaction from printer icon at the taskbar"
date: 2014-03-03
forum: Networking &amp; Wireless
---

### Post by asgard2 on 2014-03-03
Hi,

if I print something via router over the network, the icon at the taskbar is not disappearing and there is no reaction anymore with left or right click on it. The icon is still there until I restart/logout this session.

If I move to the printer settings, there is idle - "Waiting for printer to finish.", but the page is already printed.

Xubuntu 13.10 64Bit

```
ii  bluez-cups                                                  4.101-0ubuntu8b1                              amd64        Bluetooth printer driver for CUPS
ii  cups                                                        1.7.0~rc1-0ubuntu5.2                          amd64        Common UNIX Printing System(tm) - server
ii  cups-browsed                                                1.0.40-0ubuntu1                               amd64        OpenPrinting CUPS Filters - cups-browsed
ii  cups-bsd                                                    1.7.0~rc1-0ubuntu5.2                          amd64        Common UNIX Printing System(tm) - BSD commands
ii  cups-client                                                 1.7.0~rc1-0ubuntu5.2                          amd64        Common UNIX Printing System(tm) - client programs (SysV)
ii  cups-common                                                 1.7.0~rc1-0ubuntu5.2                          all          Common UNIX Printing System(tm) - common files
ii  cups-daemon                                                 1.7.0~rc1-0ubuntu5.2                          amd64        Common UNIX Printing System(tm) - daemon
ii  cups-filters                                                1.0.40-0ubuntu1                               amd64        OpenPrinting CUPS Filters
ii  cups-pk-helper                                              0.2.5-0ubuntu1                                amd64        PolicyKit helper to configure cups with fine-grained privileges
ii  cups-ppdc                                                   1.7.0~rc1-0ubuntu5.2                          amd64        Common UNIX Printing System(tm) - PPD manipulation utilities
ii  cups-server-common                                          1.7.0~rc1-0ubuntu5.2                          all          Common UNIX Printing System(tm) - server common files
ii  libcups2:amd64                                              1.7.0~rc1-0ubuntu5.2                          amd64        Common UNIX Printing System(tm) - Core library
ii  libcups2:i386                                               1.7.0~rc1-0ubuntu5.2                          i386         Common UNIX Printing System(tm) - Core library
ii  libcupscgi1:amd64                                           1.7.0~rc1-0ubuntu5.2                          amd64        Common UNIX Printing System(tm) - CGI library
ii  libcupsfilters1:amd64                                       1.0.40-0ubuntu1                               amd64        OpenPrinting CUPS Filters - Shared library
rc  libcupsfilters1:i386                                        1.0.40-0ubuntu1                               i386         OpenPrinting CUPS Filters - Shared library
ii  libcupsimage2:amd64                                         1.7.0~rc1-0ubuntu5.2                          amd64        Common UNIX Printing System(tm) - Raster image library
rc  libcupsimage2:i386                                          1.7.0~rc1-0ubuntu5                            i386         Common UNIX Printing System(tm) - Raster image library
ii  libcupsmime1:amd64                                          1.7.0~rc1-0ubuntu5.2                          amd64        Common UNIX Printing System(tm) - MIME library
ii  libcupsppdc1:amd64                                          1.7.0~rc1-0ubuntu5.2                          amd64        Common UNIX Printing System(tm) - PPD manipulation library
ii  libfontembed1:amd64                                         1.0.40-0ubuntu1                               amd64        OpenPrinting CUPS Filters - Font Embed Shared library
ii  printer-driver-gutenprint                                   5.2.9-1ubuntu2                                amd64        printer drivers for CUPS
ii  printer-driver-hpcups                                       3.13.9-1ubuntu0.1                             amd64        HP Linux Printing and Imaging - CUPS Raster driver (hpcups)
ii  python-cups                                                 1.9.63-0ubuntu1                               amd64        Python bindings for CUPS
ii  python-cupshelpers                                          1.4.2+20130920-0ubuntu1.2                     all          Python modules for printer configuration with CUPS
```

Reconfigurating the printer or changing the driver to the second one with gutenprint, changed nothing.

This problem is only by printing over the network, USB is working fine.

Any help please, thanks.

---

### Post by phidia on 2014-03-03
Sometimes-if you've checked at the Ubuntu forums for your printer and didn't find any help [the open printing site]("http://www.linuxfoundation.org/collaborate/workgroups/openprinting") may help.

---

### Post by asgard2 on 2014-03-07
I tested another xubuntu and the printer notification is not even showing the printer at taskbar, during printing, where is this option ?

---

### Post by asgard2 on 2014-03-07
I could add some cups error logs:
```
W [07/Mar/2014:10:29:46 +0100] Duplicate listen address "/var/run/cups/cups.sock" ignored.
E [07/Mar/2014:10:29:46 +0100] Unknown directive JobPrivateAccess on line 83 of /etc/cups/cupsd.conf.
E [07/Mar/2014:10:29:46 +0100] Unknown directive JobPrivateValues on line 84 of /etc/cups/cupsd.conf.
E [07/Mar/2014:10:29:46 +0100] Unknown directive SubscriptionPrivateAccess on line 85 of /etc/cups/cupsd.conf.
E [07/Mar/2014:10:29:46 +0100] Unknown directive SubscriptionPrivateValues on line 86 of /etc/cups/cupsd.conf.
W [07/Mar/2014:11:08:47 +0100] Duplicate listen address "/var/run/cups/cups.sock" ignored.
E [07/Mar/2014:11:08:47 +0100] Unknown directive JobPrivateAccess on line 83 of /etc/cups/cupsd.conf.
E [07/Mar/2014:11:08:47 +0100] Unknown directive JobPrivateValues on line 84 of /etc/cups/cupsd.conf.
E [07/Mar/2014:11:08:47 +0100] Unknown directive SubscriptionPrivateAccess on line 85 of /etc/cups/cupsd.conf.
E [07/Mar/2014:11:08:47 +0100] Unknown directive SubscriptionPrivateValues on line 86 of /etc/cups/cupsd.conf.
W [07/Mar/2014:14:03:58 +0100] Duplicate listen address "/var/run/cups/cups.sock" ignored.
E [07/Mar/2014:14:03:58 +0100] Unknown directive JobPrivateAccess on line 83 of /etc/cups/cupsd.conf.
E [07/Mar/2014:14:03:58 +0100] Unknown directive JobPrivateValues on line 84 of /etc/cups/cupsd.conf.
E [07/Mar/2014:14:03:58 +0100] Unknown directive SubscriptionPrivateAccess on line 85 of /etc/cups/cupsd.conf.
E [07/Mar/2014:14:03:58 +0100] Unknown directive SubscriptionPrivateValues on line 86 of /etc/cups/cupsd.conf.
```

/etc/cups/cupsd.conf
```
LogLevel warn
MaxLogSize 0
Listen /var/run/cups/cups.sock
Listen /var/run/cups/cups.sock
Browsing Off
BrowseLocalProtocols dnssd
DefaultAuthType Basic
WebInterface Yes
<Location />
  Order allow,deny
</Location>
<Location /admin>
  Order allow,deny
</Location>
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  Order allow,deny
</Location>
<Policy default>
  JobPrivateAccess default
  JobPrivateValues default
  SubscriptionPrivateAccess default
  SubscriptionPrivateValues default
  <Limit Create-Job Print-Job Print-URI Validate-Job>
    Order deny,allow
  </Limit>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job Cancel-My-Jobs Close-Job CUPS-Move-Job CUPS-Get-Document>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default CUPS-Get-Devices>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After Cancel-Jobs CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
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
<Policy authenticated>
  JobPrivateAccess default
  JobPrivateValues default
  SubscriptionPrivateAccess default
  SubscriptionPrivateValues default
  <Limit Create-Job Print-Job Print-URI Validate-Job>
    AuthType Default
    Order deny,allow
  </Limit>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job Cancel-My-Jobs Close-Job CUPS-Move-Job CUPS-Get-Document>
    AuthType Default
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After Cancel-Jobs CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Cancel-Job CUPS-Authenticate-Job>
    AuthType Default
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit All>
    Order deny,allow
  </Limit>
</Policy>
JobPrivateAccess default
JobPrivateValues default
SubscriptionPrivateAccess default
SubscriptionPrivateValues default
```

I replaced the file with one from my virtual box xubuntu and restarted cups
```
#
#
# Sample configuration file for the CUPS scheduler.  See "man cupsd.conf" for a
# complete description of this file.
#

# Log general information in error_log - change "warn" to "debug"
# for troubleshooting...
LogLevel warn

# Deactivate CUPS' internal logrotating, as we provide a better one, especially
# LogLevel debug2 gets usable now
MaxLogSize 0

# Only listen for connections from the local machine.
Listen localhost:631
Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
Browsing Off
BrowseLocalProtocols dnssd

# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Web interface setting...
WebInterface Yes

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
  # Job/subscription privacy...
  JobPrivateAccess default
  JobPrivateValues default
  SubscriptionPrivateAccess default
  SubscriptionPrivateValues default

  # Job-related operations must be done by the owner or an administrator...
  <Limit Create-Job Print-Job Print-URI Validate-Job>
    Order deny,allow
  </Limit>

  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job Cancel-My-Jobs Close-Job CUPS-Move-Job CUPS-Get-Document>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  # All administration operations require an administrator to authenticate...
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default CUPS-Get-Devices>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # All printer operations require a printer operator to authenticate...
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After Cancel-Jobs CUPS-Accept-Jobs CUPS-Reject-Jobs>
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

# Set the authenticated printer/job policies...
<Policy authenticated>
  # Job/subscription privacy...
  JobPrivateAccess default
  JobPrivateValues default
  SubscriptionPrivateAccess default
  SubscriptionPrivateValues default

  # Job-related operations must be done by the owner or an administrator...
  <Limit Create-Job Print-Job Print-URI Validate-Job>
    AuthType Default
    Order deny,allow
  </Limit>

  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job Cancel-My-Jobs Close-Job CUPS-Move-Job CUPS-Get-Document>
    AuthType Default
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
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After Cancel-Jobs CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # Only the owner or an administrator can cancel or authenticate a job...
  <Limit Cancel-Job CUPS-Authenticate-Job>
    AuthType Default
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

After one printing job, I can see these errors, but the "Unknown directive" are gone.
```
W [07/Mar/2014:17:18:26 +0100] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'deskjet_5550_USB-Gray..' already exists
W [07/Mar/2014:17:18:26 +0100] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'deskjet_5550_USB-RGB..' already exists
W [07/Mar/2014:17:18:26 +0100] CreateDevice failed: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-deskjet_5550_USB' already exists
W [07/Mar/2014:17:18:26 +0100] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'Epson-Stylus-DX3800-Gray..' already exists
W [07/Mar/2014:17:18:26 +0100] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'Epson-Stylus-DX3800-RGB..' already exists
W [07/Mar/2014:17:18:26 +0100] CreateDevice failed: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Epson-Stylus-DX3800' already exists
W [07/Mar/2014:17:18:26 +0100] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'HP-Deskjet-5550-Gray..' already exists
W [07/Mar/2014:17:18:26 +0100] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'HP-Deskjet-5550-RGB..' already exists
W [07/Mar/2014:17:18:26 +0100] CreateDevice failed: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-HP-Deskjet-5550' already exists
E [07/Mar/2014:17:18:26 +0100] Unable to bind socket for address [v1.::1]:631 - Address already in use.
E [07/Mar/2014:17:18:26 +0100] Unable to bind socket for address 127.0.0.1:631 - Address already in use.

```
But the printer icon is still freezing.

---

### Post by Fernandobot on 2014-04-16
I have also had this exact same bug.  I am new to linux, having only run it on my old PS3 back in the day.  One of my office laptops was running Windows XP so I decided to make the swtich and so far I'm loving it.  I've just installed xubuntu 13.10 32 bit on an old celeron M Toshiba laptop.  After sending a print over the network a printer icon appears on Panel 0 next to the icons for the task manager and battery etc.  This seems to correspond to service Scp-dbus-service.py.  Checking the printer status in the printer settings reveals the message "idle - waiting for printer to finish" but the printer (Ricoh Afficio 2075) has already completed the print job in reality.

I was able to make the printer icon go away by stopping and then killing the service Scp-dbus-service.py.  But as a linux noob I have no idea why that service decided to keep running after a print has completed.  Anyways, hopefully this information is helpful in figuring out the cause of this bug.

---

