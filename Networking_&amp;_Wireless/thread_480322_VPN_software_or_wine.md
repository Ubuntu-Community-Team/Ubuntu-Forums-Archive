---
title: "VPN software or wine"
date: 2007-06-21
forum: Networking &amp; Wireless
---

### Post by purple melon on 2007-06-21
Hi all

I have been using Ubuntu 7.04 for a couple of weeks now and am so impressed I would like to dump windows completely, two problems though.

1. My work requires me to connect to their intranet with Sonicwall VPN client.
		Is there a Linux alternative to SonicWall?
		Is it possible to run SonicWall via Wine?

2. I need to use IE6/7 for an aspx web application.
		can this be run via wine?

any help appreciated, thanks

---

### Post by dashnak on 2007-06-21
Don't know about the 1st point, for the 2nd, take a look in:
[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

---

### Post by purple melon on 2007-06-21
Thanks to dashnak point 2 IE6 above has been fixed, very easy it was to.  cheers

---

### Post by purple melon on 2007-06-22
I have now installed Sonicwall via wine and imported the sonicwall config file which i presume has all the settings for the company VPN but when i try to run sonicwall the error "ISAKMP socket initialzation failed" sonicwall then starts with the error "failed to load IPSec driver". I'm not sure if this is a problem with wine or ubuntu?

Any help appreciated, thanks

---

### Post by ejs7597 on 2007-10-26
I also get that same error when the application starts.  Does anyone know how to make this work in Wine?

---

### Post by incudie on 2008-02-05
I've been having the same problem. Looks wine (in its current state) is unable to install the Virtual Network Adapter (not sure if that has something to do with the DNE). If your company has Sonicwall SSL VPN device, they have a Java VPN Client that I just got working but it doesn't work with the Firewall appliance.

---

### Post by Road on 2008-02-10
Why this may be obvious and not exactly what you want, I use virtualbox (great software by the way) and the sonic wall software via a virtual machine.  As far as I know sonic wall is pretty much proprietary garbage so it's going to be a long road trying to bypass it.  

We use openvpn and I think it's much better.  Tell your IT guys they can go to a completely free VPN client that is compatible with multiple OS's, easier to use and I will say better.  Internally we dumped Sonic Wall years ago and I just need to use it now for a few clients.

---

### Post by HDave on 2008-03-06
I have the same problem with sonicwall.  Apparently there is an answer in this thread:

[http://www.uluga.ubuntuforums.org/showthread.php?t=566019]("http://www.uluga.ubuntuforums.org/showthread.php?t=566019")

---

