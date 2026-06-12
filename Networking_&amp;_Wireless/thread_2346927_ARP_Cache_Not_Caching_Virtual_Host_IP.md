---
title: "ARP Cache Not Caching Virtual Host IP"
date: 2016-12-20
forum: Networking &amp; Wireless
---

### Post by anspectrum on 2016-12-20
Hi,

I've this particular problem where I'm using a web application known as IOU-Web. This application is used to execute CISCO IOS software in a browser. Here is what topology looks like

[http://pasteboard.co/bZymURnlD.png](http://pasteboard.co/bZymURnlD.png)

And here is what interfaces config snap

[http://pasteboard.co/bZxvSsN6r.png](http://pasteboard.co/bZxvSsN6r.png)

Now the idea is that R1 should be able to access the host machine which is my Laptop (Ubuntu-12.04). When I ping from my laptop terminal to R1, R1 successfully caches the ARP entry against my laptop Eth1 MAC. However, Ubuntu does not cache / update the MAC address of R1. I used "tcpdump" to inspect the traffic and interestingly, I can see the ARP reply from R1. Then I also tried static binding of R1-MAC in the Ubuntu ARP table, but even after that I was unable to ping R1. Though a debug on R1 shows that it did send reply to echo requests (ping).

I hope I have explained this partular issue, but just to sum it up "Ubuntu machine is not updating its ARP-cache even though ARP replies are being recived". Earlier I had domne some googling and stumbled upon a post where it mentioned the similar issue but got resolved after disabling "Reverse Path Forwarding Kernel Parameter". That kinda made sense and I tried that solution as well by disabling "RP_Filter" using command 

```
sudo sh -c 'echo 0 > /proc/sys/net/ipv4/conf/all/rp_filter'
```
and
```
sudo sh -c 'echo 0 > /proc/sys/net/ipv4/conf/eth1/rp_filter'
```

But that didn't help either. Can someone please give some tip on possible course of action to resolve this issue.

Thanks and regards,

---

