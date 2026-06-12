---
title: "Ubuntu 22.04 dns issues with T-Mobile 5G Gateway"
date: 2023-03-18
forum: Networking &amp; Wireless
---

### Post by ben187 on 2023-03-18
I have several devices on my new T-Mobile 5G gateway - 2 chromebooks which connect via wifi, and a single Ubuntu 22.04 desktop, which uses a wired connection.

Both chromebooks work correctly on the gateway, without making any changes from my previous comcast access point, only had to select the new 5G gateway and enter the password, and everything works fine.

The desktop however, does not function correctly: if connected wired to comcast router, everything works.  If connected instead wired to T-Mobile, (the same one the chromebooks are connected to), it appears to have a problem with DNS.  I have a static ip address of 192.168.1.208 assigned to my desktop.  When I use a webpage to get to Google.com, it works; if i try to get to DuckDuckG.com, it times out.  The chromebooks are able to get to both Google.com and DuckDuckGo.com.

Any suggestions on what the problem is?  I feel that it is with Ubuntu 22.04, since the chromebooks are able to access all web pages, but desktop can only find some sites.  Note that my comcast network if ipv4, and the Tmobile gatewayis ipv6.

I made some suggested changes to /etc/systemctl/resolved.conf, setting the DNS=DNS=208.67.222.222 208.67.220.220 (among others when testing - none worked), and tried setting DNSSEC=false, DNSSEC=no, DNSSEC=yes, and none of these settings worked.

Anyone with any suggestions?

Thanks,

BBQBailey, Georgia USA

---

### Post by TheFu on 2023-03-19
The resolved.conf settings you posted appear to be in the wrong format.  Rather than interpreting, just post the text and wrap it inside forum 'code tags'

BTW, do you really want to use Cicso's DNS?
Because you aren't using DHCP, the router's DNS isn't being picked up automatically.  You need to specify
```
DNS=1.0.0.1
FallbackDNS=1.1.1.1
```
one per line, then restart
```
sudo systemctl  restart  systemd-resolved
```

BTW, ALE meets virtually at 3pm today, if you need more help, or I got that last command wrong.  I don't use resolved myself.

---

### Post by ben187 on 2023-03-19
Thanks everyone for the help!

I was able to fix the problem in this manner:

How I fixed: on Ubuntu 22.04, go to Settings, Network, Wired 1 (yours may be named something else), settings gear, ipv6 tab.  Change ‘IPV6 Method’ from ‘Automatic’ to ‘Automatic, DHCP only.


 


I was able to then click between the two selections, in my case “Wired 1” and “Profile 1”, and that case, it toggled my ip address from 192.168.1.208 to 192.168.12.79, and changed the default router from 192.168.1.1 to 192.168.12.1.  


 


If after you changed the settings, it doesn’t work, try restarting the service using:


sudo systemctl restart systemd-resolved.service


 


Thanks everyone for your assistance!

---

