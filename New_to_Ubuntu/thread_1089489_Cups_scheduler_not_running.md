---
title: "Cups scheduler not running ?"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by ex-wirecutter on 2009-03-07
Have just had to reinstall Ubuntu 8.10 and my printer no longer works . When I try to nominate the printer I get cups scheduler not running , how do I start it ? My printer still shows up in the etc/cups folder. Have tried to run cupsd config but this cannot be found . Numerous restarts with and without the printer switched on have no effect and have double checked the printer cable .

---

### Post by ex-wirecutter on 2009-03-07
Further to the above have also reinstalled cupsys from package manager.

---

### Post by iamkrazee on 2009-03-07
Try this:```
sudo service cups start
```

---

### Post by ex-wirecutter on 2009-03-07
Tried the above as suggested and got " child exited status 1  [ fail } whatever that means .

---

### Post by rhcm123 on 2009-03-07
> **ex-wirecutter said:**
> Tried the above as suggested and got " child exited status 1  [ fail } whatever that means .

You have a problem with your config file.

Post /etc/cups/cupsys.conf please

---

### Post by ex-wirecutter on 2009-03-07
For some reason I get the file not found for /etc/cups/cupsys.config
Also when I try to connect to printer I get http connectencrypt failed .
Also when I go into services cupsys is not listed .

---

### Post by ex-wirecutter on 2009-03-07
Found cups.config ;
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
Listen localhost:631
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
  Encryption Required
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

---

### Post by rhcm123 on 2009-03-07
Would you mind posting /etc/cups/cupsd.conf

also, go to System -> Administration -> Printing and try to fix it from there

---

### Post by rhcm123 on 2009-03-21
Has this thread died? or am i missing somthing (this is a bump to the OP)

---

### Post by jwood1961 on 2009-07-15
I have the same problem on one machine. CUPS appears to fail to start and previously installed printers have been forgotten. Problem emerged after some update, but as it's not my personal machine, not sure which.

Have reinstalled cups components. But each time try to install a new printer, get the same error message as above; printer admin screen shows "not connected" in bottom left, and diagnosis says that "CUPS server stopped". However Cups service is selected in System->Admin->Services. Deselecting then reselecting (after unlocking) has no effect.

Tried "sudo service cups start" and get following error message:
> * Starting Common Unix Printing System:cupsd
cupsd: Child exited on signal 6!

Current cupsd.conf is attached; there is no cupsys.config or similar; there is only a cupsd.conf.default also attached. (renamed to .txt file because of upload restrictions.

Any help appreciated
Kind Regards
JW

---

### Post by Engenia on 2009-08-24
Had the same / similar problem, although it was not as a result of an upgrade to ubuntu 9.04 (that's the only version I've had on this box).
I'm running GNOME 2.26.1

After finding that I had no printer access, I opened System -> Administration -> Printing & got the warning
 "CUPS Scheduler not running"
Then, after trolling for solutions, tried
 $ sudo /etc/init.c/cups restart
which then warned
 "command not found"

I then had a look in Synaptic Package Manager, searching for "cups", & discovered that the cups package wasn't marked ! (what-the?) So I marked it for installation, as well as the "system-config-printer" & "cups-pdf" (shouldn't have done 3 things at once, but couldn't help myself)

Stuff-me-mushrooms if it doesn't work again [-o<

---

### Post by clobs on 2009-09-14
When nothing of the above works, the problem could be that you have an old CUPs server configuration that is 'blocking' the printing services. To test this type in a terminal:

```
sudo gedit /etc/cups/client.conf
```

In my case, there was an old server that I configured once that I'll call old-printserver.com. This name could be anything so search for the line that start with ServerName and comment it (add a # at the begining of the line):

```
#ServerName old-printserver.com
```

Save the file and now your cups should be totally configurable from your browser at:
[http://localhost:631/]("http://localhost:631/")
Or by using 'System->Preferences->Default printer' and 'System->Administration->Printing'

It worked for me :P

---

### Post by bbrg548 on 2009-09-20
I'm having a similar problem that started today - and I was able to print yesterday.

When I try to run "sudo service cups start" I get:
```
/usr/sbin/cupsd: symbol lookup error: /usr/lib/libdns_sd.so.1: undefined symbol: __stack_chk_fail_local
```

If I look in "/etc/cups" I have:
```
acroread.conf       mime.types      printers.conf    snmp.conf
classes.conf        oopstops.convs  printers.conf.O  ssl
cupsd.conf          oopstops.types  pstopdf.convs    subscriptions.conf
cupsd.conf.default  pdftops.conf    raw.convs        subscriptions.conf.O
mime.convs          ppd             raw.types
```

No "cups.conf" or "cupsys.conf".

Cups is selected in the package manager, but when I run "$ sudo /etc/init.c/cups restart"

```
command not found
```

It was working yesterday, but I don't remember if it was before or after I ran the updates that were waiting.

---

### Post by clobs on 2009-09-21
You might use:
```
sudo /etc/init.d/cupsys restart
```

instead of 
```
sudo /etc/init.c/cups restart
```

Hope it works.

---

### Post by bbrg548 on 2009-09-22
No joy - same result.

> **clobs said:**
> You might use:
```
sudo /etc/init.d/cupsys restart
```

instead of 
```
sudo /etc/init.c/cups restart
```

Hope it works.

---

### Post by clobs on 2009-09-22
When you visit the local page: [http://localhost:631/](http://localhost:631/) in your browser, do you already see your printer installed? If not, you should do that first and then you can try printing a test from: [http://localhost:631/printers/](http://localhost:631/printers/)

If you can't see any of those pages, you probably should reinstall your cups packages from synaptic.

If printing test page works, but printing other documents don't, try doing what I wrote before in this thread about manually editing your /etc/cups/client.conf file.

If that doesn't work, I don't know what else to do. :confused:

---

### Post by coolmanlg on 2009-09-23
Has this problem been resolved? Am having exactly the same problem. I have tried reinstalling cups but no luck.

Tried :```
sudo service cups start
```
and got:
 ```
Starting Common Unix Printing System: 
  Child exited on signal 6!
```

Tried:```
  sudo /etc/init.d/cupsys restart 
```
Got 
```
command not found
```

It used to work few days back!

---

### Post by rp3 on 2009-09-24
> **clobs said:**
> When you visit the local page: [http://localhost:631/](http://localhost:631/) in your browser, do you already see your printer installed? If not, you should do that first and then you can try printing a test from: [http://localhost:631/printers/](http://localhost:631/printers/)

If you can't see any of those pages, you probably should reinstall your cups packages from synaptic.

If printing test page works, but printing other documents don't, try doing what I wrote before in this thread about manually editing your /etc/cups/client.conf file.

If that doesn't work, I don't know what else to do. :confused:

I get something similar but worse, when I do system-admin-printing, I see nothing, no "add printer" nothing, when I try to connect to the sever it fails..  I try 'localhost:631' nope nothing...

This is an old laptop running 9.04 and I just want to be able to print 1980 style banners, as I found an old Panasonic KX-P1124 and some paper. :)

So removing CUPS (COmpletely) via synaptic now, and will try to reload...

UPDATE - I reloaded CUPS and now all is functioning, the funny thing is I thought I had done this once already, but I guess not.. Banners printing away, now I need to get a new ribbon :)...

Chow..

---

### Post by fishmorg909 on 2009-10-07
After a recent ubuntu-linux update, my HP printer stopped working. After reading this thread, I opened Synaptic and completely removed and reinstalled **cupsddk** though **cupsys-common**, but that didn't help. Then I added **hpijs**, **hplip**, and **foomatic-gui**, and then my HP printer worked again. 

(The **foomatic-gui** was important, it re-enabled the choices in the 'advanced' printing tab.)

---

### Post by Selaro on 2009-10-08
I ran into the same problem after a recent update. I have a Xerox PE120 printer. All of my printers were lost and when I selected System/Preferences/default printer i received the error cups scheduler not running. This is what worked for me...

I opened System/administration/synaptic package manager. In the quick search box I entered cupsys-common and selected all of the packages that came up for reinstallation, here's a list of the packages;

cupsys-driver-gutenprint
cupsys-common
cupsys-client
cupsys-bsd
cupsys
cupsys-dbg 

after those were reinstalled or installed my printers showed up!

---

### Post by geent1 on 2010-02-02
> **ex-wirecutter said:**
> Have just had to reinstall Ubuntu 8.10 and my printer no longer works . When I try to nominate the printer I get cups scheduler not running , how do I start it ? My printer still shows up in the etc/cups folder. Have tried to run cupsd config but this cannot be found . Numerous restarts with and without the printer switched on have no effect and have double checked the printer cable .
I had the same problem but "sudo service cups start" worked to me!

---

### Post by bbrg548 on 2010-02-03
I got it working!

I've been getting this error when I run "sudo service cups start"
```

/usr/sbin/cupsd: symbol lookup error: /usr/lib/libdns_sd.so.1: undefined symbol: __stack_chk_fail_local
```

So in Synaptic, is did a search for "libdns". I saw I had 3 packages installed: libdns45, libdns46, and libavahi-compat-libdnssd1. I reinstalled each of them, and now it's working again. From the similarity in the names, I would guess the problem was in the avahi file, but I could be wrong.

---

### Post by presence1960 on 2010-02-03
> **ex-wirecutter said:**
> Have just had to reinstall Ubuntu 8.10 and my printer no longer works . When I try to nominate the printer I get cups scheduler not running , how do I start it ? My printer still shows up in the etc/cups folder. Have tried to run cupsd config but this cannot be found . Numerous restarts with and without the printer switched on have no effect and have double checked the printer cable .

open a terminal and run ```
sudo cupsd
```
This will start the cups scheduler.

I had the same problem in karmic until an update for cups came down the pike. Once the update was applied I didn't have to start the cups scheduler manually any longer.

---

### Post by wired99 on 2010-03-22
I don't understand, there are many comments about an update having fixed this issue, yet my system started doing this a few days ago.

I can manually start the services from the command line:

sudo service cups start

and 

sudo cupsd

they both work fine. But why do I need to do this manually? Am I missing something?

---

