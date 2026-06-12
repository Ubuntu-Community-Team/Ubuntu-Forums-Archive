---
title: "specify multiple DNS server"
date: 2008-07-04
forum: Networking &amp; Wireless
---

### Post by remyvrs on 2008-07-04
Hy guys!

I simply want to use multiple DNS servers , such as they are specified in Windows like Alternate DNS.
 
I have tried to edit /etc/resolv.conf to be :

nameserver first.dns.server.1
nameserver second.dns.server.1

but it seems that it is using only the first entry in the file, so if i comment the first nameserver it will correctly lookup the hosts that are to be found by the second nameserver .... but the machine names corresponding to the first nameserver won't be available...

by the way, how do i flush these changes ???(is it enough to only edit and save the /etc/resolv.conf file?)

thanks in advance!!

---

### Post by HalPomeranz on 2008-07-05
> **remyvrs said:**
> Hy guys!

I simply want to use multiple DNS servers , such as they are specified in Windows like Alternate DNS.
 
I have tried to edit /etc/resolv.conf to be :

nameserver first.dns.server.1
nameserver second.dns.server.1

but it seems that it is using only the first entry in the file, so if i comment the first nameserver it will correctly lookup the hosts that are to be found by the second nameserver .... but the machine names corresponding to the first nameserver won't be available...


This will never work the way you want it to.  It turns out that the Windows Alternate DNS implementation is very non-standard, and the Linux/Unix resolver implementations (which much more rigidly adhere to standards) don't work this way.  The only way the second name server in your resolv.conf file will be queried is if the first name server is down and unresponsive.

If you can explain why you want the Windows-like DNS behavior, perhaps I can suggest a work-around.

> 
by the way, how do i flush these changes ???(is it enough to only edit and save the /etc/resolv.conf file?)


Yes, it's enough to simply edit the file and save it.  The Linux/Unix resolver libraries read the resolv.conf file on every lookup, so any changes you make take effect immediately.

---

### Post by superprash2003 on 2008-07-05
if you are using DHCP in any of your network cards then resolv.conf file will be overwritten by the router every few minutes.. you could add dns servers in the dhclient.conf file

---

### Post by nidelius on 2009-03-05
for static dns as superprash2003 says try changing the line in

```

/etc/dhcp3/dhclient.conf

prepend domain-name-servers ISP-DNS1,ISP-DNS2;

```

---

