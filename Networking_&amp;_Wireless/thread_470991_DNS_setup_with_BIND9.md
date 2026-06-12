---
title: "DNS setup with BIND9"
date: 2007-06-11
forum: Networking &amp; Wireless
---

### Post by squinter on 2007-06-11
Hi all,

I've setup DNS server in my Ubuntu machine following this [thread]("http://ubuntuforums.org/showthread.php?t=236093") and this [thread]("http://ubuntuforums.org/showthread.php?t=469147&highlight=Ubuntu+DNS+server").

It's working locally but when I test the DNS through [http://www.ip-plus.net]("http://www.ip-plus.net"), I got this report:

Domain example.com, DNS server 233.233.10.9

Check if the server "233.233.10.9" is configured for "example.com" ... ok.

Check SOA Record ...
Server: 233-233-10-9.cable.someisp.net
Address: 233.233.10.9

Query about example.com for record types SOA
Trying example.com ...
example.com      	38400	IN	SOA	ns1.example.com admin.example.com (
			2006081401	;serial (version)
			28800	;refresh period (8 hours)
*** WARNING *** Refresh 28800 , use recommended value "10800"

			3600	;retry interval (1 hour)
			604800	;expire time (1 week)
			38400	;default ttl (10 hours, 40 minutes)
*** WARNING *** TTL 38400 , use recommended value "86400"


Check NS Records ...
Server: 233-233-10-9.cable.someisp.net
Address: 233.233.10.9

Query about example.com for record types NS
Trying example.com ...
Query done, 1 answer, authoritative status: no error
example.com      	38400	IN	NS	ns1.example.com
ns1.example.com is primary nameserver
Additional information:
ns1.example.com  	38400	IN	A	233.233.10.9
Found IP address "233.233.10.9" for server "ns1.example.com"
*** ERROR *** At least two nameservers are required.

Check SOA Record for Consistency on all Servers  ...
*** WARNING ***  !!! example.com has only one nameserver ns1.example.com

example.com      	NS	ns1.example.com
ns1.example.com	admin.example.com	(2006081401 28800 3600 604800 38400)


Check Zone Transfer
This may take a while, please wait ... /opt/wwwtools-1.0/checkdom/hostsqs  -Z -a -l -v -A -G -D -S   -P 233.233.10.9 example.com 233.233.10.9 2>&1
 done.
*** ERROR *** 233.233.10.9 (233-233-10-9.cable.someisp.net) connect: Connection timed out


2 errors found in "example.com" please correct
3 warnings found in "example.com"

My questions are:

* Does it mean it's working? e.g.: example.com is fully accessible from the internet.
* What's those errors mean and how do I fix them?

Note: The IP and domain in information above have been replaced with fictional ones for security purpose.

Cheers

---

### Post by kidders on 2007-06-12
Hi there,

What are you trying to achieve, exactly? Your post almost makes it look as though you're trying to set up a publicly accessible DNS server!

---

### Post by squinter on 2007-06-13
I was trying to make my Ubuntu server to host my internet domains. Anyway I got it to work. Just set the IP to the Internet IP instead of local IP and the world will be able to access it.

---

