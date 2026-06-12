---
title: "networking issue (stopped working)"
date: 2005-06-02
forum: Networking &amp; Wireless
---

### Post by rubixDead on 2005-06-02
So far i have been running hoary hedgehog for about 3 months, with no issues, (well other than little stuff i can fix :P) 

But just yesterday when I booted up my network card failed (Well it said "Network Failed Name Recognition"). 

Anyway, I am relatively new to linux, not quite an expert but not fresh meat exactly, you might call me a casual linux user. 

Back to the issue, the network just stopped working, i couldnt connect to my router, couldnt connect to the internet, nothin, I checked all my cables, even re connecting all my cables, still to no avail. 

Is there anything I can do to reset/reinstall the network card, maybe i should be looking for new drivers. 

Oh and its an onboard NIC, i cant remember what motherboard it is (ill have to look when i get home). But if someone could give me somewhere to start, I would greatly appreciate it!

---

### Post by alastair on 2005-06-02
First things first ... check the system log.

Have a look through :

/var/log/syslog

from the time you boot. Look for network device probe/recognition, and driver load. Anything odd?

Also, for the device/interface configuration :

ifconfig -a
route -n

---

### Post by rubixDead on 2005-06-02
The only thing that seems odd to me in the /var/log/syslog is I get a series of these:

NETDEV WATCHDOG: eth0: transmit timeout
eth0: Tansmit timeout, status 00000005 00000000

as well as

no DHCPOFFERS received.
No working leases in persistent database - sleeping.

and if I run
ifdown -a
ifup -a

i get esentially the same thing.

Edit:

All right, after working on it on and off today, trying everything I have possibly come across relating to my problem,  it has GOT TO be a hardware issue, nothing I do makes any difference at all. BTW the onboard NIC I have is the SiS 900.

---

### Post by alastair on 2005-06-03
There should be other messages in the syslog (at least device probe/load) - worth a check.

Assuming the device is UP and configured i.e.

ifconfig -a
route -n

Then perhaps a cable, DHCP server issue? Hard to say. Perhaps you could verify the device by booting windows, knoppix etc.

---

### Post by rubixDead on 2005-06-07
Okay someone is going to have to explain this one.
I tried everything, changed to dynamic ip, static ip, changed cables, changed the router, all with no results. I started up earlier today still with no suck luck. I changed the fan out to a quiter one, and BAM internet works. I dont understand  :-? 

Anyway, works now, thanks for the tips alastair! :)

---

