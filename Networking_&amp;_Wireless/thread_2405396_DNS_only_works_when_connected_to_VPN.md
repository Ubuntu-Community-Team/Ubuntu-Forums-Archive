---
title: "DNS only works when connected to VPN"
date: 2018-11-05
forum: Networking &amp; Wireless
---

### Post by john-flournoy on 2018-11-05
OS:  Ubuntu 18.04  

When connected via wired ethernet, I can ping various ips and  domains like 1.1.1.1 and google.com. I can use nslookup to lookup ips of  hosts I've never accessed before like `nslookup yeehaw.com`. However,  in firefox, I can't access any websites -- firefox gives "The connection has timed out". I've checked that my proxy  server is not set (I've also tried to set it to automatically set or to  use system settings). I've tried `wget` as well, and it also cannot  resolve host names. I've tried setting the dns ip addresses manually to  just use 1.1.1.1 or 1.0.0.1 and not the gateway's suggest IPs (by setting the DNS auto option to off in NetworkManager) but that doesn't allow any  services (e.g., ping no longer works). In other words, the automatically configure DNS is giving me some traction, and it appears I can't even connect to public DNS ips. I *can* see internal hosts, like stuff on the LAN (in Files) and internal webpages hosted on the LAN. If I connect to an internal VPN and use the required proxy, I *can* connect to  websites via firefox and wget etc. 

Thanks for your help, and pardon me if I haven't included relevant or standard output -- obviously, a first-time poster here.

~j

---

### Post by TheFu on 2018-11-06
The ISP might be blocking all external DNS requests.  Many will have account settings to allow local DNS control.  If you can ping 1.1.1.1, but can't use it for DNS, that would be my first guess - the ISP is blocking outbound DNS. They do this as a security feature, since taking over the DNS on a computer means that spoofing google.com, microsoft.com is much easier.

I saw in another thread here where Network-Manager was causing issues recently.  Another volunteer suggested switching to wicd instead or manually configuring the network settings.  I have no idea about network-manager. When it was first release, it didn't work for me at all, but that was years ago.  I remove it and setup static IPs on all my systems using either the config files or DHCP reservations in the DHCP server.  For my laptop, I use wicd to control wifi access.

I know nothing about 18.04 except that the underlying network configuration tools were all changed.  We still use 16.04 here.

Anyways, welcome to the forums.

---

### Post by john-flournoy on 2018-11-06
Thanks for these suggestions. I have a ticket with local IT as well. It does really feel like the sort of situation you're describing -- the device is new to the network, so perhaps not registered properly. I'll post back if this is the case. Trying to do all I can to rule out a problem with my system.

---

