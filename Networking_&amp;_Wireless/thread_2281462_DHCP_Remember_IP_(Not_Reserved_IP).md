---
title: "DHCP Remember IP (Not Reserved IP)"
date: 2015-06-07
forum: Networking &amp; Wireless
---

### Post by Jason_Hunter on 2015-06-07
I know how to setup reserved IP with dhcpd, but is there an option to make it remember IP (if it's available)?

Every time I boot up a device, it seems to get a different IP, even though the IP that it had before is available. 

I can set up each host with a reserved IP, but what I'm actually after is for the dhcpd to assign the IP it had before, as long as it's available and as long as it not too long ago that it had a specific IP. 

Is there such an option?

---

### Post by Bucky Ball on 2015-06-07
Unsure how you would do that. Why not use a static IP for each machine (which equates to pretty much the same as having a 'reserved' IP) and bypass DHCP completely? Set your DHCP server (presumably on the router) to serve IPs in a range, say between 192-168.0.100-110.

Open Network Manager on the local machine, go to the IPv4 tab and set the config method to 'Manual' rather than automatic. Plug in your details and use an IP address outside the range the DHCP server is set to serve, for instance a static IP of 192.168.0.111. Done.

---

### Post by SeijiSensei on 2015-06-07
Are you talking about isc-dhcp-server?  The simplest solution is to use long lifetimes for the leases.  From "man dhcpd.conf":
> The min-lease-time statement
min-lease-time time;

Time should be the minimum length in seconds that will be assigned to a lease.

A day is 86,400 seconds.  If you want the lease to remain fixed for a year, use "min-lease-time 31536000" (=365*86400).

---

### Post by Jason_Hunter on 2015-06-25
Thanks, SeijiSensei; I'll try that and report back;)

---

### Post by Doug S on 2015-06-26
I am a bit confused by this thread, because as far as I have ever experienced on my LAN the desired behavior is what happens by default anyhow.

Only when the IP address had to be re-used for a different device in between, does the /var/lib/dhcp/dhcpd.leases actually forget the previous assignment. It would only have been re-used if the pool was exhausted and expired leases were then looked at. I guess I am saying that a bigger pool might be all that is required. I guess I am also saying that Seiji's idea might result in a bigger pool being required anyhow.

---

