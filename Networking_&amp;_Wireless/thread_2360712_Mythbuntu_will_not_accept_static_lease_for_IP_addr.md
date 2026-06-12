---
title: "Mythbuntu will not accept static lease for IP address"
date: 2017-05-07
forum: Networking &amp; Wireless
---

### Post by Yippee38 on 2017-05-07
I am running Mythbuntu based on Ubuntu 16.04.2 LTS.  My home network has always used static IP addressing.  However, I now have a work device and my wife has several work devices that require DHCP.  To attempt to simplify my network setup I've decided just to run with DHCP and assign static leases for IP addresses for the PCs in the house.  Having the PCs on a static lease makes running a lot of software much simpler (like games and MythTV).  My router is a Netgear wndr3700v2, and it has DD-WRT on it.  I set up the static leases to be with the first 98 addresses (.1 is the router, and 100 starts the DHCP range).  I've got six PCs on my network, 4 desktops and 2 laptops.  Both laptops and 2 of the desktops are running Windows 7.  One of the desktops is running OpenSUSE Leap - my HTPC frontend.  My HTPC backend is running Mythbuntu.  It is the only PC that will not accept the static lease.  It keeps taking .102, and I can't figure out why.

I've verified the MAC address several times.  In fact, I've copied the MAC address from running ifconfig -a and pasted it into the Static IP Lease screen on the DD-WRT services page on the same computer.  I've tried restarting both the router and the PC.  I've changed the lease time to 10 minutes, shut down that PC for 1/2 hour, then restarted it.  I've tried emptying and deleting /var/lib/dhclient.leases.  I've also tried deleting the network setup and starting from scratch on the setup.  Nothing makes a difference.

Does anybody have any ideas why Ubuntu would not be accepting a static lease IP address?  I figure there has to be a file lurking somewhere that's looking for that .102 address that I don't know about.

---

### Post by The Cog on 2017-05-07
Can you try the commands
```
sudo dhclient -r -v
sudo dhclient -v
```
to release the existing lease and then request another lease. Post the output here.

---

### Post by Yippee38 on 2017-05-07
```
:~$ sudo dhclient -r -v
<copyright stuff>

Listening on LPF/eth0/bc:5f:f4:bf:6b:59
Sending on   LPF/eth0/bc:5f:f4:bf:6b:59
Sending on   Socket/fallback
```

```
:~$ sudo dhclient -v
<copyright stuff>

Listening on LPF/eth0/bc:5f:f4:bf:6b:59
Sending on   LPF/eth0/bc:5f:f4:bf:6b:59
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 (xid=0xa4842827)
DHCPREQUEST of 10.6.2.102 on eth0 to 255.255.255.255 port 67 (xid=0x272884a4)
DHCPOFFER of 10.6.2.102 from 10.6.2.1
DHCPACK of 10.6.2.102 from 10.6.2.1
RTNETLINK answers: File exists
bound to 10.6.2.102 -- renewal in 261 seconds.
```

Based on that, it looks like the machine is requesting .102, and the router is giving it.

---

### Post by The Cog on 2017-05-07
Hmm. Odd. It didn't do a DHCPRELEASE when it was told to. But then, even after doing a dhcp release on my laptop, the next dhcp request asks for the same address again, so I don't think we have actually proved anything of significance here. I think it is just asking for a repeat of the same address it was allocated last time. I don't know how to stop it doing that.

---

### Post by Yippee38 on 2017-05-08
I figured it out, and the solution is stupidly simple.

Apparently, for some reason, on this machine only, the MAC address is case sensitive.  I set it to lower-case, and suddenly, it works.  Very strange.

---

### Post by Yippee38 on 2017-05-08
Just a quick update for anybody else having this problem.  Apparently, this is not a Ubuntu problem, but a problem with DD-WRT.  After fixing my Mythbuntu system, I discovered today that my OpenSUSE system was not assigned correctly.  I changed the case, but that didn't help.  Finally, I did what I did on my Mythbuntu machine; I removed the static lease for that device, then re-entered it.  Then it worked.

So if somebody else runs into this problem, remove the device from your static leases, then re-add it.

---

### Post by The Cog on 2017-05-08
Good to remember. Thanks for the fix.

---

