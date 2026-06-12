---
title: "Cannot access Huawei through browser"
date: 2017-10-21
forum: Networking &amp; Wireless
---

### Post by lautaroo on 2017-10-21
Hi. I have a Huawei HG8245 and I'm trying to access the router page but it's impossible. The default IP is supposed to be 192.168.100.1 but when I try to enter it it keeps loading or I get a ERR_CONNECTION_REFUSED. 
Tried with Chrome and Firefox. I also tried over Wi-fi and Ethernet, and with "https://". I have no proxy and Ubuntu firewall seems to be deactivated. I tried also resetting the router and trying with the IPv6 address.
Also, my DNS seems to be the same as the router IP, has it anything to do with this?

Thanks.

---

### Post by praseodym on 2017-10-22
Please show the output of
```

route -n
```
Can you ping it?
```

ping -c 4 192.168.100.1
```

---

