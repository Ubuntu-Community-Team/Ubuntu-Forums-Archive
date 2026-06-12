---
title: "DHCP Server Problem"
date: 2007-01-03
forum: Networking &amp; Wireless
---

### Post by terazen on 2007-01-03
Hi,
I'm using dhcpd3 for our dhcp server and am trying to get our windows xp clients to get a second DNS Search Suffix.  I've looked through the man pages and searched google and forums, but so far the only answer I've found is to try a setting like this in dhcpd.conf:
option domain-name "example.org example.com";

When I set it up this way neither suffix works.  I get this with ipconfig/all:
        DNS Suffix Search List. . . . . . : example.org example.com

Hardcoding the suffixes works and it looks like this:
        DNS Suffix Search List. . . . . . : example.org
                                                      example.com

I've tried typing it with commas and different things but I'm out of ideas.  Is there a different syntax to get it working with xp?  Any help would be so appreciated.

Thanks in advance!
Austin

---

### Post by linuchsan on 2007-01-03
option domain-name-servers  dns1, dns2;

---

### Post by terazen on 2007-01-03
Thanks for your post. I've got that option working already using the syntax you posted.  Sorry if I didn't post it clear enough the first time.

My problem is I'm having trouble getting the dhcp clients to have multiple domain suffixes in the DNS Suffix Search List.

For example if the pc is searching for a server named admin it'll search admin.example.com first then admin.example.org second.  Hope this helps!

---

### Post by terazen on 2007-01-04
I think I may have finally found the problem.  It looks like the dhcp server is right, but windows don't know how to interpret the information it's getting correctly.

[http://support.microsoft.com/kb/275553/en-us](http://support.microsoft.com/kb/275553/en-us)

---

