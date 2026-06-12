---
title: "Networking stopped working :-("
date: 2006-10-06
forum: Networking &amp; Wireless
---

### Post by ArchibaldButtle on 2006-10-06
Hey gang,

So this morning I get into work and boot up my PC, only to find that networking (wired Ethernet) has stopped working.

I'm running Ubuntu 6.06, and have been installing all the updates as they come down.  The system has been running stably ever since I installed it some 3 months ago, with no networking problems until today.

I'm not an Ubuntu expert, so I'm at a bit of a loss as to how to resolve this problem.

The steps I've taken so far have been to replace the ethernet cable, plug it directly into the router (rather than the hub), and to reboot.  No joy there.  Other machines on the same network are working just fine.  This is a DHCP network - I have changed *no* settings at all, and can confirm that eth0 is still configured to use DHCP.  I have also attempted to disable and re-enable eth0 using the GUI network-admin also to no avail.

The errors I'm getting are Thunderbird reports "failed to conenct to server mail.<myhost>.com".  If I run "sudo ifdown eth0" I get the report "send_packet: Network is unreachable".  When I run "sudo ifup eth0" I get repeated "DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval x" (where x = 7, 18, 9, 13, 12, 2) followed by "No DHCPOFFERS received." and "No working leases in persistent database - sleeping."  Pings to the router result in "connect: Network is unreachable".

As I said, this computer was working fine on the network yesterday...  Any ideas as to what I should be checking?

---

### Post by ArchibaldButtle on 2006-10-06
A bit more info...

I have tried disabling ipv6 using advice found elsewhere on these forums by editing /etc/modprobe.d/aliases and rebooting to no avail.

I have also tried a static IP address.  When I do this I can ping machines on the same network, but DHCP does not work.  I also still cannot ping machines on other networks (I get "connect: Network is unreachable") and DNS also still fails.

I have checked "ifconfig /all" on this Windows PC I'm using - the gateway, DHCP, and DNS servers are all set to 192.168.1.1 (the router) and this machine is functioning perfectly.  It obtained its DHCP lease just an hour ago - after I had powered up my Ubuntu box, so this would seem to indicate that the DHCP server in the router is functional.  As far as I can tell besides having set my Ubuntu PC to a static address (192.168.1.79, which is definitely not used elsewhere) it has identical settings for gateway and DNS.

lscpi -v tells me that I'm running an "Intel Corporation 82801DB PRO/100 VE (CNR) Ethernet Controller (rev 81)".  As I said before, this machine has been working perfectly until today.

---

### Post by ArchibaldButtle on 2006-10-06
Just tried booting up using my old Ubuntu install CD.  Initially networking didn't work.  Trying a static address *did* work though.

I then proceeded to reboot the router.  Once it had restarted I changed the Ubuntu box to use DHCP, and browsing remained working.

Rebooting the machine so that it ran from the HD install of Ubuntu was not successful though.  Still no networking.  I changed its configuration from static to DHCP, still no joy.  Rebooted, and found that eth0 is coming up disabled.  It will "activate" but this takes a long time (about a minute) and doesn't actually work - "sudo ifdown eth0" reports that "eth0 not configured".  Similarly running "sudo ifup eth0" does a DHCPDISCOVER and fails to get an address.

:-(

The good news though is that a static address *is* now working.

So it seems that DHCP got broken in an update I downloaded yesterday.  Not sure why I didn't manage to get a static address to work earlier though.

---

