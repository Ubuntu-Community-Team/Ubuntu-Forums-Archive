---
title: "Help with ordinary LAN connection under Kubuntu Feisty"
date: 2007-08-29
forum: Networking &amp; Wireless
---

### Post by mcms on 2007-08-29
I've just installed Kubuntu Feisty on my ASUS W7S laptop and tried to connect to my desktop pc runnning Windows XP through Wired LAN.
I have configured device eth0 with following:
inet addr:192.168.0.2 Bcast:192.168.0.255 Mask:255.255.255.0
and my desktop IP address is 192.168.0.1 .

But unfortunately I can not ping my desktop and it says "Destination host unreachable".

The interesting thing is that I have successfully connected to my desktop with Vista on my laptop with te same configuration at the same time.

lspci | grep Ethernet:
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI EXPRESS Gigabit Ethernet controller (rev 01)

---

### Post by noob12 on 2007-08-29
Can you check the link light and also post the result of

```

sudo ethtool eth0

```

If the link state is down (link light off or ethtool reports Link detected: no) try the solution in this posting:

[http://ubuntuforums.org/showpost.php?p=3209279&postcount=18](http://ubuntuforums.org/showpost.php?p=3209279&postcount=18)

([COLOR="Red"]UPDATE:[/COLOR]  Please use the following HOWTO:  [http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448))

Otherwise let me know.  We'll need more diagnostics.

---

### Post by mcms on 2007-08-29
Yes, Dual Booting with Windows was the problem.

```
#ethtool eth0
...
Link detected: no
```

The last line on output says that link is not detected while it was surely connected.
I just enabled the Wake-On-Lan ability in Windows Device Setting and the problem fixed.

Thanks.

---

