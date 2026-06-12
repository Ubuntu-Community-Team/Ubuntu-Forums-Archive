---
title: "No dns, no ping, both wifi and ethernet connections no internet"
date: 2007-12-25
forum: Networking &amp; Wireless
---

### Post by nosoup4you on 2007-12-25
I can connect to my local network router (dd-wrt) and get an ip address from wifi without a problem. same thing with wired connection. problem is internet doesn't work. this just started happening. i cannot ping google.com, yahoo.com, etc. I can ping some ip addresses on the internet, but not my local router's ip, or anyone else on the LAN.

This just started about a month after I setup dns local caching with directions from [http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/](http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/)

So I removed the settings I added for this, and removed dnsmasq. however, this did not change anything. I still cannot get on the internet, connect to the router, ping the router, or anything else. any ideas what might be the problem? THANKS!

---

### Post by nosoup4you on 2007-12-26
Any help would be greatly appreciated!

Happy holidays!

---

### Post by nosoup4you on 2007-12-28
Still not luck. Tried using another router at friends house and also directly to cable modem with no luck. I can ping internet IP addresses though. Can't visit any domains. Everything works fine in vista still.... *gulp*

Any ideas?

---

### Post by carverj on 2007-12-28
Did you keep a backup of your system before altering the config files?
If you follow the link in my signatures for easy system backup (which I am in the middle of doing now!), this will ensure that messed up config files do not kill your system again.
Always backup any config file you are altering.

> So I removed the settings I added for this, and removed dnsmasq. however, this did not change anything. I still cannot get on the internet, connect to the router, ping the router, or anything else. any ideas what might be the problem? THANKS!

Just wondering, have you removed all possible settings that could be altered?
Such as /etc/resolv.conf and /etc/http3 or whatever and the zone file

Possibly remove all dnsmasq stuff and try again with:
[http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html](http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html)
[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/dns.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/dns.html)

---

