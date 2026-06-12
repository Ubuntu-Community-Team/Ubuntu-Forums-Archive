---
title: "Realtek RTL8101E"
date: 2013-09-08
forum: Networking &amp; Wireless
---

### Post by fugue2 on 2013-09-08
I am a newbie to Linux and Ubuntu. I just replaced the clumsy Win8 by Ubuntu from my new HP laptop. But the wireless connection on Ubuntu is extremely weak/unstable. Even if I stay within 3 meters from my router, the wireless connection is still weak and get disconnected easily.

I have followed some solutions that I found online, such as turning of the wlan power manager or updating the driver (my network card is RTL8101E). But none of them works.

Can someone please kindly tell me what to do with that? Thanks!!!

---

### Post by carl4926 on 2013-09-08
Post the output of

```
[COLOR=#000000][FONT=Droid Sans]lspci -nnk | grep -iA2 net[/FONT][/COLOR]
```

---

### Post by fugue2 on 2013-09-08
> **carl4926 said:**
> Post the output of

```
[COLOR=#000000][FONT=Droid Sans]lspci -nnk | grep -iA2 net[/FONT][/COLOR]
```



Thansk so much for your reply. The output is:

```

01:00.0 Network controller [0280]: Ralink corp. Device [1814:539b]
    Subsystem: Hewlett-Packard Company Device [103c:18ed]
    Kernel driver in use: rt2800pci
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:1843]
    Kernel driver in use: r8169

```

---

### Post by carl4926 on 2013-09-08
This your wireless
```
[COLOR=#000000][FONT=Ubuntu Mono]01:00.0 Network controller [0280]: Ralink corp. Device [1814:539b][/FONT][/COLOR]    Subsystem: Hewlett-Packard Company Device [103c:18ed] [COLOR=#000000][FONT=Ubuntu Mono]    Kernel driver in use: rt2800pci[/FONT][/COLOR]
```
The driver is in place. Install rfkill

Then post result of

```
sudo rfkill list
```

---

### Post by carl4926 on 2013-09-08
Also, what version of Ubuntu are you using
Check this thread
[http://ubuntuforums.org/showthread.php?t=2083566&p=12356696#post12356696](http://ubuntuforums.org/showthread.php?t=2083566&p=12356696#post12356696)

---

### Post by fugue2 on 2013-09-08
> **carl4926 said:**
> Also, what version of Ubuntu are you using
Check this thread
[http://ubuntuforums.org/showthread.php?t=2083566&p=12356696#post12356696](http://ubuntuforums.org/showthread.php?t=2083566&p=12356696#post12356696)


Thanks for your reply again!! My version is 13.04 64bit.

The result after sudo rfkill list is

```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

---

### Post by carl4926 on 2013-09-08
Not sure what to suggest

---

