---
title: "[SOLVED] wireless connection works for Pidgin, not aMSN"
date: 2008-01-12
forum: Networking &amp; Wireless
---

### Post by scradock on 2008-01-12
Hi all - can anyone help with a novel and very annoying problem?

I've been running Gutsy 32-bit with my Broadcom wireless connection since July. In the last couple of weeks something changed, and neither aMSN nor Google Earth can log-in.

The connection comes up, but some step in authentication fails. On the other hand, Pidgin logs in fine to the same MSN account, and Firefox connects to all known web-sites.....

iwconfig shows the wireless connection on eth1, with traffic stats.

Any ideas?

---

### Post by ebutton on 2008-01-12
If I read you correctly, your wireless network is not the problem.  That is, you've proven that your wireless connection is doing correctly everything that it is supposed to do.  The network layer is analogous to a "connection conduit".  It doesn't "care" what ports and protocols pass back and forth through the conduit.  And it can't pass all of those authentication and data transport protocols for one application and not for another application.

If I've misunderstood the symptoms, please forgive and ignore me.

Regards,
EdB

---

### Post by scradock on 2008-01-13
You're right, of course. That's why this is so annoying. One program suddenly stops working - OK, program problem.... but TWO? I've re-installed aMSN, upgraded Google Earth, but they continue to fail at the stage of connecting to a server. It's as if the system got its firewall rules changed without telling me. I don't know anything about a firewall program running in a default Gutsy install - I have a router that is very effective as a firewall, so I don't feel a need for one.

And of course, the two programs work fine with a different install on the same machine. How can I check if there are ports that have been blocked by some recent update? I can compare config files between Gutsy and Hardy on the same machine, for instance - I just don't know what to look for.

Any help much appreciated............

---

### Post by scradock on 2008-01-15
The mystery is solved!

I was using a "hyper-cautious" hosts file in my Gutsy 32-bit system, and some time recently it appears MS  started to require connection to ad-servers that were being blocked as part of the log-in procedure for their "free" service (Messenger Live). I suspect Google has done the same for Google Earth. Now it's just a matter of finding which particular servers they are requiring me to log in to, and deciding whether I'm prepared to do that to use the service.

For now, stripping out the majority of the ad servers from my hosts file allows me to connect.

Further experimenting suggests it may not be specific servers being banned, but the sheer size of the hosts file - adding more than a few dozen banned servers causes the two services mentioned (MSN Messenger via aMSN and GoogleEarth) to be unreachable. So maybe it isn't a conspiracy after all, just a mismatch between the login procedures and an enormous hosts file.....

---

