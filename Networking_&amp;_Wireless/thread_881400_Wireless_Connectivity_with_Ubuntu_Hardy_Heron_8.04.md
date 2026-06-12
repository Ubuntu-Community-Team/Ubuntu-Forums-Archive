---
title: "Wireless Connectivity with Ubuntu Hardy Heron 8.04"
date: 2008-08-06
forum: Networking &amp; Wireless
---

### Post by pixie44 on 2008-08-06
Hi ...
I am new to ubuntu.
I am having trouble in connecting to wireless internet. after much brainstorming and searching the internet for solutions i was able to have the wlan0 up and running

now my iwlist wlan0 scan list the rounters (including my own). the only hitch that i feel now is that wlan0 is setup using IPV6 and i dont think my router supports that.

I tried different options of disabling the IPV6 by ammending the /etc/modprobe.d/aliases but IPV6 is not going away.
Do note that when I use my eternet wire for connecting to Internet, it works fine (a bit slow though)
Please let me know if you guys can bail me out

-p

---

### Post by tuxxy on 2008-08-06
Have you checked the wireless guide

[https://help.ubuntu.com/8.04/internet/C/wireless.html](https://help.ubuntu.com/8.04/internet/C/wireless.html)

---

### Post by smalldog on 2008-08-06
add this to /etc/modprobe.d/blacklist with "blacklist ipv6", then reboot.

---

### Post by pixie44 on 2008-08-14
> **tuxxy said:**
> Have you checked the wireless guide

[https://help.ubuntu.com/8.04/internet/C/wireless.html](https://help.ubuntu.com/8.04/internet/C/wireless.html)

Thanks for quick response. I did and redid these steps but does not help. wired internet works like a charm but wireless is a problem

---

### Post by pixie44 on 2008-08-14
> **smalldog said:**
> add this to /etc/modprobe.d/blacklist with "blacklist ipv6", then reboot.

SD-

thanks for the reply. well when i do that i am unable to see any IPs on the network tools window. blacklisting IPV6 takes away both IPv4 and IPv6

---

