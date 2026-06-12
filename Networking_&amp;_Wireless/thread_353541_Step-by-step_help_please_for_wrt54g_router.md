---
title: "Step-by-step help please for wrt54g router"
date: 2007-02-04
forum: Networking &amp; Wireless
---

### Post by Roddo on 2007-02-04
hi Guys.

I am a noob when it comes to linux/ubuntu. 

Freshly loaded 6.1 and everything works dreamlike except I cant figure out how to configure/setup/install my Linksys wrt54g broadband wireless router. (I want to connect directly via lanport, rather then wirelessly.)

(on my win network, my Desktop PC connects to the internet via router using lan cable, and the laptop connects wirelessly)

I have duel boot, and the router works ok using WinXP.

I have messed around in the networking config but with no luck.

One thing I have noticed is that ubuntu bootup is a lot quicker if the router is switched off. If I turn it on, bootup is a heck of a lot longer, and as previously stated above, I cant seem to connect to the internet.

Would be greatful for a step by step (in layman's terms) process on how to resolve this.

Cheers!


Roddo

---

### Post by bnuytten on 2007-02-18
The boot is longer because... you don't get a DHCP address from your WRT54G very fast. You should normally not notice the difference. I have a similar setup and it works flawlessly.

Please post the output of
```
cat /etc/network/interfaces
ifconfig
```

---

### Post by sdide on 2007-02-18
hey, 

if you are directly connected to the wrt54g you should be able to see it.
Please post output from 

# ip link
# ip neigh
# dhclient eth0

If your network device is not eth0, then dhclient <whatever_your_network_device_is_called> :)

---

