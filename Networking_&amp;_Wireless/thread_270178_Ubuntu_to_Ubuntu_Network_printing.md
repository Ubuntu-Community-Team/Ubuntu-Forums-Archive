---
title: "Ubuntu to Ubuntu Network printing"
date: 2006-10-02
forum: Networking &amp; Wireless
---

### Post by CameronCalver on 2006-10-02
Hello i have had my ubuntu to be able top print to my ubuntu box for a while now but i did a restart of all my ubuntu boxes and used the same forum to set up my cups conf but now it does not work.
And for some reason there is no option to select lan printers ??.
I attatched both my client and my servers conf files

---

### Post by tagra123 on 2006-10-03
Here's the workaround I came up with:

How To Work Around Broken Cups 1.2 Sharing Problem

[http://ubuntuforums.org/showthread.php?t=245052](http://ubuntuforums.org/showthread.php?t=245052)

---

### Post by CameronCalver on 2006-10-03
nope didnt work i didnt really get the thing where you add a network printer

---

### Post by tagra123 on 2006-10-03
Here's my working cupsd.conf from the server.  I don't think the client side should matter since the cupsd is setting up the server.


```

# Show troubleshooting information in error_log.
LogLevel debug
SystemGroup lpadmin
# Enable printer sharing and shared printers.
Browsing On
BrowseOrder allow,deny
BrowseAllow @LOCAL
BrowseAddress @LOCAL
BrowseAddress 192.168.1.255 # Added 8-26-2006
DefaultAuthType Basic
<Location />
  # Allow shared printing...
  Order allow,deny
  Allow @LOCAL
  Allow 192.168.1.*
</Location>
<Location /admin>
  # Restrict access to the admin pages...
  Order allow,deny
  Allow localhost
</Location>
<Location /admin/conf>
  AuthType Basic
  Require user @SYSTEM
  # Restrict access to the configuration files...
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
Include /etc/cups/cups.d/ports.conf
Include /etc/cups/cups.d/browse.conf
# Allow remote access
Port 631
Listen /var/run/cups/cups.sock
```

Now this cupd.conf works when using the workaround in my earlier post.

---

### Post by CameronCalver on 2006-10-04
will that work with my ip of 192.168.1.101

---

### Post by CameronCalver on 2006-10-04
ok nearly done but now i can add a printer on the server and i can see it on the client and if i print from the server on the client it says busy - printing but if i print it just says 
```
Ready: Network host '192.168.1.101' is busy; will retry in 30 seconds...
```

---

### Post by king20878 on 2006-12-17
Just what I was looking for.  Thanks!

---

### Post by angliski on 2007-09-18
I have an ubuntu server connected my by wireless to an ubuntu client. I am having problems with getting my client to connect to my host. What I think I need to know is the ip address of my server printer and then it will work.
I have tried all the other fixes but to no avail.
Can someone please tell me how I use terminal to give me the address of my servers ip address?

Cheers
Steve

---

### Post by Porpoise on 2007-09-18
> **CameronCalver said:**
> ok nearly done but now i can add a printer on the server and i can see it on the client and if i print from the server on the client it says busy - printing but if i print it just says 
```
Ready: Network host '192.168.1.101' is busy; will retry in 30 seconds...
```

It may not be the same issue, but I just had a similar experience (same error message) trying to set up my HP BusinessJet 2230 connected to a Netgear PS101 Print Server. After going round & round in circles for several days (checking and double-checking IPs and everything), it turned out I was using the wrong printer driver.

I made my original selections from here:
[IMG]http://srenterprises.co.uk/Screenshot-Change%20Driver.png[/IMG]

but I should have selected this one:
[IMG]http://srenterprises.co.uk/Screenshot-Change%20Driver-1.png[/IMG]

Now everything is working fine.

---

