---
title: "local name resolution - HOWTO?"
date: 2008-04-30
forum: Networking &amp; Wireless
---

### Post by Lexje on 2008-04-30
Hi forum,

I'm in the process of setting up Ubuntu Gutsy as a local server.
A dhcp server is present in my network (linux LMCE).

My problem is this:
local box nameresolution doesn't seem to work properly;
when I ping 'hostname' from a windows box that has got it's settings from dhcp the reply resolves to the hostname's IP address.

when I do the same from the Gutsy server, I get unknown host 'hostname'

How can I solve this?

Thanks a lot!!

Erwin

---

### Post by lemming465 on 2008-04-30
On the windows box does ```
nslookup *hostname*
``` fail?  Windows ping is willing to use Netbios name resolution if DNS fails.

If your network has stable IP's and is small, the easiest solution is to put the various machines in each other hosts files.  Failing that you need a lot of infrastructure to get a DHCP leases into dynamic DNS with local zones.

---

### Post by Lexje on 2008-04-30
Thanks for answering!
```
nslookup freenas
*** Can't find server name for address 192.168.80.1: Non-existent domain
*** Default servers are not available
Server:   UnKnown
Address:  192.168.80.1

*** UnKnown can't find freenas: Non-existend domain
```

ping freenas gives me the correct ip address.

I have a domain server (linux box) and am setting up LinuxMCE.
For this I am experimenting with this.
I would like to get a better understanding and a well functioning network.

Do you have any pointer as to where to get some good documentation to get [HTML]infrastructure to get a DHCP leases into dynamic DNS with local zones[/HTML]working?

Thanks a lot!

Erwin

---

### Post by lemming465 on 2008-05-01
Integrating DHCP with Dynamic DNS has three basic solutions:
1. Install a Windows server and use the Microsoft WINS, DHCP, and DNS.  Microsoft has lots of white papers at technet.microsoft.com describing how to do this.

2. Install Samba for Wins, something like ISC DHCP for DHCP, and something like BIND for DNS.  A typical reference for this would be the [O'reilly DNS and Bind]("http://www.oreilly.com/catalog/dns5/") book.

3. Buy a commercial 3rd party tool from someone like Mice&Men.

This is not for the faint of heart; enterprise-grade infrastructure takes some significant setup work.  But you can definitely learn a lot doing it.

If you want to avoid the work on a home network, just avoid DHCP entirely and use 100% static addresses and host file entries.

---

### Post by Grosneg on 2009-09-29
I have a similar problem, however it differs in that my LinkSys WRT54g handled local name resolution just fine. When I upgraded to the WRT610n, Ubuntu machines would no longer resolve. I found that tacking .local to the end of the name made it resolve, but I don't know why. Does the new router not offer local name resolution? I can find nothing on the topic. Would love to hear others' solutions.

thanks

Grosneg

---

### Post by Iowan on 2009-09-30
So far, I'm fond of **dnsmasq** as my DHCP/DNS server. **djbdns** is another option.

---

