---
title: "Broadcom NetXtreme II (BCM5709) doesn't work?"
date: 2020-06-29
forum: Networking &amp; Wireless
---

### Post by alsadk10 on 2020-06-29
Hey all,

Has anyone else run into this, or have any suggestions on what to try in order to fix it?

I have Dell Power Edge Gigabit Ethernet Card which uses the Broadcom NetXtreme II BCM5709 chip.

lspci shows that the card is there:

Ethernet controller: Broadcom Corporation NetXtreme II BCM5709 Gigabit Ethernet 

But it never shows up in ifconfig or ip a as a device I can configure.

I searched online and found an old driver, but I have ubuntu 16.04 LTS, is there any new driver compatible with BCM5709? Hence, I do not have internet connection only a loopback interface.

I'd really appreciate any suggestions.

Thanks,
Sadek

server specs:
Ubuntu Server Edition 16.04 
Dell Power Edge R710

---

### Post by LHammonds on 2020-06-29
I installed Ubuntu Server 16.04 LTS on a Dell PowerEdge 2950 back in the day and did not have any issues.  The NIC should have been a [FONT=sans-serif]Broadcom[/FONT][FONT=sans-serif] NetXtreme II[/FONT][FONT=sans-serif] 5708 Gigabit[/FONT][FONT=sans-serif][/FONT][FONT=sans-serif] Ethernet.

LHammonds
[/FONT]

---

### Post by alsadk10 on 2020-06-29
The thing is I am installed EVE-NG which is emulation tool based on ubuntu, so it's not clean ubuntu, and now I have no internet connection si I can not update the system or anything, maybe there is a driver of a newer Broadcom chip that is compatible with BCM5709 but I do not know it!!

> **LHammonds said:**
> I installed Ubuntu Server 16.04 LTS on a Dell PowerEdge 2950 back in the day and did not have any issues.  The NIC should have been a [FONT=sans-serif]Broadcom[/FONT][FONT=sans-serif] NetXtreme II[/FONT][FONT=sans-serif] 5708 Gigabit[/FONT][FONT=sans-serif][/FONT][FONT=sans-serif] Ethernet.

LHammonds
[/FONT]

---

### Post by LHammonds on 2020-06-30
Ubuntu proper always worked for me regarding the physical servers I installed them on so I don't know the process of fixing broken / missing drivers.

You might want to ask this question on [their forum](https://www.eve-ng.net/forum/viewforum.php?f=5) as well.

Also, 3.0.1-16 (June 25th) is based on Ubuntu 18, not 16.  Are you installing an older version?

LHammonds

---

### Post by alsadk10 on 2020-07-02
The Ubuntu release is 16.04.3 LTS 
uname -a command output is Linux EVE-NG 4.4.0
I am installing the latest free EVE community edition

> **LHammonds said:**
> Ubuntu proper always worked for me regarding the physical servers I installed them on so I don't know the process of fixing broken / missing drivers.

You might want to ask this question on [their forum](https://www.eve-ng.net/forum/viewforum.php?f=5) as well.

Also, 3.0.1-16 (June 25th) is based on Ubuntu 18, not 16.  Are you installing an older version?

LHammonds

---

### Post by slickymaster on 2020-07-02
Thread moved to **Networking & Wireless** for a better fit

---

### Post by alsadk10 on 2020-07-02
Thanks

> **slickymaster said:**
> Thread moved to **Networking & Wireless** for a better fit

---

### Post by alsadk10 on 2020-07-07
Up

---

### Post by chili555 on 2020-07-07
> lspci shows that the card is there:

Ethernet controller: Broadcom Corporation NetXtreme II BCM5709 Gigabit Ethernet
Details! We need details! Please run and post:

```
lspci -nnk | grep 0200 -A3
```

---

