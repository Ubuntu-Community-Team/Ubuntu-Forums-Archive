---
title: "US Robotics Sportster Flash Serial Modem"
date: 2005-04-08
forum: Networking &amp; Wireless
---

### Post by No-One on 2005-04-08
Hi there,

I've been having trouble with my serial modem since I tried Warty a few months back. I've installed Kubuntu Hoary today in the hope that my modem problems would be fixed, but no such luck.

I didn't think it would be so difficult to get a reasonably popular serial modem to work. What happens is that I can get it to dial, negotiate a link, but just before pppd starts (I think) something goes wrong, because the connection fails and disconnects.  ](*,) 

Here's a screenshot of the kind of garbage that was getting spat at my connection log. 

[[img]http://img210.exs.cx/img210/6296/snapshot15so.th.png[/img]](http://img210.exs.cx/my.php?loc=img210&image=snapshot15so.png)

Any ideas as to what could be wrong? I've also got some other issues, such as some screen bluring, but I'll look into that later.

Thanks!

---

### Post by No-One on 2005-04-10
One bump before I give up on Linux, again :(

---

### Post by bnutting on 2005-04-11
Do you see any messages in /var/log/messages ? It looks like you may have a ppp connection, that might be what the 'garbage' is that you see on your terminal window.

---

