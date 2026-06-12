---
title: "iPhone modem help"
date: 2008-09-16
forum: Networking &amp; Wireless
---

### Post by NoMax2 on 2008-09-16
Hello,

I have an iPhone 3G and NetShare. I want to use my iPhone as a modem. Netshare is an iPhone application that acts as a wireless SOCKS proxy.  I set up an ad-hoc wireless network between my Ubuntu PC and my iPhone. When it's up and running I can ping my iPhone address from my Ubuntu PC. I then go into Firefox and specify the iPhone IP as my SOCKS 5 proxy.

Now the problem. . .I have no DNS resolution, so if I enter "http://www.google.com" nothing happens...I need to enter "http://64.233.161.99" to get the Google page. Not too useful as-is!!!

I tried adding some public DNS server addresses in /etc/resolv.conf, no effect. I tried going into preferences and specifying the SOCKS address there, didn't help. I also tried to edit the advanced Firefox settings (through "about:config") telling it to use remote DNS through SOCKS, not even that helped

I need a solution that will pass all traffic through the iPhone's SOCKS proxy, and give me DNS. . .any clues as to what I can do?

Thanks in advance for any help you can give me.

NM2

---

### Post by dmizer on 2008-09-16
Try using OpenDNS dns servers: [https://www.opendns.com/smb/start/device/ubuntu](https://www.opendns.com/smb/start/device/ubuntu)

That may be enough to get you going ...

---

### Post by howL_ on 2008-09-16
In Firefox type 'about:config' in the address bar and hit enter.  Enter 'socks' in the filter box and hit enter.  Change network.proxy.socks_remote_dns to True.

---

