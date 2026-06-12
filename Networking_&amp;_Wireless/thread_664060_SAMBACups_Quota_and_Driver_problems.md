---
title: "SAMBA/Cups Quota and Driver problems"
date: 2008-01-10
forum: Networking &amp; Wireless
---

### Post by madflyguy on 2008-01-10
I'm making a print server for a lab with about 60 computers. Using Ubuntu server 7.10 I currently have a functional SAMBA/CUPS print server - the lab computers can print via the print server. I followed a [_howtoforge guide_ ]("http://howtoforge.com/ubuntu-gutsy-samba-domaincontroller") for the basic setup, however I do not have or want a domain controller. Ultimately all I really need is to restrict the amount printed from any and every computer (some students are printing tons of garbage)

So here are 2 problems I currently have, the first being far more important;
-I can't get print quotas working
-I can't get samba to push drivers to computers that are mapping printers from it

Here are my smb.conf and cups.conf files (respectively);
```
#======================= Global Settings =======================

[global]

workgroup=UGRAD_LAB
# netbios name=labserver
security = share

#Set CUPS for printing:
load printers = yes
printcap name = cups
printing = cups

wins support = no

#======================= Printer Settings =======================

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   public = yes
   guest ok = yes
   writable = no
   create mode = 0700
#  printer admin = root

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers/W32X86
   browseable = yes
   read only = yes

   guest ok = yes
   public = yes
   writeable = no
   printable = yes
   write list = root, @Administrator

#======================= Shared Folders =======================

[Images]
path = /common/Images
available = yes
browsable = yes
public = yes
writable = no

[labshare]
path = /labshare
comment = Common Files for the Lab
available = yes
browsable = yes
public = yes
writable = no
```

```
LogLevel warning
SystemGroup lpadmin
# Only listen for connections from the local machine.
Listen localhost:631
Listen /var/run/cups/cups.sock
# Disable printer sharing and shared printers.
Browsing Off
/usr/sbin/guest -p socket://128.138.96.162 -o job-quota-period=60 \
-o job-page-limit=1
DefaultAuthType Basic
<Location />
  # Restrict access to the server...
  Order allow,deny
  Allow localhost
</Location>
<Location /admin>
  # Restrict access to the admin pages...
  Order allow,deny
  Allow localhost
</Location>
<Location /admin/conf>
  AuthType Default
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
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit All>
    Order deny,allow
  </Limit>
</Policy>



```

With regards to the second problem, I've been fiddling with **cupsaddsmb** thinking that was the problem and here is what I get when I run cupsaddsmb after changing security = share to security = user in the smb.conf file, and restarting samba (you can see the options I use in the code)
```
administrator@labserver:~$ sudo su
[sudo] password for administrator:
root@labserver:/home/administrator# cupsaddsmb -a -v -H localhost
Password for root required to access localhost via SAMBA: 
Running command: smbclient //localhost/print$ -N -A /tmp/4786a53ce648a -c 'mkdir W32X86;put /tmp/4786a539a4fd6 W32X86/1140_Lab_HP_LJ_8000.ppd;put /usr/share/cups/drivers/ps5ui.dll W32X86/ps5ui.dll;put /usr/share/cups/drivers/pscript.hlp W32X86/pscript.hlp;put /usr/share/cups/drivers/pscript.ntf W32X86/pscript.ntf;put /usr/share/cups/drivers/pscript5.dll W32X86/pscript5.dll'
Domain=[LABSERVER] OS=[Unix] Server=[Samba 3.0.26a]
NT_STATUS_OBJECT_NAME_COLLISION making remote directory \W32X86
putting file /tmp/4786a539a4fd6 as \W32X86/1140_Lab_HP_LJ_8000.ppd (16649.8 kb/s) (average 16650.1 kb/s)
putting file /usr/share/cups/drivers/ps5ui.dll as \W32X86/ps5ui.dll (18499.7 kb/s) (average 17646.2 kb/s)
putting file /usr/share/cups/drivers/pscript.hlp as \W32X86/pscript.hlp (12713.2 kb/s) (average 16988.5 kb/s)
putting file /usr/share/cups/drivers/pscript.ntf as \W32X86/pscript.ntf (32252.6 kb/s) (average 26381.9 kb/s)
putting file /usr/share/cups/drivers/pscript5.dll as \W32X86/pscript5.dll (34884.4 kb/s) (average 28507.6 kb/s)

Running command: smbclient //localhost/print$ -N -A /tmp/4786a53ce648a -c 'put /usr/share/cups/drivers/cups6.ini W32X86/cups6.ini;put /usr/share/cups/drivers/cupsps6.dll W32X86/cupsps6.dll;put /usr/share/cups/drivers/cupsui6.dll W32X86/cupsui6.dll'
Domain=[LABSERVER] OS=[Unix] Server=[Samba 3.0.26a]
putting file /usr/share/cups/drivers/cups6.ini as \W32X86/cups6.ini (35.2 kb/s) (average 35.2 kb/s)
putting file /usr/share/cups/drivers/cupsps6.dll as \W32X86/cupsps6.dll (6136.4 kb/s) (average 3085.9 kb/s)
putting file /usr/share/cups/drivers/cupsui6.dll as \W32X86/cupsui6.dll (6675.5 kb/s) (average 4282.6 kb/s)

Running command: rpcclient localhost -N -A /tmp/4786a53ce648a -c 'adddriver "Windows NT x86" "1140_Lab_HP_LJ_8000:pscript5.dll:1140_Lab_HP_LJ_8000.ppd:ps5ui.dll:pscript.hlp:NULL:RAW:pscript5.dll,1140_Lab_HP_LJ_8000.ppd,ps5ui.dll,pscript.hlp,pscript.ntf,cups6.ini,cupsps6.dll,cupsui6.dll"'
result was DOS code 0x00000042

Unable to install Windows 2000 printer driver files (1)!

```
from here the 2 "running command" commands loop. 

Anyone have any ideas? I really only need the first question addressed, but the second would be nice too   :)

FYI I'm fairly new to linux, so if anyone has some suggested commands I ought to run or permissions I ought to check, pls write the command/syntax so I can easily follow along. Thanks for the help.

---

### Post by derelict888 on 2008-01-11
:confused:

---

### Post by madflyguy on 2008-01-17
Anyone?  :confused:

---

