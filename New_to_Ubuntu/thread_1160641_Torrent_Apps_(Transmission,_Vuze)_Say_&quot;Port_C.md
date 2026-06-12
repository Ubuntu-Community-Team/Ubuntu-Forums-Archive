---
title: "Torrent Apps (Transmission, Vuze) Say &quot;Port Closed&quot;???"
date: 2009-05-15
forum: New to Ubuntu
---

### Post by Noobs*McGee on 2009-05-15
Hey guys,

So, I'm a brand new convert to the Linux (Ubuntu) community.  I'm totally new to Linux (in any form) but I've heard good things about it and I decided to request a cd for Jaunty Jackalope from the Ubuntu Linux/Canonical website when it released.  I tried it out as soon as I got it, and loved it, so I installed it alongside XP on my Toshiba Satellite notebook.  After a short time I realized I could do everything (and more) on Ubuntu that I could do on XP, much more effeciently and with fewer headaches, so I decided to just do a clean install of Ubuntu.  And so far, I haven't regretted it for a second :).  Everything seems to run significantly faster, and I'm very satisfied with the ease of use of the OS.

The only issue I've encountered so far has to do with downloading torrents.  I tried out Transmission BitTorrent Client when I first installed, and I was able to run downloads, but the transmission speed was very slow and kept dropping off at random intervals.  I checked the settings and under the "Network" tab in "Preferences" and it said the "Listening Port" was "closed", so I tried fiddling with that, but every port I tried gave the same result.  I thought it might be a problem with Transmission itself, so I decided to download another client (I went with Vuze from Azureus).  After setting Vuze up, however, I got the same result: every port I tried under "Connection" in the settings came back as "closed" when I ran the NAT/Firewall test.

This is really confusing to me, because I have port forwarding configured on my router, and it worked perfectly on XP, but for whatever reason it doesn't seem to want to work on Ubuntu.  I don't know anything about IPTables or firewalls or whatever in Ubuntu.  Is there something I need to change to get this working properly?  Any help is much appreciated.

Thanks.

P.S. I'm not exactly a tech guru, and my understanding of/familiarity with command line interfaces and so forth is pretty limited, but I'm learning, and so far it hasn't been an issue since Jaunty Jackalope has such an intuitive interface.  But please keep this in mind when providing help and instructions, as I'll probably need a fairly step-by-step guide.

---

### Post by mikewhatever on 2009-05-15
Let me start by saying that you don't have to iptables, since no rules are engaged.
First, you need to check that the correct port is selected for Transmission, that is, the same port you got forwarded in the router. If that doesn't fix it, check the IP address the port is forwarded to and the IP address the computer has. They have to be the same too.

---

### Post by lovinglinux on 2009-05-15
Possible scenarios I can think of:

1 - The port forwarded from your router is not the same as the one used in the torrent client

2 - The network manager is configured to get the IP automatically from the router using DHCP and the IP is different from the one you are port forwarding to. If this is the case, then use a static IP, by configuring your connection manually in "System >> Preferences >> Network Manager"

3 - If you installed any firewall manager like Firestarter or UFW, then the port might be closed by iptables rules. If you didn't install anything like that and didn't change iptables settings, then this is not the cause of the problem

4 - The address used to test the port in the torrent client might be down or being blocked by the torrent client blocklists or by system wide ip filters like moblock or iptlist.

Anyways, visit [http://www.pcflank.com/scanner1.htm](http://www.pcflank.com/scanner1.htm) and test if scanner can reach the port used by the torrent client. If the result is "Stealth", then you have a problem with the port forwarding or firewall.

---

### Post by Noobs*McGee on 2009-05-15
Thanks for the responses guys, but I think I fixed the problem.  I think it had something to do with my router not forwarding properly, though I'm not sure why :confused:

> **mikewhatever said:**
> First, you need to check that the correct port is selected for Transmission, that is, the same port you got forwarded in the router.

As I said before, I had my torrent client on my XP setup (uTorrent, incidentally) working perfectly with port forwarding set up from my router.  The first thing I did upon setting up Vuze in Ubuntu was to ensure that the proper listening port was selected.  This wasn't the problem.

> **mikewhatever said:**
> If that doesn't fix it, check the IP address the port is forwarded to and the IP address the computer has.

One of the first things I thought of (before I even posted) was to check and make sure that my router was forwarding to the correct IP.  I checked my router page from my laptop (I'm connected via wireless) and it listed my computer with the new name I had assigned when I installed Linux as well as a new IP address.  "Aha!" I thought, and went to the port forwarding config page to fix the problem.  But even after I adjusted the IP address being fowarded to, I encountered the same problem (slow torrent speeds and NAT/Firewall test said the port was closed).  That's when I decided to post here, figuring it must be something to do with the configuration of Ubuntu.

Anyway, in the interim, I decided to remove the port forwarding configuration on my firewall and set it up all over again, just for the heck of it.  I did this, then refreshed my wireless connection on my laptop (turned off wireless via the panel icon, then turned it back on), and voila :popcorn:, NAT/Firewall test came back "OK" and torrent speeds improved.  Not sure what exactly made the difference, but there you have it.

P.S. lovinglinux, thanks for the link to the scanner, that's a pretty neat tool ;).

---

### Post by Noobs*McGee on 2009-05-16
...interestingly, now Pidgin is no longer working properly (it was working fine before I started fiddling with Vuze).  Not sure if this is related to the other problem (since I'm not sure what the other problem was).  I'll start a new thread and link back here I guess...

---

