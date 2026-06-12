---
title: "Having trouble connecting to Ubuntu printer from Windows XP via CUPS"
date: 2007-04-12
forum: Networking &amp; Wireless
---

### Post by gongzero on 2007-04-12
Hi all,

I'm a bit of a n00b to *nix but I'm trying to slowly move to Ubuntu here.  I've got my desktop working nicely but I need a little help sharing my printer with my Windows network.

The salient parts of my home network are as follows:

- Ubuntu Edgy on desktop (@192.168.1.106) with printer connected
- Router as DHCP server
- Two other WinXP computers trying to connect to the Ubuntu printer

This is a fresh install with only my default user on the system.

The printer is installed and working in Ubuntu:

[img]http://gongzero.com/assets/images/printer_ready.png[/img]

It's been set as the default printer for the Desktop, and I've got **System > Administration > Printing > Global Settings > Share Printers** checked.

I tried editing [FONT="Courier New"]/etc/cups/cupsd.conf[/FONT] to allow connections to the printer but I think I've probably messed that up:

> [FONT="Courier New"]#
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
**Listen localhost:631**
Listen /var/run/cups/cups.sock
**Listen 192.168.1.103:631**

# Show shared printers on the local network.
Browsing Off
BrowseOrder allow,deny
BrowseAllow @LOCAL
BrowseAddress @LOCAL

# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Restrict access to the server...
<Location />
  Order allow,deny
[B]  Deny From All
  Allow 127.0.0.1
  Allow localhost[/B]
  Allow @LOCAL
**  Allow 192.168.1.***
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
#[/FONT]

I've bolded the parts that I made changes to per various guides I've seen around ubuntuforums.org and the Ubuntu wiki.

I then restarted the service with [FONT="Courier New"]sudo /etc/init.d/cupsys restart[/FONT] and it returns an OK.

The complete output for [font="Courier New"]netstat -ln -A inet[/font]:

> [font="Courier New"]Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 127.0.0.1:2208          0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:49810         0.0.0.0:*               LISTEN     
[B]tcp        0      0 192.168.1.103:631       0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN  [/B]   
udp        0      0 0.0.0.0:68              0.0.0.0:*                 [/font]

The complete output for [font="Courier New"]sudo iptables -L[/font]:

> [font="Courier New"]Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination     [/font]

-------------------------------------------------------------------------------------------------------------------

**So, onto the WinXP client machine:**

- I go to **Start > Printers and Faxes** and select **Add a printer**.

- I choose to add **a network printer, or a printer attached to another computer**.

- I choose to [B]connect to a printer on the Internet or on a home or office network:

[INDENT]URL:[/B] [font="Courier New"] [http://192.168.1.103:631/printers/OfficeJet-Pro-K550](http://192.168.1.103:631/printers/OfficeJet-Pro-K550)[/font][/INDENT]

- In the **Configure Internet Port**, I choose **Use the specified user account** and enter my Ubuntu default username and password.

-------------------------------------------------------------------------------------------------------------------

[COLOR="Red"]So, here's the problem:[/COLOR] **Configuration Error: You do not have access to the printer, please try a different username or password.**

Trying to **use anonymous account** gives me the same error.

Trying to browse to [font="Courier New"]http://192.168.1.103:631/printers/OfficeJet-Pro-K550[/font] gives me a **403 Forbidden** error.

-------------------------------------------------------------------------------------------------------------------

I'm sure I've made some egregious error but I'm too new to CUPS to figure it out.  Any ideas?  Do I need to have Samba installed and configured and running for this (I haven't set it up yet)?

Thanks in advance!


-A

---

### Post by dmizer on 2007-04-12
try this:
```
sudo adduser cupsys shadow
sudo adduser <yourusername> lpadmin
sudo sudo /etc/init.d/cupsys restart
```
of course ... replacing <yourusername> with your ubuntu user name.  then see if you can print.

---

### Post by gongzero on 2007-04-13
Thanks dmizer, I'll give that a shot.


-A

---

### Post by meadmarc on 2007-04-16
> **dmizer said:**
> try this:
```
sudo adduser cupsys shadow
sudo adduser <yourusername> lpadmin
sudo sudo /etc/init.d/cupsys restart
```
of course ... replacing <yourusername> with your ubuntu user name.  then see if you can print.

Dmizer,

You are my hero.  This immediately fixed my printing problem.  Could you possible elaborate a little about what this command did?  It appears to add my username to, what, a config file?

Just curious...  new user learning as fast as I can.

Thanks, 

Marcus

---

### Post by dmizer on 2007-04-17
it just added your ubuntu user to the print administration group (lpadmin), to allow your machine to be a print server.  this is turned off by default because an open, non-configured print server is a huge security risk.  many server functions will require this step in order for the server operation to work properly ... for example, samba.

---

