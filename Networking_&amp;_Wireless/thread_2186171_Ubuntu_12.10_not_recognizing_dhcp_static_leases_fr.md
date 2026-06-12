---
title: "Ubuntu 12.10 not recognizing dhcp static leases from router"
date: 2013-11-06
forum: Networking &amp; Wireless
---

### Post by bhweb on 2013-11-06
I have a machine running Ubuntu 12.10 and Windows 7.  In my Buffalo router running dd-wrt (came stock from Buffalo that way), I have setup a static lease for this computer to use ip address 192.168.123.47.  When booting Windows, there is no issue and the computer gets the proper IP.  When booting to Ubuntu, it always just gets the first available dhcp address, not the reserved address.  Of course it's the same mac address for both OS's and the hostname is the same, though I don't think the router cares about the hostname.  I run in Ubuntu most of the time and I've tried clearing all the dhcp lease files and restarting the networking as well as the router, but it still won't get the proper address.  This isn't isolated to this machine.  Seems most of my other Ubuntu machines have a similar issue.  My usual workaround is to just set the Ubuntu machine to a static ip that matches the dhcp static lease, however, that's causing another problem on this machine with ssh connections getting a write failed broken pipe error (that problem needs to be addressed in another thread).

So, I really need the static leases to work, but can't figure out why they are not.

---

### Post by TheFu on 2013-11-06
I use DHCP reservations with Ubuntu 12.04 all the time. Never had any issues at all.
What do the log files show?  On Linux, always start with the log files - always.  

You are lucky to have dd-wrt - so you can look at the log files on the router too. What do those show? You'll need to ssh into the router - the web interface doesn't show what you need.

If my memory is correct, there are 2 parts to setting up static leases on dd-wrt - the MAC-IP part and the IP-DNS part. Both are on the same tab on the router GUI.  On the client PC side, only "use DHCP" is necessary.

---

### Post by bhweb on 2013-11-07
I found the problem.  I looked at the lease file created in /var/lib/dhcp.  Though I had looked at it before, I didn't notice that there were 2 dhcp servers listed.  Turns out I had a NAS box on my network that somehow got it's dhcp server turned on.  So my Ubuntu computers were actually getting their ip addresses from the NAS instaed of the router.  DOH!

---

### Post by Bucky Ball on 2013-11-07
Just throwing this in for interest ... I go about it slightly differently. I allow the router to serve DHCP in a range, for example 192.168.0.100-110, so guests can connect easily, then set the static IPs for each computer outside of that range on the computer itself using Network Manager (they are all setup from 192.0168.0.1-10). ;)

---

### Post by TheFu on 2013-11-07
Thanks for sharing the root cause.  Could happen to anyone.

DHCP reservations for semi-static IPs should be outside the normal DHCP ranges for ad hoc clients.  I've seen people use 1-50 for static IPs, 60-100 for DHCP reservations and 200-254 for ad hoc DHCP clients.  Makes it easier to easily see when a device is inside the wrong range.

Think I will move my static leases to a specific range. After all, the devices in those are portable and their IPs change when outside the normal network.

Again, thanks for sharing the solution.

---

