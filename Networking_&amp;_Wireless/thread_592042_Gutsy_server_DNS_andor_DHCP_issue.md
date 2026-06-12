---
title: "Gutsy server DNS and/or DHCP issue"
date: 2007-10-26
forum: Networking &amp; Wireless
---

### Post by ikAt on 2007-10-26
Good day to all,

I'm experiencing a problem that I need some help with.

Situation:

Have followed the instructions from two great howtos in order to install a local DNS server using bind9 and a DHCP server using dhcp3-server.

Both services are up and running and as far as I can tell they are doing there job as I've instructed. Webmin which is also installed confirms this.

Problem:

Even though I can ping the server using it's hostname from any other workstation on the network, I cannot ping the workstations from the server via their hostnames. IP address ping works.

I know I can add the hostnames to the hosts file and that will of course work, but I'm sure that if my DNS server was running properly I should be able to do this without editing the hosts file. Obviously something isn't right with my DNS server.

If anybody can help me out here that would be much appreciated.

I understand you may need some more info from me, please ask away and I shall provide.

Thanks in advance,

ikat

Assume I know nothing as that is probably closer to the truth

---

### Post by conjur3r on 2007-10-26
You need to add "A" record entries into your DNS zone file for each of your internal computers.  Running a DNS server doesn't automatically allow you to ping any computer on your lan using its netbios name.  This is a Windows feature and handled by WIND on all windows computers.  I've tried automating it in the past but always gave up so maybe you're able to find a solution?

---

### Post by ikAt on 2007-10-26
Thanks for the quick reply.

That did work of course, but in terms of housekeeping it's about as effective as adding to the hosts file solution. It is however a step in the right direction and would work great if the host IP never changed. In a DHCP environment that is of course untrue.

There must be a way though. If Microsoft can make it happen I'm sure Bind can too.

The search continues. Maybe we can find the solution together, or maybe someone that already has it will accidentally come across this post and make our lives easier.

Regards,


ikat

---

### Post by twistedtwig on 2007-11-01
One thing I would check is your firewall.. It is possible that it is blocking it some how... drop all your rules test it.. then put them back up again.

Also you may get a better response in the server and security section (I have had some great help in the past there for this issue)

Where ever you post I would suggest posting all your bind files and your dhcp files so we can have a good look and see what is going on under the hood... 

what do you have in your /etc/hosts file?

lastly I would suggest looking at the logs... messages, error.log, etc see if you can find any clues there.

---

