---
title: "Wireless only works if turned on in Windows"
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by Chuchaqui on 2008-11-04
I have a strange problem that I haven't been able to find anything about on other threads. I dual boot Windows XP/Ubuntu 8.10. I had problems with 8.04 so I downgraded back to 7.10, but recently decided to start fresh with 8.10, and everything has been working fine accept my wireless.
There are two main problems:
[LIST]
[*]When I turn off my wireless card in Windows, and then boot into Ubuntu, I cannot see any wireless connections from NetworkManager.
[*]When I turn on my wireless card in Windows then boot into Linux, my wireless card sees wireless in NetworkManager but usually cannot connect to those connections. Also, on the occasion that I can connect to those connections, the connection will only remain for a short amount of time before dropping the connection and usually not able to connect any more.
[/LIST]
I cannot seem to find the program that displays hardware information -.-, but I know that I use a sort of BCM43xx series of wireless card. I have to use third-party drivers for my wireless card to function properly. I have tried going to jocky-gtk (or 'System/Administration/Hardware Drivers' from the pannel) to see if there was any relevent information and I received a weird error/exception, but I'm not sure if it's related at all.

**editorial**
The exception was a timeout error from the python script it uses (from what I understood it connects to someplace). I think the server was down and works fine now.
The driver is said to be installed and active for me wireless card, which it usually is (back in the 7.10 days) and I've never had troubles with before outside of a couple things. It just says:
Broadcom B43 wireless driver
fwcutter is a tool which can extract firmware from various source files.It's written for BCM43xx driver files.
and it has a greenlight indicating that it's enabled.

---

### Post by jimv on 2008-11-04
Please post the output of:

lspci

---

### Post by Chuchaqui on 2008-11-04
```

...
03:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

```

---

### Post by Chuchaqui on 2008-11-10
bump... I would really like to use my wireless. Plugging in at school is a real pain in the butt.

---

