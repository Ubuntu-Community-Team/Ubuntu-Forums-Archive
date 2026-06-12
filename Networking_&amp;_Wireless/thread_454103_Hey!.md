---
title: "Hey!"
date: 2007-05-25
forum: Networking &amp; Wireless
---

### Post by uranous on 2007-05-25
Hey, I am completely new to linux (installed ubuntu v.7.04 yesterday 24.05)
and I need some help. I've been reading the other posts in the forum, but even though ppl say they are new to linux it seems like the know much more than me, so i couldn't find help in an easy for me to understand way :( . I installed ubuntu on my laptop (HP AMD Athlon 64 Processor 3200+ 1.9GHz, 512 RAM) but I can't get connected on my wireless connection, it only works with a wire. I've a Realtek RTL8139/810x Family Fast Ethernet NIC card and a Broadcom 802.11b/g WLAN card and the router is a Linksys WRT54G Wireless - G Broadband Router. So could somebody pls tell if it is possible and step by step how to connect on my wireless network or where I can get some help??? Thnx :D

---

### Post by spin2cool on 2007-05-25
A good place to start woule be searching these forums for your ethernet card model.

Another search term you might try is 'ndiswrapper'

---

### Post by uranous on 2007-05-25
Thnx for the reply, i read a little but it didn't help!
I found that:

```
03:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
```

```
03:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Hewlett-Packard Company Unknown device 3085
        Flags: bus master, medium devsel, latency 128, IRQ 20
        I/O ports at a000 [size=256]
        Memory at b020a400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

```  

But still don't know what the problem is an what to do...:(

P.S. I installed wifi-radar but it doesn't find any networks

---

### Post by uranous on 2007-05-26
So? Anybody who wants and can help me??? :)

---

### Post by chili555 on 2007-05-26
This is the easy way; it works for many people. Ndiswrapper, for which you can search this forum, is another way.

[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

---

### Post by ugm6hr on 2007-05-26
Someone else has just solved this:
[http://ubuntuforums.org/showthread.php?t=455160](http://ubuntuforums.org/showthread.php?t=455160)

Final entry leads to solution:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Ndiswrapper_for_Broadcom_43xx_wireless_chipset](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Ndiswrapper_for_Broadcom_43xx_wireless_chipset)

---

### Post by uranous on 2007-05-26
Well thnx, but as a noob i am, i don't get the ''Open a terminal window and **navigate** to the directory where you extracted the *.fw files.'' thing :P Could you pls help me with that? 
Thnx in advice :)

---

### Post by uranous on 2007-05-26
> **uranous said:**
> Well thnx, but as a noob i am, i don't get the ''Open a terminal window and **navigate** to the directory where you extracted the *.fw files.'' thing :P Could you pls help me with that? 
Thnx in advice :)
Ok, i found it... it is just to type cd ~/And/The/Directory ... :)

---

### Post by uranous on 2007-05-26
> **chili555 said:**
> This is the easy way; it works for many people. Ndiswrapper, for which you can search this forum, is another way.

[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

It WORKED!!!! Man i am so glad now :D:D:D:D:D 
With such help even a noob like me can use linux ;)

---

