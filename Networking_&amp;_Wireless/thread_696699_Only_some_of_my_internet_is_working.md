---
title: "Only some of my internet is working"
date: 2008-02-14
forum: Networking &amp; Wireless
---

### Post by giant_99 on 2008-02-14
Hi all,

I have a weird problem, I can only connect to *some* internet sites. I'm having no other performance problems with my connection. Just plain and simple, some sites like theregister.co.uk, thepiratebay.org, this forum, and many others work. Others such as Google (gmail, google.com, google-analytics.com), Yahoo, Hotmail just don't work. Name resolution works fine but connecting or pinging gets no response.

I don't think the problem is to do with my network (Wireless (or cable) from my Dell Inspiron 6400 to a D-Link DI524 router, to the net via Virgin cable), as when I reboot into Vista everything is fine. I also tried a proxy (Tor), and I can access whatever, but just slowly.

I have no idea what would be causing selective connectivity on my Ubuntu setup. The sites that are working all seem to be part of the Akamai dns system (maybe, I don't even really know what that is).  If you could help, please drop me a suggestion, this is frustrating.

Thanks George.


PS: I found this thread with someone else that has had a similar problem: (No solution tho :( )
[http://ubuntuforums.org/showthread.php?t=585800]("http://ubuntuforums.org/showthread.php?t=585800")

---

### Post by lloyd_b on 2008-02-15
That could be an "MTU" issue.  Here's a way to test this:

First, you need to identify your network interface (eth0, ath0, ppp0, etc).  There are various gui utilities to do this, or in a terminal window type "route" and look for a line with a "*" in the "Gateway" column - the interface is in the right-hand column.

The following assumes the interface is "eth0" - if not, substitute the correct interface.

In a terminal window:
```
sudo ifconfig eth0 mtu 1500
ping www.google.com
```
Keep repeating these commands, changing the "1500" to "1400", "1300", etc.

If at some point it starts working, then it *is* an MTU problem - let me know, and we can try and figure out the best way to resolve it.

If you get down to 500 with no connection, then it is *not* an MTU problem.

Lloyd B.

---

### Post by polmir on 2008-02-15
Your problem in /etc/resolv.conf
[http://ka1fsb.home.att.net/resolve.html]("http://ka1fsb.home.att.net/resolve.html")

---

### Post by giant_99 on 2008-02-17
Thanks guys for the response. I could get neither to work tho unfortunately :(


@lloyd_b
Interesting solution, would had been champ if it had worked. I'll reboot into windows, and see if I can spot what the MTU is in there.

I have a quick question tho. Below is the output of route. The link-local line, what's up with that? Or is it worth worring about. route -n gives it an IP of 169.254.0.0.

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         192.168.0.1     0.0.0.0         UG    0      0        0 eth1
```

@polmir

I think my DNS server's are set up correctly (I think. I could easily be wrong), as they are set by DHCP from my router. I'll reboot into windows after this post to check I'm getting the same there. But, name resolution appears to be working correctly:

```

george@laptop:~$ dig www.google.co.uk

; <<>> DiG 9.4.1-P1 <<>> www.google.co.uk
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 5625
;; flags: qr rd ra; QUERY: 1, ANSWER: 5, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;www.google.co.uk.              IN      A

;; ANSWER SECTION:
www.google.co.uk.       284572  IN      CNAME   www.google.com.
www.google.com.         603937  IN      CNAME   www.l.google.com.
www.l.google.com.       121     IN      A       66.249.93.99
www.l.google.com.       121     IN      A       66.249.93.147
www.l.google.com.       121     IN      A       66.249.93.104

;; Query time: 35 msec
;; SERVER: 62.31.144.39#53(62.31.144.39)
;; WHEN: Sun Feb 17 09:29:27 2008
;; MSG SIZE  rcvd: 130

george@laptop:~$ ping www.google.co.uk
PING www.l.google.com (66.249.93.99) 56(84) bytes of data.

--- www.l.google.com ping statistics ---
14 packets transmitted, 0 received, 100% packet loss, time 13011ms

```

---

### Post by giant_99 on 2008-06-10
Im going to bump my thread. 

I gave up using Ubuntu because of this problem, duel booting Vista was just easier.

I thought after moving house, new internet connection(s), and upgrading to Hardy Heron the problem might resolve itself. Since it hasn't, it must be a configuration issue on my machine. I haven't (intentionally at least) done any tinkering with configuration files either.

If anyone has any advice, please reply. I am familiar enough with Linux having run Gentoo for 18 or so months, just networking isnt my strong point.

Thnks.

---

