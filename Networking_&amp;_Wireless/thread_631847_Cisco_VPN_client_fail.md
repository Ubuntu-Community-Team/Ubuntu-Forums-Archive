---
title: "Cisco VPN client fail"
date: 2007-12-04
forum: Networking &amp; Wireless
---

### Post by knowledge_is_power on 2007-12-04
Had Cisco VPN client working before (VPN group p/w is encrypted so i cant just use network manager) perfectly, but intalled update for network man and now its telling me it cant enable the virtual adapter.  Im geussing this is cisco_ipsec and is enabled thru the included script vpnclient_init.
what do i do?
```

d00d@katmandu:~$ cd vpnclient
d00d@katmandu:~/vpnclient$ sudo ./vpnclient_init reload
Shutting down /opt/cisco-vpnclient/bin/vpnclient: Done
Starting /opt/cisco-vpnclient/bin/vpnclient: Done
d00d@katmandu:~/vpnclient$ sudo vpnclient connect pg_campus_wireless
Cisco Systems VPN Client Version 4.8.00 (0490)
Copyright (C) 1998-2005 Cisco Systems, Inc. All Rights Reserved.
Client Type(s): Linux
Running on: Linux 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Config file directory: /etc/opt/cisco-vpnclient

Initializing the VPN connection.
Contacting the gateway at 142.207.120.5
User Authentication for pg_campus_wireless...

Enter Username and Password.

Username [UNI\jorgense]: 
Password []: 
Authenticating user.
Negotiating security policies.
Securing communication channel.
Secure VPN Connection terminated locally by the Client
Reason: Failed to enable Virtual Adapter.
There are no new notification messages at this time.

```

---

