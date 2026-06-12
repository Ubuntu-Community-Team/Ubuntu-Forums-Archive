---
title: "samba shares"
date: 2008-11-28
forum: Networking &amp; Wireless
---

### Post by cezarica on 2008-11-28
Hi,

It's possible to have a certain share shown to a specific PC (based on IP/MAC) and a different one to another PC?

PC 1 can see share /home/stuff/pc1
PC 2 can see share /home/stuff/pc2
PC 3 can see share /home/stuff/pc1 and /home/stuff/pc2

is this possible in Samba?

---

### Post by olivesandtrees on 2008-11-28
Wouldn't it be much, much simpler and probably more secure to control share access at the user level?

user 1 can see share /home/stuff/pc1
user 2 can see share /home/stuff/pc2
user 3 can see share /home/stuff/pc1 and /home/stuff/pc2

Even if user 1 was on PC 2 he could still access his share etc... and even though the other users can see the other share they cannot access them.

It's really a much better solution.

---

### Post by cezarica on 2008-11-28
I got 3 Windows running PC's that browse a separate server share, as for that PC switching thing it doesn't happen, and to be honest I prefer that over having everyone to type in a user name/password.

---

### Post by olivesandtrees on 2008-11-28
It looks to me that you can only use IP addresses to allow and deny access to the Samba system as a whole (I.E. all SMB shares on a server).

> Limiting hosts

Another way that Samba will allow you to control who has access is to control the hosts from which they can connect. In fact, Samba has two ways of controlling access at a host level.

Pick the interfaces

If your Samba system has more than one network card installed, you can limit where Samba will answer requests. If, for instance, you have a network card installed on a private network and one connected to the public Internet because you’re also using the server for NAT, you can tell Samba to only answer requests from the private network.

This is done by setting the Bind Interfaces Only global attribute to Yes. This will tell Samba to only respond to requests on the interfaces that you specify. The next step is to specify the acceptable interfaces by adding an interfaces global attribute and specifying the interfaces to support. The interfaces attribute will accept the UNIX interface name or the IP address of the interface.

Allow hosts

The second way within Samba to control which hosts can get through is to use the Hosts Allow global attribute. This allows you to specify which hosts you want to allow access. This list of addresses can be address/subnet masks so that you can allow access to entire subnets at a time. For instance, if your private networks used the reserved Class A address (10.x.x.x), you could specify either 10. or 10.0.0.0/255.0.0.0 to allow any computer that is on the private network access to the Samba server.

As for typing in your user name and password for user level security, try setting your Linux user names and passwords to match their Windows counter parts exactly.  This should allow Windows to automatically authenticate itself to the SMB share the user has access to with no user input (it works best if you map a network drive to the SMB share).

---

