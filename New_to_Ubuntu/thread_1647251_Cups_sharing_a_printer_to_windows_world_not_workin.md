---
title: "Cups: sharing a printer to windows world not working;)"
date: 2010-12-17
forum: New to Ubuntu
---

### Post by honeybear on 2010-12-17
Using the cups it is not working, printer is on linux machine, but windows xp can mount it to printers but not capable to print.

 /etc/cups/cupsd.conf


```


LogLevel warn
MaxLogSize 0
SystemGroup lpadmin
# Allow remote access
Port 631
Listen /var/run/cups/cups.sock
# Enable printer sharing and shared printers.
Browsing On
BrowseOrder allow,deny
BrowseAllow all
BrowseRemoteProtocols CUPS
BrowseAddress @LOCAL
BrowseLocalProtocols CUPS dnssd
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
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job CUPS-Get-Document>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default CUPS-Get-Devices>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
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
  <Limit Create-Job Print-Job Print-URI>
  AuthType Default
  Order deny,allow
</Limit>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job CUPS-Get-Document>
AuthType Default
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
  <Limit Cancel-Job CUPS-Authenticate-Job>
      AuthType Default
      Require user @OWNER @SYSTEM
      Order deny,allow
        </Limit>
  <Limit All>
        Order deny,allow
          </Limit>
</Policy>


```

---

### Post by Wobblybob on 2010-12-18
on the Linux box with the printer attached, try going into Printing on System menu select [Server], [Settings] tick "Publish shared printers etc" and any other you wish.

check out the name of your printer in cups by opening this address in a browser [http://localhost:631](http://localhost:631)

and selecting the [Printers] tab, this should show your printers queue name in my case Epson-Stylus-Photo-R200 

When adding the printer on Windows the url of the printer will be in my case;

```
http://name_of_linux_hostPC:631/printers/EPSON-Stylus-Photo-R200
```

Good Luck

---

