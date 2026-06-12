---
title: "Qualcomm Atheros QCA8172 Not network traffic is showed"
date: 2014-06-20
forum: Networking &amp; Wireless
---

### Post by waffen on 2014-06-20
Hello

I just buy a new Lenovo Ideapad S410p with this ethernet card:

```

mario@mario-IdeaPad-S410p:~$ lspci -nn | grep 0200
03:00.0 Ethernet controller [0200]: Qualcomm Atheros QCA8172 Fast Ethernet [1969:10a0] (rev 10)

```

Any tool I used for check the traffic on it show me zero in both up/down traffic. And this happen ONLY with the ETH0 interface, with the wireles card (another Qualcom Atheros) the traffic is showed, I search in google with no lucky, any idea about how to fix it?

---

### Post by waffen on 2014-06-28
Any help here?

---

### Post by The-Valk on 2014-07-02
> **waffen said:**
> Any help here?

I have a Qualcomm Atheros AR8161 Gigabit Ethernet (rev 10) on Ubuntu 1404.
I use conky to show network traffic and found that it doesn't work properly with kernel 3.13 that is used with 1404.
I am informed that the driver included with that kernel had some code missed from it which would be corrected with kernel 3.15.
I live in the hope that 3.15 will be added to Ubuntu Trusty Tahr soon or I may have to swap distros yet again.

Hope that helps.

---

### Post by waffen on 2014-07-02
Hi,
yes I can confirm the same, looking into the internet I can found some info about the previous developer delete the code for generating statistics, it will be updated in the kernel 3.15, so we need to wait for it or change distro like you said.

---

