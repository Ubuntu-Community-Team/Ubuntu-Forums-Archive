---
title: "Cups printing and iptables problems"
date: 2008-07-26
forum: Networking &amp; Wireless
---

### Post by misterfixit on 2008-07-26
> **dmizer said:**
> don't share your printer via samba.  share your printer via cups:

system > administration > printing
under "server settings", turn on "Share published printers connected to this system"

that's it.  uber simple.

more information here: [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

Will not work here:  CUPS on Firefox shows both printers available on remote Ubuntu 8.01 PC located 2 meters away and connected via LAN. Network shows both Ubuntu 8.01 machines; CUPS config looks like this:

LogLevel debug
SystemGroup lpadmin
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
  # Allow shared printing and remote administration...
  Order allow,deny
  Allow all
</Location>
<Location /admin>
  # Allow remote administration...
  Order allow,deny
  Allow all
</Location>
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  # Allow remote access to the configuration files...
  Order allow,deny
  Allow all
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

When both computers are rebooted and Windows XP is selected (Dual Boot) all printers work perfectly, of course.  When compuers are again rebooted back to Ubuntu, The computer to which to printers are physically connected will print without problem.  The remote computer cannot print.

Access Log looks like this:

localhost - - [26/Jul/2008:09:08:18 -0500] "POST / HTTP/1.1" 200 416 CUPS-Get-Classes client-error-not-found
localhost - - [26/Jul/2008:09:36:12 -0500] "POST / HTTP/1.1" 200 129 CUPS-Get-Classes client-error-not-found
localhost - - [26/Jul/2008:10:00:01 -0500] "POST / HTTP/1.1" 200 411 CUPS-Get-Classes client-error-not-found
localhost - - [26/Jul/2008:10:00:01 -0500] "POST / HTTP/1.1" 200 411 CUPS-Get-Classes client-error-not-found
localhost - - [26/Jul/2008:10:00:00 -0500] "POST / HTTP/1.1" 200 1798 CUPS-Get-Devices -
localhost - - [26/Jul/2008:10:00:13 -0500] "POST / HTTP/1.1" 200 2570986 CUPS-Get-PPDs -
localhost - - [26/Jul/2008:10:01:14 -0500] "POST / HTTP/1.1" 200 129 CUPS-Get-Classes client-error-not-found
localhost - - [26/Jul/2008:10:01:19 -0500] "POST / HTTP/1.1" 200 411 CUPS-Get-Classes client-error-not-found
localhost - - [26/Jul/2008:10:01:19 -0500] "POST / HTTP/1.1" 200 411 CUPS-Get-Classes client-error-not-found
localhost - - [26/Jul/2008:10:01:18 -0500] "POST / HTTP/1.1" 200 1798 CUPS-Get-Devices -
localhost - - [26/Jul/2008:10:01:31 -0500] "POST / HTTP/1.1" 200 2570986 CUPS-Get-PPDs -
localhost - - [26/Jul/2008:10:02:43 -0500] "POST / HTTP/1.1" 200 2570986 CUPS-Get-PPDs -
localhost - - [26/Jul/2008:10:03:15 -0500] "POST / HTTP/1.1" 200 45566 CUPS-Get-PPD -
localhost - - [26/Jul/2008:10:03:35 -0500] "POST /admin/ HTTP/1.1" 401 45882 CUPS-Add-Modify-Printer successful-ok
localhost - root [26/Jul/2008:10:03:35 -0500] "POST /admin/ HTTP/1.1" 200 45882 CUPS-Add-Modify-Printer successful-ok
localhost - - [26/Jul/2008:10:03:35 -0500] "POST / HTTP/1.1" 200 178 Get-Jobs successful-ok
localhost - root [26/Jul/2008:10:03:35 -0500] "POST /admin/ HTTP/1.1" 200 129 Resume-Printer successful-ok
localhost - root [26/Jul/2008:10:03:35 -0500] "POST /admin/ HTTP/1.1" 200 129 CUPS-Accept-Jobs successful-ok
localhost - root [26/Jul/2008:10:03:35 -0500] "POST /admin/ HTTP/1.1" 200 129 CUPS-Set-Default successful-ok
localhost - root [26/Jul/2008:10:03:35 -0500] "POST /admin/ HTTP/1.1" 200 164 CUPS-Add-Modify-Printer successful-ok
localhost - root [26/Jul/2008:10:03:35 -0500] "POST /admin/ HTTP/1.1" 200 147 CUPS-Add-Modify-Printer successful-ok
localhost - root [26/Jul/2008:10:03:35 -0500] "POST / HTTP/1.1" 200 129 CUPS-Get-Classes successful-ok

Error Log Looks like this:

D [26/Jul/2008:22:37:22 -0500] [CGI] admin.cgi started...
D [26/Jul/2008:22:37:22 -0500] [CGI] http=0x8079ff8
D [26/Jul/2008:22:37:22 -0500] [CGI] No form data, showing main menu...
D [26/Jul/2008:22:37:22 -0500] [CGI] /usr/share/cups/drivers/pscript5.dll: No such file or directory
D [26/Jul/2008:22:37:22 -0500] cupsdAcceptClient: 281 from localhost (Domain)
D [26/Jul/2008:22:37:22 -0500] cupsdReadClient: 281 POST / HTTP/1.1
D [26/Jul/2008:22:37:22 -0500] cupsdAuthorize: No authentication data provided.
D [26/Jul/2008:22:37:22 -0500] Get-Subscriptions ipp://localhost/
D [26/Jul/2008:22:37:22 -0500] Get-Subscriptions client-error-not-found: No subscriptions found.
D [26/Jul/2008:22:37:22 -0500] cupsdProcessIPPRequest: 281 status_code=406 (client-error-not-found)
D [26/Jul/2008:22:37:22 -0500] PID 1932 (/usr/lib/cups/cgi-bin/admin.cgi) exited with no errors.
D [26/Jul/2008:22:37:22 -0500] cupsdCloseClient: 281
D [26/Jul/2008:22:37:22 -0500] [CGI] lang="en_US.UTF8", locale="/en_US"...
D [26/Jul/2008:22:37:22 -0500] [CGI] lang="en_US.UTF8", locale="/en_US"...
D [26/Jul/2008:22:37:22 -0500] [CGI] lang="en_US.UTF8", locale="/en_US"...
D [26/Jul/2008:22:37:27 -0500] cupsdReadClient: 21 GET /admin/log/access_log HTTP/1.1
D [26/Jul/2008:22:37:27 -0500] cupsdAuthorize: No authentication data provided.
D [26/Jul/2008:22:37:53 -0500] cupsdNetIFUpdate: "lo" = localhost...
D [26/Jul/2008:22:37:53 -0500] cupsdNetIFUpdate: "eth0" = 192.168.0.105...
D [26/Jul/2008:22:37:53 -0500] cupsdNetIFUpdate: "lo" = localhost...
D [26/Jul/2008:22:37:53 -0500] cupsdNetIFUpdate: "eth0" = fe80::213:d3ff:fecd:f019%eth0...
D [26/Jul/2008:22:37:53 -0500] Report: clients=1
D [26/Jul/2008:22:37:53 -0500] Report: jobs=2
D [26/Jul/2008:22:37:53 -0500] Report: jobs-active=0
D [26/Jul/2008:22:37:53 -0500] Report: printers=3
D [26/Jul/2008:22:37:53 -0500] Report: printers-implicit=0
D [26/Jul/2008:22:37:53 -0500] Report: stringpool-string-count=827
D [26/Jul/2008:22:37:53 -0500] Report: stringpool-alloc-bytes=9800
D [26/Jul/2008:22:37:53 -0500] Report: stringpool-total-bytes=17552
D [26/Jul/2008:22:38:37 -0500] cupsdCloseClient: 21
D [26/Jul/2008:22:38:55 -0500] cupsdNetIFUpdate: "lo" = localhost...
D [26/Jul/2008:22:38:55 -0500] cupsdNetIFUpdate: "eth0" = 192.168.0.105...
D [26/Jul/2008:22:38:55 -0500] cupsdNetIFUpdate: "lo" = localhost...
D [26/Jul/2008:22:38:55 -0500] cupsdNetIFUpdate: "eth0" = fe80::213:d3ff:fecd:f019%eth0...
D [26/Jul/2008:22:38:55 -0500] Report: clients=0
D [26/Jul/2008:22:38:55 -0500] Report: jobs=2
D [26/Jul/2008:22:38:55 -0500] Report: jobs-active=0
D [26/Jul/2008:22:38:55 -0500] Report: printers=3
D [26/Jul/2008:22:38:55 -0500] Report: printers-implicit=0
D [26/Jul/2008:22:38:55 -0500] Report: stringpool-string-count=827
D [26/Jul/2008:22:38:55 -0500] Report: stringpool-alloc-bytes=9800
D [26/Jul/2008:22:38:55 -0500] Report: stringpool-total-bytes=17552
D [26/Jul/2008:22:39:35 -0500] cupsdAcceptClient: 21 from localhost:631 (IPv4)
D [26/Jul/2008:22:39:35 -0500] cupsdReadClient: 21 GET /admin/log/error_log HTTP/1.1
D [26/Jul/2008:22:39:35 -0500] cupsdAuthorize: No authentication data provided.

---

### Post by misterfixit on 2008-08-23
BUMP ....  80+ views ?  Wonder if anyone has any idea about this problem???  Hello Ubuntu?

---

### Post by dmizer on 2008-08-23
> **misterfixit said:**
> BUMP ....  80+ views ?  Wonder if anyone has any idea about this problem???  Hello Ubuntu?

What version of ubuntu are you using?

---

### Post by misterfixit on 2008-08-24
> **dmizer said:**
> What version of ubuntu are you using?


Release 8.04 (Hardy)
Kernel Linux 2.6.24-19-generic
GNOME 2.22.3

Memory 4.0 GiB
Processor AMD Athlon 64 Processor 3700+

Running 32-bit on the AMD

---

### Post by dmizer on 2008-08-24
Have a firewall in place on either Windows or Ubuntu?

Please post the output of
```
sudo iptables -L
```

---

### Post by misterfixit on 2008-08-24
> **dmizer said:**
> Have a firewall in place on either Windows or Ubuntu?

Please post the output of
```
sudo iptables -L
```

No Firewall.. There are NO Windows machines involved here.  Only two Ubuntu boxes.

dave@dave-desktop:~$ sudo iptables -L
sudo: unable to resolve host dave-desktop
[sudo] password for dave: 
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.0.1          anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  192.168.0.1          anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       all  --  anywhere             255.255.255.255     
DROP       all  --  anywhere             192.168.0.255       
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5 
INBOUND    all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.0.105        192.168.0.1         tcp dpt:domain 
ACCEPT     udp  --  192.168.0.105        192.168.0.1         udp dpt:domain 
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
OUTBOUND   all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output' 

Chain INBOUND (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  192.168.0.102        anywhere            
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:netbios-ns 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:netbios-ns 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:52741 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:52741 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:netbios-dgm 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:netbios-dgm 
LSI        all  --  anywhere             anywhere            

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST 
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       icmp --  anywhere             anywhere            icmp echo-request 
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound ' 
DROP       all  --  anywhere             anywhere            

Chain LSO (0 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere            
dave@dave-desktop:~$

---

### Post by dmizer on 2008-08-24
Two things I notice with that output.

1) You do indeed have a firewall running that is likely to be interfering with your printing ability.

2) This is a problem:
```
unable to resolve host dave-desktop
```

Please post the output of:
```
cat /etc/hosts
```

What have you used to configure iptables? You'll need to make a rule for printing on port 631.

---

### Post by misterfixit on 2008-08-24
> **dmizer said:**
> Two things I notice with that output.

1) You do indeed have a firewall running that is likely to be interfering with your printing ability.

-----------------------
I didn't know that.
-----------------------
2) This is a problem:
```
unable to resolve host dave-desktop
```

-----------------------
I think this has something to do with the message about 644 permissions for .dmrc and HOME; But I have followed all the guidance to fix that error message, but with no luck.
-----------------------

Please post the output of:
```
cat /etc/hosts
```

-----------------------
dave@dave-desktop:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 dave-desktop.misterfixit

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
dave@dave-desktop:~$ 
-----------------------------

What have you used to configure iptables? You'll need to make a rule for printing on port 631.

----------------------------
I have used the CUPS web-based application to search for and configure printers.  Here is the output from the "Server Config File" which is shown by the CUPS printer set up application:

# Show troubleshooting information in error_log.
LogLevel debug
SystemGroup lpadmin
# Allow remote access
Port 631
Listen *:631
Listen /var/run/cups/cups.sock
# Enable printer sharing and shared printers.
Browsing On
BrowseOrder allow,deny
BrowseAllow all
BrowseAddress @LOCAL
DefaultAuthType Negotiate
<Location />
  # Allow shared printing and remote administration...
  Order allow,deny
  Allow all
</Location>
<Location /admin>
  # Allow remote administration...
  Order allow,deny
  Allow all
</Location>
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  # Allow remote access to the configuration files...
  Order allow,deny
  Allow all
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

------------------

Thank you for your help.

Dave

---

### Post by dmizer on 2008-08-24
You'll need to edit /etc/hosts as root:
```
sudo nano /etc/hosts
```

and edit the file so it looks like this:
```

127.0.0.1 localhost
127.0.1.1 dave-desktop

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

You'll have to reboot after changing this file. This will also fix your problem with permissions in .dmrc and HOME.

The cups config file won't do any good if iptables is blocking your access.  Did you install firestarter, Ubuntu firewall, anything that would allow you to configure things like port forwarding, internet connection sharing, or any other kind of NAT tasks?

---

### Post by misterfixit on 2008-08-24
> **dmizer said:**
> You'll need to edit /etc/hosts as root:
```
sudo nano /etc/hosts
```

and edit the file so it looks like this:
```

127.0.0.1 localhost
127.0.1.1 dave-desktop

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

You'll have to reboot after changing this file. This will also fix your problem with permissions in .dmrc and HOME.

The cups config file won't do any good if iptables is blocking your access.  Did you install firestarter, Ubuntu firewall, anything that would allow you to configure things like port forwarding, internet connection sharing, or any other kind of NAT tasks?


Thank you again.

I believe that a few weeks ago I loaded firestarter and tried to get it to do something besides blocking my access to the Internet.  However, it would usualy crash after a few minutes so I uninstalled it.

Can you point me towards a good iptables example?

Dave

---

### Post by dmizer on 2008-08-24
Apparently your uninstall of Firestarter left behind some iptables configuration.

To return your iptables to their default state, use this command:
```
sudo iptables -F
```

You'll have to fix your /etc/hosts before this will work.

---

### Post by misterfixit on 2008-08-24
> **dmizer said:**
> Apparently your uninstall of Firestarter left behind some iptables configuration.

To return your iptables to their default state, use this command:
```
sudo iptables -F
```

You'll have to fix your /etc/hosts before this will work.

OK, I repaired the /etc/hosts and did the return to default on iptables.  I've just rebooted.  I still see the 644 permissions message on boot up.

I'll start checking to see if the printing is fixed.

Thanks
Dave

---

### Post by dmizer on 2008-08-24
> **misterfixit said:**
> OK, I repaired the /etc/hosts and did the return to default on iptables.  I've just rebooted.  I still see the 644 permissions message on boot up.

You should be able to fix this by following the directions in post number 3 of this thread now: [http://ubuntuforums.org/showthread.php?t=698068](http://ubuntuforums.org/showthread.php?t=698068)

---

### Post by misterfixit on 2008-08-24
> **misterfixit said:**
> OK, I repaired the /etc/hosts and did the return to default on iptables.  I've just rebooted.  I still see the 644 permissions message on boot up.

I'll start checking to see if the printing is fixed.

Thanks
Dave

Sorry.  Nothing has changed.

Thanks anyway.  If you can spare the time, perhaps we can continue to figure out what is wrong?

Dave

---

### Post by dmizer on 2008-08-24
> **misterfixit said:**
> Sorry.  Nothing has changed.

Thanks anyway.  If you can spare the time, perhaps we can continue to figure out what is wrong?

Dave

Your iptables may not have cleared.  Try looking at the output of sudo iptables -L again. It should look like this:
```
Chain INPUT (policy ACCEPT)
target prot opt source destination

Chain FORWARD (policy ACCEPT)
target prot opt source destination

Chain OUTPUT (policy ACCEPT)
target prot opt source destination
```

You may be unsuccessful until you solve this problem:
> **dmizer said:**
> You should be able to fix this by following the directions in post number 3 of this thread now: [http://ubuntuforums.org/showthread.php?t=698068](http://ubuntuforums.org/showthread.php?t=698068)

---

### Post by misterfixit on 2008-08-24
> **dmizer said:**
> Your iptables may not have cleared.  Try looking at the output of sudo iptables -L again. It should look like this:
```
Chain INPUT (policy ACCEPT)
target prot opt source destination

Chain FORWARD (policy ACCEPT)
target prot opt source destination

Chain OUTPUT (policy ACCEPT)
target prot opt source destination
```

You may be unsuccessful until you solve this problem:

Here is the iptables output again.  I can see where it is saying DROP instead of ACCEPT.  I don't know how to change that.

dave@dave-desktop:~$ sudo iptables -L
[sudo] password for dave: 
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.0.1          anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  192.168.0.1          anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       all  --  anywhere             255.255.255.255     
DROP       all  --  anywhere             192.168.0.255       
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5 
INBOUND    all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.0.105        192.168.0.1         tcp dpt:domain 
ACCEPT     udp  --  192.168.0.105        192.168.0.1         udp dpt:domain 
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
OUTBOUND   all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output' 

Chain INBOUND (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  192.168.0.102        anywhere            
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:netbios-ns 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:netbios-ns 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:52741 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:52741 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:netbios-dgm 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:netbios-dgm 
LSI        all  --  anywhere             anywhere            

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST 
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       icmp --  anywhere             anywhere            icmp echo-request 
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound ' 
DROP       all  --  anywhere             anywhere            

Chain LSO (0 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere            
dave@dave-desktop:~$

---

### Post by dmizer on 2008-08-24
Did you change your username, add a new account, or anything with the root account which would explain your problem with permissions?

---

### Post by misterfixit on 2008-08-25
> **dmizer said:**
> Did you change your username, add a new account, or anything with the root account which would explain your problem with permissions?

 am not sure, but I don't think so.  Like I said before, everyting was working before the last upgrade cycle.

---

### Post by dmizer on 2008-08-25
Has your permissions issue been resolved yet? If not, I would concentrate on fixing that.  You should be able to fix it by following the howtos now because /etc/hosts is correct.

If it has been fixed, and you still can't clear your iptables rules. Try this series of commands:
```
iptables -F
iptables -X
iptables -t nat -F
iptables -t nat -X
iptables -t mangle -F
iptables -t mangle -X
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT
```

Look at iptables -L and it should look like this:
```
Chain INPUT (policy ACCEPT)
target prot opt source destination

Chain FORWARD (policy ACCEPT)
target prot opt source destination

Chain OUTPUT (policy ACCEPT)
target prot opt source destination
```

If -
1) Your permission problems HAVE been resolved
- and -
2) Your firewall rules still will not clear

then post the output of this command:
```
ps aux
```

---

### Post by misterfixit on 2008-08-25
> **dmizer said:**
> Has your permissions issue been resolved yet? If not, I would concentrate on fixing that.  You should be able to fix it by following the howtos now because /etc/hosts is correct.

If it has been fixed, and you still can't clear your iptables rules. Try this series of commands:
```
iptables -F
iptables -X
iptables -t nat -F
iptables -t nat -X
iptables -t mangle -F
iptables -t mangle -X
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT
```

Look at iptables -L and it should look like this:
```
Chain INPUT (policy ACCEPT)
target prot opt source destination

Chain FORWARD (policy ACCEPT)
target prot opt source destination

Chain OUTPUT (policy ACCEPT)
target prot opt source destination
```

If -
1) Your permission problems HAVE been resolved
- and -
2) Your firewall rules still will not clear

then post the output of this command:
```
ps aux
```

OK, I did all of the above mentioned commands.  Here is the ps aux output:

------------

dave@dave-desktop:~$ sudo ps aux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   2844  1692 ?        Ss   Aug24   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   Aug24   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   Aug24   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S<   Aug24   0:04 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   Aug24   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   Aug24   0:00 [events/0]
root         7  0.0  0.0      0     0 ?        S<   Aug24   0:00 [khelper]
root        41  0.0  0.0      0     0 ?        S<   Aug24   0:01 [kblockd/0]
root        44  0.0  0.0      0     0 ?        S<   Aug24   0:00 [kacpid]
root        45  0.0  0.0      0     0 ?        S<   Aug24   0:00 [kacpi_notify]
root       147  0.0  0.0      0     0 ?        S<   Aug24   0:00 [kseriod]
root       187  0.0  0.0      0     0 ?        S<   Aug24   0:02 [kswapd0]
root       228  0.0  0.0      0     0 ?        S<   Aug24   0:00 [aio/0]
root      1506  0.0  0.0      0     0 ?        S<   Aug24   0:00 [ksuspend_usbd]
root      1510  0.0  0.0      0     0 ?        S<   Aug24   0:00 [khubd]
root      1524  0.0  0.0      0     0 ?        S<   Aug24   0:05 [ata/0]
root      1530  0.0  0.0      0     0 ?        S<   Aug24   0:00 [ata_aux]
root      2274  0.0  0.0      0     0 ?        S<   Aug24   0:00 [scsi_eh_0]
root      2276  0.0  0.0      0     0 ?        S<   Aug24   0:09 [scsi_eh_1]
root      2316  0.0  0.0      0     0 ?        S<   Aug24   0:00 [scsi_eh_2]
root      2765  0.0  0.0      0     0 ?        S<   Aug24   0:00 [scsi_eh_3]
root      2768  0.0  0.0      0     0 ?        S<   Aug24   0:00 [scsi_eh_4]
root      2937  0.0  0.0      0     0 ?        S<   Aug24   0:00 [scsi_eh_5]
root      2941  0.0  0.0      0     0 ?        S<   Aug24   0:02 [usb-storage]
root      3156  0.0  0.0      0     0 ?        S<   Aug24   0:07 [kjournald]
root      3448  0.0  0.0   2496  1040 ?        S<s  Aug24   0:00 /sbin/udevd --d
root      3926  0.0  0.0      0     0 ?        S<   Aug24   0:00 [btaddconn]
root      3933  0.0  0.0      0     0 ?        S<   Aug24   0:00 [btdelconn]
root      3951  0.0  0.0      0     0 ?        S<   Aug24   0:19 [rt2500pci]
daemon    5276  0.0  0.0   1836   476 ?        Ss   Aug24   0:00 /sbin/portmap
root      5453  0.0  0.0   1716   512 tty4     Ss+  Aug24   0:00 /sbin/getty 384
root      5454  0.0  0.0   1716   512 tty5     Ss+  Aug24   0:00 /sbin/getty 384
root      5458  0.0  0.0   1716   512 tty2     Ss+  Aug24   0:00 /sbin/getty 384
root      5459  0.0  0.0   1716   504 tty3     Ss+  Aug24   0:00 /sbin/getty 384
root      5461  0.0  0.0   1716   504 tty6     Ss+  Aug24   0:00 /sbin/getty 384
root      5629  0.0  0.0   2456  1356 ?        Ss   Aug24   0:00 /usr/sbin/acpid
root      5661  0.0  0.0      0     0 ?        S<   Aug24   0:18 [kondemand/0]
syslog    5734  0.0  0.0   1936   688 ?        Ss   Aug24   0:00 /sbin/syslogd -
root      5792  0.0  0.0   1872   540 ?        S    Aug24   0:02 /bin/dd bs 1 if
klog      5794  0.0  0.0   3824  2736 ?        Ss   Aug24   0:00 /sbin/klogd -P
106       5816  0.0  0.0   3168  1564 ?        Ss   Aug24   0:04 /usr/bin/dbus-d
root      5832  0.0  0.0  21208  2352 ?        Ssl  Aug24   0:02 /usr/sbin/Netwo
root      5846  0.0  0.0   3536  1316 ?        Ss   Aug24   0:00 /usr/sbin/Netwo
root      5859  0.0  0.0   4112  1112 ?        Ss   Aug24   0:00 /usr/bin/system
bind      5892  0.0  0.2  35220  7492 ?        Ssl  Aug24   0:00 /usr/sbin/named
root      5937  0.0  0.0   5316   992 ?        Ss   Aug24   0:00 /usr/sbin/sshd
avahi     5985  0.0  0.0   2900  1532 ?        Ss   Aug24   0:00 avahi-daemon: r
avahi     5986  0.0  0.0   2760   464 ?        Ss   Aug24   0:00 avahi-daemon: c
root      6003  0.0  0.0   1868   520 ?        Ss   Aug24   0:00 /usr/sbin/avahi
clamav    6262  0.0  1.5  55636 52868 ?        Ss   Aug24   0:05 /usr/sbin/clamd
clamav    6358  0.0  0.0   3020  1336 ?        Ss   Aug24   0:00 /usr/bin/freshc
dictd     6373  0.0  0.6  59800 22016 ?        Ss   Aug24   0:00 dictd 1.10.10: 
root      6390  0.0  0.0   2736   684 ?        Ss   Aug24   0:08 /usr/bin/dirmng
partimag  6433  0.0  0.0   6236  1700 ?        Ss   Aug24   0:00 /usr/sbin/parti
privoxy   6451  0.0  0.0   2728  1048 ?        Ss   Aug24   0:00 /usr/sbin/privo
root      6461  0.0  0.0  27040  2040 ?        Ss   Aug24   0:00 /usr/bin/qtsmbs
root      6479  0.0  0.0   9996  2240 ?        Ss   Aug24   0:00 /usr/sbin/smbd
root      6486  0.0  0.0   3036   748 ?        Ss   Aug24   0:00 /usr/sbin/senso
root      6489  0.0  0.0   9996   916 ?        S    Aug24   0:00 /usr/sbin/smbd
117       6499  0.0  0.3  15428 13212 ?        S    Aug24   0:28 /usr/sbin/tor
root      6574  0.0  0.0   8092  1352 ?        Ss   Aug24   0:00 /usr/sbin/winbi
root      6579  0.0  0.0   8092  1068 ?        S    Aug24   0:00 /usr/sbin/winbi
root      6599  0.0  0.0   2424   852 ?        Ss   Aug24   0:00 /usr/sbin/xinet
root      6709  0.0  0.0   2020   908 ?        Ss   Aug24   0:04 /usr/sbin/dhcdb
109       6728  0.0  0.1   6348  4404 ?        Ss   Aug24   0:03 /usr/sbin/hald
root      6731  0.0  0.0   7884  2380 ?        Ssl  Aug24   0:00 /usr/sbin/conso
root      6793  0.0  0.0   3352  1188 ?        S    Aug24   0:00 hald-runner
root      6825  0.0  0.0   3416  1148 ?        S    Aug24   0:00 hald-addon-inpu
root      6827  0.0  0.0   3428  1228 ?        S    Aug24   0:00 /usr/lib/hal/ha
109       6828  0.0  0.0   2204   908 ?        S    Aug24   0:00 hald-addon-acpi
root      6856  0.0  0.0   3420  1140 ?        S    Aug24   0:01 hald-addon-stor
root      6858  0.0  0.0   3420  1136 ?        S    Aug24   0:01 hald-addon-stor
root      6860  0.0  0.0   3420  1132 ?        S    Aug24   0:01 hald-addon-stor
root      6863  0.0  0.0   3420  1132 ?        S    Aug24   0:01 hald-addon-stor
root      6866  0.0  0.0   3420  1140 ?        S    Aug24   0:10 hald-addon-stor
root      6908  0.0  0.0   3172  1356 ?        Ss   Aug24   0:00 /usr/sbin/hcid
root      6920  0.0  0.0   3084  1304 ?        S    Aug24   0:00 /usr/lib/blueto
root      6921  0.0  0.0   3020  1112 ?        S    Aug24   0:00 /usr/lib/blueto
root      6926  0.0  0.0      0     0 ?        S<   Aug24   0:00 [krfcommd]
root      6991  0.0  0.0  14060  1652 ?        Ss   Aug24   0:00 /usr/sbin/gdm
root      6994  0.0  0.1  18560  4316 ?        S    Aug24   0:00 /usr/sbin/gdm
root      6998  1.3  1.7  65568 58984 tty7     RLs+ Aug24  19:28 /usr/bin/X :0 -
dhcp      7005  0.0  0.0   2440  1188 ?        S    Aug24   0:00 /sbin/dhclient
root      7216  0.0  0.0   5956  2568 ?        Ss   Aug24   0:00 /usr/sbin/cupsd
daemon    7455  0.0  0.0   1984   420 ?        Ss   Aug24   0:00 /usr/sbin/atd
root      7475  0.0  0.0   2104   896 ?        Ss   Aug24   0:00 /usr/sbin/cron
root      7661  0.0  0.0   1716   508 tty1     Ss+  Aug24   0:00 /sbin/getty 384
ntp       7693  0.0  0.0   4136  1236 ?        Ss   Aug24   0:01 /usr/sbin/ntpd
dave      7707  0.0  0.1   6932  4040 ?        S    Aug24   0:41 /usr/lib/libgco
dave      7709  0.0  0.0  14340  2152 ?        S    Aug24   0:00 /usr/bin/gnome-
dave      7713  0.0  0.4  55964 14236 ?        Ssl  Aug24   0:01 x-session-manag
dave      7770  0.0  0.0   3668   760 ?        Ss   Aug24   0:02 /usr/bin/gpg-ag
dave      7776  0.0  0.1  22888  6632 ?        Ss   Aug24   0:00 /usr/bin/seahor
dave      7782  0.0  0.0   2828  1248 ?        Ss   Aug24   0:06 dbus-daemon --f
dave      7783  0.0  0.8  58556 29064 ?        Sl   Aug24   0:09 gnome-settings-
dave      7789  0.1  0.1  37012  6532 ?        Sl   Aug24   1:52 /usr/bin/pulsea
dave      7792  0.0  0.0   5776  2316 ?        S    Aug24   0:00 /usr/lib/pulsea
dave      7806  0.0  0.1  16196  6200 ?        Ss   Aug24   0:56 gnome-screensav
dave      7807  0.2  0.3  21340 13084 ?        S    Aug24   3:02 metacity --sm-c
dave      7808  0.3  2.8 168996 94832 ?        Sl   Aug24   5:04 nautilus --sm-c
dave      7809  0.1  0.8  74384 29652 ?        Sl   Aug24   2:36 gnome-panel --s
dave      7811  0.0  0.0  40184  3252 ?        Ssl  Aug24   0:00 /usr/lib/bonobo
dave      7813  0.1  1.0 131912 36252 ?        Sl   Aug24   2:20 pidgin --sessio
dave      7815  0.0  0.4  46996 13700 ?        S    Aug24   0:01 update-notifier
dave      7822  0.0  0.0   5504  2168 ?        S    Aug24   0:00 /usr/lib/gvfs/g
dave      7823  0.0  0.2  39908  8244 ?        S    Aug24   0:00 bluetooth-apple
dave      7828  0.0  0.1  15712  6116 ?        S    Aug24   0:01 tracker-applet
dave      7829  0.0  0.3  62340 10212 ?        Sl   Aug24   0:00 /usr/lib/evolut
dave      7836  0.1  0.6  40980 20864 ?        SNl  Aug24   1:46 trackerd
dave      7838  0.0  0.0   4772  1796 ?        S    Aug24   0:00 /usr/bin/obex-d
dave      7841  0.0  0.4  46692 14788 ?        S    Aug24   0:12 /usr/lib/notifi
dave      7843  0.0  0.3  24280 12204 ?        S    Aug24   0:06 python /usr/sha
dave      7846  0.0  0.3  66392 11252 ?        S    Aug24   0:42 nm-applet --sm-
dave      7847  0.0  0.1  20796  4832 ?        Ss   Aug24   0:01 /usr/lib/gnome-
dave      7849  0.0  0.0  29048  1900 ?        Ssl  Aug24   0:00 /usr/lib/gvfs//
dave      7866  0.0  0.4  24352 15140 ?        S    Aug24   0:23 /usr/bin/python
dave      7867  0.0  0.2  45104  7356 ?        Ss   Aug24   0:00 seahorse-daemon
dave      7868  0.0  0.2  23452  7684 ?        Ss   Aug24   0:01 gnome-power-man
dave      7909  0.0  0.2  38940  9752 ?        Sl   Aug24   0:00 /usr/lib/evolut
dave      7925  0.0  0.5  60252 17856 ?        S    Aug24   0:01 /usr/lib/gnome-
dave      7931  0.0  0.1  67956  6596 ?        Sl   Aug24   0:00 /usr/lib/evolut
dave      7933  0.0  0.0  22132  2772 ?        S    Aug24   0:00 /usr/lib/gvfs/g
dave      7943  0.0  0.0   5372  2140 ?        S    Aug24   0:00 /usr/lib/gvfs/g
dave      7985  0.0  0.7  69608 25876 ?        Sl   Aug24   0:02 mono /usr/lib/t
dave      8009  0.0  0.3  24384 12196 ?        S    Aug24   0:22 /usr/lib/gnome-
dave      8012  0.0  0.4  48068 14468 ?        S    Aug24   1:22 /usr/lib/gnome-
dave      8021  0.0  0.2  20940  8312 ?        S    Aug24   0:53 /usr/lib/gnome-
dave      8025  0.0  0.4  65996 15888 ?        Sl   Aug24   0:00 /usr/lib/gnome-
dave      8041  0.0  0.3  47196 13280 ?        S    Aug24   0:00 /usr/lib/fast-u
dave      8138  0.0  0.9  95580 31104 ?        Sl   Aug24   0:00 /usr/lib/openof
dave      8231  0.0  0.0   1772   512 ?        S    Aug24   0:00 /bin/sh /usr/bi
dave      8243  0.0  0.0   1772   520 ?        S    Aug24   0:00 /bin/sh /usr/li
dave      8247  0.1  2.2 238864 75560 ?        Sl   Aug24   2:01 /usr/lib/thunde
dave      8267  0.0  0.9 109600 32192 ?        S    Aug24   0:08 /usr/games/sol
dave     10662  0.0  0.1   8636  3500 ?        S    Aug24   0:00 /usr/lib/gnome-
dave     19521  1.7  3.5 272840 118424 ?       Sl   16:24   4:17 /usr/lib/firefo
dave     19979  0.0  0.4  60484 16124 ?        Sl   16:39   0:01 gnome-terminal
dave     19981  0.0  0.0   2912   856 ?        S    16:39   0:00 gnome-pty-helpe
dave     19982  0.0  0.1   6148  3560 pts/0    Ss+  16:39   0:00 bash
root     21228  0.0  0.0      0     0 ?        S    17:14   0:00 [pdflush]
root     21249  0.0  0.0      0     0 ?        S    17:15   0:00 [pdflush]
dave     22132  0.0  0.0  14404  3152 ?        Sl   17:41   0:00 /usr/lib/gvfs/g
root     22150  0.0  0.0      0     0 ?        S<   17:42   0:00 [kjournald]
dave     22280  0.0  0.0   1772   492 ?        S    17:43   0:00 /bin/sh /usr/bi
dave     22281  0.0  0.5  47812 16968 ?        S    17:43   0:00 python ./EasyCr
root     22510  0.0  0.0   3008   632 ?        S    17:48   0:00 dbus-launch --a
root     22511  0.0  0.0   2564   932 ?        Ss   17:48   0:00 /usr/bin/dbus-d
dave     26615  0.0  0.1   6092  3508 pts/1    Ss   20:20   0:00 bash
dave     26734  0.0  0.0      0     0 ?        Z    20:24   0:00 [sh] <defunct>
root     26736  0.0  0.0   2644  1004 pts/1    R+   20:24   0:00 ps aux
dave@dave-desktop:~$ 


---------------

---

### Post by dmizer on 2008-08-25
Just making sure ... I understand that:
1) Your permissions problems are solved?
and
2) That you still have iptables rules in place.

If so, I'll need a more complete copy of ps aux because the above got cut off.  Please perform this command:
```
ps aux > ps.txt
```

Then attach the ps.txt to your post please (it should be located in your home folder).

---

### Post by misterfixit on 2008-08-25
> **dmizer said:**
> Just making sure ... I understand that:
1) Your permissions problems are solved?
and
2) That you still have iptables rules in place.

If so, I'll need a more complete copy of ps aux because the above got cut off.  Please perform this command:
```
ps aux > ps.txt
```

Then attach the ps.txt to your post please (it should be located in your home folder).

OK, ps aux is attached.  I am glad you can figure this out.  I am now pretty much lost, although every time you post I immediately look up on both the on-line Linux helps, the man pages and so forth to try and learn what you are doing for me.

Thanks again ..

Dave

---

### Post by dmizer on 2008-08-25
I'm just trying to see what's running on your system so I can figure out what's making your iptables.

I see that you have configured tor and privoxy.  Did you follow a howto which included firewall or iptables configuration?

---

### Post by misterfixit on 2008-08-26
> **dmizer said:**
> I'm just trying to see what's running on your system so I can figure out what's making your iptables.

I see that you have configured tor and privoxy.  Did you follow a howto which included firewall or iptables configuration?

I "thought" that I followed the install guides.  Perhaps I should make tor and privoxy go away?  I have never been able to get tor to work anyway.  Would "sudo aptitude remove tor | sudo aptitude remove privoxy" work?

---

### Post by dmizer on 2008-08-26
Split this out into it's own thread, as this was a complete hijack of the original.

There's nothing wrong with installing tor or privoxy. Neither should give you this problem.

Your problem is that you have an iptables script in place that's blocking all your requests including incoming printing requests. I gave you multiple ways of removing the iptables configuration, but you seem to be indicating that it's still in place. Since that's the case, we need to determine why or how your iptables has been configured so we can figure out how to turn it off.

Once we get your iptables unconfigured, tor, privoxy, cups, and a host of other problems you may be experiencing will be solved.

So, I am simply trying to figure out where that configuration comes from. Since you don't recall doing this configuration, my thinking is that it was part of a tutorial you followed.

---

### Post by misterfixit on 2008-08-31
[QUOTE=dmizer;5668024]Split this out into it's own thread, as this was a complete hijack of the original.


Yeah yeah, whatever.  Since this last bit of "advice" I've gone ahead and done the usual Windows thing.  Wiped out the old install and completely reinstalled a newly downloaded version of Ubuntu.

Everything works perfectly now.  So much for all of the previous jerking around with trying this and trying that..  As soon as I got thenew system installed and all ofmy old files brought up to date, I used rsync to create a duplicate bootable image on another HD which I;ll use to go back whenever I manage to screw up Ubuntu again.

Thanks for everything.

Thus ends this thread.

:popcorn:

---

