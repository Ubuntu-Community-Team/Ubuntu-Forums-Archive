---
title: "[SOLVED] resolv.conf search domains ignored?"
date: 2008-03-06
forum: Networking &amp; Wireless
---

### Post by Chireru on 2008-03-06
I'm running into a weird issue.  I've set up a static resolv.conf file (not managed by Network Manager), which includes this configuration:

search example.com
nameserver 192.168.0.10

When I ping "www", it works just fine (resolves to [www.example.com](www.example.com)), 
When I ping "www.local", it fails.  (should resolve [www.local.example.com](www.local.example.com)).
Using dig or host I can resolve it just fine (using the FQDN).

Watching the DNS cache's logs, the system doesn't even try a query.

System started doing this after I reformatted (complete reinstall) to Gutsy Gibbon.  Worked fine before that.

---

### Post by Eiríkr on 2008-03-06
Forgive me for possibly asking an obvious question, but the host [www.local.example.com](www.local.example.com) *is* defined in your DNS setup, correct?  :)

Cheers,

Eiríkr

> Using dig or host I can resolve it just fine (using the FQDN).

Never mind, I'm a bobo.  Doh.  Some days I really think I should try to get more sleep...  :-|

Reading again through the [TLDP DNS HOWTO]("http://tldp.org/HOWTO/DNS-HOWTO.html"), I think it's because the second example is for a subdomain.  I'll look more into this and post later.

---

### Post by Chireru on 2008-03-06
> **Eiríkr said:**
> Forgive me for possibly asking an obvious question, but the host [www.local.example.com](www.local.example.com) *is* defined in your DNS setup, correct?  :)
Yes, the record exists, and works fine on my other boxes.  I have gone to the length of copying the resolv.conf from one of the other boxes, and it still fails here.

Pinging "www" works.  
Pinging "www.local.example.com" works.  

However, pinging "www.local" with a search domain of "example.com" doesn't work.  I expect it to complete the hostname with ".example.com",  but it does not.  Checking my DNS cache's logs, it doesn't try any lookup at all, it simply times out after exactly 5 seconds.

This carries over into any application on the box, eg: firefox, ssh, etc.

---

### Post by Eiríkr on 2008-03-06
[This page]("http://www.zytrax.com/books/dns/ch9/subdomain.html") looks like it might be what you're looking for.  

Cheers,

Eiríkr

---

### Post by Chireru on 2008-03-06
The problem is not the zone; the zone works just fine.

Here is an example.... from a box that is working (Feisty Server):
> **$ cat /etc/resolv.conf**
nameserver 10.10.221.4
search blackpacket.net
**$ ping -c1 momiji.local**
PING momiji.local (10.10.221.6) 56(84) bytes of data.
64 bytes from momiji.local.blackpacket.net (10.10.221.6): icmp_seq=1 ttl=64 time=0.155 ms

--- momiji.local ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.155/0.155/0.155/0.000 ms

From the broken box (Gutsy Desktop):
> **$ cat /etc/resolv.conf **
nameserver 10.10.221.4
search blackpacket.net
**$ time ping -c1 momiji.local**
ping: unknown host momiji.local

real    0m5.006s
user    0m0.004s
sys     0m0.000s
**$ ping -c1 momiji.local.blackpacket.net**
PING momiji.local.blackpacket.net (10.10.221.6) 56(84) bytes of data.
64 bytes from momiji.local.blackpacket.net (10.10.221.6): icmp_seq=1 ttl=64 time=2.98 ms

--- momiji.local.blackpacket.net ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 2.989/2.989/2.989/0.000 ms

---

### Post by Eiríkr on 2008-03-06
Interesting.  And the broken box is also the DNS server?  Hmmm....

---

### Post by Chireru on 2008-03-06
> **Eiríkr said:**
> Interesting.  And the broken box is also the DNS server?  Hmmm....

Nope, the broken box is just a desktop system.  The DNS cache runs on another system (10.10.221.4)

---

### Post by Eiríkr on 2008-03-07
I added the following line to my own hosts file:
```
fred.local      A       192.168.111.111
```

And my resolv.conf file includes:
```
search local.example.com example.com
```

Pinging "fred.local" fails out with "unknown host", but I *can* ping "fred".  If I remove the "local.example.com" bit from resolv.conf, pinging just "fred" fails, but so does "fred.local".  But then you've got a "www" at both levels of your domain setup this might not be all that helpful.

---

### Post by Eiríkr on 2008-03-07
Bingo!  Got it -- 

It's because you're using the ".local" suffix.  Avahi uses this by default as part of its zeroconf setup, and this is likely interfering with your DNS.  

Here's a test: on your "broken" machine, try to ping a known-bad hostname.  Ping should return immediately with the "unknown host" message.  Now try to ping any hostname suffixed with ".local".  Ping should take a few seconds to return.  Also check:
```
user@ubuntu:~$ ps aux | grep avahi
avahi     4846  0.0  0.1   2852  1548 ?        Ss   Mar04   0:00 avahi-daemon: running [ubuntu.local]
avahi     4847  0.0  0.0   2736   460 ?        Ss   Mar04   0:00 avahi-daemon: chroot helper
user     22917  0.0  0.0   2972   748 pts/1    R+   23:01   0:00 grep avahi
user@ubuntu:~$
```

Avahi runs its own multicast DNS mini-server, and grabs any lookups in the ".local" space.  More about it [here]("http://avahi.org/").  Either shut down Avahi and configure it not to run on boot, change its config to use a different domain, or change the ".local" name to something else in your DNS zone files, and you should be good to go.

HTH,

Eiríkr

---

### Post by Chireru on 2008-03-07
That did it!

It looks like Avahi was interfereing with the requests.  By stopping the service, my dns requests now resolve correctly.  I'll take a look a bit later to see if I can configure it to use another domain.

Thanks

---

### Post by Eiríkr on 2008-03-07
Glad that worked.  :)  I'm just sorry my earlier posts weren't more helpful.  Anyway, if that fixes your issue more or less, don't forget to mark the thread SOLVED in the Thread Tools dropdown at the top of the page.

Cheers,

Eiríkr

---

### Post by Chireru on 2008-03-07
Thanks :)

---

