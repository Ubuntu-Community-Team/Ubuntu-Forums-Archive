---
title: "IP Address has been swapping after &quot;netplan apply&quot; command in ubuntu 20.04 version"
date: 2022-06-14
forum: Networking &amp; Wireless
---

### Post by kraishak on 2022-06-14
[COLOR=#000000]Hi all,[/COLOR]

[COLOR=#000000]I am using ubuntu version 20.04.o4(server edition) and I am facing the issue that my IP address is swapping between two or more IP addresses after executing "netplan apply". I am using ISC DHCP with 4.4.3b1(the latest version) in primary and failover mode. As part of packet capture analysis, I found a weird case the ubuntu client is sending the DHCP release packets for some trials, and for other trials, it is directly sending the discover packet bypassing the DHCPRelease packet.[/COLOR]

[COLOR=#000000]I observed that in the trials when it is sending the DHCPRelease it is swapping the IP address and for other trials where it is sending the Discover packets the IP address seems to be consistent from the DHCP server, I am a bit confused as to why does the ubuntu client will send the DHCPRelease some times and not for other trails, for the same command. Do we have anything like a concept of caching and timeout for it?[/COLOR]

[COLOR=#000000]If anyone has encountered the same issue and found the workaround or fix please let us know[/COLOR]

[COLOR=#000000]Thanks in Advance[/COLOR]

---

### Post by TheFu on 2022-06-14
We set static IPs for all our servers.  Never trust DHCP.

---

### Post by kraishak on 2022-06-14
Hi, 
But we have a required case where we have many VM's to spin up, the count is too large so we want to make it automatic instead of manual

---

### Post by TheFu on 2022-06-15
> **kraishak said:**
> Hi, 
But we have a required case where we have many VM's to spin up, the count is too large so we want to make it automatic instead of manual

If you are spinning up VMs, every enterprise VM creation tool I've ever seen supports seeding logins and IPs.  But since we seldom spin up more than 1 VM a week, we haven't bothered to automate that process in the installer.  We do it through ansible.

---

