---
title: "Wireless network Card not pulling IP Address"
date: 2007-03-18
forum: Networking &amp; Wireless
---

### Post by 429148 on 2007-03-18
I cannot get my Wireless card to pull down an IP Address.  I have changed my router to WEP.  I have followed all of the directions from the Unbuntu On-line set-up guide.  I can see the wireless network.  But everytime I try to connect.  No good.  When I run a conf command I see all of the information regarding the card, except an IP Address as seen in the example image.  Does anyone have any ideas as to what I can do to get the ath0 to pull an IP Address from my DHCP Router.  Thanks.

---

### Post by Floppyjoe on 2007-03-18
> **429148 said:**
> I cannot get my Wireless card to pull down an IP Address.  I have changed my router to WEP.  I have followed all of the directions from the Unbuntu On-line set-up guide.  I can see the wireless network.  But everytime I try to connect.  No good.  When I run a conf command I see all of the information regarding the card, except an IP Address as seen in the example image.  Does anyone have any ideas as to what I can do to get the ath0 to pull an IP Address from my DHCP Router.  Thanks.
We need to know a bit more information. How are you trying to connect? Are you using Network-Manager? If not what is in your /etc/network/interfaces file.
```
sudo gedit /etc/network/interfaces
```
What is the output of:
```
iwconfig
```

---

