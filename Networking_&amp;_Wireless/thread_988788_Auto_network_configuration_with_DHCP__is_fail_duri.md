---
title: "Auto network configuration with DHCP  is fail during installation. How to solve?"
date: 2008-11-20
forum: Networking &amp; Wireless
---

### Post by asaren on 2008-11-20
Hi,

During Ubuntu installation, auto network configuration with DHCP is fail (LAN).

I've tried to install with another same spec computer, it works fine. But only this computer won't work. I have checked the CD is no defect. 

Where should i look to solve this problem?

Thank you

---

### Post by Iowan on 2008-11-20
It's possible that the interface card isn't recognized. You didn't specify wired or wireless, but **ifconfig -a ** should shed some light - as might **lspci** or **lshw -C network**.  If it's wireless, **iwconfig** might be useful.  Much of this information should affect contents of /**etc/network/interfaces** file, so check there, too.

That should do for starters...

---

### Post by asaren on 2008-11-20
> **Iowan said:**
> It's possible that the interface card isn't recognized. You didn't specify wired or wireless, but **ifconfig -a ** should shed some light - as might **lspci** or **lshw -C network**.  If it's wireless, **iwconfig** might be useful.  Much of this information should affect contents of /**etc/network/interfaces** file, so check there, too.

That should do for starters...

It's Wired. Sorry didnt mention before. Thank you

---

### Post by superprash2003 on 2008-11-21
so you are saying that you cannot install ubuntu because of this network issue?? post output of ifconfig from terminal

---

### Post by asaren on 2008-11-22
> **superprash2003 said:**
> so you are saying that you cannot install ubuntu because of this network issue?? post output of ifconfig from terminal

Install Ubuntu is fine.
I meant the computer couldn't find the network.

---

### Post by superprash2003 on 2008-11-24
does tatic ip work fine?? post outpt of cat /etc/network/interfaces and output of ifconfig

---

