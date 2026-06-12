---
title: "Web access only to Ubuntu sites"
date: 2007-03-06
forum: Networking &amp; Wireless
---

### Post by mfmarion on 2007-03-06
Ubuntu 6.10
AMD Duron 950MHz, 512 Mb Ram
ISP:  Qwest
NIC:  Intel Ethernet Pro 100, 82557/8/9, PCI
Modem:  ADSL Modem with Wireless Gateway, Actiontec Mdl GT701-WG
Firefox 2

I am able to download Software Updates.  OK.

I am able to go to Ubuntu sites from Firefox.  For example, from:  file:///usr/share/ubuntu-artwork/home/index.html I can get to [https://help.ubuntu.com](https://help.ubuntu.com) and other links...  OK

PROBLEM:  I can get to the Ubuntu sites BUT I CANNOT get to Google, Yahoo, or anywhere else using Firefox.  Aargh.

I can even ping Yahoo and Google, but the Browser won't get me there.  It tries real hard but I can't get anywhere else on the web.  It finally times out. "The connection has timed out.  The server at [www.yahoo.com](www.yahoo.com) his taking too long to respond.

I've followed all of the instructions to get online.  I obviously can get online, but only to Ubuntu sites.

Why?

Thanks.

Mike

P.S.  My Windows computers work just fine.

---

### Post by Mr. C. on 2007-03-07
You have not specified DNS servers.  Your system requires knowing your ISP DNS servers to translate hostnames into IP addresses.

Network settings panel.  Ensure you have valid DNS servers under the DNS tab.

MrC

---

### Post by mfmarion on 2007-03-07
Thanks for the response.  But still no joy.

I did an IPCONFIG /ALL on my Windows machine to find the DNS addresses.

Then I checked the DNS entries as you suggested.  Both the internal IP (192.168.0.1) and the external IP are listed in the DNS tab.

I am running my network with DHCP.

Any other ideas?

Thanks

---

### Post by Mr. C. on 2007-03-07
Your router might have an internal DNS implementation.  Use your ISPs DNS servers instead.  Commodity routers have poor DNS implementations.

Your router should be configured to use your ISPs DNS servers.

Go to your ISPs site, and locate their help section, or contact them, to obtain your DNS IPs for your network.  When you receive those, place them the DNS entry in the Network settings panel.

You can test that these work correctly in a terminal window.  Try

nslookup apple.com DNS_IP1_HERE
nslookup [www.harvard.edu](www.harvard.edu) DNS_IP2_HERE

replacing the DNS_IP... numbers above with the numbers.  Only the first query for each name above will be useful, as subsequent queries are cached.  Your goal is to ensure that you get reliable hostname < -- > IP lookups.  You can test the current numbers you have now, but pick new host sites to test each time.

MrC

---

### Post by mfmarion on 2007-03-07
The problem appears to be the ORDER in which the DNS entries are listed.

I moved the internal IP below the external IP.  Now I'm zoomin' the Internet.

I'm gonna re-boot and check that the re-ordering "sticks."

M

---

### Post by Mr. C. on 2007-03-07
There you go!

The DNS entries are tried in order.  There is a long timeout before the next one is tried, and this causes you needless delays.

Always put the most reliable DNS entries first.  You only need one, a second or third are just backups.

If you router does not have a DNS cache, remove the 192 entry; it serves no purpose.

MrC

---

### Post by mfmarion on 2007-03-07
Well, thanks so much.  You must love this stuff.  I enjoy it as well.  This Ubuntu is really quite impressive.  I've never used Linux before.  I've been working with Windows for years as a Network Admin.  This is as good if not better (plus I don't have to take out a loan to get it :-)   )

I changed my Ubuntu PC to static, put in both external IP's and she's running like a top.  I should probably set all 3 hosts as static for security reasons.

Thanks again,

Mike

---

### Post by Mr. C. on 2007-03-07
I enjoy helping folks like yourself learn and discover the joys of all things computer.

Here's some stuff to get you started down learning Unix if you want: 

[http://cis68a.mikecappella.com](http://cis68a.mikecappella.com)  (unix intro)
[http://cis68c1.mikecappella.com](http://cis68c1.mikecappella.com) (admin intro)
[http://cis68c2.mikecappella.com](http://cis68c2.mikecappella.com) (advanced admin)
[http://cis68b1.mikecappella.com](http://cis68b1.mikecappella.com) (shell scripting)

All notes, etc are in the Coursework areas.

There's no inherent security in static IPs; dynamic is fine.

Welcome to the a new environment!
MrC

---

