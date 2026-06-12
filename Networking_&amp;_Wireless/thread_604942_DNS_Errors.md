---
title: "DNS Errors"
date: 2007-11-06
forum: Networking &amp; Wireless
---

### Post by professorTHC on 2007-11-06
Hello there!:)
Im having some problems with my connection. Firefox seems to take way too long to load pages at first, but then surfing is fine. 

when i did a DNS test on DNSstuff.com i got some failures and warnings. ive tried googling it but to no avail, do you know how to solve these issues?

Number One:

FAIL Missing (stealth) nameservers FAIL: You have one or more missing (stealth) nameservers. The following nameserver(s) are listed (at your nameservers) as nameservers for your domain, but are not listed at the parent nameservers (therefore, they may or may not get used, depending on whether your DNS servers return them in the authority section for other requests, per RFC2181 5.4.1). You need to make sure that these stealth nameservers are working; if they are not responding, you may have serious problems! The DNSreport will not query these servers, so you need to be very careful that they are working properly.

ns6.yahoo.com.
ns8.yahoo.com.
This is listed as an ERROR because there are some cases where nasty problems can occur (if the TTLs vary from the NS records at the root servers and the NS records point to your own domain, for example).

Number Two:


FAIL Stealth NS record leakage Your DNS servers leak stealth information in non-NS requests:

Stealth nameservers are leaked [ns6.yahoo.com.]!
Stealth nameservers are leaked [ns8.yahoo.com.]!

This can cause some serious problems (especially if there is a TTL discrepancy). If you must have stealth NS records (NS records listed at the authoritative DNS servers, but not the parent DNS servers), you should make sure that your DNS server does not leak the stealth NS records in response to other queries.


Number Three:


WARN SOA MINIMUM TTL value WARNING: Your SOA MINIMUM TTL is : 600 seconds. This seems low (unless you are just about to update your DNS). You should consider increasing this value to somewhere between 3600 and 10800. RFC2308 suggests a value of 1-3 hours. This value used to determine the default (technically, minimum) TTL (time-to-live) for DNS entries, but now is used for negative caching.

---

### Post by noob12 on 2007-11-06
I don't think these are particularly bad; certainly the last TTL issue is not.  I doubt that they are causing the issue you are seeing.  

However you might want to try the OpenDNS servers and see if they behave any better.  If you are configuring your DNS servers manually you can just put in the addresses:

208.67.222.222
208.67.220.220

If you are getting them via DHCP, you can use the first section in this thread: [http://ubuntuforums.org/showthread.php?t=543659](http://ubuntuforums.org/showthread.php?t=543659)
as a guide.

---

### Post by professorTHC on 2007-11-06
awesome, thanks

---

