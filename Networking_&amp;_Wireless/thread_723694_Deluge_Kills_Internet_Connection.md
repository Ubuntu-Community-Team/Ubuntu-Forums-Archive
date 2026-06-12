---
title: "Deluge Kills Internet Connection"
date: 2008-03-13
forum: Networking &amp; Wireless
---

### Post by yochaigal on 2008-03-13
hello everyone!
First let me say that I am a Network Technician; so lets assume that all the basic stuff is a-ok on my end.  not that i'm infallible; it's just that in this situation I know enough to ask questions.

I have had this problem on EVERY ubuntu machine I've installed deluge-torrent on; I've since been using ktorrent or transmission with no problems.

Here's what happens: While downloading a torrent in deluge I begin to experience on INCREDIBLE slowdown of the internet; regardless of the download speed.
I can't ping or traceroute anything, nor can I browse the web. My download speed is 6 mb/sec, so no problems there. 

For example, I could be downloading PCLINUXOS with 300 peers and 1000 seeders at a rate of 300 KB/sec, or I could be downloading from a different tracker with 5 peers and 1 seeder at a rate of 10 KB/sec, and the problem happens in both scenarios.  I switch torrent clients, viola, no problem.
I believe it is killing all my ports except the one it's using,; this could be a router issue but I've tried it on a variety of routers all with the same result.  I tried disabling IPV6; i've had the same problem.
by the way I've seen this on feisty, gutsy, and hardy. 

Any tried and true results that work?

thanks

---

### Post by croto on 2008-03-13
I've never used Deluge, but I have experienced network slowdowns using other bittorrent clients. 

You don't mention your upload bandwidth. Make sure you cap your bittorrent upload to no more than about 75% of your max upload rate (try to measure it uploading a file to some host over the internet, that would be more reliable than the number your ISP quotes).

In my case, the problem was the number of IP connections. Bittorrent connections were choking my router (it is a well known problem with linksys routers using ddwrt, because ddwrt keeps connections not properly closed for too much time, not leaving room for newer connections), so I fixed that in my router, and capped the max number of connections in my bt client. It worked as a charm. I'm not sure that is your problem, but it may be worth a try to set the number of max connections to something like 50 to see if that helps.

---

### Post by yochaigal on 2008-03-14
Ok, again:

This problem ONLY happens with deluge.
Let me make a short list of the clients I've used:
utorrent/wine, ktorrent, qbittorent, azureus, rtorrent, transmission, the gnome bittorrent client---
anyways it goes on.  The point is, this is a program issue that has happened on numerous machines, distros, and installations.
My upload is 120 at least.  I have an excellent connection, DSL-wise.

I really think this is program-specific.

thanks!

---

### Post by vikrant82 on 2008-03-14
I have seen a lot of people complaining about this.

> While downloading a torrent in deluge I begin to experience on INCREDIBLE slowdown of the internet; regardless of the download speed.

When you experience this sudden slowdown, does Deluge keep on downloading at consistent speed ? Or the download speed comes down there also ?

If the download at deluge keeps working fine then, It could be a DNS problem. When you open a website, does it get stuck at "Looking up .." or "Connecting to..."

If its "Looking up ..", and Deluge is downloading fine all this while then it is probably a choked DNS server ?? May be you have enabled, resolve IPs in Deluge ?

Also keep track of a setting which relates to , "Maximum no of concurrent outbound connections Deluge starts" , I don't know where is that setting in Deluge. Keeping this '0' i.e. unlimited could also be an issue. 

Are you using a Wireless connection, If yes then try a wired connection. I have seen old wireless routers having these black outs.

---

### Post by yochaigal on 2008-03-14
Yes, Deluge does continue downloading at a regular pace. 
I have not been able to find the "resolved IPs" option in deluge.
Concurrent connections is, as always, 8 concurrent connections.
Wired Connection.

Thanks

---

### Post by vikrant82 on 2008-03-14
Try hitting a website by IP ...

---

### Post by yochaigal on 2008-03-14
Good Idea! That would prove that it's a DNS issue.

be back.

---

### Post by netztier on 2008-03-14
> **yochaigal said:**
> 
My upload is 120 at least.  I have an excellent connection, DSL-wise.


How much of this upstream capacity is being used by Deluge?

A saturated upstream will always impact your download rates. With the output queue to the upstream DSL being full, your router will start dropping upstream packets - pings, DNS lookups and TCP ACKs from dowload streams included. If the TCP ACKs from your client don't make it to the server in due time, that server will start sending at slower rates.

Check Deluge's settings for the "upstream/upload behaviour" and if possible throttle it to half of your DSL's upstream bandwith.

regards

Marc

---

### Post by Nameless_one on 2008-04-04
I am also having this problem, and have read about it on the deluge forums too. It seems very common. 

I think the problem is that deluge is very aggressive in taking connections. I partially resolved my problem by lowering very much the maximum connections deluge keeps, from the recommended 200 to 80, and also the maximum half-open connections from 20 to 9. I hadn't tried limiting the maximum connection attempts per second (it was unlimited), I will try that and report back here. 

However, the above limits made things a little better (I managed to at least partly browse most pages). So, what I want is to find out the maximum tcp connections for my computer. Does it depend on my router? Does ubuntu limit them? Where can I see that limit? How can I change it?

---

### Post by netztier on 2008-04-04
> **Nameless_one said:**
> Does it depend on my router? 

If that router is of the common "broadband router" type (i.e. one external "WAN" port as Ethernet or DSL, 4 internal "LAN" ports, serving some 192.168.x.x-Addresses via DHCP and picking up one external IP address from your ISP via PPPoE or DHCP), it has to perform NAT/PAT, sometimes called NAPT (Network Address Port Translation), also called "IP masquerading" or similar.

For that purpose, it has to track the state of all tcp and udp communication flowing through it - and this can be quite a burden to the system, consuming memory and CPU. There are routers that limit the amount of connection establishments per second or rapidly drop in performance once a large number of connections is already in place - hence the trouble with new connections.

This has an advantage: Maintaining such a connection table is an actual core function of a firewall, and hence every common broadband router can - to some extent - be called a (simple) firewall.

But since a lot of these products are built upon commodity low-end hardware, some just can't cope with higher loads. We used to run the DSL access for guests and cosultants (up to 20-30 people at the same time) on such a simple DSL router - at least once a week we had to reboot it because it's connection table was overflowing when several of our guests fired up their Skype or peer2peer-clients. We had to upgrade to another router platform and had no trouble since, even after several bandwith upgrades.


regards

Marc

---

### Post by Nameless_one on 2008-04-04
Thank you for the informative reply. The router is of the common type, and it isn't one of the expensive ones either. So I guess I shouldn';t put too much strain on it. 

I limited the maximum connections per second, and now things are much better, though. My connection has 2 Mbps downstream and 256 Kbps Upstream, and I set it to 8 connections per second, and it works reasonably well.

---

### Post by yochaigal on 2008-05-04
SOLVED

I just thought I should mention that this problem persisted in Hardy Heron; but I was able to fix it by upgrading my router firmware.
I was using dd-wrt v24 (circa 2006) on my WRT54G v6.
They haven't yet released any stable firmware since then; but the release candidate of v27 seems to have done the trick.

Yochai

---

### Post by someonestolemyname on 2008-05-24
I also saw this problem. I have the same router (default firmware), Gutsy, most recent deluge.

Changing the settings to be more conservative works fine for me. No problems now. Thanks!

Daniel

---

### Post by A$h X on 2008-06-06
Anyone have a definitive answer for stopping deluge from eating up all available bandwidth? I've tried version 0.5.8.9 to 0.5.9.1 and they all suffer from the same problem. I've limited the upload speed to 5kBps to no avail, and updated my router firmware and set QoS with no success. I've seen this problem crop up across many threads, someone must know which version of deluge started becoming a bandwidth hog.

---

### Post by yochaigal on 2008-06-06
What router do you have?  I had a Linksys WRT54G v 7.0 running dd-wrt v23 mini.
Deluge hogged my internet connection like crazy, then I updated the dd-wrt firmware, reset the settings, now the problem is gone.

In the meantime, you can always use ktorrent.

---

### Post by A$h X on 2008-06-06
> **yochaigal said:**
> What router do you have?  I had a Linksys WRT54G v 7.0 running dd-wrt v23 mini.
Deluge hogged my internet connection like crazy, then I updated the dd-wrt firmware, reset the settings, now the problem is gone.

In the meantime, you can always use ktorrent.

I have a WRT54GS v4 running DD-WRT v24. You reckon a reset will sort out deluge?

---

### Post by yochaigal on 2008-06-06
Make sure you've updated to the newest, most current firmware version, copy all your settings and reset.

---

### Post by A$h X on 2008-06-08
Good news, I have managed to solve deluge killing my connection while it is active. It comes down a setting in my router config. If you have a setting called "UDP timeout" set it to 120 seconds or a slightly higher value. 

Mine was set to 3600 and it was flooding my connection with UDP packets that took ages to expire, so my bandwidth was being stifled. If you have similar problems, try looking for this value in your router setup.

---

