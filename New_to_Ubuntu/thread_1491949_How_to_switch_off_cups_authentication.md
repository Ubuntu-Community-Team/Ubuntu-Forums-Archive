---
title: "How to switch off cups authentication ?"
date: 2010-05-24
forum: New to Ubuntu
---

### Post by WitchCraft on 2010-05-24
Can anybody tell me why cups insists I have to enter a username and a password ?

I tried to switch that annoyance off permanently, so I did change the config file (/etc/cupsd.conf) to the below and did /etc/init.d/cups restart

but cups insists I enter username + pw.


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

# Administrator user group...
SystemGroup lpadmin


# Only listen for connections from the local machine.
Listen localhost:631
Listen 192.168.1.4:631

Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
Browsing Off
BrowseOrder allow,deny
BrowseAllow all
BrowseLocalProtocols CUPS dnssd
BrowseAddress @LOCAL

# Default authentication type, when authentication is required...
#DefaultAuthType Basic
DefaultAuthType None
# Restrict access to the server...
<Location />
  Order allow,deny
Allow From 127.0.0.1
Allow From 192.168.1.*
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Order allow,deny
Allow From 127.0.0.1
Allow From 192.168.1.*
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
  #AuthType Default
  AuthType none
  Require user @SYSTEM
  Order allow,deny
  Allow 192.168.1.*
</Location>

# Set the default printer/job policies...
<Policy default>
  # Job-related operations must be done by the owner or an administrator...
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job CUPS-Get-Document>
    Require user @OWNER @SYSTEM
    Order deny,allow
    Allow 192.168.1.*
  </Limit>

  # All administration operations require an administrator to authenticate...
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default CUPS-Get-Devices>
    #AuthType Default
    AuthType none
    Require user @SYSTEM
    Order deny,allow
    Allow 192.168.1.*
  </Limit>

  # All printer operations require a printer operator to authenticate...
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    #AuthType Default
    AuthType none
    Require user @SYSTEM
    Order deny,allow
    Allow 192.168.1.*
  </Limit>

  # Only the owner or an administrator can cancel or authenticate a job...
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
    Allow 192.168.1.*
  </Limit>

  <Limit All>
    Order deny,allow
    Allow 192.168.1.*
  </Limit>
</Policy>

# Set the authenticated printer/job policies...
<Policy authenticated>
  # Job-related operations must be done by the owner or an administrator...
  <Limit Create-Job Print-Job Print-URI>
    #AuthType Default
    AuthType none
    Order deny,allow
    Allow 192.168.1.*
  </Limit>

  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job CUPS-Get-Document>
    #AuthType Default
    AuthType none
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  # All administration operations require an administrator to authenticate...
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    #AuthType Default
    AuthType none
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # All printer operations require a printer operator to authenticate...
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    #AuthType Default
    AuthType none
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # Only the owner or an administrator can cancel or authenticate a job...
  <Limit Cancel-Job CUPS-Authenticate-Job>
    #AuthType Default
    AuthType none
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  <Limit All>
    Order deny,allow
    Allow 192.168.1.*
  </Limit>
</Policy>

#
#

```


> 

eth1      Link encap:Ethernet  HWaddr 00:16:6f:ad:53:48  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:6fff:fead:5348/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21856 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18198 errors:0 dropped:5 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11846874 (11.8 MB)  TX bytes:2858376 (2.8 MB)
          Interrupt:17 Memory:dfbfd000-dfbfdfff 



---

### Post by wojox on 2010-05-24
Were you running it as root?

---

### Post by WitchCraft on 2010-05-24
> **wojox said:**
> Were you running it as root?

You mean the cups client or the cups server ?


The cups client/OpenOffice -  yes.
Changing the cups config and restart - as root.
Don't know under which user cups runs.

The funny thing is, printing on the cups printer from windows works without password...

---

### Post by fatality_uk on 2010-05-24
I think wojox is right. Only time I have seen a usrnme + pw required is when the user has logged in a root.

Check out this article and try adding your user.

[http://www.cups.org/articles.php?L274](http://www.cups.org/articles.php?L274)

---

### Post by expatCM on 2010-05-24
You have set

DefaultAuthType None

what happens if you set

DefaultAuthType Basic

---

### Post by WitchCraft on 2010-05-24
> **expatCM said:**
> You have set

DefaultAuthType None

what happens if you set

DefaultAuthType Basic

AuthType was Basic, I've changed it to none, because a howto said comment it out (that didn't work), and another said change it to none.

---

### Post by expatCM on 2010-05-24
The reason I asked is that I have not seen None used in this context.

In my case I use DefaultAuthType Basic

But all the options are set out in the cups documentation.  Take a look at [this]("http://www.cups.org/documentation.php/ref-cupsd-conf.html") link, scroll down a bit and you will see what I mean.

---

### Post by jalexstark on 2010-07-16
There is a persistent and definitive bug with cups (perhaps specific to Ubuntu).

I cannot get it to remember the authentication details, even going through the printer setup.  We have a number of smb printers, and one seems to have to resort to deleting the printer and reinstalling.

The problem appears to start when a printer becomes unavailable and you try to print to it.  When it becomes available, the authentication has to be typed every time then on, perhaps until reinstallation.

Network printing is in the category "we can put a man on the moon but can't...".  It has improved slightly in 20 years, but not more.

---

### Post by dqvn on 2013-02-25
Tested with this modify

# All administration operations require an administrator to authenticate...   <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default CUPS-Get-Devices>     #AuthType Default     #Require user @SYSTEM     Order allow,deny   </Limit>

---

### Post by overdrank on 2013-02-25
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

