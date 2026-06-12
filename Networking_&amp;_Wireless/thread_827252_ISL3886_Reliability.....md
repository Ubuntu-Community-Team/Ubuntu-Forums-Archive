---
title: "ISL3886: Reliability...."
date: 2008-06-12
forum: Networking &amp; Wireless
---

### Post by matc on 2008-06-12
Back in gutsy I was using KNetWorkManager and ndiswrapper to configure my Intersil Prism with 54Mbit and WPA-PSk connection (the open source prism54 driver was painfully slow with download rates below 30k/s....).

But in hardy I have 2 choices:
- ndiswrapper cannot connect to ANY WPA-enabled network (it just never seems to succeed authentication)
- the open-source p54pci driver can sometimes connect to the network, but somehow after a while new TCP/IP connections simply starve to death by not receiving more than about a packet per minute! Old established connections still work without any issues. Also ICMP pings are not a problem at all... As you might imagine, surfing the web is quite impossible or at least hard to do! 
Solution: Sometimes a simple reconnect is sufficient, sometimes you need to rmmod the driver and modprobe it again. Then it works fast again (until the next slowdown)

Can anybody give me a hint what might be wrong or how to resolve this?

---

### Post by matc on 2008-06-15
Suppose I could resolve this myself...

After I moved out of my flat with the laptop on it didn't detect 2 networks but 13 wireless networks where almost all are misconfigured with standard SSID and partly equal channels!!!

When I was at my parent's house (far out of town) there wasn't any problem at all :)


(Maybe also the crappy DLink router might be an issue - had 3 DLink routers and all were crappy and buggy...)

---

