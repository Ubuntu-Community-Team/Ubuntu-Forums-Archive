---
title: "Help with Networked Printing"
date: 2008-07-21
forum: Networking &amp; Wireless
---

### Post by kavon89 on 2008-07-21
I have installed Hardy Server edition on my server box, and connected my printer to it via USB.

Problem is I can't seem to get CUPS on my server working properly, I followed a guide i found on the forums but I can't seem to make it work out. When i do 192.168.1.50:631 I get a 403 forbidden page. Same goes for connecting to it via the Printer menu. I get "There was an error during the CUPS operation: 'client-error-forbidden'."

Here is my server's cupsd.conf file:

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
Listen 631
Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
Browsing On
BrowseOrder allow,deny
BrowseAllow all
BrowseAddress all

# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Restrict access to the server...
<Location />
  Order allow,deny
</Location>

# Restrict access to the admin pages...
<Location /admin>
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
  # Job-related operations must be done by the owner or an administrator...
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscriptio$
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
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer $
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

#
#

```

---

### Post by dmizer on 2008-07-21
first:

this section:
```
# Restrict access to the admin pages...
<Location /admin>
  Order allow,deny
</Location>
# Restrict access to the admin pages...
<Location /admin>
  Order allow,deny
</Location>
```

should look like this:
```
<Location /admin>
AuthClass System

## Restrict access to local domain
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
Allow from 192.168.1.0/24
</Location>
```

next, add the cupsys user to the shadow group:
```
sudo adduser cupsys shadow
```

add yourself to the lpadmin group:
```
sudo adduser [COLOR="Red"]kavon89[/COLOR] lpadmin
```
(where [COLOR="Red"]kavon89[/COLOR] is your ubuntu server user name)

restart cups:
```
sudo /etc/init.d/cupsys restart
```

edit:
let me know if this works.  i haven't had to do this since dapper ...

---

### Post by Belerophon on 2008-08-09
Hi, I have the same problem.
I installed hardy server, and installed a printer in it, and I also have openssh server running there, and I'm running all the commands through ssh.

So, the idea is to have access to the cups web pages through another computer in the network since, obviously, I don't have "windows" in the server...

here's my cupsd.conf:
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
Listen 631
Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
Browsing Off
BrowseOrder allow,deny
BrowseAllow all
BrowseAddress @LOCAL

# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Restrict access to the server...
<Location />
  Order allow,deny
</Location>

# Restrict access to the admin pages...
<Location /admin>
  AuthClass System
  ## Restrict access to local domain
  Order Deny,Allow
  Deny from All
  Allow from 127.0.0.1
  Allow from @LOCAL
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  Order allow,deny
</Location>

# Set the default printer/job policies...
<Policy default>
  # Job-related operations must be done by the owner or an administrator...
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
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
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
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

#
#
```

I had to change the line you wrote as:
```
Allow from 192.168.1.0/24
```
to:
```
Allow from @LOCAL
```
since the first gave me error when restarting the daemon, and I think the second does the same as the first from what I saw in the [COLOR="Red"]cups website[/COLOR].

After I wrote that in the file and restarted the daemon, I still can't access the cups in firefox. I had the error "[COLOR="Red"]403 Forbidden[/COLOR]".
So I tried to create a proxy with ssh:
```
ssh belerophon@169.254.0.2 -D 1080 -N -f
```
and changing firefox configuration to use that proxy (I'm using it right now).
But when trying to [http://169.254.0.2:631/](http://169.254.0.2:631/), still I had no luck: "[COLOR="Red"]403 Forbidden[/COLOR]".
So at this moment I'm thinking that I can't access cups neither from "inside" or "outside"!

After this, I tried to do the line you wrote:
```
sudo adduser cupsys shadow
```
but I had this:
```
[COLOR="Red"]adduser: The user `cupsys' does not exist[/COLOR].
```

So...what do I do now?

Thanks!

---

### Post by Belerophon on 2008-08-13
*Bump* :(

---

### Post by Belerophon on 2008-09-12
Bump again...:(

---

### Post by QuimNuss on 2008-10-28
I don't know if it's the right answer, but I've solved the same issue on another forum. The user cupsys doesn't exist, so create it:
```
sudo adduser cupsys
```

And then, the previous command would work:

```
sudo adduser cupsys shadow
```

Still, I don't know if thats the right choice ;) somehow, I think it is (newbie)

---

### Post by Belerophon on 2008-10-29
Thanks a lot for the reply! I was giving up on this thread...:P

I currently don't have access to my server, 'cause I'm not at home. But either this weekend or a week after, I'll try again to set up my print server and I'll post my results here.

Thanks.

---

