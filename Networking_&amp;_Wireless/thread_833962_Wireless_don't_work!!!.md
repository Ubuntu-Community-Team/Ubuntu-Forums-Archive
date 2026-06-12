---
title: "Wireless don't work!!!"
date: 2008-06-19
forum: Networking &amp; Wireless
---

### Post by __hj__ on 2008-06-19
Hi, I am using a Dell Latitude D531 and the wireless won't work.. When I click on the internet icon it just says:
Wired network
Manual configuration...

How can i make the wireless work?

---

### Post by zxscooby on 2008-06-19
is the wireless card turned on?
what is the card type ?
```
lspci | grep Network
```

---

### Post by __hj__ on 2008-06-19
How to see if the card is turned on?
I think the card name is "Dell Wireless 1505 Draft 802.11n WLAN Mini-Card".

---

### Post by __hj__ on 2008-06-19
I tried this but it didn't work: [http://ubuntuforums.org/showthread.php?t=769990](http://ubuntuforums.org/showthread.php?t=769990)

---

### Post by lisati on 2008-06-19
> **__hj__ said:**
> How to see if the card is turned on.

Some cards have an LED that glows when the card is on. On my laptop (**not** a Dell) it's on the right. next to a switch that can turn wireless on and off.

---

### Post by Mav7rick on 2008-06-19
I have the same problem, when i turn the card on, only the bluetooth light glows. This is my card information > Atheros Communications Inc. AR5418 802.11abgn Wireless PCI Express Adapter
I tried to follow this guide [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) but after i downloaded the windows driver files for my wireless adapter, i couldn't open or unpack it

---

### Post by __hj__ on 2008-06-19
I finally made it work, I don't know how but I think it actually was [http://ubuntuforums.org/showthread.php?t=769990](http://ubuntuforums.org/showthread.php?t=769990) that made it work anyway...

---

### Post by chili555 on 2008-06-19
@Mav7rick-

I suggest you start a new thread and make the title something similar to, "How do I extract .inf and .sys?"

We will be glad to help.

---

