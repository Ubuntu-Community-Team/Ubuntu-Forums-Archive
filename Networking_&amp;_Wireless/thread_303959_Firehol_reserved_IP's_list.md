---
title: "Firehol reserved IP's list"
date: 2006-11-21
forum: Networking &amp; Wireless
---

### Post by Bogaurd on 2006-11-21
Hi all, I'm writing a firewall using firehol.
Im using the inbuilt list of unroutable and reserved IP's, though sadly this list is out of date, and blocking hosts that I need to use.

Firehol's website says:

RESERVED_IPS
Description
This variable includes all the IP addresses defined as IANA - Reserved by IANA. The supplied get-iana.sh script creates this variable by directly fetching this document.

Doesnt look like the ubuntu firehol package comes with a copy of 'get-iana.sh' - anybody got a solution to this?
Thanks!

---

### Post by funkydan2 on 2008-04-27
In Debian based distros it's been renamed to just get-iana.  However, the script doesn't seem to work in Hardy.

--Edit:
It is easily fixed: [http://sourceforge.net/tracker/index.php?func=detail&aid=1929051&group_id=58425&atid=487692](http://sourceforge.net/tracker/index.php?func=detail&aid=1929051&group_id=58425&atid=487692)

---

