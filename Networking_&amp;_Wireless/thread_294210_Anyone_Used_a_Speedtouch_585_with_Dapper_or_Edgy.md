---
title: "Anyone Used a Speedtouch 585 with Dapper or Edgy?"
date: 2006-11-06
forum: Networking &amp; Wireless
---

### Post by JamesNorris on 2006-11-06
I'm planning on setting up a wireless network in my house. I was looking at integrated adsl modems with wireless routers and I saw the speedtouch 585. 

I'm currently using a 330 modem so I figure the dial scripts would still be the same, or similar, but I was wondering if anyone else has any experiences of this model under dapper or edgy?

---

### Post by raymanoz on 2006-12-07
Hi James,

yeah, I've upgraded from Dapper to Edgy and currently use this modem as the gateway for my place. Unfortunately I'm currently experiencing problems where the /etc/resolve.conf gets the nameserver lines replaced with the IP Address of the router whenever I reboot (or dhcp renew).

Apparently it should work as the nameserver (and it does in windoze), but when this is the case, my Edgy install cannot resolve names to ip addresses.

I have to change the nameserver lines in /etc/resolve.conf to the nameservres that my ISP provide to get anything to work. Currently don't know the correct way to fix this. If anyone knows the right thing for me to do (or even a good temp workaround), that'd be excellent!

-Raymond Barlow

(2 minutes of googling later): checkout this post, it resolved my problems: [http://www.ubuntuforums.org/showthread.php?t=305275](http://www.ubuntuforums.org/showthread.php?t=305275)

---

### Post by mips on 2006-12-07
> **JamesNorris said:**
> I'm planning on setting up a wireless network in my house. I was looking at integrated adsl modems with wireless routers and I saw the speedtouch 585. 

I'm currently using a 330 modem so I figure the dial scripts would still be the same, or similar, but I was wondering if anyone else has any experiences of this model under dapper or edgy?

You do not need dial-scripts if you use it as a Router, yes it's a router.
I prefer Linksys, Netgear, Billion. But it should work fine.

---

