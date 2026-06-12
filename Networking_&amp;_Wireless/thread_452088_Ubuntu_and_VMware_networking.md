---
title: "Ubuntu and VMware networking"
date: 2007-05-22
forum: Networking &amp; Wireless
---

### Post by 5horizons on 2007-05-22
HI there,

I've got a nice setup at work, using Ubuntu 6.06 as the server and VMware server running lots of virtual machines (several Linux and Windows).

I have Samba running on the Linux host, which works great.  Mounting a share from the Linux host to a Windows guest works fine when the firewall (firestarter) is off.

However, when my firewall (firestarter) is on it seems to be blocking connections from vmnet8 (nat networking).  This means I'm not able to mount the Linux host SMB share in any of the virtual machines.

So the firewall is clearly blocking the SMB ports on this vmnet (vmnet8, since its NAT) network.  This is confirmed by using nmap in one of the VMware images, scanning the Linux host.  Vmnet8 has IP's of 172.16.121.0-255, 172.16.121.1 being the Linux host.

Firestarter is a nice simple firewall GUI, and I'd like to keep using it if possible.  There are scripts called 'user-pre' and 'user-post'.  I'd like to stick an iptables rule in user-post to open up the vmnet networks internally.

What iptables command would I use to open up this vmnet8 (possibly vmnet0, and vmnet1) to allow traffic to and from these virtual machines and the Ubuntu host?

Thanks,
Chris

PS: I tried using guarddog, but it crashed on me - leaving my machine virtually unusuable.  I'd like to stay away from it.

---

### Post by 5horizons on 2007-05-23
I managed to find a relaitvely easy way to get it working.

- I changed the 'local network connected device' to vmnet8 in Firestarter.

- I then added a rule so Samba (ports 137-139 and 445) would be shared for all IPs in the vmnet8 range (in my case 172.16.121.1/24).

This seems to do the trick quite nicely, now I have a user friendly firewall GUI and useful VMware virtual machines mounting my shared paths.  Cool!

Cheers,
Chris

---

