---
title: "unstable wifi connection ubuntu 20.10"
date: 2020-12-21
forum: Networking &amp; Wireless
---

### Post by ciszko on 2020-12-21
Hi!
I'm totally new with ubuntu, I switched to it from windows a week ago. And here is my problem. I have terribly unstable connection with my home wifi while I'm in my room. It's disconnecting constantly and with every reconnection asking for a password to this wifi. When I'm closer to my router it happens less often. None of my family have the same issue. I don't know how I can fix this. 

Here is my wireless-info: [https://pastebin.com/xirGkrXW](https://pastebin.com/xirGkrXW)

I hope someone knows how to solve this problem... Thank you in advance!

---

### Post by morrownr on 2020-12-22
The first thing that caught my attention is that your router seems to be using the same name for both the 2g and 5g bands. I'd recommend changing that. Here is a list of things I have learned over the years regarding wifi routers:

Recommended Router Settings for WiFi:


Note: These are general recommendations based on years of experience but may not apply to your situation so testing to see if any help fix your problem is recommended.


Security: Use WPA2-AES. Do not use WPA or WPA2 mixed mode or TKIP.


Channel Width for 2.4G: Use 20 MHz fixed width. Do not use 40 MHz or 20/40 automatic.


Channel width for 5G: Using a 40 MHz fixed width may help in some situations.


Channels for 2.4G: Use 1 or 6 or 11. Do not use automatic channel selection.


Mode for 2.4G: Use G/N or B/G/N. Do not use N only.


Network names: Do not set the 2.4G Network and the 5G Network to the same name. Note: Many routers come with both networks set to the same name.


Power Saving: Set to off. This can help in some situations. If you try turning it off and you see no improvement then set it back to on so as to save electricity.

---

### Post by chili555 on 2020-12-24
> Power Saving: Set to off. This can help in some situations. If you try turning it off and you see no improvement then set it back to on so as to save electricity.You can do this easily from the terminal:

```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```I also recommend that you set your router to a fixed, non-overlapped channel: [https://www.metageek.com/training/resources/why-channels-1-6-11.html](https://www.metageek.com/training/resources/why-channels-1-6-11.html)

You can find out what channels are the least occupied in your setting with:

```
nmcli device wifi list
```

---

