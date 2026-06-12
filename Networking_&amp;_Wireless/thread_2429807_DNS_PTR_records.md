---
title: "DNS PTR records"
date: 2019-10-23
forum: Networking &amp; Wireless
---

### Post by rsteinmetz70112 on 2019-10-23
I'm finally beginning to add full IPv6 support to my networks and the first thing is to add PTR records for my mail servers.

My Public DNS records are held by my registrar Network Solutions, but my ISP provides the static IPV4 addresses. I use NAT 1 to 1 to translate incoming and outgoing traffic from a Private IPv4 to a Public IPv4. 

I've read that the PTR record must be established by the ISP as "owner" of the IP addresses.

Can anyone tell me what do I need to do to get this set up properly?

---

### Post by TheFu on 2019-10-23
DNS has forward lookups   name.com --> IP
and
DNS has reverse lookups    IP --> name.com

The reverse lookups are only important for running an email server, IME.  The ISP will need to make those changes. Open a support ticket with them to get the change made.
I've never had any issues with any non-SMTP servers needing the reverse lookup.

---

### Post by Skaperen on 2019-10-23
there are 2 ways an ISP can set this up.  1: they can host the PTR records.  2: they can delegate a zone to your DNS server with an NS record.  they may document or not.  they may ask for your DNS server name or not.  how many network blocks did they allocate to you?

---

### Post by #&amp;thj^% on 2019-10-23
> I've read that the PTR record must be established by the ISP as "owner" of the IP addresses.
These are just the steps I take, and please don't assume I know how you want yours setup. :)
Contact your ISP (or whoever owns your IP block) and request a zone for your mail server’s IP address. 
My Zone was in this type of format "“in-addr.arpa”" And they were actually my IP block with the octets reversed.

Most mail servers don’t care where the PTR points to. They just want to see that the ISP has delegated the reverse DNS to your provider and that you have a PTR record for your delegated zone with the name of your IP address. 

When a mail server performs a reverse DNS lookup it will initiate a three-way handshake: 
[list]
    [*]The forward DNS must match the reverse DNS.
    [*]The reverse DNS must resolve to the mail server’s IP address. 
    [*]The reverse DNS must match the fully qualified domain name (FQDN) of the email header. [/list]
I find the "Dig" tool useful here.

---

