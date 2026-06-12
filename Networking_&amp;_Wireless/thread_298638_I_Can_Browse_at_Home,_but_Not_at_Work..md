---
title: "I Can Browse at Home, but Not at Work."
date: 2006-11-13
forum: Networking &amp; Wireless
---

### Post by SendDerek on 2006-11-13
As the title states, I can connect and browse just fine at home, but once I get into work, I can connect to the network, but I cannot browse using firefox or opera.  

I can, however, access two known websites:  
1.) ubuntuforums.org
2.) google.com  

Sites I cannot browse, but can ping [SIZE="1"](just important ones that I would use at work)[/SIZE]:
1.) catch80.com
2.) statcounter.com
3.) plenty of others...

I am connecting wirelessly, and the connection at work is with a linksys router (same as my home).  Unfortunately, I do not know the encryption type (WEP, WPA, etc.), but I can login just fine with the right password.

Any ideas on what could be happening?  Connection strength is excellent and I can browse on my windows partition.

Again, I cannot browse websites under Ubuntu 6.06, but I can ping them successfully.

:-k 

I'm using:

Ubuntu 6.06
Network Manager 0.6.2
Opera 9.00
Firefox 2.0

Thanks in advance.

---

### Post by abbeychase on 2006-11-13
Talk to your Systems Administrator or Network admin.  There may me a firewall.

---

### Post by SendDerek on 2006-11-13
> **abbeychase said:**
> Talk to your Systems Administrator or Network admin.  There may me a firewall.

Heh... funny thing.  I am pretty much the administrator.  There is no IT help.  This is a small business with a normal residential Qwest DSL account.  There's an actiontek modem hooked to a linksys router and only about 4 computers hooked to that (wireless and wired).

Now, I guess I could call Qwest, but I don't really know if they would support any router/linux issues.  ISP's usually only support their connection to the modem and windows.

Would there really be a firewall blocking all linux-based connections?  Or is something else going on?  Remember, I can access the whole world on my windows partition, but only two sites on my Ubuntu.

---

### Post by FrodoB on 2006-11-13
Check your proxy settings in Firefox:

Edit --> Preferences --> Advanced --> Settings

Look at the Configure Proxies to Access the Internet:

The choices are:

Direct Connection to the Internet

Auto-Detect proxy settings for this network

Manual proxy configuration


Compare these to the setting in your windows machines.


This does not seem a likely solution, but with the data available 
it is the only thing I can think of to check that is Firefox
only related.

Have you tried to ping [www.redhat.com](www.redhat.com) from work and if you can try to
access the web site using FireFox?

---

### Post by SendDerek on 2006-11-13
Thank you for the replies!

I am not running through a proxy.  Firefox settings are good (direct connection with the internet).

Remember, it's both Opera and Firefox that aren't working (I havn't tested any other browser).  

I will try and ping redhat.com when I get into work.  I am able to ping the sites that I can't browse to most of the time though (like ping catch80.com and ping statcounter.com work).

---

### Post by Iowan on 2006-11-13
> **SendDerek said:**
> Now, I guess I could call Qwest, but I don't really know if they would support any router/linux issues.  ISP's usually only support their connection to the modem and windows.
I'm still considering upgrading from dialup... my discussion w/ Qwest revealed that their MSN account would not work with my Linux router or workstation.

---

### Post by SendDerek on 2006-11-13
So I guess this has quickly become a "How Do I Connect to Qwest DSL Service" thread. 

Any ideas?

---

### Post by SendDerek on 2006-11-16
Does anybody else here have service with Qwest?  I'd like to know if you were able to get online and how...

---

### Post by Robert.Zapata on 2006-11-16
I'm having the same issue. This started like two weeks ago, yesterday I found that the IT Dept. upgraded the Firewall equipment. I work for a very big company (16,000 employees) and the Internet browsing policies are heavily enforced. Lots of sites are blocked.

I used to have Qwest as my ISP but the service was real bad, now I'm very happy with Earthlink as my ISP via Cable Modem provided by Time-Warner.

---

### Post by ilcarlos on 2006-11-17
> **SendDerek said:**
> ... but I cannot browse using firefox or opera...
Hi, I'm new to linux and tried ubuntu, fedora and mandriva.
I had the same issue at home(with ubuntu, fedora and mandriva)](*,) ,
but is interesting because when I browse frist with kronqueror(mandriva)then I can get to the same site with firefox.
Is like open a path with kronqueror to firefox.
Anyway I browse fine with windows and I use verizon :mad: dsl.

---

### Post by SendDerek on 2007-03-06
Okay, so I found out that I need to use the OpenDNS addresses and it works fine.

Thanks for all the help!

---

### Post by Tomshaq on 2007-03-06
Hi,

I have been having a similar issue at home connecting through Qwest. Could you let me know exactly what it was that you had to do to get it working? Thanks

---

### Post by SendDerek on 2007-03-06
It's really quite easy...

Just delete the DNS servers that you currently have listed under the "DNS" Tab in the Network settings and add in these:

208.67.222.222
208.67.220.220

Apply the settings, and restart firefox or whatever and you're good to go.

If you want to set this permanatly, you'll want to refer to this thread:
[http://www.ubuntuforums.org/showthread.php?t=282034](http://www.ubuntuforums.org/showthread.php?t=282034)

I hope this helps!

---

