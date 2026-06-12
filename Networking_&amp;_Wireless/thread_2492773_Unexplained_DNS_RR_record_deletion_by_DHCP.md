---
title: "Unexplained DNS RR record deletion by DHCP"
date: 2023-11-22
forum: Networking &amp; Wireless
---

### Post by mfenton222 on 2023-11-22
Bind version: bind-9.11.4
ISC DHCP version: dhcp-4.2.5
 
I&#8217;m trying to track down what might have caused the deletion of the DNS Resource Records below. DHCP appears to have had DNS remove these records, but we can&#8217;t seem to find why.  Multiple devices were affected by this within 30 minutes of the first deletion below. In all cases it was almost exactly 1 hour from the DHCP renewal. Devices that were not affected had not yet renewed their lease. A reboot of the devices that had their records removed caused a new registration via DHCP. There was no repeat of the event after the reboots.
 
Our DNS & DHCP configurations are rather large so if someone wants to see a portion of them I can extract the relevant portions.
 
 
[B]*Nov 16 07:02:33 dns01a named[1326]: client @0x7fe08b195dc0 192.168.100.100#44766/key dhcpkey: signer "dhcpkey" approved*
[/B][I]**Nov 16 07:02:33 dns01a named[1326]: client @0x7fe08b195dc0 192.168.100.100#44766/key dhcpkey: updating zone 'services.site.local/IN': deleting an RR at cam13.services.site.local A**
**Nov 16 07:02:33 dns01a named[1326]: zone services.site.local/IN: sending notifies (serial 2021080336)**
[B]Nov 16 07:02:33 dns01a dhcpd: Removed forward map from cam13.services.site.local. to 192.168.70.31
Nov 16 07:02:33 dns01a named[1326]: client @0x7fe0780793c0 192.168.100.100#45224/key dhcpkey: signer "dhcpkey" approved
Nov 16 07:02:33 dns01a named[1326]: client @0x7fe0780793c0 192.168.100.100#45224/key dhcpkey: updating zone 'services.site.local/IN': deleting an RR at cam13.services.site.local TXT[/B]
Nov 16 07:02:33 dns01a named[1326]: client @0x7fe08b165e80 192.168.100.101#40854 (services.site.local): transfer of 'services.site.local/IN': IX FR started (serial 2021080335 -> 2021080336) [/I]
*Nov 16 07:02:33 dns01a named[1326]: client @0x7fe08b165e80 192.168.100.101#40854 (services.site.local): transfer of 'services.site.local/IN': IX** FR ended*
 
Things we have looked at and ruled out.
 
DHCP Lease time
DHCP Lease time is being set correctly (Min: 8 Hours, Default 24 Hours, Max 36 Hours)
 
DHCP Failover
We do have a failover pair, our MCLT is set for 1 hour, but the servers were in sync at the time of the deletion. In addition, there is no attempt in the logs for these devices attempting to renew an expired or expiring lease.
 
Rogue DNS/DHCP servers
No indication of another device handling DHCP Leases or registrations.

---

