---
title: "Wireless Disabled"
date: 2010-11-05
forum: New to Ubuntu
---

### Post by CGumpLinux on 2010-11-05
Hi there I am really new to linux, but so far i have been able to do pretty well the issue i am having is my wireless connection is disabled and i am not sure what to do to fix it.  
so far i have been able to research and find this 

rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
home@home-MX6438:~$

but i am not sure how to fix this problem... from some things i have gathered i might have to reinstall windows and change some setting in there to fix this....  
so i know this post is really unclear hopefully someone can make some sense of it and give me some feed back

gateway mx6438  broadcom wireless

---

### Post by cariboo on 2010-11-05
What broadcom chipset does your device use? To find out, open an Applications->Accessories->Terminal and type:

```
lspci | grep Network
```

the output should look something like this:

```
01:00:0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
```

As you can see from the output above my netbook uses the BCM4312 chipset.

---

### Post by CGumpLinux on 2010-11-05
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)


so BCM4318

---

