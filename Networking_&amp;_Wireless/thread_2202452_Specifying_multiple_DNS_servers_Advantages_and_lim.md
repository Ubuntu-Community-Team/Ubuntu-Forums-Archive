---
title: "Specifying multiple DNS servers: Advantages and limitations"
date: 2014-01-29
forum: Networking &amp; Wireless
---

### Post by hiig on 2014-01-29
Since you can specify a heap of different DNS servers to use, I have a few questions regarding how it works, and what the limitations are.

First off, is there a limit to how many DNS servers you can use? I've seen some people with countless addresses.

Secondly, is more truly better? If you triple the number of DNS servers in your list, will your network times and/or reliability improve? At what cost?

Third, how do multiple DNS servers work? Is a request made to every server simultaneously, so that you find the IP address of whatever you need from the DNS server that replies the quickest, or is one request sent to the first in your list, then after a certain time, the next one, and so on?

Also, how does running your own DNS server work? If your network is making up to 30 000 simultaneous connections, what sort of hardware would you need to be able to handle that sort of activity? I've always been interested in running a DNS server for myself to improve those connection times, even if by a small amount, but my hardware limitations are what hold me back. I really only have a bunch of old laptops at my disposal, but would the hard drive really be the best place to store data, or a flash drive, since many random seeks would be made, as opposed to sequential ones.

I'll have plenty more questions on this as this thread progresses, I'm sure.

---

### Post by SeijiSensei on 2014-01-29
On the client side, you can specify multiple server addresses to resolvconf.  You'll get an /etc/resolv.conf that looks like this:

```

nameserver 127.0.0.1
nameserver 192.168.0.1
nameserver 8.8.8.8
search example.com

```

The resolver only consults later entries if it cannot connect to the first server in the list.  If it can see that server, but receives an NXDOMAIN ("not found") reply to a query, it will not send the same request to other servers in the list.  The additional servers provide backup; they do not affect performance.

What are you doing that generates 30,000 *simultaneous* connections?  I'm having trouble understanding why DNS plays any role here at all.  Remember that the results of DNS queries are cached by remote nameservers and resolvers.  Once someone has asked her ISP to resolve example.com, that record will remain in the ISP's cache for as long as the time-to-live specified in the domain's zone records.  So you won't be seeing nearly as many DNS queries as connections.

I ran BIND servers on i386 hardware nearly two decades ago.  BIND is very fast and not very demanding of hardware.  Other than logging, pretty much everything happens within the server's memory image.  If you're only handing queries for a small number of domains, I wouldn't worry about the hardware requirements.

According to "man resolv.conf" the maximum number of nameservers that can be listed by default is three.  It describes the search process as follows:
> The algorithm used is to try a  name server, and if the query times out, try the next, until out of name servers, then repeat trying all the name servers until a maximum number of retries are made.
Notice the criterion is whether the query "times out" not its disposition (e.g., NXDOMAIN).

---

### Post by chili555 on 2014-01-29
I suggest that no study of this subject will be complete without: [http://code.google.com/p/namebench/](http://code.google.com/p/namebench/)>  The additional servers provide backup; they do not affect performance.If I understand correctly, the second nameserver is only there in case the first is off line. The third, in case  both the second and the first are off line.

---

### Post by hiig on 2014-01-29
I've already got a list of best performing DNS servers, but thanks.

> **SeijiSensei said:**
> The resolver only consults later entries if it cannot connect to the first server in the list.  If it can see that server, but receives an NXDOMAIN ("not found") reply to a query, it will not send the same request to other servers in the list.  The additional servers provide backup; they do not affect performance.

What are you doing that generates 30,000 *simultaneous* connections?  I'm having trouble understanding why DNS plays any role here at all.  Remember that the results of DNS queries are cached by remote nameservers and resolvers.  Once someone has asked her ISP to resolve example.com, that record will remain in the ISP's cache for as long as the time-to-live specified in the domain's zone records.  So you won't be seeing nearly as many DNS queries as connections.

I ran BIND servers on i386 hardware nearly two decades ago.  BIND is very fast and not very demanding of hardware.  Other than logging, pretty much everything happens within the server's memory image.  If you're only handing queries for a small number of domains, I wouldn't worry about the hardware requirements.


That's the thing though, these connections are made by a web crawler, so the URLs would mostly be unique. That's why I was wondering about performance. If having almost no latency by running the DNS server from your computer helps even a small amount, it's something I'd do to increase output. If we assume every connection to be to a new site each time, what sort of hardware needs would I be looking at in that case? And what specific hardware is stressed the most?

I'll check out BIND later on. Can it also run on Windows (can't check right now. Awaiting a replacement for my dead video card)? I haven't decided which of my computers to put it on just yet.

---

### Post by SeijiSensei on 2014-01-29
First, the URLs don't matter for DNS, just the host and domain names do. So even if all the URLs are unique, many of them will share the same server name.

So does this task consist of one machine making lots of connections, or lots of machines making lots of connections?  If the latter, you'd almost certainly see some performance improvement by running a central caching DNS server that all the clients use.  If it's just one machine, I'm not sure that adding BIND would be a substantial improvement over something like [dnsmasq]("https://wiki.archlinux.org/index.php/dnsmasq").  You just want something that will efficiently cache DNS lookups on this single computer.  By default dnsmasq only caches [150 names]("http://www.thekelleys.org.uk/dnsmasq/docs/dnsmasq-man.html") though; you'll probably want to increase that substantially via the "-c" parameter.  Make sure you have a lot of memory as well.

---

### Post by hiig on 2014-01-30
Yes, it would be the former. One machine making many connections.

How much memory are we talking about here? Am I to assume this all runs in the RAM then (or mostly)?

The DNS thing has always been a bit of a grey area for me. How does the DNS server actually get the host and domains to begin with? Where does it look for the information?

---

### Post by SeijiSensei on 2014-01-31
> **hiig said:**
> How much memory are we talking about here? Am I to assume this all runs in the RAM then (or mostly)?

I'd bet 512MB would cache a lot of lookups.  Most of these will be hostname-IP pairs, so they can't be very long. 

You most definitely want this to run in RAM to minimize lookup times.

Try installing dnsmasq and bump its maximum number of cached entries from 150 to something like 10,000 or 100,000.  Then watch the dnsmasq process with the top command while the machine does its thing.  You'll get a sense of the memory usage involved.

> The DNS thing has always been a bit of a grey area for me. How does the DNS server actually get the host and domains to begin with? Where does it look for the information?

The presentation is a bit clunky, but you can start with this page at [Verisign](http://www.verisigninc.com/en_US/domain-names/online/how-dns-works/index.xhtml).  It explains the recursive method of resolving queries.

---

### Post by hiig on 2014-01-31
Yeah, I'll definitely give that a shot once I get my main rig up and running again. Cheers

---

