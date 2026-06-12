---
title: "Did I lose my onboard networking?"
date: 2007-06-14
forum: Networking &amp; Wireless
---

### Post by Fraoch on 2007-06-14
Last night there was a 1-second power failure.  The last time this happened my motherboard blew something...this time I believe I lost my onboard networking.

I put in a spare NIC I had lying around and after a little futzing, I'm back up.

However, did I really lose my onboard NIC?  The network applet was very unstable even before this, could something have happened on the software front?

I'm using the networking applet with a static IP configuration.  As I indicated, it's very unstable.  In order to lock it up, all I have to do is try to select another saved "location" from the pull-down list or select the "Hosts" tab and the app freezes with one core of my dual-core CPU pegged at 100%.

I would do this from the command-line if possible, but I didn't know the appropriate commands.

The symptoms after the power failure but before the replacement NIC installation: no networking at all, no Internet data, no DNS resolution, no ping, no LAN networking, nothing.  ifconfig indicated the interface was up with the proper IP and MAC address.  The networking applet, such as it was, indicated the same as it always did and operated the same as it always did.

If I truly did lose my onboard networking, could it have been possible to bring up the interface with the proper IP and MAC address?  My router indicated a good connection too.

Also, configuring my replacement NIC wasn't problem-free either.  It did come up as eth1 as expected since the onboard was eth0.  But when I went to give it a static IP address, the network applet suddenly indicated it was disconnected and there was no networking activity after that.  I configured the rest of the networking applet (IP address, subnet mask, gateway, DNS) without any change.  When I rebooted, suddenly everything was up again.

Should I have given up on the onboard networking?  Was it a networking applet issue?  How can I resolve it - any command-line tools worth studying up on?

Thanks.

---

### Post by Fraoch on 2007-06-18
So - no one has any ideas?

Would my onboard networking be dead if Ubuntu assigns it an IP address, lists a proper MAC address and indicates networking is up?

---

### Post by charleseddy on 2007-06-18
That doesn't sound like a nic problem to me, really.  One thing to check is the file /etc/network/interfaces.  See if everything looks fine there, then let me know through this thread.

---

### Post by Fraoch on 2007-06-18
Thanks for the response.  I also recently updated the hosts file and, in addition to that, it looks like Adblock Plus added a whole whack of stuff on it all on the first line, so much so that gedit can't edit that line.  Perhaps networking didn't like that so much - as I indicated, the replacement NIC didn't work right away either.

---

### Post by charleseddy on 2007-06-18
Yeah, that sounds like a problem.  Go alt+f2 --> gksudo gedit.  Then see if you can remove those lines.

---

