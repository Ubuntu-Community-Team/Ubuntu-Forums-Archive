---
title: "Cups problems -- disappearing printers"
date: 2007-08-20
forum: Networking &amp; Wireless
---

### Post by stiv2k on 2007-08-20
Ok, this has been a very aggravating problem for me, it has been going on for a while now.  It is not printer specific.  What happens is I'll go and add a printer, and it will be there working perfectly fine for a couple of hours, then I'll go out and do something, and when I come back, the printer is gone.  The CUPS admin page shows No printers.   I have to constantly re-add the printer only for it to disappear again later.

my setup is as follows:
- The printer is connected to my server running Feisty attached via USB cable
- Using SAMBA for the windows clients (should be irrelevant to my issue?)
- Cups 1.2.8
- The only output i seem to find from the Error log is as follows:
```

D [20/Aug/2007:06:30:36 -0400] Discarding unused printer-deleted event...
D [20/Aug/2007:06:30:36 -0400] Remote destination "Lexmark_Printer" has timed out; deleting it...

```

- CUPS configuration:
```


#
#
#   Sample configuration file for the Common UNIX Printing System (CUPS)
#   scheduler.  See "man cupsd.conf" for a complete description of this
#   file.
#

# Log general information in error_log - change "info" to "debug" for
# troubleshooting...
LogLevel debug

# Administrator user group...
SystemGroup lpadmin

# Only listen for connections from the local machine.
Listen 192.168.1.10:631
Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
Browsing On
BrowseOrder allow,deny
BrowseAllow @LOCAL
BrowseAddress 192.168.1.255

# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Restrict access to the server...
<Location />
  Order Deny,Allow
  Deny From All
  Allow From 192.168.1.*
  Allow From 127.0.0.1
</Location>

# Restrict access to the admin pages...
<Location /admin>
  AuthType Basic
  AuthClass System
  Allow From 192.168.1.*
  Allow From 127.0.0.1
  Order Deny,Allow
  Deny From All
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
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current$
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  # All administration operations require an adminstrator to authenticate...
  <Limit Pause-Printer Resume-Printer Set-Printer-Attributes Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-$
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

mime.convs:
application/octet-stream application/vnd.cups-raw 0 -

mime.types:
application/octet-stream



```

PS: This all started when I reformatted the drive on my server.  Before that it was working quite perfectly.  What could be causing this??   I really need to get it working soon as school has started and me and my room mates will be relying on this printer to work.  Thanks in advance

EDIT: Someone told me it may be a dbus issue?? Here's my dbus version:
```
ii  libdbus-1-3                                   1.0.2-1ubuntu4                                simple interprocess messaging system
```

---

### Post by stiv2k on 2007-08-20
bump?

---

### Post by dacap06 on 2007-09-06
I am having a similar problem.

I run Kubuntu Feisty on two computers at home - a workstation, and a laptop.  In mid-August, I upgraded my server from Mandriva to Kubuntu Feisty as well.  My problem started about the same time, but I think that may be coincidence.  

My server hosts printing services and shares an HP Laserjet 4 and an Epson Stylus Color 800 with the other two using CUPS.  I have done this setup for years, and CUPS worked fine doing it.  I do not have a problem using printings on my servers, but I do have a problem with using these server printers from both the workstation and the laptop.

Starting about the 25th of August, strange things began happening.  I suddenly started losing the printers on my server in my laptop and workstation.  I would recreate them, but I could still not print in non-KDE applications such as Firefox and Open Office on both my workstation and laptop.   

Investigation showed that some unusual things.  These are true both on the laptop and the workstation:

1)  Going to K -> System Settings -> Printer icon -> Printer settings window showed no reference to the remote printers on the server.  I checked the CUPS server in the print manager and saw it had reset to localhost on its own.  I changed it back to the server name and the printers reappeared in the printer settings. 

2)  After step 1, I could print from things like Kedit, but neither Firefox nor Openoffice presented the printers as choices.  Logging out and back in didn't help.  Rebooting didn't help. 

3)  I opened an X-term, and did an lpq command only to find it did not know the default printer at the command line, despite the fact it was displayed in the Printer System Setting right next to it.  Very odd.  Looks like KDE is not exporting the default printer to the environment.

4) Further investigation revealed the following:

A)  Trying to store revised printer settings changed via the KDE Printer Configuration dialog didn't change the file content, even in administrator mode.

B)  I had new CUPS configuration files in /etc/cups.  The ones I had set up in May (when I installed Feisty on the laptop and the workstation) and had used ever since had been moved to /etc/cups/cupsd.conf.O and /etc/cups/printers.conf.O.  The content of the new configuration files was obviously wrong, and the files belong to a different user.  I moved them to *.new and copied the *.O files into the configuration files and restarted cupsd.  That got me my printers back in the environment.  Here's the listing now:

-rw------- 1 lp     lpadmin   338 2007-09-03 23:02 printers.conf
-rw-r--r-- 1 root   lpadmin 20127 2007-09-03 23:01 cupsd.conf
-rw-r--r-- 1 cupsys lp      20126 2007-09-02 15:30 cupsd.conf.new
-rw-r--r-- 1 cupsys lp      20127 2007-09-02 15:29 cupsd.conf.O
-rw-r--r-- 1 root   lp        196 2007-09-02 15:28 lpoptions
drwxr-xr-x 2 lp     lpadmin  4096 2007-09-02 15:20 ppd
-rw------- 1 lp     lpadmin    84 2007-09-02 15:20 printers.conf.new
-rw------- 1 cupsys lp        338 2007-09-02 15:19 printers.conf.O
-rw-r--r-- 1 root   root      242 2007-04-17 23:48 raw.convs
-rw-r--r-- 1 root   root      213 2007-04-17 23:48 raw.types
drwx------ 2 lp     lpadmin  4096 2007-04-17 23:48 ssl
drwxr-xr-x 2 root   root     4096 2007-04-04 04:32 interfaces
-rw-r--r-- 1 root   root     4461 2007-04-04 04:32 mime.convs
-rw-r--r-- 1 root   root     6109 2007-04-04 04:32 mime.types

C)  I am seeing errors in syslog every time I restart the CUPS daemon.  They say:

Sep  5 20:24:48 tomws cupsd: Unable to open log file "/var/log/cups/page_log" - Permission denied
Sep  5 20:24:58 tomws cupsd: Unable to open log file "/var/log/cups/page_log" - Permission denied

D)  At least once a day, I lose printer selection in my non-KDE apps.  I have to restart the cups daemon again to get it back.  to do that, as root I enter "/etc/init.d/cupsys restart" at the command line.

OK - I'm terribly confused.  What ID is cupsd supposed to run under?  What ID should own the configuration files?  Did some package update screw this up?  It worked perfectly for me for months after I installed Kubuntu Feisty on my laptop and workstation (interoperating with Mandriva on the server).  Is there something about cupsd in Feisty on the server?  These odd printing issues began about the same time I installed it on the server, but I'll be darned if I can figure out how that would relate to the symptoms on the workstation and laptop.  Help?

---

### Post by dacap06 on 2007-09-10
I figured out the solution to the disappearing printer problem myself.  

1) First, in the print manager dialog, ( System settings -> Printer Icon -> Print Manager -> Configure Manager -> CUPS Server Icon ) make localhost the host printer server, even if the local machine has no printers.  Port 631 is correct.

2) Restart the print manager ( System settings -> Printer Icon -> Print Manager -> Initialize Manager View).

3) Add each printer on the remote cups server individually.  Use (System settings -> Printer Icon -> Print Manager -> Add -> Add Printer/Class) to bring up the Add Printer Wizard.  Make sure you select the Internet Printing Protocol (IPP) by selecting the Remote Cups Server option.  The rest should be obvious.

---

