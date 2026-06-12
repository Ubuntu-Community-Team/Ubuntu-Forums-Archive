---
title: "Minor mtu troubles"
date: 2008-04-16
forum: Networking &amp; Wireless
---

### Post by Old Marcus on 2008-04-16
I know stuff like this has been posted before and I read a good chunk of it, but I'm a bit confused, and I would like someone to explain a couple of things:
```

auto lo
iface lo inet loopback
address 192.168.1.47
netmask 255.255.255.0
gateway 192.168.1.0
mtu 1492

```
(last four lines added by me)
I know in the second line I have to put my device in there somewhere (eth0) but I'm not sure where. If I do, will this make my mtu changes permanent?

---

### Post by Old Marcus on 2008-04-16
Ok, slightly more disastrous, I did```
sudo ifdown eth09
``` and it told me that 'eth0 had not been configured' I rebooted and I can't access any website whatsoever. I'm currently running off my Windows install. I tried ```
sudo ifup eth0
``` but it told me it failed to bring eth0 up.

So all of a sudden I'm stuck without internet access on linux. is there a way to get it back up again?

---

### Post by Old Marcus on 2008-04-16
No problem now, changed my network configuration to dhcp and it works fine. :)

---

### Post by kutjara on 2008-04-16
> **Old Marcus said:**
> No problem now, changed my network configuration to dhcp and it works fine. :)

That seems to be the safest approach. I've seen lots of posts from people having big problems trying to set static IP addresses. Usually, enabling DCHP and getting rid of the references to static addresses  at least gets them back online.

---

### Post by Old Marcus on 2008-04-17
I still can't keep my mtu permanent for some reason.
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
address 192.168.1.47
netmask 255.255.255.0
gateway 192.168.1.0
mtu 1492
```
That's my interfaces file from etc/network/. Is there something I've missed out? because I still can't keep my mtu to 1492, every time I reboot it resets to 1500.

---

### Post by Old Marcus on 2008-04-17
*bump* Any help guys?

---

### Post by kutjara on 2008-04-17
> **Old Marcus said:**
> I still can't keep my mtu permanent for some reason.
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
address 192.168.1.47
netmask 255.255.255.0
gateway 192.168.1.0
mtu 1492
```
That's my interfaces file from etc/network/. Is there something I've missed out? because I still can't keep my mtu to 1492, every time I reboot it resets to 1500.

I just did a little googling and found this:

[http://ubuntuforums.org/showthread.php?t=3985](http://ubuntuforums.org/showthread.php?t=3985)

The third and fourth posts seem most relevant. Let me know if they help.

---

### Post by Old Marcus on 2008-05-03
Sorry to bump, but thanks, post 4 was most useful. :)

---

