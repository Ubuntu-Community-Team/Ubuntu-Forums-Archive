---
title: "Help with wg111 v2 and ndiswrapper"
date: 2006-10-02
forum: Networking &amp; Wireless
---

### Post by Yurij on 2006-10-02
I have a wg111 v2 from netgear.
I have followed these steps:
[http://ubuntuforums.org/showthread.php?t=51993](http://ubuntuforums.org/showthread.php?t=51993)

And added this to /etc/network/interfaces:
```

auto wlan0
iface wlan0 inet dhcp
        hostname <hostname>
        wireless_mode managed
        wireless-essid <essid>

```
And replaced <hostname> and <essid>.

But this makes me only able to acsess my router
and the internet for awhile then I have to
reboot the computer. :( 

Someone who knows how to fix this?

---

### Post by pjbgravely on 2006-10-21
I just ran into a similar problem. My wireless worked like I was running Windows. I would still be connected but the connection would drop all packets. If I shut off the connection in Network-manager and then restarted it it would work again for a while. I doubt if a reboot was required. The problem turned out to be the wireless access point. After changing it, I am back to rock solid wireless like only Linux can give you.

Paul

---

### Post by Yurij on 2006-10-22
> **pjbgravely said:**
> I just ran into a similar problem. My wireless worked like I was running Windows. I would still be connected but the connection would drop all packets. If I shut off the connection in Network-manager and then restarted it it would work again for a while. I doubt if a reboot was required. The problem turned out to be the wireless access point. After changing it, I am back to rock solid wireless like only Linux can give you.

Paul

What exactly was it that you changed?

---

### Post by pjbgravely on 2006-10-26
> **pjbgravely said:**
>  After changing it, I am back to rock solid wireless like only Linux can give you.

I Changed the WAP AKA the wireless router DSL modem, and put another wireless router on the network after it. 

Paul

---

