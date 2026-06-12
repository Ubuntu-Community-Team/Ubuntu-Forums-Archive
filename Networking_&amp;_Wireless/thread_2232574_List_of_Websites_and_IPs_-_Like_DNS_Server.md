---
title: "List of Websites and IPs - Like DNS Server"
date: 2014-07-02
forum: Networking &amp; Wireless
---

### Post by Tristan_Williams on 2014-07-02
First of all I know I probably misunderstand something and my question is probably not possible at all

So my understanding is that somewhere, there is a large file or folder that contains all known IPs(the ones that go to websites) with their correlating URLs
For example, 173.194.46.78 = [www.google.com](www.google.com)

How would someone compile a list like this?

If I am misunderstanding something, please explain how web browsers know that [www.google.com](www.google.com) corresponds to 173.194.46.78

---

### Post by lisati on 2014-07-02
I don't know of any such file in one central location, but there is such a thing as [Reverse DNS lookup]("http://en.wikipedia.org/wiki/Reverse_DNS_lookup"). How you'd use it can depend on the context. 

There are several websites which can do some of the work for you, e.g. [MX Toolbox]("http://mxtoolbox.com/ReverseLookup.aspx") and [DNS Watch]("http://www.dnswatch.info/").

---

### Post by capscrew on 2014-07-03
> **Tristan_Williams said:**
> First of all I know I probably misunderstand something and my question is probably not possible at all

So my understanding is that somewhere, there is a large file or folder that contains all known IPs(the ones that go to websites) with their correlating URLs
For example, 173.194.46.78 = [www.google.com](www.google.com)

Your understanding is wrong.  DNS is a hierarchical database that maps  IP addresses to Fully Qualified  Domain Names.  The top level domains (TLD) are .com, .net, .uk, .us etc.  Originally these TLD were split up between 13 servers (now there are many more) These are managed by one group.  You can read more about this [here]("http://en.wikipedia.org/wiki/Root_name_server").  The rest of the sub-domains are managed by other entities.  The entire listing is held world wide.
> 

How would someone compile a list like this?
You don't.> 

If I am misunderstanding something, please explain how web browsers know that [www.google.com](www.google.com) corresponds to 173.194.46.78
The TCP/IP stack in the OS asks for a name to be resolved locall by the /etc/hosts file.  f it can't resolve it it is sent to the DNS server you configured.  That request is sent to a TLD DNS server and is then redirected to the proper server below to resolve the name to address mapping.

If you want to configure some of these on you local LAN you can add mappings the local hosts /etc/hosts file.  This file is checked first by any properly configured Linux host.  There is no real advantage to using this method for anything outside of the LAN however.  There are literally thousands of DNS servers that are interconnected to the TLD Root DNS servers.

The best thing to do is read up on *[how DNS works]("https://www.google.com/search?q=how+DNS+works&btnG=Go!&gws_rd=ssl")*.

---

