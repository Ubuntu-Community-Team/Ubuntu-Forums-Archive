---
title: "Comcast and Linux?"
date: 2007-07-30
forum: Networking &amp; Wireless
---

### Post by Bartender on 2007-07-30
Took 2 PC's over to a guy's house.  He's got Comcast cable.  One PC loaded with Ub 7.04, the other PCLOS TR4.  
I've tweaked both of these installs (creating /etc/resolv.conf and such) so that they'd dial out with my external dial-up modem.  So whatever entries are made into resolv.conf so that dial-up works are there.

I unplugged the Comcast modem for a minute, then plugged it back in, jacked it into the Linux PC, and started the Ubuntu PC.  When I started Firefox I got a Comcast message saying that the os is not supported by their Install Wizard.  I think this message was coming straight from the modem, not from the internet (??)
Anyway, the PCLOS machine didn't do any better.  Called Comcast techie, he said he knows that Linux works but he can't give me any support.  Gave up and went home.
Before I go back and disturb this guy again I'd like to hear some suggestions.  Should I wipe any entries from /etc/resolv.conf?  Should I have left the Comcast modem off longer than a minute?  Maybe wait longer for it to reboot entirely?  Should I start up a Windows HDD and go thru the Comcast setup wizard, then switch to Linux?
I've got very little experience with networking stuff.  The few times I've hooked these PC's up to broadband they just worked without me having to do anything!

---

### Post by NilsE on 2007-07-30
This may not be conclusive but with Comcast at a family members home in NJ I was NOT able to connect to Comcast via their modem with my  cable plugged in.  It was a case where Comcast configures the system to the modem and it only appears to work on Windows with a web based utility. I think this has something to do with them being able to throttle the usage.

So, what I did was put a Linksys wireless router hard wired to the Comcast modem.  I then hard wired his Windows system to the back of the Linksys router and configured his connection.  Now the good part is once the PC was configured the Linksys router was also configured and got it's fixed IP address. After that other system including Ubuntu were able to connect to the router via wireless using the Linksys DHCP.

This may also work with a Ethernet Router that has DHCP capabilities but I did not try that and just left him the extra wireless router I happen to have with me.  He has since purchased a Belkin wireless router and it worked the same way.

---

### Post by Bartender on 2007-07-30
Hi, Nils -
Thanks for the reply.  While trolling the internet I found some other threads that indicated the same thing - get a router, get Comcast working, even if you had to do it with a Windows PC, then plug any Linux PC's into the router, not the modem.
I don't have a router and neither does he.  Will scrounge around for one.  Oughta be able to find a plain old wired router for cheap...

EDIT:  Did you have to use the manual address when setting up the Linux PC or did you let it get addresses automatically?

---

### Post by NilsE on 2007-07-30
> **Bartender said:**
> EDIT:  Did you have to use the manual address when setting up the Linux PC or did you let it get addresses automatically?

The Linksys router took the Comcast assigned IP address as it's IP address and assigned IP addresses in it's own range via DHCP to the later connected systems.  So no, I did not have to assign static IP's to anything.

You can get a Linksys wireless G router pretty cheap now on eBay that has both wireless and 4 wire connections. Then you have a choice or wired or wireless.

---

