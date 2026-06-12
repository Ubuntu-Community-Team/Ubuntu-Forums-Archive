---
title: "Can't see my server on IP scan"
date: 2020-04-11
forum: Networking &amp; Wireless
---

### Post by stevermann on 2020-04-11
I have two Intel NUCs on my local network with Ubuntu installed on both.
I also have a few dozen other devices on my local net, PC's, tablets, IOT devices, a network LAN, a couple of Raspberry Pi's and a Debian server.
From the PC, I run an IP Scan, and I can see the first NUC and all 60 of the devices on my LAN, but not the second NUC.
I can ping it, and from the second NUC, I can ping other devices on my LAN.

I don't know if this is related or just a data point:
On the first NUC which does show up on the IP scan, the command arp -a also shows everything on the LAN.
On the second NUC, arp -a only shows itself and two of my PC's.

I installed Samba to share a disk on the NUC with Windows, but the Windows PC can't connect by hostname.  IP, yes, but not hostname. (Remember, the second NUC doesn't show in my IP scan).

Can anyone give me hint what might be wrong with my second NUC?

Thanks

---

### Post by TheFu on 2020-04-12
How are you handling name resolution on the LAN?  
[LIST]
[*]DNS local server?
[*]/etc/hosts?
[*]ZeroConf?
[/LIST]
At least 1 of those methods must be setup on each system/device.
Allowing random ip assignments on a LAN with that many devices is a bad idea.

---

### Post by stevermann on 2020-04-12
Thanks for the tip.  I used to be a fan of static IP's until I had a conflict, so now I let my router handle fixed leases based on the MAC address.
Your post got me to think again about my installation.  As I said, this is my second NUC and the installation was otherwise identical to the first.
Almost.
I had set my first NUC to a static lease in my router, but I was allowing the router DHCP to assign the IP for the second NUC.  When I set  the IP to a static lease, the server now shows in the IP Scan (Advanced IP Scanner).  It is also visible to Windows File Manager by the hostname.

I thought this odd because every other device where I let the Router handle the IP over DHCP shows up with a hostname on IP Scan.

---

### Post by TheFu on 2020-04-13
> **stevermann said:**
> Thanks for the tip.  I used to be a fan of static IP's until I had a conflict, so now I let my router handle fixed leases based on the MAC address.
Your post got me to think again about my installation.  As I said, this is my second NUC and the installation was otherwise identical to the first.
Almost.
I had set my first NUC to a static lease in my router, but I was allowing the router DHCP to assign the IP for the second NUC.  When I set  the IP to a static lease, the server now shows in the IP Scan (Advanced IP Scanner).  It is also visible to Windows File Manager by the hostname.

I thought this odd because every other device where I let the Router handle the IP over DHCP shows up with a hostname on IP Scan.

I've had a failed DHCP server take down an entire subnet after a patch session and reboot.  Never again.  It is fine when desktops can't get an IP. Not a problem, but when servers cannot, that's unacceptable.  I know lots of businesses and server admins are trained to use DHCP reservations because it often addresses both IPs and DNS centrally.  On a non-Windows, home, network, the router would usually handling those things, if it does DNS at all.  

Lots of people are deploying pi-hole DNS systems in their homes to block content and advertisements. Actually, think I want to move mine from a VM into an LXD container.  Hummmm.

BTW, it isn't clear to me whether the issue is solved or not.  If it is, please help the community by using the "**Thread Tools**" button and mark it so.  This helps people seeking answers AND helps people wanting to help not to waste their time.

---

