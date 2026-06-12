---
title: "I can't see my ESSID"
date: 2007-02-04
forum: Networking &amp; Wireless
---

### Post by PRICE on 2007-02-04
Hi,

I have P3 450mhz with 192mb ram desktop computer. I bought an Aztech Wireless card one year ago. In few days, I have installed Ubuntu 6.06 Drapper to it. I read a lot of pages documents to describe wireless Internet Connection to Ubuntu but I haven't been successful. These are the steps:

1. I am sure that I installed wireless card successfully. Also I installed wireless card driver using Windows driver which has been told at Wiki.
2. The parameter of showing ESSID of my modem is open.
3. I switched off filtering MAC address of the modem.
4. I saw some wireless connection without an ESSID name when I type iwlist wlan0 (i am sure it is wlan0) scan.

My wireless modem is Airties Rt-210.

Is there any suggestion?

Thank you...

PS: There is no problem on my Internet Connection. I have a laptop with Windows XP and I use Internet Connection without any error. If I solve this Internet Connection problem, I want to install Ubuntu to my laptop.

---

### Post by Kulgan on 2007-02-04
waddya get when you type ```
iwlist scanning
``` into the terminal?

---

### Post by PRICE on 2007-02-04
I saw another ESSIDs...

Actually, I solved this problem but new problem appears: When I disable networking key correction (WEP), I can see my ESSID. To connect my ESSID, I must also disable MAC filtering. But at the end, there is nothing to secure my wireless network. Now, I am reading new documents about security. Of course, I need help :lolflag: 

Thanks for your interest...

---

### Post by Kulgan on 2007-02-04
normally all you do is 

```

# iwconfig <interface> mode Managed channel <X> key <key in hex>
# dhclient <interface>

```

but i presume you have tried that? 

The fact that you can't see the essid when you turn off the wep implies that there is some other security feature linked with it on the router. Such as essid broadcast. 

I've just set up and (successfully) cracked my own network, so I'm not all that thrilled with WEP... could you post the appropriate section of the output of:

```
# iwconfig
```

there might be somthing someone has encountered before :D

---

