---
title: "kvpnc always times out using when run in VMware Server"
date: 2008-07-03
forum: Networking &amp; Wireless
---

### Post by cpudney on 2008-07-03
G'day,

I'm running the following virtual machine set-up:

VMWare Server 1.6
Host: Windows Vista
Guest: Ubuntu 8.04 (Hardy Heron)

I use the Ubuntu guest VM to connect to a Cisco VPN Gateway.

I can connect successfully if I use the Cisco VPN client **vpnc** (from the command-line).

However, I prefer to use the GUI front-end **kvpnc**.  Whenever I try to connect using this kvpnc I get the following error message dialog:

[INDENT][I]Timeout while connecting to ###.###.###.### (XXXX) after 0s. Please check if the VPN server is reachable and the settings (UDP/TCP, local port, UDP encapsulation port) are correct. Maybe the timeout must be increased too.
[/I][/INDENT]

with the following in the kvpnc console:

*[INDENT]error: Timeout while connecting to ###.###.###.###. vpnc connect process will be killed.![/INDENT]*

Googling for this error message suggests setting the timeout to 60sec and restarting Ubuntu.  I've tried this without success.

I also have Ubuntu 8.04 running outside VMware and use kvpnc with the same settings without any problems.  This suggests the problem is a combination of **using kvpnc with a VM**.

Any suggestions gratefully appreciated.

Thanks,
Chris.

---

### Post by cowmix on 2008-07-15
BUMP!

I'm having the same problem from two installs of 8.04.1.



> **cpudney said:**
> G'day,

I'm running the following virtual machine set-up:

VMWare Server 1.6
Host: Windows Vista
Guest: Ubuntu 8.04 (Hardy Heron)

I use the Ubuntu guest VM to connect to a Cisco VPN Gateway.

I can connect successfully if I use the Cisco VPN client **vpnc** (from the command-line).

However, I prefer to use the GUI front-end **kvpnc**.  Whenever I try to connect using this kvpnc I get the following error message dialog:

[INDENT][I]Timeout while connecting to ###.###.###.### (XXXX) after 0s. Please check if the VPN server is reachable and the settings (UDP/TCP, local port, UDP encapsulation port) are correct. Maybe the timeout must be increased too.
[/I][/INDENT]

with the following in the kvpnc console:

*[INDENT]error: Timeout while connecting to ###.###.###.###. vpnc connect process will be killed.![/INDENT]*

Googling for this error message suggests setting the timeout to 60sec and restarting Ubuntu.  I've tried this without success.

I also have Ubuntu 8.04 running outside VMware and use kvpnc with the same settings without any problems.  This suggests the problem is a combination of **using kvpnc with a VM**.

Any suggestions gratefully appreciated.

Thanks,
Chris.

---

