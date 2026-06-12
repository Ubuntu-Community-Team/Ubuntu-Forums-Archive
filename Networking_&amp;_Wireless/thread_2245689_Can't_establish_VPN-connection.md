---
title: "Can't establish VPN-connection"
date: 2014-09-25
forum: Networking &amp; Wireless
---

### Post by chris137 on 2014-09-25
Hi,
suddenly my VPN-connection does not work anymore.
I use hide.me and it definitely worked yesterday or the day before!
I made no changes (well.. not intentionally..) on my network configuration.
Trying to activate the connection via the network manager gives me no response at all.
Here is what I get for nmcli con up id VPN
```
Error: Connection activation failed: no valid VPN secrets
```
When running that command a few times in a row I get these:
```
Error: Connection activation failed.
```
```
** (process:9313): WARNING **: Could not create object for /org/freedesktop/NetworkManager/ActiveConnection/40: Method "GetAll" with signature "s" on interface "org.freedesktop.DBus.Properties" doesn't exist
Error: Connection activation failed: Creating object for path '/org/freedesktop/NetworkManager/ActiveConnection/40' failed in libnm-glib
```

---

### Post by rose5 on 2014-09-26
The problem seems to be, that your password in keyring is not accessible.
A solution is to open file** /etc/NetworkManager/system-connections/ConnectionName** and set the
```

password-flags=0
```

and add the below lines to the file

 [HTML][vpn-secrets]
 password=YourPassword[/HTML]

Hope it could help.

---

### Post by chris137 on 2014-11-06
Hi
since my problem disappeared like it appeared I forgot to write.
Now I got something similar again:
```
Error: Connection activation failed the vpn service failed to start
```
Using nmcli con up id CA again I get the same message.

syslog looks like this:
```
Nov  6 17:41:44 knix NetworkManager[5259]: <info> Starting VPN service 'pptp'...
Nov  6 17:41:44 knix NetworkManager[5259]: <info> VPN service 'pptp' started (org.freedesktop.NetworkManager.pptp), PID 5579
Nov  6 17:41:44 knix NetworkManager[5259]: <info> VPN service 'pptp' appeared; activating connections
Nov  6 17:41:44 knix NetworkManager[5259]: <info> VPN plugin state changed: init (1)
Nov  6 17:41:44 knix NetworkManager[5259]: <info> VPN plugin state changed: starting (3)
Nov  6 17:41:44 knix NetworkManager[5259]: <info> VPN connection 'CA' (Connect) reply received.
Nov  6 17:41:44 knix NetworkManager[5259]: <warn> VPN connection 'CA' failed to connect: 'pppd-Binärdatei konnte nicht gefunden werden.'.
Nov  6 17:41:44 knix NetworkManager[5259]: <info> Policy set 'Tahiti' (eth0) as default for IPv4 routing and DNS.
Nov  6 17:41:44 knix NetworkManager[5259]: <warn> error disconnecting VPN: Could not process the request because no VPN connection was active.
Nov  6 17:41:49 knix NetworkManager[5259]: <info> VPN service 'pptp' disappeared
```
I think the important part is "pppd-Binärdatei konnte nicht gefunden werden"
I could not find anything on google so I cannot translate it either.
Means something like 'binary-file could not be found"

Any ideas on that?
Since there seem to be random issues with that I reinstalled pptp and rebooted multiple times but it still occurs.

---

