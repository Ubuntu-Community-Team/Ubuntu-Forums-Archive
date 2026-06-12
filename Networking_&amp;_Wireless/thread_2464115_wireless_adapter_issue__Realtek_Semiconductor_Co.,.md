---
title: "wireless adapter issue : Realtek Semiconductor Co., Ltd. RTL810xE PCI Express Fast Et"
date: 2021-06-24
forum: Networking &amp; Wireless
---

### Post by zelandroid009 on 2021-06-24
Today, at approximately 4 pm my wireless connection stopped working. I rebooted the router several times. I used settings to forget the wireless connection. I rebooted my laptop. Despite this, I keep getting the following error: Activation of network connection failed.

I'm confused and frustrated by all this.

John

---

### Post by chili555 on 2021-06-24
> Realtek Semiconductor Co., Ltd. RTL810xE PCI Express Fast EtThat is an ethernet adapter, not wireless. Let's see what your wireless actually is:

```
lspci -nnk | grep 0280 -A3
```

---

### Post by zelandroid009 on 2021-06-24
My apologies. I may have copied the wrong information from the wireless-info.txt file. This is the correct wireless adapter:
Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01)

I'd post that txt file, but I don't know how. Sorry.

John

---

### Post by chili555 on 2021-06-24
> I'd post that txt file, but I don't know how.Paste it here and give us the link: [http://paste.ubuntu.com](http://paste.ubuntu.com)

---

### Post by zelandroid009 on 2021-06-24
I hope that I've done this correctly, lol.

[https://paste.ubuntu.com/p/5PCWypf7fC/](https://paste.ubuntu.com/p/5PCWypf7fC/)

---

### Post by chili555 on 2021-06-24
You have the wireless turned off in Network Manager. 
> 0: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: no

> wlp13s0   Interface doesn't support scanning : Network is down

That prevents quite a lot of useful information from being gathered and reported. Please turn on the wireless, detach the ethernet, run the script again and give us a new paste.

---

### Post by zelandroid009 on 2021-06-24
I thank you for all your support so far. To create the wireless-info.txt file I posted, I had to use the ethernet connection for the wget output. With the ethernet disabled, the wgett command won't run because the wireless connection fails.

Is there another command I can use to gather the information you seek?

---

### Post by zelandroid009 on 2021-06-24
I think I've got the information you require. I'll post it in a few moments. I thank you for your patience.

---

### Post by zelandroid009 on 2021-06-24
I think this is the correct info:

[https://paste.ubuntu.com/p/TpGc5SqdqR/](https://paste.ubuntu.com/p/TpGc5SqdqR/)

---

### Post by zelandroid009 on 2021-06-25
Update...I had a tech from my internet provider in to look at things this morning. We narrowed the issue down to 2.4 GHz connectivity. He believes there's something interfering with connections on that bandwidth. 5 GHz works fine, which is why all my other devices work ok. My solution is to buy a dual-band USB dongle.

Thank you for your generous help. Much appreciated.

---

