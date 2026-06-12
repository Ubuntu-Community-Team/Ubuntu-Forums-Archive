---
title: "Setting up BIND for a Windows domain"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by Arceon on 2008-04-25
The title may imply i know what i'm talking about, don't be fooled :)

We're basically trying to setup a virtualized ubuntu box to act as a DNS server for our call center. This box would use openDNS to retrieve web pages for our call center, allowing the content to be screened. It must however, know the locations of our other network computers, to access shares etc.

So far i've been following this excellent guide:
[http://ubuntuforums.org/showthread.php?t=236093]("http://ubuntuforums.org/showthread.php?t=236093")

However, my eyes glaze over at the mention of NS, reverse DNS, and pretty much everything in the conf files :confused:

I've managed to setup bind and point to openDNS, as some sites are being blocked, indicating it is functioning correctly. However client computers take 5-10 mins to log on due to their only DNS server being the ubuntu box, which must mean its failing to find the main server (GPO fails to apply also).

If someone could post the contents of the conf files with an idiots guide (or just their contents if they've managed to do this themselves) it would be GREATLY appreciated :)

Some details if they help! :
MAINSVR (192.168.41.1.2) - Name of our Windows domain controller
UBUNTUSVR (192.168.1.129) - Name of our Linux box (virtual)
208.67.222.222,208.67.220.220 - OpenDNS servers
OVERDRIVE.local - Our domain name

Thanks in advance!

Joe

---

### Post by Arceon on 2008-04-28
No one? :(

I'm going to try and muddle through today, but if anyone could post anything at all it would be greatly appreciated :)

---

