---
title: "Restart the wifi connection"
date: 2008-11-27
forum: Networking &amp; Wireless
---

### Post by Telémakhos on 2008-11-27
Hi, my RTL8187 sucks. It goes down every other minut and I've to restart the whole system to bring it up... How can I restart the wifi connection or network without restarting ubuntu?

Don't tell me...

```
sudo /etc/init.d/networking restart
``` 

...cos doesn't work

Thanks =)

---

### Post by rlzyoner on 2008-11-27
You could just take down the adaptor and then bring it back up again

sudo ifconfig ath0 down
sudo ifconfig ath0 up

---

### Post by kevdog on 2008-11-27
Can you post ifconfig
 

Most likely your interface is not going to be ath0

---

