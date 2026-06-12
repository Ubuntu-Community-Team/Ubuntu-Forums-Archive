---
title: "CUPS - Print jobs shows completed, but page doesn't print"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by akelsall on 2008-12-06
I thought I had everything finally configured, but when I try to print a test page, it shows it as completed, but the page never prints. I'm using a Canon MP600 and using the canonmp600en.ppd file to configure it. Here's the output of my conf file. Any ideas what's going on?

```
# Show troubleshooting information in error_log.
LogLevel debug
SystemGroup lpadmin sys root
# Allow remote access
Port 631
Listen /var/run/cups/cups.sock
# Enable printer sharing and shared printers.
Browsing On
BrowseOrder allow,deny
BrowseAllow all
BrowseAddress @LOCAL
DefaultAuthType Basic
<Location />
  # Allow shared printing...
  Order allow,deny
  Allow @LOCAL
</Location>
<Location /admin>
  # Restrict access to the admin pages...
  Order allow,deny
</Location>
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  # Restrict access to the configuration files...
  Order allow,deny
</Location>
<Policy default>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit All>
    Order deny,allow
  </Limit>
</Policy>

```

---

### Post by akelsall on 2008-12-08
bump. Anybody? Anybody?........ Buehler?

---

### Post by tjandracom on 2008-12-09
i don't know with Canon MP600, but i used to have the same problem with Canon IP1880 and Canon IP1980. after i installed the driver, i try to print a test page. it shows it as completed, but the page is not printed. then I tried in Ubuntu 8.04 Hardy machine, and it works using the above driver (previously, my distro is Ubuntu 6.06 Dapper). i have tested it in several Dapper machine and it never work, and i tested it in several Hardy machine, and it always work. i don't know what's wrong, but maybe you have try different driver or try to test it in newer distro.

---

### Post by saturnine fei on 2008-12-28
My MP-600 was working fine under Hardy and has the same problem under Intrepid.  Between this and the bluetooth pairing bug I think I may have to downgrade to Hardy...  I resist this because it looks like that would require a complete reinstall, which is the sort of thing I left windoze over.

I'm too much of a novice to have done much.  I did try running it as an MP610.  It printed the test page but the colors were all misaligned.  I don't know if there are other drivers that might work for this machine.  Has anyone tried the 400 series drivers on the 600?

I have not been able to scan from it since the upgrade either... it's just a very big low capacity paper storage unit now... sigh...  Back to the LaserJet 4P for now... double sigh.

---

