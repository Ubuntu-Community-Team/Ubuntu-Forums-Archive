---
title: "network printing through windows"
date: 2007-05-18
forum: Networking &amp; Wireless
---

### Post by MacD on 2007-05-18
I am on a university campus.  I am trying to print to printers through a windows XP box in the same room.  This print server has printer sharing enabled, and printing is possible over the network from windows machines.   I connect to the network through a wired connection and static IP.

There are about 70+ other windows machines on this subnet.

If I try to add new printer- network printer - windows printer (smb)... I get a string of popups asking to authenticate to other machines on the subnet- but it never gets to the print server I want to work through.

If I do findsmb from terminal- I see all the machines on the subnet including this server of interest.

If I do smbtree from terminal- I see directories on many machines on the subnet- but see something to the effect of "NT access denied" for my print server and many other machines.

I am able to access files on the print server via smb://name

Is there are config file where I can just manually enter the IP & queue for this print server?

Alternatively I have also tried setting it up as IPP with the URI:  [http://ipaddy:631/printers/name](http://ipaddy:631/printers/name) (with the right names)  and I opened port 631 on the windows firewall. No luck- "network host is busy"

any ideas?

---

