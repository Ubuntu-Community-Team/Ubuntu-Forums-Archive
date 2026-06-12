---
title: "another ethernet problem"
date: 2006-12-04
forum: Networking &amp; Wireless
---

### Post by kubo85 on 2006-12-04
My problem is, that on my new HP laptop I`m unable to connect to ethernet. My eth. card is Broadcom NetXtreme and ubuntu recognized it without any problems and it even worked, when I connected it to my home PC.
When I wanted to connect to network at my boarding house, it just won`t work. Network status of eth0, which I believe is my eth.card, keeps switching from idle to receiving and keeps receiving until I disable it, but I`m unable to connect to internet.
I`m running latest Ubuntu 6.10. Yesterday, while I was still at home, I even had it updated and downloaded some apps. The network works fine with windows XP and also on my old desktop with DamnSmallLinux and Win`98. I`m using DHCP and I tried using ipconfig release when turning off windows.
Thanks for any replies

---

### Post by trubblemaker on 2006-12-06
here post some info and I'll try and help you out:

```

ifconfig
iwconfig
iwlist scan
lspci | grep ontroller
/etc/network/interfaces
dmesg | grep bcm

```

---

