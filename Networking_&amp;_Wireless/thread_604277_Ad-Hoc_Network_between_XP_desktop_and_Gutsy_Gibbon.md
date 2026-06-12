---
title: "Ad-Hoc Network between XP desktop and Gutsy Gibbon Laptop"
date: 2007-11-05
forum: Networking &amp; Wireless
---

### Post by Moey on 2007-11-05
Hello All,

I just recently got a laptop (Acer Aspire 5315 ($348 bucks from Walmart Sale)) and naturally the first thing I did to speed it up was reformat to get rid of vista and get ubuntu running.  I was able to get past well knows problems of this laptop of the wireless card not working and the sound not working.  But now I have stumbled across a new problem.

On my desktop (running xp) I have a wired internet connection, and I also have a Wireless card that I have an Ad-Hoc network setup on.  I have tested this network with another computer that is running xp, and they are able to connect to the internet through this wireless connection.

The problem is with my laptop (running Gutsy Gibbon).  It will connect perfectly to my Ad-Hoc network (signal strength at 95%) the internet wont work.  

Any help would be greatly appricated!

Also I am not too good with commands in terminal, so simply instructions please.

---

### Post by gsiliceo on 2007-11-06
Try giving it a static ip.

---

### Post by Moey on 2007-11-06
Yes, I have tried that too.

Today I tried bringing my Laptop to class with me to see if it could wirelessly connect to my schools network.  And it didnt have any luck with that either.  So I am back to square one.  My wireless doesnt work.  I have attempted the fix for this wireless card and its still not working.  

Here is what it spits out when i type in "lspci"
```

06:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
        Subsystem: AMBIT Microsystem Corp. Unknown device 0428
        Flags: bus master, fast devsel, latency 0, IRQ 19
        Memory at 54100000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

```

---

### Post by spd106 on 2007-11-06
Make sure that you've switched it into ad-hoc mode before you try to connect. This procedure is different on Atheros cards that use the Madwifi driver.

See this help page for more [https://help.ubuntu.com/community/WifiDocs/Adhoc](https://help.ubuntu.com/community/WifiDocs/Adhoc)

---

