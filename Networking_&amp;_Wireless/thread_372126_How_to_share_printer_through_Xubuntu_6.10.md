---
title: "How to share printer through Xubuntu 6.10"
date: 2007-02-27
forum: Networking &amp; Wireless
---

### Post by majkball on 2007-02-27
I am trying to share my HP Laserjet 5P printer connected to my Xubuntu machine through the network, so that I can print from my Windows XP laptop. 

Just before I installed Xubuntu 6.10 I had Ubuntu 6.10 installed and actually managed to get the printer sharing to work, but I needed to change to Xubuntu because my machine was too slow, and now I can't get it to work anymore. :(

My laptop has ip (192.168.0.10) and at the "add printer wizard" I specified the url for the printer to ([http://192.168.0.20:631/printers/HP-Laserjet-5P](http://192.168.0.20:631/printers/HP-Laserjet-5P)) were 192.168.0.20 is the ip to my Xubuntu machine. When I specify this url I just get a fault message telling me that windows cannot connect to the printer, operation could not be completed. And yes I have tried to ping my machines and it seems to work that way... so probably there is some setting needed to be made.

My Xubuntu 6.10 is a fresh install and I have updated to the latest through the update-manager. I haven't installed samba or anything like that.

Here is a copy and paste from my "cupsd.conf":

```
# Show general information in error_log.
LogLevel info
SystemGroup lpadmin
# Allow remote access
Listen 192.168.0.*:631
Listen /var/run/cups/cups.sock
# Enable printer sharing and shared printers.
Browsing On
BrowseOrder allow,deny
BrowseAllow @LOCAL
BrowseAddress @LOCAL
DefaultAuthType Basic
<Location />
  # Allow shared printing and remote administration...
  Order allow,deny
  Allow From 192.168.0.10
  Allow @LOCAL
</Location>
<Location /admin>
  # Allow remote administration...
  Order allow,deny
  Allow @LOCAL
</Location>
<Location /admin/conf>
  AuthType Basic
  Require user @SYSTEM
  # Allow remote access to the configuration files...
  Order allow,deny
  Allow @LOCAL
</Location>
<Policy default>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Pause-Printer Resume-Printer Set-Printer-Attributes Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Add-Printer CUPS-Delete-Printer CUPS-Add-Class CUPS-Delete-Class CUPS-Accept-Jobs CUPS-Reject-Jobs CUPS-Set-Default>
    AuthType Basic
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  # Only the owner or an administrator can cancel a job...
  <Limit Cancel-Job>
    Order deny,allow
    Require user @OWNER @SYSTEM
  </Limit>
  <Limit All>
    Order deny,allow
  </Limit>
</Policy>

```

---

### Post by tgalati4 on 2007-02-27
Make sure your /etc/hosts have all of your important local IP's specified.  Otherwise CUPs will get confused.

Don't forget these essential lines:

127.0.0.1 localhost
127.0.1.1 yourhostname

---

### Post by majkball on 2007-02-28
Checked the /etc/hosts

It got the two lines you mentioned, and then some Ipv6 lines...

No one got a clue? Should I use Samba or something like that?

---

### Post by tgalati4 on 2007-03-01
Does your /etc/hosts contain all of your local network IPs with domain names?

---

