---
title: "multiple ips in ubuntu after giving the ip address.lan is nt working"
date: 2014-01-20
forum: Networking &amp; Wireless
---

### Post by bhanuprakash2 on 2014-01-20
hi all,


in my desktop i am having only one lan card..i given 4 i ips in my desktop ...

sudo gedit /etc/network/interfaces   by using these command  i have given ip,netmask,gateway...

after restarting the network i am unable to connect my lan...lan popup will be not be displaying ..after rebooting my sysetm also lan is not connecting ..????

plz help me

---

### Post by Iowan on 2014-01-20
Please post */etc/network/interfaces*.
Network Manager probably won't touch an interface defined there (without some "adjustment").

---

### Post by Zhivargo on 2014-01-20
```
ifconfig eth0
```

---

