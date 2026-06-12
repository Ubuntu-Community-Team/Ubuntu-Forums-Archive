---
title: "Difficulty sharing Feisty printer to XP"
date: 2008-01-04
forum: Networking &amp; Wireless
---

### Post by dryder on 2008-01-04
Hi,
I have followed [[COLOR="Blue"]_these_[/COLOR]]("https://help.ubuntu.com/community/NetworkPrintingFromWinXP") instructions  yet still can not share my cups Canon LBP3000 on Feisty to XP machines on my network.
The printer was installed successfully using the instructions [[COLOR="Blue"]_here._[/COLOR]]("https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900") which also works for the LBP3000.

This is my /etc/cups/cupsd.conf file:> LogLevel warning
SystemGroup lpadmin
# Allow remote access
Port 631
Listen /var/run/cups/cups.sock
# Share local printers on the local network.
Browsing On
BrowseOrder allow,deny
BrowseAddress @LOCAL
DefaultAuthType Basic
<Location />
  # Allow shared printing...
  Order allow,deny
  Allow localhost
  Allow @LOCAL
</Location>
<Location /admin>
  Order allow,deny
  Allow localhost
</Location>
<Location /admin/conf>
  AuthType Basic
  Require user @SYSTEM
  Order allow,deny
  Allow localhost
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
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit All>
    Order deny,allow
  </Limit>
</Policy>
Printcap /var/run/cups/printcap

When I Add Printer on the XP boxes I use the network address [http://192.168.0.*:631/printers/LBP3000](http://192.168.0.*:631/printers/LBP3000)
(The '*' is the fixed number of my Ubuntu machine).

I then Add my Windows driver for the printer (it does not recognize the Ubuntu driver obviously) but when I try to print it tells me the port number is wrong.

Any help greatly appreciated.

any thanks,
David

---

### Post by dryder on 2008-01-04
Umm ... re my post:
I have just discovered that the XP machines DO print on the Ubuntu printer BUT the XP machines tell me it failed: "The Print Server is Down. Check the server".

Any clues please?

Many thanks,
David

---

