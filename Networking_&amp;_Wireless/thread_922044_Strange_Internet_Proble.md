---
title: "Strange Internet Proble"
date: 2008-09-16
forum: Networking &amp; Wireless
---

### Post by jose_ramirez on 2008-09-16
Hi friends,

For several weeks now I have been experiencing a strange situation with my internet connection. There are several sites which I can't access or that are extremely slow. Or maybe I can access the site but when I try to do a specific action it goes in a timeout state. For example, I can browse amazon.com but when I try to add a new item to my cart I receive no response. Similar situation with my online banking... The thing is that sometimes it works and other times it doesn't. In fact, this message is been created on my Vista laptop because when I tried to submit the thread on my Kubuntu PC it didn't do anything. I try disabling IPV6 and also modified my sysctl.conf file to include the following:

net.ipv4.tcp_window_scaling = 0
net.ipv4.tcp_wmem = 4096 16384 131072
net.ipv4.tcp_rmem = 4096 87380 174760

But so far no luck, I also try changing my DNS to use OpenDNS with no luck... I'm a little frustrated... any help and/or advice will be really appreciated. My current kernel is 2.6.24-19-generic.

Regards,

Jose

---

