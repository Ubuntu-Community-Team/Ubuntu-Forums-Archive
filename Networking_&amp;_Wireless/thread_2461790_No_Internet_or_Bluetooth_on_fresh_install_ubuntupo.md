---
title: "No Internet or Bluetooth on fresh install ubuntu/pop!_os"
date: 2021-05-06
forum: Networking &amp; Wireless
---

### Post by lishiyua on 2021-05-06
[COLOR=#242729][FONT=inherit]I did a dual boot on my new Asus G14 and followed the Ubuntu dual boot option. I noticed it was weird it didn't ask me to sign into my network. Now that I am in Ubuntu I noticed that there is no option for Network and Bluetooth as well. I don't have any wired connections either since I installed from usb, But I have connection on the windows side.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial][FONT=var(--theme-question-body-font-family)][FONT=inherit]edit: I also tried Pop!_OS in demo mode and it has the exact same issue. The Wifi card in the laptop is MediaTek Wi-Fi 6 MT7921 Wireless LAN Card, 802.11ax.[/FONT]
[/FONT]
[/FONT][/COLOR]

[https://imgur.com/gallery/nQFIO5H?fbclid=IwAR10kKr3nFfMWyyjkVheyUvZQZBGXMPEv6z1fQAlYbi1mJPKH6jQ2Vk1ZgE](https://imgur.com/gallery/nQFIO5H?fbclid=IwAR10kKr3nFfMWyyjkVheyUvZQZBGXMPEv6z1fQAlYbi1mJPKH6jQ2Vk1ZgE)

---

### Post by wildmanne39 on 2021-05-06
Hello and welcome to the forum, thread moved to networking and wireless.

---

### Post by mohanok on 2021-07-05
The same problem for me too in AUSU TUF 15. I could not able to get the  drive for MT7921 wifi.
I also tried changing the kernel to latest 5.12.10+ using mainline but still i could not able to solve the problem.

Any help?

---

### Post by xpuserpjc on 2022-04-06
When I booted from an Ubuntu USB, I was surprised to find only VPN or Proxy as network connection options. It took me awhile to find how to enable my WiFi driver that I knew was there. I found it under the "Software & Updates" > "Additional Drivers" tab. It showed my Broadcom driver listed but "Do not use the device" selected by default. Checking the "Use Broadcom..." button, "WiFi Not Connected" appeared in the Network settings window. I could then choose my LAN connection and enter its password. (I used the same approach when I installed Ubuntu to connect to the network and setup Livepatch.)

---

### Post by him610 on 2022-04-07
When you first installed Ubuntu there was an option to install third party drivers that you may have overlooked.

---

