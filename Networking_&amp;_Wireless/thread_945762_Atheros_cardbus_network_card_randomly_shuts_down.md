---
title: "Atheros cardbus network card randomly shuts down"
date: 2008-10-12
forum: Networking &amp; Wireless
---

### Post by klepto on 2008-10-12
I am using Ubuntu proprietary drivers for my Netgear wireless card.
Here is the only thing I see in syslog:

86827.418868] ADDRCONF(NETDEV_UP): ath0: link is not ready
[86827.426018] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[86837.549477] ath0: no IPv6 routers present
[86850.401548] ADDRCONF(NETDEV_UP): ath0: link is not ready
[86850.405951] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[86861.225862] ath0: no IPv6 routers present
[177105.242051] ADDRCONF(NETDEV_UP): ath0: link is not ready
[177105.246388] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[88559.958519] ath0: no IPv6 routers present

I also have a Broadcom wireless card but ndiswrapper crashes Ubuntu and at times I can't even boot into it so I am using this Netgear card that has an Atheros chipset. 

Any ideas on what is happening?

Thanks.

---

### Post by inxygnuu on 2008-10-12
Wait so do you want to use the broadcom card?

---

### Post by klepto on 2008-10-12
It isn't really necessary that I use the Broadcom card.
I just want to find out why my Netgear wireless card is randomly shutting off.

---

### Post by inxygnuu on 2008-10-12
No idea, do you change anything while you are using it, like the power, starting the browser, etc...?

---

### Post by klepto on 2008-10-12
It does this randomly and at times when I am not even near the computer.
Does Ubuntu still use madwifi? I had no problems using this card in the past using Madwifi.

---

### Post by inxygnuu on 2008-10-12
yes, it does. I used to use it.:)

---

