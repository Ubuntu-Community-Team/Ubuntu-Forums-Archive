---
title: "Lost internet after restart."
date: 2008-01-31
forum: Networking &amp; Wireless
---

### Post by kerunt on 2008-01-31
Hi All,

I installed Ubuntu 7.10 today, and did the updates. Everything was working great.

I then decided to use the "advanced visual effects" which required some nvidia drivers. I let the system do everything, it then asked me to reboot. I ignored it and kept using the system for 10-20 minutes. Everything was fine. I then rebooted, the visual effects came on, but the internet disappeared.

I tried rebooting, removing the nvidia drivers (disabling them), and the following:

/etc/init.d/networking restart

No luck.

My /etc/resolv.conf is as follows:

```
nameserver 192.168.0.1
```

... which is my router.

Help please?

//edit

I should mention that my router sees the Ubuntu computer.

//edit2

I can browse my windows desktop's shares from the Ubuntu laptop...

//edit 3

Can't connect to my wireless network.
Connected to my neighbour's network, but still no internet :(

---

### Post by kerunt on 2008-01-31
Well what do ya know... It's the morning after and internet suddenly works.

I'm used to this kind of "experience" with Windows, didn't expect it here :(

---

### Post by dannyboy79 on 2008-01-31
most consumer routers are not real dns servers, they only forward requests. so sometimes things like this happen, it's no fault of linux. you could hard code the dns servers into your resolv.conf  like  following guide points out:
[http://www.cyberciti.biz/tips/linux-how-to-setup-as-dns-client.html](http://www.cyberciti.biz/tips/linux-how-to-setup-as-dns-client.html)
you can find out what your dns servers are by logging into your router, they should be somewhere in there or you could call the isp. Or you can even use opendns servers which 
are:
208.67.222.222 
208.67.220.220
per this website. [https://www.opendns.com/start](https://www.opendns.com/start)

---

### Post by Crimson_Wake on 2008-01-31
Use opendns.com servers.  I have had MUCH better speeds, and I need alternative DNS entries for routing my modem anyway.

If you go into command or terminal (tracert in windows) you can actually find out how many jumps it takes the signal to get to your PC from the DNS.  Generic ones (especially big city ISPs) take a lot of jumps and slow your connection down.  I have a Swedish DNS and it's three jumps to my flat in Chicago.  

Fancy that!

Now if I could only get my bloody internet to work wirelessly on my laptop, I'd be set.

---

