---
title: "wireless won't get IP"
date: 2006-08-17
forum: Networking &amp; Wireless
---

### Post by savethesquirrels on 2006-08-17
I just switched from Suse 10.1 to Xubuntu. Lots faster on my old laptop, and I also switched because I heard the wireless support is better, and it is. But I still have an issue. I have a TrendNet TEW421PC PCMCIA wirless adapter. Ubuntu finds the card fine and I have wlan0 in my iwconfig. I set the essid, and the key, but it never associates with the AP. What I had to do in Suse before was actually manually configure the ap with the MAC address of the access point. The problem is I used to get the MAC by running "iwlist wlan0 scan" but now I get "wlan0 No Scan Results" grrr ... ;) I am su'd so I have rights. I tried running dhclient but of course it just sits there and keeps trying "DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4" 

Now I am at a loss ... I'm so close! hehe ... oh I did try a static IP as well but it did not work. Thanks!

---

