---
title: "Wifi connect, but VERY slow"
date: 2006-09-29
forum: Networking &amp; Wireless
---

### Post by hoodooworks on 2006-09-29
Hey all -- 
I got my wifi card working, but the connection seems to be very slow connecting to some sites, like google, for instance.  The card is the infamous Linksys WPC54GS ver. 2.  Link quality is great and the router is connected to 256k dsl, so I can't seem to figure out why it's so slow.  It's not that slow in Windows.

Anybody else have similar experience?

---

### Post by x64Jimbo on 2006-09-29
only some sites? can you list which ones?

---

### Post by hoodooworks on 2006-09-29
Let me run down the scenario for you:
I set google as my start page in firefox.  I boot up firefox, it says "connecting to www.google.com" and then just spins away.  So my first thought is, hey, it's not able to contact the dns.  However, when I go to my outlook webmail, it loads it up in a second.  Myspace loads, but is a little slower (which prbly has more to do with their server load).  Ubuntu.com loads very quick.  :confused:

---

### Post by x64Jimbo on 2006-09-30
But is it JUST google, or are other sites affected? If so, which ones? 
I'm almost certain that this is not related to your wifi connection.

---

### Post by sonoftheclayr on 2006-09-30
I am having a similiar problem. I am using a D-Link Airplus G DWL-G630 Version E1 with the RT61 STA Driver on 6.06.

I can access some websites by typing in the domain name, others I have to type the IP address in and for many I have to ping them first before it will load and some won't load at all, it took me about 5 minutes to get into Google.

I am thinking it might be related to the driver because the card works(ed?) fine in Windows and I haven't had any other problems with it before, signal strength is always strong as there is just a wall separating my laptop from the router. The connection is encrypted (WEP, 128bit), but would that have anything to do with it not working?

I have only really started to use Ubuntu for a couple of days and I am a newbie.

Any help would be appreciated and I'm sure hoodooworks is suffering from the same problem. The connection is fine, 512kbps DSL, so I am thinking the problem is at my end.

---

### Post by x64Jimbo on 2006-09-30
As I said, the issue is almost certainly not a wifi problem and more likely an ISP, DNS, or configuration problem.

---

### Post by RideYourBike on 2007-01-06
Hello,

I am having a similar issue.  For me the problem appears to be associated with WEP using ubuntu 6.06.

Without WEP, connectivity is completely fine, but with 128 bit WEP, connecting to websites is very slow (about 30 seconds) using either Firefox or Lynx.  This happens for any website.  However, once a page is loaded from particular domain, subsequent connections to that domain are fine until the browser is closed or ignored for a few minutes.  

It seems like a domain name resolution issue however, pinging a domain name reponds promptly and so does dig,  

Has anyone seen this?  or have any suggestions on other tests that I can try?

Thanks,
Tim

---

### Post by scoon on 2007-01-06
Hey there, 

check out the man page for iwconfig.  I'd guess that you wifi is set to the fastest it can be.

s-coon

---

### Post by RideYourBike on 2007-01-08
As I mentioned above, I had a similar issue and found the cause

After capturing some packets, I discovered the router was dropping AAAA (IPv6) DNS requests.

I documented my solution here:
[http://www.rideyourbike.org/rants/2007/01/slow-wireless-connection-ipv6-not.html](http://www.rideyourbike.org/rants/2007/01/slow-wireless-connection-ipv6-not.html)

Hope this helps.

---

### Post by x64Jimbo on 2007-01-11
Good job posting the solution. That is definitely the way to go about being a Linux citizen. Please continue to do this when you find solutions.

---

