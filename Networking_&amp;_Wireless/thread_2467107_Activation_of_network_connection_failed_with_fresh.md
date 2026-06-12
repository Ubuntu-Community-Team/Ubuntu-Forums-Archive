---
title: "Activation of network connection failed with fresh 20.04.3 install"
date: 2021-09-16
forum: Networking &amp; Wireless
---

### Post by woshialex on 2021-09-16
tried ubuntu with the live usb and I run into the same issue.

I installed windows 10 on the computer, and If I boot to windows the network works fine.

tried all solutions on line in the past two days, no one worked.

My desktop computer only have wired connection.

product: Killer E2400 Gigabit Ethernet Controller
logical name: enp5s0
size: 1Gibt/s
capacity: 1Git/s
width: 64bits
...

Any idea on what could be done? I remember I installed 16.04 on this computer before and it worked with no problem.

Thanks very much

---

### Post by chili555 on 2021-09-16
Please run and post:

```
sudo dmesg | grep enp
```

Thanks.

---

### Post by woshialex on 2021-09-16
Thanks so much!
with the command dmesg, I see the error 
[FONT=var(--ff-mono)]enp5s0: fatal interrupt 0x200, resetting

[/FONT][FONT=var(--ff-mono)]and then based on this error message I found the solution on this page:
[/FONT]https://askubuntu.com/questions/853881/killer-ethernet-e2400-not-connecting-16-04
[FONT=var(--ff-mono)]basically disable iommu (internet is back) and then set iommu to soft in grub (usb is back)

[/FONT]
> **chili555 said:**
> Please run and post:

```
sudo dmesg | grep enp
```

Thanks.

---

