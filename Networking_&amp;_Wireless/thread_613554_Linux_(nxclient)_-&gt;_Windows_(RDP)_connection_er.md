---
title: "Linux (nxclient) -&gt; Windows (RDP) connection error"
date: 2007-11-15
forum: Networking &amp; Wireless
---

### Post by ImNeat on 2007-11-15
I am getting a connection error when connecting to Windows Vista (RDP connections enabled) from Ubuntu 7.10 (nxclient set to RDP).

The Linux nxclient provides this message and output:
*Connection Error*
Detail:
[I]NX> 203 NXSSH running with pid: 11806
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 10.10.10.107 on port: 3389[/I]

The firewall on the Windows RDP server (ZoneAlarm) logs no activity. 

The two machines are connected locally so I don't have any port forwarding enabled. Any suggestions as to what could be going wrong? I'm quite stumped...

---

### Post by atomkarinca on 2007-11-15
you can use terminal server client on gnome and krdc on kde. hit alt+f2 and type tsclient or krdc.

---

### Post by ImNeat on 2007-11-15
Yea I got tsclient working for the most part but I would still prefer to get nxclient working if at all possible.

---

