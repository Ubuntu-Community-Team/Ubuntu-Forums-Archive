---
title: "wired connection doesn't work after ubuntu reinstall"
date: 2013-09-14
forum: Networking &amp; Wireless
---

### Post by Marchello_Lippi on 2013-09-14
Hi all, 

my wired connection doesn't work after ubuntu reinstall. 
It is great that my pc has also wi-fi card. 
So what details should I post here for you to help me restore wired connection? 
Thanks ahead.

Unity
Ubuntu 12.0.4 LTS

---

### Post by carl4926 on 2013-09-14
```
lspci -nnk | grep -iA2 net
```Result of this

---

### Post by Marchello_Lippi on 2013-09-14
user@pc:~$ lspci -nnk | grep -iA2 net
00:07.0 Bridge [0680]: NVIDIA Corporation MCP61 Ethernet [10de:03ef] (rev a2)
        Subsystem: Gigabyte Technology Co., Ltd Device [1458:e000]
        Kernel driver in use: forcedeth
--
01:07.0 Network controller [0280]: Ralink corp. RT2561/RT61 802.11g PCI [1814:0301]
        Subsystem: ASUSTeK Computer Inc. Device [1043:837e]
        Kernel driver in use: rt61pci

---

### Post by carl4926 on 2013-09-14
> **Marchello_Lippi said:**
> user@pc:~$ lspci -nnk | grep -iA2 net
00:07.0 Bridge [0680]: NVIDIA Corporation MCP61 Ethernet [10de:03ef] (rev a2)
        Subsystem: Gigabyte Technology Co., Ltd Device [1458:e000]
        Kernel driver in use: forcedeth
--
01:07.0 Network controller [0280]: Ralink corp. RT2561/RT61 802.11g PCI [1814:0301]
        Subsystem: ASUSTeK Computer Inc. Device [1043:837e]
        Kernel driver in use: rt61pci

It looks OK
Does it work from the Live session?
And if yes, what is the result of the same code?

---

### Post by Marchello_Lippi on 2013-09-14
[**[COLOR=#DD4814][B]carl4926**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=809261"),

I'm sorry for stupid question, but what is ``Live session`` ? 
Do you mean ``what if I load from live cd`` ?

---

### Post by carl4926 on 2013-09-14
> **Marchello_Lippi said:**
> [**[COLOR=#DD4814][B]carl4926**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=809261"),

I'm sorry for stupid question, but what is ``Live session`` ? 
Do you mean ``what if I load from live cd`` ?

Yes
I mean if you load the live CD, does wired work? And if yes, what is the output of that code?

---

### Post by Bucky Ball on 2013-09-14
*Thread moved to **Networking & Wireless**.*

Unsure why this was posted in ***Absolute Beginners***. :-k

---

### Post by Marchello_Lippi on 2013-09-18
I'm sorry, it works now after I've added mac address at router. Don't know why this mac was absent if I didn't change my network card.

---

### Post by carl4926 on 2013-09-18
> **Marchello_Lippi said:**
> I'm sorry, it works now after I've added mac address at router. Don't know why this mac was absent if I didn't change my network card.

If you permit connection by MAC, you have to manually set this up
So does someone else have access to the router? And is wireless set to use WPA?

---

### Post by Marchello_Lippi on 2013-09-18
[COLOR=#DD4814][carl4926]("http://ubuntuforums.org/member.php?u=809261"),[/COLOR]

Yes, wireless is set to use WPA. 
No, nobody else has access to router. 
I think that changes was made by me during sleepless night, so I just don't remember it. 
I'm looking for some kind of ``concentration-improvement course`` already ;) 
Thanks for your attention.

---

