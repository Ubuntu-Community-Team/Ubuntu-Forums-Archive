---
title: "No Internet connection"
date: 2005-10-27
forum: Networking &amp; Wireless
---

### Post by tunnelblick on 2005-10-27
Hello.
I have a problem here. First, my network consists of 2 computers, one win2k, one ubuntu. The win2k is connected to a router by WLAN. As I haven't found by now an 11g-usb-stick working with my ubuntu, I wanted to use ICS, so that my linux can also access internet. But this didn't work. I was able to ping sites, but when i tried to surf or to run apt-get, no data was really transferred. When I was using Lynx, I could see that ubuntu found the Site but when the Site was to deliver data, nothing happened. It looked like only icmp was getting through. Today, I plugged in an 11b-usb-stick and it works just fine. It connects to the ap and everything. After setting the right IP-Adress for the net with gateway and dns-lookup (both router-ip), I tried to surf and again, nothing happens! I can only do "ping". Nothing more. Do you have any idea on this?

Regards
Tunnelblick

---

### Post by mlomker on 2005-10-27
> Do you have any idea on this?


If you are assigning a static address then you also need to edit the /etc/resolv.conf file to configure your DNS server entries.

---

### Post by tunnelblick on 2005-10-28
Yes, of course I did that :) The problem seems to be another one. If I use Lynx to surf the web, it comes to the point (when it finds the name of the site): "HTTP request sent; waiting for response." But there is no response. Only ping seems to answer me. If I do telnet "site" 25, I also get the typical messages. I just can't really "surf the web". And thus, I can't do an apt-get update or something. Btw, the firewall is _not_ running.

Tunnelblick

---

### Post by mlomker on 2005-10-28
Are you still using ICS?  I'm not clear on what you are trying right now.

Have you already configured the [proxy settings]("http://www.ubuntuforums.org/showpost.php?p=364026&postcount=2") for terminals?

---

### Post by tunnelblick on 2005-10-28
I want to connect to the internet :)
the problem is: it does not *fully* work. i tried to connect to my university via ssh and worked without a problem. i can even access my router via "http://fritz.box" but when i try to go somewhere "outside" like slashdot or something, there just comes nothing. although it looks like dns works. It does not work via ICS (which *has* worked once) and it does not via WLan (but it does via WLan with my 2k). and, as i said, ping also works.

???

---

### Post by tunnelblick on 2005-10-28
I just read about the ipv6-problem and thought, this could be the problem. Well, in my /etc/modprobe.d/ there were one aliases and one aliases~. The first one had ipv6 off, the other one enabled.  I deleted the "backup" and changed to "ipv6" instead of "off". Nothing changed I still could ping but could not browse. Turning it off again didn't change anything. Is there another way to en-/disable ipv6? How can I check what is used?

---

