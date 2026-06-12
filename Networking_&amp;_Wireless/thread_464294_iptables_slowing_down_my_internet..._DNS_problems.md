---
title: "iptables slowing down my internet... DNS problems?"
date: 2007-06-04
forum: Networking &amp; Wireless
---

### Post by aks44 on 2007-06-04
Even though (K)Ubuntu is very secure, I recently dumped the default filter ACCEPT/ACCEPT/ACCEPT iptables policy in favor of a hand made script.

However, since I installed that script, my internet connection is very slow at creating new TCP connections (established connections are just as fast as usual). As soon as I shutdown my firewall and restore iptable's default policies, internet access is lightning fast again.

FWIW, I only use like 30-40 rules, and I just can't believe those few rules can cause so mush slow down on an i686 HT 3ghz with 2gb ram... (CPU usage happily stays at 0 or 1% anyways)

The symptoms lead me to believe that Ubuntu uses UDP DNS requests (that can't come back in due to my firewall rules), and only when those requests time out it falls back to using TCP requests.

But before making useless holes in my firewall, I have a few questions...

1) Where is that damn file that iptables logs into ???? Dropped packets are logged but I just can't find where :(

2) Can anyone confirm Ubuntu's supposed behavior regarding DNS queries?

3) I connect to internet through PPPOE, with a variable IP (DHCP), so I get my DNS servers through DHCP too. Is there any way I can use fixed DNS servers? (I used to do that under Windows, worked like a charm). If I open incoming UDP 53, there is NO WAY I open it for everyone, only to trusted DNS servers...

4) As a *last resort*, can I tell Ubuntu to immediately use TCP for DNS requests, skipping UDP altogether ?


Thanks by advance.

BTW, if anyone is interested I can post my (rather hardened though perfectible) firewall script.

---

### Post by scrooge_74 on 2007-06-04
For DNS you can use this instructions

[http://www.opendns.com/start/](http://www.opendns.com/start/)

---

### Post by nixfaced on 2007-06-04
Hi,

If you're blocking UDP DNS traffic, then that is definitely causing your slowdown.  UDP DNS queries are not unique to Ubuntu.  Every variant of Linux and Windows that I've used does the same.  Probably ditto for Macs, though I can't say from first-hand experience.  Last I knew, this behavior was specified as a MUST in RFC1123 (Requirements for Internet Hosts), so I think every sane OS out there does it this way.  Here's the relevant section (although this bit may have been updated or obsoleted somewhere along the line, but if so, I can't find where):

> 
            DNS resolvers and recursive servers MUST support UDP, and
            SHOULD support TCP, for sending (non-zone-transfer) queries.
            Specifically, a DNS resolver or server that is sending a
            non-zone-transfer query MUST send a UDP query first.  If the
            Answer section of the response is truncated and if the
            requester supports TCP, it SHOULD try the query again using
            TCP.


So there's that.  Moving on...

Although you are obtaining your DNS server settings dynamically, this does not mean they will change whenever your IP does.  In fact, they should rarely change at all, unless your ISP assigns them on a round-robin basis or similar, and even then you should be able to choose any two and have them work.  That means that it should be okay to set an ACCEPT rule for UDP traffic coming from your ISP's DNS servers.  You can still drop all other UDP port 53 traffic, since your computer will really only ever talk to your ISP's servers.

You can, if you wish, specify DNS servers to be used regardless of what DHCP (or PPP, as the case may be) tells your computer.  Unfortunately, I'm pretty foggy on the specifics of how PPPoE works with regards to dynamic host configuration, so I couldn't tell you how to make this work.  A "supersede" statement in /etc/dhcp3/dhclient.conf would be my guess, though.

As far as the logs, I believe netfilter will log to /var/log/kern.log if you are using ubuntu's default settings, but I could very easily be mistaken.  It's a place to start, anyway.

Hope this helps

---

### Post by aks44 on 2007-06-04
Thanks guys.

nixfaced, your clarifications concerning the DNS protocol are confirming what I thought but I was really unsure, due to the fact that I only used Windows until now and that I'm not very knowledgeable in the networking area...

Your suggestion about supersede in /etc/dhcp3/dhclient.conf is correctly detailed in the site that scrooge_74 gave (using the "prepend" variant), so I'd bet this is the way to go.

I don't have time right now to try it out, but I'm pretty confident this will solve my latencies. If it doesn't I'll let you know tomorrow.


Thanks again to you both. :D

Edit: /var/log/kern.log is the log I was looking for. Linux can be so frustrating when you're just a rookie... ;)

---

### Post by aks44 on 2007-06-05
Well, no luck with this one...

Changing /etc/dhcp3/dhclient.conf doesn't allow me to override the DNS servers that are provided through PPPOE. And /etc/resolv.conf is indeed overwritten every time I "pon dsl-provider".

As a quick & dirty fix I could allow every incoming UDP 53 traffic, but I'd rather get used to those 5 seconds delay for every connection...

Anyone around here has some experience with using *fixed* DNS servers with PPPOE?

Edit:

I managed to override my ISP's DNS servers that are attributed through PPPOE, and I now use fixed DNSs.

To do that, edit /etc/ppp/peers/dsl-provider (the file that is generated by pppoeconf), and comment out the line that reads "usepeerdns". Now pppd won't overwrite your /etc/resolv.conf when it boots up, so you can now tinker with it without problem... :D

---

