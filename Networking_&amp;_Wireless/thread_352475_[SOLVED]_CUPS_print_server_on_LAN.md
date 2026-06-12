---
title: "[SOLVED] CUPS print server on LAN"
date: 2007-02-03
forum: Networking &amp; Wireless
---

### Post by quigleydoor on 2007-02-03
Hi, I want to set up my Xubuntu box as a CUPS print server for my LAN at home.  All the other hosts on the LAN are Windows PCs.  I believe that I can configure the Windows PCs to send print jobs to CUPS using Internet Printing Protocol.  Can anyone confirm that this will work?

The trouble I'm having is DNS or IP related.  I **_can_** telnet to localhost 631, but not using machine name.  Look at this, a terminal session on my Xubuntu box:

```

quigley@quigley-desktop:~$ **telnet localhost 631**
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
helo
Connection closed by foreign host.
quigley@quigley-desktop:~$ **telnet quigley-desktop 631**
Trying 127.0.1.1...
telnet: Unable to connect to remote host: Connection refused
quigley@quigley-desktop:/home/netshare$ telnet quigley-desktop
Trying 127.0.1.1...
telnet: Unable to connect to remote host: Connection refused
quigley@quigley-desktop:~$ **ping quigley-desktop**
PING quigley-desktop (127.0.1.1) 56(84) bytes of data.
64 bytes from quigley-desktop (127.0.1.1): icmp_seq=1 ttl=64 time=0.170 ms
64 bytes from quigley-desktop (127.0.1.1): icmp_seq=2 ttl=64 time=0.127 ms
64 bytes from quigley-desktop (127.0.1.1): icmp_seq=3 ttl=64 time=0.132 ms
64 bytes from quigley-desktop (127.0.1.1): icmp_seq=4 ttl=64 time=0.130 ms
64 bytes from quigley-desktop (127.0.1.1): icmp_seq=5 ttl=64 time=0.128 ms
64 bytes from quigley-desktop (127.0.1.1): icmp_seq=6 ttl=64 time=0.129 ms
64 bytes from quigley-desktop (127.0.1.1): icmp_seq=7 ttl=64 time=0.131 ms

--- quigley-desktop ping statistics ---
7 packets transmitted, 7 received, 0% packet loss, time 6000ms
rtt min/avg/max/mdev = 0.127/0.135/0.170/0.016 ms

```

Why can't I establish a telnet connection using the machine name and port 631?

Also, from one of the Windows PCs, I _**can**_ ping quigley-desktop by name.  Check this out:

```

C:\Documents and Settings\jgalley>**ping quigley-desktop**

Pinging quigley-desktop [192.168.2.6] with 32 bytes of data:

Reply from 192.168.2.6: bytes=32 time=2ms TTL=64
Reply from 192.168.2.6: bytes=32 time=1ms TTL=64
Reply from 192.168.2.6: bytes=32 time=2ms TTL=64
Reply from 192.168.2.6: bytes=32 time=1ms TTL=64

Ping statistics for 192.168.2.6:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 1ms, Maximum = 2ms, Average = 1ms

C:\Documents and Settings\qdoor>**telnet quigley-desktop**
Connecting To quigley-desktop...Could not open connection to the host, on port 23: Connect failed

C:\Documents and Settings\qdoor>**telnet 192.168.2.6**
Connecting To 192.168.2.6...Could not open connection to the host, on port 23: Connect failed

```

Why can't I telnet at all from my Windows PC?

---

### Post by quigleydoor on 2007-02-07
I figured it out.  I changed some settings in the CUPS config file, cupsd.conf.  Specifically, I had to change the Listen directive to *:631,  And I had to disable all denials of access to the web admin pages.

All set now.  My Windows PC can print to [http://quigley-desktop:631/printers/Ezra](http://quigley-desktop:631/printers/Ezra) (which is my printer's name).  Yay!

---

### Post by kochen on 2007-02-08
Hi,
can you explain what exactly did you change?

---

### Post by quigleydoor on 2007-02-11
Here is my cupsd.conf.  Changed config instructions are in red:
```
# Show general information in error_log.
LogLevel info
SystemGroup lpadmin
# Enable printer sharing and shared printers.
Browsing On
BrowseOrder allow,deny
BrowseAllow @LOCAL
BrowseAddress @LOCAL
DefaultAuthType Basic
[COLOR="Red"]<Location />
  # Allow shared printing and remote administration...
  Order allow,deny
  # Deny from all
  Allow from All
  # Allow from 127.0.0.1
  # Allow from 192.168.1.*
</Location>[/COLOR]
<Location /admin>
  # Allow remote administration...
  Order allow,deny
  Allow [COLOR="Red"]from All[/COLOR]
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
  <Limit All>
    Order deny,allow
  </Limit>
</Policy>
[COLOR="Red"]# Include /etc/cups/cups.d/ports.conf[/COLOR]
Include /etc/cups/cups.d/browse.conf
# Allow remote access
[COLOR="Red"]Listen *:631
# Port 631[/COLOR]
Listen /var/run/cups/cups.sock
```

---

