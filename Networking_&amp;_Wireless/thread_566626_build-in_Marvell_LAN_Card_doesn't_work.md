---
title: "build-in Marvell LAN Card doesn't work"
date: 2007-10-03
forum: Networking &amp; Wireless
---

### Post by iAmNewbee on 2007-10-03
I'm trying to setup my home network. The LG R400 laptop has a build-in network card called

Marvel Yukon 88E8039.

Unfortunately when I go to the Network-Settings it cannot detect the card. It even doesn't have a button 'Add' for adding a new network interface.

So I followed the tips in this thread: [http://ubuntuforums.org/showthread.php?t=75292](http://ubuntuforums.org/showthread.php?t=75292).

I tried using NDISwrapper. It installed a driver for Win XP, that I found in internet. The driver inf-file was called: yk60x86.inf

But network-settings still doesn't show the eth0 interface!

What's wrong with me? 

Here is the relevant part of the output of lspci:

```
...
0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd.: Unknown device 4353 (rev 15)
0000:05:00.0 Ethernet controller: Atheros Communications, Inc.: Unknown device 001c (rev 01)
...
```

---

### Post by noob12 on 2007-10-04
This should be covered in Feisty by the sky2 driver.   What release are you running?

---

### Post by iAmNewbee on 2007-10-04
> This should be covered in Feisty by the sky2 driver. What release are you running?

I am using Dapper Drake

---

### Post by noob12 on 2007-10-04
If this is a new installation, and you don't have any LTS requirement, then you might want to consider going to Feisty.  It will work out-of-box for this chipset.

If you really must use Dapper, you might find people that can help you on that thread you referenced.

---

